# Luz gilzy


Luz gilzy jest duży. Wynosi on 0.80mm w kierunku przód-tył (kierunek silnik-operator wiertarki) przy maksymalnym wysuwie 52mm
i całkowicie wykręconej śrubie kasowania luzu.
Ta część gilzy, która przesuwa się w kołnierzu ma długość około 90mm. Im większy wysuw gilzy to luz jest większy. Producent ustawił 
maksymalny wysuw gilzy na ok. 52mm. Ta wartość jest wieksza niż połowa przesuwnej części gilzy. Intuicja mi podpowiada, że dobrze
by było by jednak wieksza część gilzy pozostawała w kołnierzu, aby luz był jednak mniejszy. Wynika z tąd wniosek, że maksymalne
wysunięcie gilzy powinno być nie większe niż 46mm.

Wykręcona gilza przedstawia się poniżej:
<p align="center">
  <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/bench-drill/backlash/gilza1.jpg" width="60%" >
</p>

Śruba kasowania luzu wraz z kontrnakrętką wygląda tak:
<p align="center">
  <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/bench-drill/backlash/regulation_screw3.jpg" width="60%" >
</p>

Śrube tę od razu trzeba poprawić (zeszlifować) gdyż ma ona nieregularne czoło i w zasadzie nie idzie nią dobrze skasować
luzu. Na rysunku poniżej widać nieregularność płaszczyzny śruby:
<p align="center">
  <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/bench-drill/backlash/screw_before_1.jpg" width="60%" >
</p>

Najlepiej by było splanować płaszczyznę na tokarce. Tokarki jeszcze nie mam więc zeszlifowałem śrubę za pomocą szlifierki stołowej.
Teraz regulacja działa lepiej.

Wyróżniam dwa typy luzu gilzy:
1. luz przód-tył (lub w kierunku silnik-operator wiertarki) przy przesuwaniu gilzy w kierunku przód-tył. Jest on kasowany
śrubą kasującą luz.
2. luz boczny przy przesuwaniu gilzy na bok, z prawa na lewo. Ten luz nie ma swojej osobnej śruby kasującej.


[Tutaj na forum CNC](https://www.cnc.info.pl/luz-pinoli-w-ws15-t31908.html) znalazłem fajny sposób na kasowanie luzu gilzy. Kopia tego materiału znajduje się
[tutaj jako PDF](https://raw.githubusercontent.com/wmarkow/sandbox/master/bench-drill/backlash/cnc.info.pl_Luz_pinoli_w_WS15.pdf).


Zainspirowany tym artykułem wpadłem na pomysł by owinąć gilzę blaszką aluminiową wyciętą z puszki po piwie. Nie chciałem tego kleić tylko owinąć
folią i zobaczyć czy luz się zmniejszy.

Najpierw wyciąłem kawałek folii po piwie "Dębowe". Folia ma wysokość około 8cm (trochę mniej niż długośc gilzy) i szerokość odpowiednią by owinąć
ją wokól gilzy. Trzeba zostawić miejsce na śrubę kasującą luz. Maglownica, po której jeźdźi koło zębate od korby jest cała owinięta foilią. Tym się
na razie nie trzeba przejmować:
<p align="center">
  <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/bench-drill/backlash/reduce_backlash_1.jpg" width="60%" >
</p>

Potem wsunąłem gilze z folią do kołnierza:
<p align="center">
  <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/bench-drill/backlash/reduce_backlash_2.jpg" width="60%" >
</p>

Wciskamy korbę z kołem zębatym na swoje miejsce i delikatnie obracamy korbą tak, jakbyśmy chcieli wiercić. Okazuje się, że koło
zębate przebija folię aluminiową i sprawnie przesuwa sie po maglownicy torując sobie drogę. Jednocześnie blaszka aluminiowa zostaje
wbita w maglownicę, co niejako kasuje luz na maglownicy i dodatkowo zakleszcza folię w gilzie uniemożliwiając jej zsunięcię się
z gilzy. Same plusy!
<p align="center">
  <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/bench-drill/backlash/reduce_backlash_3.jpg" width="60%" >
</p>

Tak to wygląda po wyjęciu korby z kołem zębatym:
<p align="center">
  <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/bench-drill/backlash/reduce_backlash_4.jpg" width="60%" >
</p>

A tak wygląda cała gilza ponownie wyjęta z kołnierza:
<p align="center">
  <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/bench-drill/backlash/reduce_backlash_5.jpg" width="60%" >
</p>

Wydaje mi się, że ta blaszka aluminiowa mogłaby być ciut dłuższa. Nawet dłuższa od samej gilzy.

Zbudowałem układ pomiarowy:

jeden do pomiaru luzu przód-tył:
<p align="center">
  <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/bench-drill/backlash/test_setup_1.jpg" width="60%" >
</p>

i drugi do pomiaru luzu bocznego:
<p align="center">
  <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/bench-drill/backlash/test_setup_2.jpg" width="60%" >
</p>


Wyniki pomiarów w poniższych tabelkach. Pomiary oznaczone **?** nie zostały wykonane.


| Wysuw gilzy [mm] | Luz przód-tył bez śruby i bez blaszki Al [mm]| Luz przód-tył bez śruby ale z blaszką Al [mm]| Luz przód-tył ze śrubą i blaszką Al [mm]|
|---|---|---|---|
|  0 | 0.29 | 0.05 | ? |
| 40 |    ? | 0.30 | ? |
| 52 | 0.80 | 0.40 | ? |


| Wysuw gilzy [mm] | Luz boczny bez śruby i bez blaszki Al [mm]| Luz boczny bez śruby ale z blaszką Al [mm]| Luz boczny ze śrubą i blaszką Al [mm]|
|---|---|---|---|
|  0 | 0.22 | 0.01 | ? |
| 40 |    ? | 0.25 | ? |
| 52 | 0.60 | 0.25 | ? |




