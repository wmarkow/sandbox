# Sztywność konstrukcji: kolumna
### 25 lipiec 2021

Kolumna jest wykonana z cienkiej rury i zamocowana jest do stopy za pomocą aluminiowego kołnierza. Z tego względu jest ona podatna
na ugięcia. W Internecie można znaleźć porady na temat ulepszenia kolumny:
 * zalanie jej zbrojonym betonem (https://youtu.be/tErg_9uDvoE?t=916)
 * zastąpienie jej grubszą kolumną (https://youtu.be/arZyzhOiV8U?t=211)
 

Ja natomiast zrobię coś innego: usztywnie kolumnę wciskając w nią grubszą stalową rurę. Ponadto ta grubsza stalowa rura
będzie od spodu zespawana z nowym stalowym kołnierzem. Oba kołnierze (ten nowy stalowy i stary aluminiowy) zostaną razem ze
sobą przykręcony do stopy. Zobaczymy czy taki zabieg usztywni kolumnę. 



Lista potrzebnych elementów na zdjęciu poniżej. Nowa stalowa rura ma średnicę zewnętrzną około 43mm i grubość ścianki 5mm.
Pasuje idealnie na lekki wcisk do orginalnej kolumny. Była trochę zardzewiała i musiałem ją oczyścić szlifierką. Kołnierz
stalowy wykonany z formatki okrągłej o grubości 5mm i średnicy 100mm. Większy otwór pośrodku wywiercony otwornicą o średnicy 44mm (nie bimetalową).
<p align="center">
  <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/bench-drill/column/column_1.jpg" width="60%" >
</p>

Tak wyglądają złożone ze sobą orginalna kolumna, rura i kołnierz stalowy. Wszystko skręcone śrubami M8. 
<p align="center">
  <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/bench-drill/column/column_2.jpg" width="60%" >
</p>

Zbliżenie na połączenie kołnierza i rury stalowej. Rury są na wcisk a kołnierze skręcone śrubami. Zaletą takiego 
rozwiązania jest to, że nowy kołnierz i nowa rura są do siebie prostopadłe. Wystarczy tylko oczyścić spód rury i 
można ze sobą zespawać oba elementy.
<p align="center">
  <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/bench-drill/column/column_3.jpg" width="60%" >
</p>

Spawałem elektrodą 2.5mm przy prądzie nieco ponad 80A. Szło bardzo sprawnie. Spoinę trzeba było lekko po obwodzie
zeszlifować aby szło ładnie skręcić to ze stopą. Zdjęcia niestety nie zrobiłem.
Poniżej zespawane elementy przykręcone już do stopy. Należy jeszcze obciąć wystający element rury wzmacniającej.
<p align="center">
  <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/bench-drill/column/column_4.jpg" width="60%" >
</p>

Po odcięciu nadmiarowego kawałka rury i wyszlifowaniu (po lewej stronie) otworu na śrubę mocującą gondoli.
<p align="center">
  <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/bench-drill/column/column_5.jpg" width="60%" >
</p>

Po zamontowaniu z resztą wiertarki wykonałem pomiary odgięcia. Ponownie zbudowałem układ pomiarowy jak w 
[sztywność konstrukcji: stolik-kolumna](https://github.com/wmarkow/sandbox/tree/master/bench-drill/table-column/README.md)
a porównawczy wynik jest w poniżeszej tabelce:

| Siła nacisku na korbę [kG] | Odchylenie bez klocka [mm]| Odchylenie z klockiem [mm]| Odchylenie ze wzmocnioną stopą [mm]| Odchylenie ze wzmocnioną kolumną [mm] |
|---|---|---|---|---|
|  0 | -0.08 | -0.08 | | -0.05 |
|  1 |  0.00 |  0.00 | 0.00 | 0.00 |
|  2 |  0.18 |  0.06 | 0.12 | 0.04 |
|  3 |  0.45 |  0.21 | 0.24 | 0.11 |
|  4 |  0.72 |  0.38 | 0.35 | 0.18 |
|  5 |  0.95 |  0.58 | 0.46 | 0.26 |
|  6 |  1.18 |  0.73 | 0.58 | 0.33 |
|  7 |  1.40 |  0.86 | 0.70 | 0.42 |
|  8 |  1.61 |  1.07 | 0.79 | 0.48 |
|  9 |  1.86 |  1.17 | 0.85 | 0.56 |
| 10 |  2.03 |  1.23 | 0.91 | 0.63 |

Krótki komentarz do wyników:
 * przy zerowej sile nacisku wiertło nie naciskało porządnie na stolik. Wskazania czujnika lekko ujemne.
 * przy sile nacisku 1kG (waga wskazuje masę 1kg) wiertło zaczyna wywierać mały ale stabilny nacisk na stolik.
 Wskazanie zegara jest 0.00mm.
 * generalnie widać poprawę w całym zakresie badanego nacisku korby
 * przy sile nacisku 10kG odchylenie podpartego klockiem stolika ze wzmocnioną stopą wynosi ok. 0.6mm. Widać znaczną poprawę.
 * UWAGA: przed modyfikacją kolumny zostało wykonane [pomniejszenie luzu gilzy](https://github.com/wmarkow/sandbox/tree/master/bench-drill/backlash/README.md) Ciekawe czy ten zabieg ma tutaj znaczenie?
 * wydaje mi się, że sztywność kolumny można jeszcze poprawić. Obecnie jedna rura jest wciśnięta w drugą i razem są skręcone ze sobą tylko na dole.
 Może to mieć taki efekt, że pod wpływem dość dużej siły nacisku korby kolumna może się jeszcze wyginać i obie rury przemieszczają się lekko względem siebie.
 Gdyby tak ograniczyć im taką swobodę przemieszczania i na początek zespawać rury ze sobą na samej górze? Tam gdzie nasuwana jest gondola. Można by jeszcze
 usunąć ten aluminiowy kołnierz i zespawać rury ze sobą również na dole albo i spawarką zespawać je punktowo w kilku miejscach gdzieś pośrodku wysokości rury?
 Spawarką by trzeba było wytopić otwór w zewnętrznej rurze i potem zespawać (i napawać) w tym miejscu łączenie z grubszą rurą.

### Aktualizacja: 14 wrzesień 2021

Dokonałem modyfikacji opisanej w poprzednim akapicie. Mianowicie zespawałem ze sobą obie rury kolumny. Wszystkie elementy po rozłożeniu
przedstawiają się na zdjęciu poniżej:

<p align="center">
  <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/bench-drill/column/column_6.jpg" width="60%" >
</p>


Zdjęcie poniżej przedstawia wygląd kolumny po zespawaniu. Spoina łącząca została utworzona na dole przy kołnierzu oraz
na górze obu rur. Ponadto w trzech punktach na kolumnie (zaznaczone czerwonymi strzałkami) dokonałem punktowego zespawania
obu kolumn ze sobą zewnętrzna cienkościenna rura została "przepalona" elektrodą a następnie połączona z grubościenną rurą
wewnętrzną. Nadwyżka napawanego materiału została usunięta szlifierką. Te trzy dodatkowe punkty połączenia są w zmontowanej
kolumnie umiejscowione po stronie operatora maszyny, czyli z przodu kolumny. Byc może przydałyby sie takie punkty również
z tyłu kolumny.
Na zdjęciu przedstawiona jest jeszcze tuleja (zółta strzałka). Ona miała być wspawana na dole, bezpośrednio do kolumny i kołnierza.
Jej zadaniem miało byc polepszenie łączenia kolumny z kołnierzem. Niestety tuleja okazała się mieć zbyt grubą ścianę, co uniemożliwiałoby
przykręcenie kołnierza śrubami do stopy. Zrezygnowałem więc z tej tuleji.

<p align="center">
  <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/bench-drill/column/column_7.jpg" width="60%" >
</p>


Ponowne pomiary ugięcia przedsatwione w tabeli poniżej:

| Siła nacisku na korbę [kG] | Odchylenie bez klocka [mm]| Odchylenie z klockiem [mm]| Odchylenie ze wzmocnioną stopą [mm]| Odchylenie ze wzmocnioną kolumną [mm] | Odchylenie ze wzmocnioną kolumną (pospawane rury) [mm] |
|---|---|---|---|---|
|  0 | -0.08 | -0.08 |      | -0.05|      |
|  1 |  0.00 |  0.00 | 0.00 | 0.00 | 0.00 |
|  2 |  0.18 |  0.06 | 0.12 | 0.04 | 0.07 |
|  3 |  0.45 |  0.21 | 0.24 | 0.11 | 0.15 |
|  4 |  0.72 |  0.38 | 0.35 | 0.18 | 0.23 |
|  5 |  0.95 |  0.58 | 0.46 | 0.26 | 0.31 |
|  6 |  1.18 |  0.73 | 0.58 | 0.33 | 0.41 |
|  7 |  1.40 |  0.86 | 0.70 | 0.42 | 0.48 |
|  8 |  1.61 |  1.07 | 0.79 | 0.48 | 0.54 |
|  9 |  1.86 |  1.17 | 0.85 | 0.56 | 0.64 |
| 10 |  2.03 |  1.23 | 0.91 | 0.63 | 0.73 |

Krótki komentarz do wyników:
Przeprowadzone pomiary wskazują, że modyfikacja polegająca na zespawaniu ze sobą obu rur kolumny nie przyniosła żadnej poprawy.
Wręcz przeciwnie nawet pogarsza sprawę. Przecież dodatkowe usztywnienie nie powinno pogaraszać wyników. Wysuwam nastepujące
wniosku z tej obserwacji:
 * błędna lub niedoskonała metoda pomiarowa ze względu na konstrukcję układu pomiarowego. Za każdym razem układ pomiarowy
 jest demontowany i montowany na nowo wg rysunku z [sztywność konstrukcji: stolik-kolumna](https://github.com/wmarkow/sandbox/tree/master/bench-drill/table-column/README.md).
 Niedoskonałość w otworzeniu pierwotnego układu pomiarowego może mieć wpływ na wyniki pomiarów.
 *  niedoskonała metoda pomiarowa ze względu na dokładność pomiaru. Po prostu kolumna została już tak ulepszona, że lepiej nie będzie
 a wyniki leżą w marginesie błędu pomiarowego metody.
 * kolumna została tak ulepszona, że jej sztywność jest duża i zaczynają odginać się inne słabsze elementy konstrukcji prowadząc 
 do ogólnego pogorszenia parametrów
 
Po takim przedstawieniu problemu zacząłem obserwować całą konstrukcję wiertarki w poszukiwaniu kolejnych słabych punktów.
Po prostu naciskałem korbę i obserwowałem maszynę, poszukiwałem słabego miejsca, które się ugina. I znalazłem: stolik. Generalnie
stolik juz został wcześniej "ulepszony" poprzez podparcie klockiem drewnianym. Do pewnego momentu to pomagało ale widocznie jest już
niewystarczające. Zaobserwowałem, że podczas zadawania siły ugina się środek stolika, po prostu wgina się w dół, niejako "do środka".
Pomiarowy czujnik zegarowy jest zamontowany bezpośrednio do stolika, blisko jego środka, i ugina się on razem ze stolikiem. Trzeba przyjrzeć się konstrukcji stolika i wymyślić sposób na jej usztywnienie. 
