# 07.04.2022 Przeróbka spawarki Magnum Power VIP4000 na MIG

## Obniżenie napięcia biegu jałowego

Interesującym pomysłem jest przerobienie spawarki elektrodowej (MMA) na spawarkę typu MIG/MAG. Sprawa nie jest prosta gdyż spawarka
elektrodowa cechuje się sterowaniem prądowym (automat pilnuje nastawy pradowej) podczas gdy spawarki MIG/MAG pilnują nastawy napięciowej.
Z drugiej strony sprawa nie jest aż tak tragiczna i została poruszona w kilku miejscach, zwłaszcza na forum elektroda.pl na przykład
tutaj:

[Spawarka inwertorowa jako źródło migomatu?](https://www.elektroda.pl/rtvforum/topic688745.html)

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

Zainspirowany różnymi amatorskimi konstrukcjami spawarek MMA/MIG/MAG w szczególności [Invertor popis](https://github.com/wmarkow/sandbox/blob/master/inverter-welder/concepts/09_mma_mig_mag/invertor_popis.pdf),
postanowiłem podjąć kroki by mimo wszystko spróbować dokonać przeróbki spawarki elektrodowej inwertorowej na MIG/MAG. Moja spawarka **Magnum Power VIP 4000** jest
oparta o układ scalony **SG3525**. Po przejrzeniu [noty katalogowej](https://github.com/wmarkow/sandbox/blob/master/inverter-welder/elements/sg3525/SG1525.pdf) postanowiłem [zbadać jego zachowanie](https://github.com/wmarkow/sandbox/blob/master/inverter-welder/elements/sg3525/tests/README.md) w różnych układach konfiguracyjnych.
W kontekście obniżenia napięcia biegu jałowego szczególnie interesujący jest [Test 4: limit PWM duty cycle with Soft-Start pin.](https://github.com/wmarkow/sandbox/blob/master/inverter-welder/elements/sg3525/tests/Test4/README.md),
gdzie wykorzystany został Pin 8 układu (tzw. Soft Start) do ograniczenia przebiegu PWM na wyjściu układu. To rozwiązanie jest godne uwagi ze względu na bezinwazyjność w układ sterowania spawarki; wystarczy wlutować jeden dodatkowy potencjometr. Pora sprawdzić to zastosowanie w praktyce.


Układ SG3525 generuje sygnał PWM nie tylko na podstawie pinów 1, 2, i 9 ale i także na podstawie pinu SoftStart. Układ posiada
wewnętrzny trójwejściowy komparator. Działa to na takiej zasadzie, że sygnał wejściowy o niższym napięciu ma wiekszy priorytet na
wartośc wypełnienia sygnału PWM. Pin 8 jest bezpośrednio podłączony do komparatora i mamy tutaj bardzo łatwą mozliwość
ograniczenia sygnału PWM na biegu jałowym. Generalnie wg producenta pin 8 służy do tzw. miękkiego startu urządzania
sterowanego za pomoca generowanego sygnału PWM. Chodzi o to, że po załączeniu zasilania nie od razu generowany jest 
sygnał PWM o wypełnieniu 50% tylko stopniowo narasta on do tejże wartości startując od zera. Wenątrz SG3525 do pinu 8
jest podłączone źródło prądowe o wartości 50uA. Spawarka wykorzystuje ten fakt w taki sposób, że z zewnątrz do pinu 8 
podłączony jest (poprzez rezystor z drugiej strony podłączony do masy) kondensator. Po włączeniu urządzenia napięcie na pinie 8 rosnie mniej więcej liniowo
od wartości 0V do ok. 5V. Przy 3.3V układ generuje już sygnały PWM o wypełnieniu 50%.
Pomysł jest taki, by do pinu 8 podłączyć jeszcze potencjometr liniowy o wartości 100k, za pomocą którego będzie można regulować
napięcie w zakresie od 0V do 5V (UWAGA: zbadać jaki jest wpływ na układ soft startu?).

Zmontowany układ pomiarowy wygląda tak:

<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/concepts/08_magnum_power_vip_4000/improvements/02/setup.jpg" width="75%" >

Na zdjęciu widać podlutowany odpowiednio potencjometr (wartość 88k zmierzona miernikiem), zaciski prądowe, multimetr i ... podłączoną do zacisków żarówkę.
Żarówka wstępnie obciąża układ względnie niską rezystancją. Występuje na niej napięcie ok 61V i przepływa
przez nią prąd ok 50mA (przy potencjometrze ustawionym na wartośc maksymalną). Bez tej żarówki napięcie wyjściowe na zaciskach jest mniej więcej stałe i wynosi około
60V bez wględu na wartość nastawy potencjometru. Innymi słowy wartość wypełnienia generowanego sygnału PWM się zmienia, ale napiecie
na wyjściu **wskazywane multimetrem** (to jest ważne) jest stałe. Okazuje się, że spawarka w obwodzie wyjściowym
ma kondensatory, które są ładowane ze źródła. Wyjście spawarki jest już "wstępnie obciążone" dzielnikiem
rezystancyjnym (o wartości kilku kiloomów) służącym do pomiaru napięcia wyjściowego i wykrywania stanu zwarcia elektrody.
Ten dzielnik rezystancyjny pwoduje powolne rozładowanie kondensatorów wyjściowych, dlatego napięcie wskazywane
przez multimer jest mniej więcej stałe bez względu na wartość ustawioną potencjometrem, a od pewnej nastwy potencjometru
po prostu spada do zera. Podłączona żarówka ma za zadanie wstępnie obciążyć układ małą rezystancją (małą w porównaniu
z dzielnikiem napięcia ale wysoką od rezystancji łuku spawalniczego), aby multimetr mógł "zauważyć" spadek napięcia
wyjściowego.
  
Nastawę potencjometru określiłem sobie w godzinach, zgodną z tarczą wskazówek zegarka, jak na zdjęciu poniżej:

<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/concepts/08_magnum_power_vip_4000/improvements/02/potentiometer.jpg" width="25%" >

Wyniki pomiarów znajdują się w tabelce poniżej:

 | Nastawa potencjometru [h] | Napięcie wyjściowe przy rozłączonej żarówce [V] | Napięcie wyjściowe przy załączonej żarówce [V]| Napięcie na potencjometrze [V]|
 |---|---|---|--|
 | max | 61.9 | 60.4 | 3.6 |
 |  15 | 61.4 | 59.5 | 3.1 |
 |  12 | 59.8 | 53.7 | 1.8 |
 |   9 | 10.0 |  0.0 | 0.0 |
 | min | 10.0 |  0.0 | 0.0 |

Potencjometr okazuje się działać ale jednak nieliniowo. Bardzo łatwo jest zbić napięcie do wartości około 45V. Później
dalsza minimalna zmiana nastawy skutkuje szybkim spadkiem napięcia do 0V. Udało mi się uzyskać napięcie wyjściowe
35V a potencjometr był ustawiony wtedy na 27.5k (nastawa gdzieś pomiędzy godziną 10 a 11).

Widać, że regulacją napięcia biegu jałowego działa. Trzeba by wykonać próbę spawania. Aby polepszyć zakres
regulacyjny potencjometru, proponuję zamienić go na opornik około 22k połączony szeregowo z potencjometrem 
o wartości ok. 56k. Powinno być wtedy możliwe bardziej selektywne regulowanie napięcia biegu jałowego w zakresie ok. 25V-60V.