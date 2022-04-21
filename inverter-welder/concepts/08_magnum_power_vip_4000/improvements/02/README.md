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

## Próba (symulacja) z potencjometrem podłączonym do pinu 8 układu SG3525

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

 | Nastawa potencjometru [h] | Napięcie wyjściowe przy rozłączonej żarówce [V] | Napięcie wyjściowe przy załączonej żarówce [V]| Napięcie na potencjometrze [V]|
 |---|---|---|--|
 | max | 61.9 | 60.4 | 3.6 |
 |  15 | 61.4 | 59.5 | 3.1 |
 |  12 | 59.8 | 53.7 | 1.8 [^2] |
 |   9 | 10.0 |  0.0 | 0.0 |
 | min | 10.0 |  0.0 | 0.0 |

Potencjometr okazuje się działać ale jednak nieliniowo. Bardzo łatwo jest zbić napięcie do wartości około 45V. Później
dalsza minimalna zmiana nastawy skutkuje szybkim spadkiem napięcia do 0V. Udało mi się uzyskać napięcie wyjściowe
35V a potencjometr był ustawiony wtedy na 27.5k (nastawa gdzieś pomiędzy godziną 10 a 11).

Widać, że regulacja napięcia biegu jałowego działa. Trzeba by wykonać próbę spawania. Aby polepszyć zakres
regulacyjny potencjometru, proponuję zamienić go na opornik około 22k połączony szeregowo z potencjometrem 
o wartości ok. 56k. Powinno być wtedy możliwe bardziej selektywne regulowanie napięcia biegu jałowego w zakresie ok. 25V-60V.
Warto by było przeprowadzić test ze zmniejszoną opornością obciążenia wstępnego (żarówki). W przeprowadzonym teście żarówka miała opór
ciut większy od 1k, być może warto by było zastosować tutaj jakiś rezystor dużej mocy o oporności np. 200 Ohm?

[^1]: Co by wskazywało, że opór podłączonej żarówki jest 1.22k
[^2]: Napięcie na potencjometrze jest jednocześnie napięciem na pinie 8 układu SG3525. Napięcie 1.8V generuje
sygnał PWM o wypełnieniu około 18%, co powinno generować napięcie 22V. Tymczasem multimetr wskazuje zawyżone napięcie 53.7V.
Być może oporność żarówki 1.22k jest jeszcze zbyt duża i wyjście spawarki nie jest dostatecznie szybko rozładowywane?

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