# Wiertarka stołowa

Coraz częściej w moim majsterkowaniu doskwierał mi brak wiertarki stołowej, za pomoca której mógłbym wykonywać
bardziej precyzyjne otwory.

Pomimo wielu różnych opinii, zakupiłem niedawno w Lidlu wiertarkę **PTBM 500** firmy **Parkside**. Koszt zakupu to 339 zł.

<p align="center">
  <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/bench-drill/parkside.jpg" width="60%" >
</p>

Kilka informacji z noty katalogowej:
 * Producent: Parkside
 * Model: PTMB 500 E5
 * Moc przyłączowa: 500 W
 * Napięcie: 230 V
 * Prędkość: 500-2500 min⁻¹ (9-stopniowo)
 * Skok podczas wiercenia: 0–50 mm
 * Maks. średnica otworu: 25 mm w drewnie, 10 mm w stali
 * Tryb pracy: Sieciowe
 * Uchwyt wiertarski: B16 (1,5–16 mm)
 * Kąt stołu wiertarskiego: -45° do +45°
 * Długość kabla sieciowego: Ok. 3 m
 * Waga urządzenia: Ok. 14.9 g
 
 
Po wykonaniu kilku otworów (zarówno w drewnie jak i w miękkiej podkładce stalowej), mogę wskazać pierwsze wady i zalety urządzenia:
* zalety
  * 9-cio stopniowa regulacja obrotów (500-2500 min⁻¹)
  * cicha praca
  * niska cena (z niską ceną idzie w parze niezbyt dobra jakość - patrz wady)
* wady
  * przede wszystkim słaba sztywność konstrukcji: stopa, stopa-kolumna, kolumna, stolik-kolumna, gondola-kolumna
  * luz gilzy
  * rezonans klapy przekładni
  * tryb pracy **S2 15 min** silnika, po 15 minutach pracy ciągłej trzeba odczekać by silnik ostygł (nie wiem, jak długo trzeba czekać)
  * mała moc silnika, 500W może się okazać zbyt małe przy niektórych pracach
  
  
Jeżeli chodzi o wady to najbardziej daje sie we znaki słaba sztywność konstrukcji. Kilka moich przemyśleń związaych z wadami:
* sztywność konstrukcji: **stopa**, czyli podstawa całego urządzenia. Jest wykonana chyba jako odcisk z blachy 2.6 mm
  Stopa nie ma konstrukcji żeberkowej i wydaje mi się, że ugina się ona nieco przy większym nacisku wiertła. Ugięcie występuje w środkowej
  części stopy (kilka centymetrów przed kolumną) oraz w miejscu łączenia kolumny ze stopą.
* sztywność konstrukcji: **stopa-kolumna**, połączenie stopy z kolumną jest na zasadzie kołnierza metalowego (wykonanego chyba z aluminium). W kołnierz jest wciśnięta
  kolumna a sam kołnierz jest przykręcony do stopy za pomocą trzech śrub. Sam kołnierz jest niski; ma tylko 25 mm
  wysokości. Przy większym docisku narzędzia do materiału obrabianego można mieć wrażenie, jakby kolumna się uginała w kołnierzu (ale to może
  być tylko takie wrażenie).
* sztywność konstrukcji: **kolumna**, kolumna jest rurą o wysokości 435 mm i średnicy zewnętrznej 45.85 mm,
  średnicy wewnętrznej 43 mm. Niestety zmierzona grubość jej ścianki jest tylko 1.2 mm, co może mieć swój negatywny skutek:
  kolumna jest podatna na wyginanie się.
* sztywność konstrukcji: **stolik-kolumna**, stolik jest też chyba wykonany jako odcisk z blachy o grubości 2.6 mm. Stolik
  jest montowany do kolumny za pomocą kołnierza o wysokości 45 mm zaciskanego za pomocą śruby. Stolik jest także przechylny
  czyli można go ustawiać pod pewnym kątem do poziomu. Taka dodatkowa funkcjonalność ma swój wpływ na zmniejszenie sztywności konstrukcji.
  Uważam, że stolik ten jest jedną z największych wad tej wiertarki: ugina się bardzo łatwo.
* sztywność konstrukcji: **gondola-kolumna**. Gondola jest osadzona na kolumnie za pomocą zintegrowanego kołnierza o długości 64 mm
  i zaciskanego dwoma śrubami. Odnosze wrażenie, że to połączenie jest dosyć solidne i ma najmniejszy negatywny wpływ na sztywność całej konstrukcji.
* luz na gilzie jest znaczny (ok 1-2 mm?). W urządzeniu jest dostępna śruba kasująca luz, ale nie jestem zbyt optymistycznie do niej przekonany.
* czasami pokrywa kół pasowych wpada w rezonans i słychać nieprzyjemny jej stukot o resztę obudowy. Dzieje się tak przy pewnych kombinacjach
  nastawy obrotów, obrabianego materiału i siły nacisku na korbę.
* tryb pracy **S2 15 minut**. Rzeczywiście silnik się nagrzewa. Nie dokonywałem konkretnych pomiarów temperatury. Silnik posiada wiatraczek
  do chłodzenia. Wiatraczek jest osadzony na spodzie silnika bezpośrednio na osi silnika. Ciekawostka: łopatki wiatraczka są ustawione pod kątem prostym
  do osi wirnika (jak w parostatku). Nie wiem jak ten wiatraczek ma kierować strumień powietrza na silnik. Wydaje mi się, że to jest poważna wadami
  konstrukcyjna. Podejrzewam, że chłodzenie wiatraka polepszyło by się, gdyby zastosować łopatki ustawione pod kątem, by podczas wirowania
  kierowały one strumień powietrza na silnik.
* mała moc silnika: 500W - w obecnej chwili to nie stanowi dla mnie zbyt dotkliwej wady

  
Postaram się empirycznie zmierzyć wielkość wad konstrukcyjnych i spróbować w jakiś sposób je zmniejszyć lub wyeliminować. 
Nadmienię fakt: w drewnie wierci się wiertarką dobrze. Z cienkim metalem (blacha 3mm) też sobie radzi.
Na samym poczatku polecam pod stolik podstawić jakiś klocek z twardego drewna, żeby zmniejszyć ugięcie na samym stoliku i jego połączeniu
z kolumną; to na prawdę pomaga.

Do dzieła:
* [sztywność konstrukcji: stolik-kolumna](https://github.com/wmarkow/sandbox/tree/master/bench-drill/table-column/README.md)
* sztywność konstrukcji: kolumna
* sztywność konstrukcji: stopa
* sztywność konstrukcji: stopa-kolumna
* sztywność konstrukcji: gondola-kolumna
* luz gilzy
* rezonans pokrywy kół pasowych
  
   
 

