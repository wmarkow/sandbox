# 15.09.2021 Sztywność konstrukcji: pomiar odchylenia gondoli względem kolumny.

Postanowiłem sprawdzić o ile odchyla się sama gondola względem kolumny.

Układ pomiarowy przedstawiony jest na rysunku poniżej:

<p align="center">
  <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/bench-drill/07/test_setup.jpg" width="60%" >
</p>

Czujnik zegarowy jest zamocowany bezpośrednio do gondoli, na jej dolnej stronie, pomiędzy wrzecionem a kolumną.
Starałem się aby układ pomiary był jak najbardziej zbliżony do tego z [sztywność konstrukcji: stolik-kolumna](https://github.com/wmarkow/sandbox/tree/master/bench-drill/01/README.md).
Niestety nie da się zamontować czujnika w odległości 115mm od kolumny, w tym miejscu znajduje się wrzeciono wiertarki.
Czujnik jest zamontowany tylko 35mm od kolumny. Okazuje się, że nie wpływa to na wynik pomiarów i oba układy pomiarowe
są ze sobą porównywalne. Jeśli założyć, że podczas wywierania siły na korbę, odgina się tylko gondola względem kolumny
(sama kolumna się też co prawda odgina, ale zaniedbamy to zjawisko), to nie ma znaczenia jak daleko od kolumny jest zamontowany czujnik pomiarowy; bez względu
na tę odległość będzie on pokazywał to samo odchylenie. Wyjaśnienie na schemacie poniżej:

<p align="center">
  <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/bench-drill/07/schema.jpg" width="60%" >
</p>

Czujnik pomiarowy zamontowany jest w odległości **l** od gondoli. Gondola odchyla sie o kąt **α** a razem z nią
o ten sam kat odchyla się czujnik. Kąt **α** jest niezależny od odległości czunika pomiarowego od kolumny.
Ze wzorów na sinusy kąta **α** wynika, że czujnik pomiarowy będzie pokazywał takie same odchylenia **Δx** i **Δx1**
bez względu na swoją odległość od kolumny. Oczywiście przy założeniu, że kolumna i gondola są sztywne (czyli nie odgniają się same w sobie).

Wyniki pomiarów odchylenia znajdują się w poniższej tabeli:

| Siła nacisku na korbę [kG] | Odchylenie gondoli od kolumny [mm]|
|---|---|
|  0 |  |
|  1 | 0.00 |
|  2 | 0.02 |
|  3 | 0.04 |
|  4 | 0.06 |
|  5 | 0.08 |
|  6 | 0.11 |
|  7 | 0.12 |
|  8 | 0.15 |
|  9 | 0.18 |
| 10 | 0.22 |

Krótki komentarz do wyników:
 * przy zerowej sile nacisku wiertło nie naciskało porządnie na stolik. Wskazania zegara nie zapisałem.
 * przy sile nacisku 1kG (waga wskazuje masę 1kg) wiertło zaczyna wywierać mały ale stabilny nacisk na stolik.
 Wskazanie zegara jest 0.00mm.
 * przy sile nacisku 10kG odchylenie gondoli względem kolumny wynosi 0.22mm
 * pomiary wskazują, że można jeszcze coś poprawić w połączeniu między gondolą a kolumną. Jeśli udałoby się zniwelować ugięcie
 do zera, to wtedy wyniki z [Sztywność konstrukcji: kolumna część 2](https://github.com/wmarkow/sandbox/tree/master/bench-drill/06/README.md)
 uległy by poprawie o 0.22mm.
 
 
Myślę, że można by gondolę z kolumną wzmocnić za pomocą połączenia kołnierzowego:
 * do gondoli dospawany jest kołnierz w tym miejscu gdzie wchodzi do niej kolumna
 * do kolumny (na odpowiedniej wysokości) dospawany jest kołnierz
 * zakłada się gondolę na kolumnę, aż oba kołnierze się spotkają a nastepnie skręca się oba kołnierze śrubami


