# Przeróbka spawarki Magnum Power VIP4000 na MIG

## Istota problemu: obniżenie napięcia biegu jałowego i napięcia spawania

Interesującym pomysłem jest przerobienie spawarki elektrodowej (MMA) na spawarkę typu MIG/MAG. Sprawa nie jest prosta gdyż spawarka
elektrodowa cechuje się sterowaniem prądowym (automat pilnuje nastawy pradowej) podczas gdy spawarki MIG/MAG pilnują nastawy napięciowej.
Z drugiej strony sprawa nie jest aż tak tragiczna i została poruszona w kilku miejscach, zwłaszcza na forum elektroda.pl na przykład
tutaj:

 * [Spawarka inwertorowa jako źródło migomatu?](https://www.elektroda.pl/rtvforum/topic688745.html)
 * [Spawarka mig mag z inwertera czy da rade ? ](https://www.elektroda.pl/rtvforum/topic1481430.html)
 * [Nakładka MIG do spawarki inwertorowej?](https://www.elektroda.pl/rtvforum/topic2955459.html)
 * [Poszukuję chętnego do przerobienia spawarki inwertorowej](https://www.elektroda.pl/rtvforum/topic2409633.html)
 * [dedra 200 przeróbka na miga czy możliwe jest zastosowanie te](https://www.elektroda.pl/rtvforum/topic959926.html)
 * [Przeróbka spawarki inwertorowej MMA na MIG-MAG](https://forum.elportal.pl/viewtopic.php?t=13849)

Kilku użytkowników forum wskazuje, że można spróbować podłączyć palnik MIG wraz z podajnikiem drutu bezpośrednio
do wyjścia spawarki elektrodowej i po prostu spróbować. Nie zawsze kończy się to sukcesem. Problemem okazuje się
również zbyt wysokie napięcie biegu jałowego w spawarkach elektrodowych, które mieści się w granicach 60-70V (zależy od
modelu urządzenia).
Tak wysokie napięcie powoduje szybkie upalanie się drutu spawalniczego, zwłaszcza w początkowej fazie spawania,
gdzie mechanizm regulacji prądowej nie zdążył jeszcze zareagować (regulacja prądu wyjsciowego odbywa sie na zasadzie
obniżenia napięcia wyjściowego: im niższe napięcie wyjsciowe tym mniejszy prąd na wyjsciu) i przez krótki moment do
drutu spawalniczego podłączone jest wysokie napięcie jałowe.
Sam dokonałem takiej próby: podłączyłem prowizoryczny palnik MIG typu SpoolGun (zbudowany na szybko tylko w celu wykonania doświadczenia).
Rzeczywiście, przy próbie spawania końcówka drutu bardzo szybko się rozgrzewa do czerwoności i upala się przy końcówce prądowej
palnika. Następuje wtedy stan rozwarcia, spawarka wykrywa brak przepływu prądu (bo drut nie styka się już
z materiałem spawanym) i przechodzi w tryb biegu jałowego, gdzie napięcie na wyjściu znów jest wysokie w ok. 60-70V. Po pewnej
chwili stale wysuwający się drut ponownie dotyka materiału spawanego, zaczyna przepływać prąd, drut się rozgrzewa (wysokie napięcie
jałowe), być może przez chwilę automat ogranicza na moment napięcie wyjsciowe by ustalić przepływ ustalonego prądu, ale często
jest już za późno, gdyż drut ponownie się upala przy końcówce prądowej, i cykl się powtarza. Generalnie nie idzie spawać.
Często się zdarza, że drut stapia się z końcówką prądową. Przestaje wtedy działać posów drutu a końcówka prądowa nadaje się
najczęściej do wymiany.

## Symulacja regulacji napięcia: układ z potencjometrem podłączonym do pinu 8 układu SG3525

Zainspirowany różnymi amatorskimi konstrukcjami spawarek MMA/MIG/MAG w szczególności [Invertor popis](https://github.com/wmarkow/sandbox/blob/master/inverter-welder/concepts/09_mma_mig_mag/invertor_popis.pdf),
postanowiłem podjąć kroki by mimo wszystko spróbować dokonać przeróbki spawarki elektrodowej inwertorowej na MIG/MAG. Moja spawarka **Magnum Power VIP 4000** jest
oparta o układ scalony **SG3525**. Po przejrzeniu [noty katalogowej](https://github.com/wmarkow/sandbox/blob/master/inverter-welder/elements/sg3525/SG1525.pdf) postanowiłem [zbadać jego zachowanie](https://github.com/wmarkow/sandbox/blob/master/inverter-welder/elements/sg3525/tests/README.md) w różnych układach konfiguracyjnych.
W kontekście obniżenia napięcia biegu jałowego szczególnie interesujący jest [Test 4: limit PWM duty cycle with Soft-Start pin](https://github.com/wmarkow/sandbox/blob/master/inverter-welder/elements/sg3525/tests/Test4/README.md),
gdzie wykorzystany został Pin 8 układu (tzw. Soft Start) do ograniczenia przebiegu PWM na wyjściu układu. To rozwiązanie jest godne uwagi ze względu na bezinwazyjność w układ sterowania spawarki; wystarczy wlutować jeden dodatkowy potencjometr. 

Schemat układu symulacji został przedstawiony na rysunku poniżej. Po lewej stronie znajduje się
orginalny układ spawarki: kondensator C32 i rezystor R40 podłączone do pinu 8 układu SG3525. Razem
z wewnetrznym źródłem prądowym 50uA realizują one układ tzw. "miękkiego startu". Dopóki napięcie
na pinie 8 jest mniejsze od 0.9V, dopóty ukłąd generuje sygnały PWM o wypełnieniu 0%. Gdy napięcie
jest wyższe od 3.3V to ukad generuje sygnały o wypełnieniu 49%. Poziomy napięć pomiędzy 0.9V a 3.3V
generują sygnały PWM o wypełnieniu od 0% do 49%. Tak rzecze dokumentacja układu SG3525. Po włączeniu
zasilania układ "miękkiego startu" powoli rozkręca układ do generacji maksymalnego wypełnienia.
Dodatkowym potencjometrem (schemat po prawej) można ustalić w miarę dowolne napięcie na pinie 8, 
co pozwoli z góry ograniczyć napięcie na biegu jałowym lub spawania. 

<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/concepts/08_magnum_power_vip_4000/improvements/02/pin8_potentiometer_sim_sch.png" width="75%" >

Symulacja pokazuje wpływ takiego rozwiązania na układ "miękkiego
startu". Wykres napięć w obu przypadkach (bez modyfikcji kolor zielony i z modyfikacją kolor niebieski) poniżej:

<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/concepts/08_magnum_power_vip_4000/improvements/02/pin8_potentiometer_sim_result.png" width="75%" >

pokazuje, że modyfikacja spowalnia rozruch urządzenia prawie dwukrotnie (na maksymalnym ustawieniu potencjometru):
* bez modyfikacji układ osiąga PWM 49% (napięcie 3.3V) po około 45ms. Kondensator ładuje się liniowo ze źródła prądowego.
* z modyfikacją układ osiąga PWM 49% (napięcie 3.3V) po około 75ms. Ponadto obecność potencjometru zmienia charakterystykę ładowania
kondensatora z liniowej na wykładniczą.

Wydaje mi się, że takie spowolnienie nie ma negatywnego wpływu na pracę urządzenia. Gorzej by było,
gdyby modyfikacja przyspieszyła rozruch.


## Próba z potencjometrem podłączonym do pinu 8 układu SG3525

Zmontowany układ pomiarowy wygląda tak:

<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/concepts/08_magnum_power_vip_4000/improvements/02/setup.jpg" width="75%" >

Na zdjęciu widać podlutowany odpowiednio potencjometr (wartość 88k zmierzona miernikiem), zaciski prądowe, multimetr i ... podłączoną do zacisków żarówkę.
Żarówka wstępnie obciąża układ względnie niską rezystancją. Występuje na niej napięcie ok 61V i przepływa
przez nią prąd ok 50mA (przy potencjometrze ustawionym na wartość maksymalną) [^1]. Bez tej żarówki napięcie wyjściowe na zaciskach jest mniej więcej stałe i wynosi około
62V bez wględu na wartość nastawy potencjometru. Innymi słowy wartość wypełnienia generowanego sygnału PWM się zmienia, ale napięcie
na wyjściu **wskazywane multimetrem** (to jest ważne) jest stałe. Okazuje się, że spawarka w obwodzie wyjściowym
ma kondensatory, które są ładowane ze źródła. Wyjście spawarki jest już "wstępnie obciążone" dzielnikiem
rezystancyjnym (o wartości 23.4k) służącym do pomiaru napięcia wyjściowego i wykrywania stanu zwarcia elektrody.
Ten dzielnik rezystancyjny powoduje powolne rozładowanie kondensatorów wyjściowych, dlatego napięcie wskazywane
przez multimer jest mniej więcej stałe bez względu na wartość wypełnienia sygnału PWM; napięcie zauważalnie maleje dopiero przy niskich
wypełnieniach PWM. Podłączona żarówka ma za zadanie wstępnie obciążyć układ małą rezystancją (małą w porównaniu
z dzielnikiem napięcia ale wysoką od rezystancji łuku spawalniczego), co spowoduje szybsze rozładowanie kondensatorów i multimetr "zauważy" spadek napięcia
wyjściowego.
  
Nastawę potencjometru określiłem sobie w godzinach, zgodną z tarczą wskazówek zegarka, jak na zdjęciu poniżej:

<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/concepts/08_magnum_power_vip_4000/improvements/02/potentiometer.jpg" width="25%" >

Wyniki pomiarów znajdują się w tabelce poniżej:

 | Nastawa potencjometru [h] | Zmierzone napięcie wyjściowe przy rozłączonej żarówce [V] | Zmierzone napięcie wyjściowe przy załączonej żarówce [V]| Zmierzone napięcie na potencjometrze [V]| Zmierzona oporność na potencjometrze [kOhm]| Obliczony PWM [%]| Obliczone napięcie wyjściowe [V]|
 |---|---|---|---|---|---|---|
 |   max | 61.9 | 60.4 | 3.7 | 88.5 | 49 | 62 |
 |    15 | 61.4 | 59.5 | 3.1 | 74.6 | 45 | 57 |
 |    12 | 59.8 | 53.7 | 1.8 [^2] | 39.6 | 18 | 23 |
 |    11 | 59.7 | 52.4 | 1.5 | 34.0 | 12 | 15 |
 | 11/10 | 20.0 |  8.9 | 1.2 | 27.8 |  6 |  8 |
 |    10 | 10.0 |  0.0 | 0.9 | 19.9 |  0 |  0 |
 |     9 | 10.0 |  0.0 | 0.6 | 11.5 |  0 |  0 |
 |   min | 10.0 |  0.0 | 0.0 |  |  0 |  0 |

Potencjometr okazuje się działać ale jednak nieliniowo. Bardzo łatwo jest zbić napięcie do zmierzonej wartości około 45V. Później
dalsza minimalna zmiana nastawy skutkuje szybkim spadkiem napięcia do 0V. Udało mi się uzyskać zmierzone napięcie wyjściowe
35V a potencjometr był ustawiony wtedy na 27.5k (nastawa gdzieś pomiędzy godziną 10 a 11).

Nadmienię jeszcze raz fakt pomiaru napięcia multimetrem. Przy rozłączonej żarówce multimetr nie zauważa zbytniego spadku napięcia
wyjściowego. Jest to spowodowane obecnością dużej wstępnej rezystancji obciążającej (23.4k) układ i powodującej
powolne rozładowywanie kondensatorów wyjsciowych. Przy załączonej żarówce o oporności około nieco ponad 1k multimetr
łatwiej zauważa spadek napięcia wyjściowego. Jednak ten pomiar multimetrem równiez należy traktować tylko jako **pomiar
orientacyjny!** Prawdziwa wartość napięcia ujawnia się dopiero podczas procesu spawania, gdzie rezystancja obciążenia jest
na prawdę niska i prawie bliska rezystancji zwarciowej. Dlatego w tabelce powyżej zamieściłem kolumny pomocnicze:
* **PWM** zawierającą wyliczoną - na podstawie napięcia na pinie 8 układu SG3525 - wartośc wypełnienia genarowanych
sygnałów PWM. Wartość 49% oznacza generowanie maksymalnego napięcia (ok. 62V), wartość 0% oznacza minimalne
napięcie na wyjściu (ok 0V).
* **Obliczone napięcie wyjściowe** - wyznaczone na podstawie wartości wypełnienia **PWM**. Wartość tego napięcia
należałoby traktować jako wyrocznię, gdyż ta wartość ujawnia się podczas procesu spawania.

Widać, że regulacja napięcia biegu jałowego działa. Trzeba by wykonać próbę spawania. Aby polepszyć zakres
regulacyjny potencjometru, proponuję zamienić go na opornik około 33k połączony szeregowo z potencjometrem 
o wartości ok. 56k. Powinno być wtedy możliwe bardziej selektywne regulowanie napięcia biegu jałowego w zakresie ok. 15V-60V.
Warto by było przeprowadzić test ze zmniejszoną opornością obciążenia wstępnego (żarówki). W przeprowadzonym teście żarówka miała opór
ciut większy od 1k, być może warto by było zastosować tutaj jakiś rezystor dużej mocy o oporności np. 200 Ohm?

Ciekawostką jest fakt, że przy rozłączonej żarówce i napięciu na pinie 8 mniejszym od 0.9V, napięcie zmierzone na wyjściu spawarki jest 10V.
Dopiero przy załączonej żarówce spada do 0V.

## Pierwsze testowe spoiny

Na potrzeby testu zbudowałem prowizoryczny uchywt typu spool-gun:
<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/concepts/08_magnum_power_vip_4000/improvements/02/simple_spoolgun.jpg" width="75%" >

Jest bardzo nieporęczny ale daje radę podczas testów. W skład konstrukcji wchodzą:
* końcówka palnika wraz z końcówką prądową przymontowane taśmą do długiej na ok. 40cm pilśniowej listwy. Do tej końcówki bezpośrednio
jest "zapięty" uchwyt elektrodowy podłączony do zacisku masowego spawarki, gdyż spawanie odbywa się z użyciem drutu proszkowego, gdzie producent zaleca,
że drut musi być podpięty do zacisku masowego. 
* podajnik drutu zrobiony z silnika krokowego NEMA 17 i ekstrudera filamentu od drukarki 3D. Silnik krokowy zapewnia odpowiedni posuw drutu. Ekstruder posiada
koło zębate (założone bezpośrednio na wał silnika) oraz element dociskowy z małego łożyska. Generalnie okazuje się to działać poprawnie. Minusem rozwiązania
jest zbyt duża waga silnika zwiększająca ciężar całego uchwytu.
* szpulka z drutem założona bezpośrednio na wkręconą w pilśniowa listwę śrubę M8. Szpulka zabezpieczona jest przed wypadnięciem nakrętką M8.
* wyłącznik krańcowym służy jako włącznik podajnika drutu
* Arduino UNO wraz z "nakładką CNC" reaguje na naciśnięcie wyłącznika krańcowego i steruje wtedy silnikiem krokowym
* potencjometr zamontowany do "nakładki CNC" służący do regulacji szybkości posuwu drutu w zakresie od 0 do 200 cm/min. 

Pierwsze próby pięciu spoin na zdjęciach poniżej. Generalnie zaczynałem od minimalnej nastawy napięcia 35V (uwaga: wartość zmierzona multimetrem - traktować tylko orientacyjnie ze względu na niedostatecznie niską
rezystancję żarówki) i minimalnej nastway prądu 100A.
Prędkość wysuwu drutu szybko ustawiłem na 200cm/min, gdyż przy mniejszych wartościach wysuwu wychodziły tylko poprzerywane krople (z prawej strony
zdjęć). Próba numer 1 okazała się mieć za niskie napięcie lub za niski prąd. Przy próbce 2 już zwiększyłem nastawę prądu do 140A. Nastawy
napięcia niestety nie zanotowałem. Generalnie przy kolejnych próbach zacząłem zwiększać nastawy prądu i napięcia,
aż przy próbce numer 4 i 5 spoina zaczęła się wtapiać w materiał podstawowy. Z lewej strony nieudolnie wspawana nakrętka.

<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/concepts/08_magnum_power_vip_4000/improvements/02/welding_1a.jpg" width="75%" >
<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/concepts/08_magnum_power_vip_4000/improvements/02/welding_1b.jpg" width="75%" >


## Kolejne testowe spoiny

Po pierwszych próbach testowych ponownie obejrzałem filmik na Youtube [How NOT TO Weld: Most Common MIG Welding Mistakes](https://www.youtube.com/watch?v=Xod-ByrxHg4), 
objaśniający podstawowe typy błędów w spawaniu MIG. Skupiłem się na prędkości wysuwu drutu spawalniczego. Optymalną prędkością na filmiku była 200 cali/min (czyli ok 500 cm/min),
podczas gdy ja używałem tylko 200 cm/min. Zmodyfikowałem program Arduino i już pseudo spool-gun był gotowy do pracy z wysuwem drutu w zakresie 0-500 cm/min.
Zdjęcia spoin testowych poniżej:

<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/concepts/08_magnum_power_vip_4000/improvements/02/welding_2a.jpg" width="75%" >
<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/concepts/08_magnum_power_vip_4000/improvements/02/welding_2b.jpg" width="75%" >

Prąd spawania ustawiłem na 200A (maksymalna nastawa spawarki) a napięcie biegu jałowego ograniczone zostało potencjometrem
do poziomu 55V (uwaga: wartość zmierzona multimetrem - traktować tylko orientacyjnie ze względu na niedostatecznie niską
rezystancję żarówki). Obliczona wartość napięcia wyjściowego dla tej nastawy - według tabelki powyżej - byłaby około 30V. Tym razem spoiny wyglądaja dużo lepiej. Widać wtopienie w materiał podstawowy. Próby 1 i 2 szły bez problemu.
W próbie 3 postanowiłem zmniejszyć nastawę prądu do 100A i zacząłem odczuwać odpychanie uchwytu od materiału podstawowego.
Prawdopodobnie zbyt niski prąd nie nadążał topić drutu wysuwanego z tak dużą prędkością. Średnia długość spoin na zdjęciach
to około 3-4 cm. Funkcja anti-stick spawarki wydawała się nie mieć negatywnego wpływu na proces spawania; na razie nie widzę 
potrzeby rozłączania tego mechanizmu podczas spawania MIG.

## Symulacja regulacji napięcia: układ ze sprzężeniem zwrotnym podłączony do pinu 8 układu SG3525

Ciekawy układ regulacji napięcia wyjściowego został przytoczony w [tym poście na forum](https://www.elektroda.pl/rtvforum/viewtopic.php?p=19978221#19978221).
Schemat zaczerpnięty prawdopodobnie z rosyjskojęzycznej strony Internetu:

<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/concepts/08_magnum_power_vip_4000/improvements/02/pin8_loopback_original_sch.jpg" width="50%" >

Kilka słów wyjasnienia:
* zaciski K+ i K- to najprawdopodobniej zaciski wyjściowe spawarki
* potencjometr 10k służy do nastawy napięcia wyjściowego
* przełącznik MMA/MIG-MAG służy do przełączania sterownika w tryb MMA lub MIG-MAG
* przekaźnik na dole po lewej jest załączany przyciskiem w uchwycie MIG. W stanie normalnym przycisk nie jest wciśnięty
(nie ma spawania) i wyjście przekaźnika zwiera pin 8 układu SG3525 do masy i napięcie na wyjściu spawarki jest 0V. Po wciśnięciu
przycisku w uchwycie (rozpoczęcie procesu spawania) przekaźnik się załącza i odcina pin 8 od masy, następuje włączenie napięcia
spawania.
* optoizolator PC817 zapewnia izolację galwaniczna pomiędzy obwodem spawania a obwodem sterowania SG3525, a jednocześnie steruje
napięciem na pinie 8

Przygotowałem symulację tego układu w programie LTSpice. Schemat układu jest następujący:

<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/concepts/08_magnum_power_vip_4000/improvements/02/pin8_loopback_sim_sch.png" width="75%" >

Symulacja układu polega na wymuszonej zmianie napięcia spawania w zakresie od 0 do 60V i obserwacji jej wpływu na napięcie pinu 8.
Wynik symulacji przedstawia sie następująco:

<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/concepts/08_magnum_power_vip_4000/improvements/02/pin8_loopback_sim_result.png" width="75%" >

Analiza:
* potencjometr nastawy napięcia ustawiony w pozycji środkowej (nastawa na 30V)
* jeżeli napięcie spawania spadnie poniżej ok. 29V to napięcie na pinie 8 jest 5V, co spowoduje generowanie sygnałów
PWM o wypełnieniu 49% i wzrost napięcia wyjściowego w kierunku wartości maksymalnej 60V
* jeżeli napięcie spawania wzrośnie powyżej ok. 29V to napięcie na pinie 8 jest 0V, co spowoduje generowanie sygnałów
PWM o wypełnieniu 0% i spadek napięcia wyjściowego w kierunku wartości minimalnej 0V
* w układzie wystepuje sprzężenie zwrotne, które dąży do ustabilizowania napięcia na zadanym poziomie
* stabilizacja napięcia jest raczej dwustabilna: albo spawarka podaje napięcie maksymalne albo minimalne. Takie cykliczne
zmiany stabilizują napięcie wyjściowe na średnim zadanym poziomie. Nasuwa się pytanie czy taki dwustabilny tryb pracy jest
dobry dla procesu spawania lub spawarki. Można przecież wysterować pin 8 napięciem pośrednim (np. 2.5V) co wygeneruje
pośrednie napięcie spawania.
* na powyższym wykresie tego nie widać, ale regulacja napięcia wyjściowego jest w zakresie od 20 do 40V.

Powyższego układu nie testowałem w praktyce. Tylko zasymulowałem jego działanie.

## Ciekawostka:
* test z wyłączoną żarówką
  * wyłączyć spawarkę
  * upewnić się, że żarówka jest wykręcona
  * upewnić się, że potencjometr biegu jałowego jest ustawiony w pozycję maksymalną (czyli nie działa ograniczanie napięcia biegu jałowego)
  * włączyć spawarkę
  * zmierzyć miernikiem napięcie na zaciskach wyjściowych: u mnie było ono 61V
* test z włączoną żarówką
  * wyłączyć spawarkę
  * upewnić się, że żarówka jest wkręcona
  * upewnić się, że potencjometr biegu jałowego jest ustawiony w pozycję maksymalną (czyli nie działa ograniczanie napięcia biegu jałowego)
  * włączyć spawarkę
  * zmierzyć miernikiem napięcie na zaciskach wyjściowych: u mnie było ono 0V!
  * wykręcić żarówkę (żeby nie obciążać nią wyjścia spawarki)
  * wkręcić żarówkę ponownie
  * zmierzyć miernikiem napięcie na zaciskach wyjściowych: teraz było ono 61V!
 
Wygląda, jakby układ spawarki wykrywał, że podczas jej uruchomienia było podłączone jakieś obciążenie; w takim przypadku - prawdopodobnie - układ SG3225 jest w stanie
zamknięcia (odcięcia) i generuje on sygnał PWM o zerowym wypełnieniu. Być może jest to jakieś dodatkowe zabezpieczenie. W tym konkretnym przypadku, żadne diody sygnałowe
na panelu urządzenia nie były zapalone.

[^1]: Co by wskazywało, że opór podłączonej żarówki jest 1.22k
[^2]: Napięcie na potencjometrze jest jednocześnie napięciem na pinie 8 układu SG3525. Napięcie 1.8V generuje
sygnał PWM o wypełnieniu około 18%, co powinno generować napięcie 22V. Tymczasem multimetr wskazuje zawyżone napięcie 53.7V.
Być może oporność żarówki 1.22k jest jeszcze zbyt duża i wyjście spawarki nie jest dostatecznie szybko rozładowywane?
