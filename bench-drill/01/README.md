# 07.02.2021 Układ pomiarowy i pomiar początkowy.

Stolik jest raczej kiepsko wykonany. Łatwo się ugina. Wydaje się zasadnym, żeby podstawić pod niego jakiś kawałek drewnianego klocka.

Układ pomiarowy przedstawiony jest na rysunkach poniżej.

W wersji stolika bez podparcia:

<p align="center">
  <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/bench-drill/01/test_setup_1a.jpg" width="60%" >
</p>

i w wersji, gdzie stolik jest podparty sosnowym klockiem:

<p align="center">
  <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/bench-drill/01/test_setup_1b.jpg" width="60%" >
</p>

Czujnik zegarowy jest zamocowany do podstawy stolika, za wiertłem łopatkowym. Mierzy on odchylenie od kolumny.
Do korby posuwu zamontowana jest waga sprężynowa. Służy ona do mierzenia siły nacisku na korbę. W ten
sposób w jakiś miarodajny sposób można określić nacisk i zapewnić powtarzalnie i porównywalne warunki
doświadczenia. W pozycji wyjsciowej waga z korbą jest z prawej strony. Po wykonaniu obrotu o około
200 stopni w kierunku przecinym do ruchu wskazówek zegara, wiertło łopatkowe zaczyna naciskać na stos
nakrętek i podkładek. Te z koleji naciskają na stolik powodująć jego ugięcie.
W tym momencie odleglość wrzeciono-stolik zwiększa się (bo stolik się odchyla w dół) i jednocześnie
oś wrzeciona odchyla się o pewną odległość od kolumny. Tę odległość mierzy czujnik zegarowy.

Wyniki pomiarów odchylenia znajdują się w poniższej tabeli:

| Siła nacisku na korbę [kG] | Odchylenie bez klocka [mm]| Odchylenie z klockiem [mm]|
|---|---|---|
|  0 | -0.08 | -0.08 |
|  1 |  0.00 |  0.00 |
|  2 |  0.18 |  0.06 |
|  3 |  0.45 |  0.21 |
|  4 |  0.72 |  0.38 |
|  5 |  0.95 |  0.58 |
|  6 |  1.18 |  0.73 |
|  7 |  1.40 |  0.86 |
|  8 |  1.61 |  1.07 |
|  9 |  1.86 |  1.17 |
| 10 |  2.03 |  1.23 |

Krótki komentarz do wyników:
 * przy zerowej sile nacisku wiertło nie naciskało porządnie na stolik. Wskazanie zegara ustawiłem na -0.08mm
 * przy sile nacisku 1kG (waga wskazuje masę 1kg) wiertło zaczyna wywierać mały ale stabilny nacisk na stolik.
 Wskazanie zegara jest 0.00mm.
 * przy sile nacisku 10kG odchylenie niepodpartego klockiem stolika wynosi ok. 2mm. Zaobserwowałem, że najsłabszym ogniwem
 wiertarki w tym momencie jest stolik. Rzeczywiście on ugina się najbardziej.
 * wskazanie czujnika zegarowego jest dla nacisku 10kG prawie dwukrotnie mniejsze, gdy stolik jest podparty klockiem. Wniosek jest prosty:
 użycie klocka znacznie poprawia sztywność konstrukcji, a raczej w dużym stopniu niweluje niedoskonałość stolika. 
 * gdy stolik był podparty klockiem to zaobserwowałem, że w dalszej kolejności najsłabszym ogniwiem konstrukcji jest stopa-kolumna lub sama kolumna.
 Kiedy stolik nie mógł już się uginać (bo był podpraty klockiem) to zaczęła wyginać się kolumna lub miejsce styku kolumny ze stopą.
 * aby poprawić w większym stopniu sztywność należałoby przyjrzeć się kolumnie i jej połączeniu ze stopą

Poniżej przedstawiam schemat pomiarów w postaci szkicu technicznego:

<p align="center">
  <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/bench-drill/01/schema.jpg" width="60%" >
</p>

W środku kolumny w odległości **l** od górnego i od dolnego jej mocowania znajduje się czujnik zegarowy, który mierzy
zmianę odległości **x** pomiędzy środkem kolumny a wiertłem łopatkowym zamontowanym w uchwycie wiertarskim. Na korbę działa
siła nacisku **F**. Stoilk się ugina. Wielkości **y** i **x** zwiększają się o **Δy** i **Δx**. Jeżeli by założyć, że sama
kolumna się nie ugina (co nie jest do końca prawdą) to można by utworzyć trójkąt prostokątny z odcinków **Δx** i **l+Δy**.
Wtedy można policzyć wartość ugięcia w stopniach, czyli o ile stopni będzie uciekać wiertło od pionu. W mianowniku wzoru
na tangens kąta **alfa** występuje suma **l+Δy**. Jeżeli założyć, że zmiana **Δy** jest bardzo mała w porównaniu z **l**
(a tak z pewnością jest: **x** odgina się i około 2mm, a **Δy** też ma wartości podobne - można to zauważyć na wysuwającej się gilzie
z kołnierza podczas większej siły nacisku), to można w mianowniku pominąć czynnik **Δy** i obliczyć w bardzo prosty sposób kąt ugięcia 
uwzględniając tylko wielkości **l** i **Δx**.
Niepodparty stolik przy sile nacisku 10kG odchyla się wtedy o 0.86 stopnia (odchył 0.15mm na każde 10mm w głąb wierconego materiału).
Podparty stolik przy tej samej sile nacisku odchyla się już tylko o 0.52 stopnia (odchył 0.09mm na każde 10mm w głąb wierconego materiał