# Przeróbka spawarki Magnum Power VIP4000: dodanie wyświetlacza panelowego

Postanowiłem wzbogacić moją spawarkę o wyświetlacz panelowy, który wyświetlałby aktualną nastawę prądu spawania. Sam potencjometr ze skalą w zasadzie wystarczy
ale jak się później okazało, wyświetlacz ma również swoją zaletę: można precyzyjniej ustawić wartość prądu spawania. Pewnego razu musiałem używać na zmianę
elektrod o grubości 1.6mm i 2.0mm. Eksperymentalnie doszedłem do wniosku, że w tej konkretnej aplikacji elektrodą 1.6mm spawa mi się najlepiej prądem ok 33A
a do elektrody 2.0mm potrzebuję prądu spawania 45A. Wyświetlacz panelowy bardzo ułatwił mi przełączanie się pomiędzy elektrodami. Polegając tylko na samej skali
potencjometru nie byłbym w stanie uzyskać tych dwóch konkretnych nastaw prądu.


Zastosowany wyświetlacz dla kilku nastaw przedstawia się następująco:

<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/concepts/08_magnum_power_vip_4000/improvements/current_setting_display/multi.jpg" width="100%" >

a zamontowany w spawarce układ wygląda tak:

<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/concepts/08_magnum_power_vip_4000/improvements/current_setting_display/mounted_pcb.jpg" width="50%" >

## Idea układu
Rozwiązanie techniczne wyświetlacza polega na zastąpieniu orginalnego potencjometru nastawy potencjometrem podwójnym oraz użyciu prostego woltomierza panelowego:
* pierwszy ślizgacz potencjometru służy do regulacji nastawy prądu i jest bezpośrednio wmontowany w układ spawarki (zamiast potencjometru orginalnego)
* drugi ślizgacz służy do wyświetlania wartości nastawy na woltomierzu panelowym

Ponieważ oba ślizgacze są regulowane jednocześnie za pomocą tej samej gałki to mamy pewność, że nastawa prądu jest zgodna z tym co przedstawia woltomierz panelowy. Układ został tak skalibrowany,
że przy nastawie minimalnej wyświetlacz pokazuje napięcie **0.20V** (co odpowiada nastawie 20A) a przy nastawie maksymalnej wyświetlacz pokazuje **2.00V** (co odpowiada
nastawie 200A). Skalibrowane nastawy bazują jedynie na tabliczce znamionowej podanej przez producenta. Nie ma pewności, że nastawa 200A rzeczywiście ustawia prąd spawania
na poziomie 200A, jednakże powtarzalność nastaw jest tutaj zapewniona. Oczywiście można wyświetlacz skalibrować również za pomocą cęgowego miernika prądu.


Przed przystąpieniem do prac dokonałem oględzin orginalnego potencjometru i jego okolic. Poniżej schemat układu, uzyskany metodą inżynierii odwrotnej:
<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/concepts/08_magnum_power_vip_4000/improvements/current_setting_display/original_schematic.png" width="75%" >

Potenjometr nastawy (VRa + VRb) ma wartość **830** ohm a jego zaciski sa podłączone do trzech przewodów w kolorach czerwonym (przez VR1 i R79 do zasilania 15.8V), czarnym (wyjście nastawy) i zielonym (do masy).
Przewód czarny idzie bezpośrednio przez rezystory R71 i R55 a potem dalej do wzmacniacza operacyjnego, który odpowiedzialny jest za utrzymanie prądu spawania podczas procesu spawania.
Poniżej przedstawiam wartość napięcia na wyjściu potencjometryu (przewód czarny) w zależności od nastawy potencjometru:

 | Nastawa prądu [A] | Napięcie na wyjściu potencjometru (przewód czarny) [V] |
 |---|---|
 | min | 0.00 |
 |  20 | 0.00 |
 |  65 | 1.90 |
 | 110 | 3.53 |
 | 145 | 5.15 |
 | 200 | 6.48 |
 | max | 6.59 |


Projektując układ wyświetlacza należy za pomoca nowego potencjometru uzyskać takie same poziomy napięć na przewodzie w kolorze czarnym, wtedy układ nastawy będzie działał taki sam sposób, jak przewidział to producent.
Dobór odpowiednigo potencjometra podwójnego nie jest prosty; trzeba użyć potencjometru o wartości jak najbardziej zbliżonej do orginalnej. Na przykład użycie takiego o wartości 10k powoduje generowanie
dużo wyższych napięć, co spowoduje niepoprawną pracę urządzenia. Taki o wartości **830** ohm był dla mnie nieosiągalny i dlatego zdecydowałem się na najprostszy (co nie oznacza, że najlepszy) 
potencjometr **1k** jak na zdjęciu poniżej:

<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/concepts/08_magnum_power_vip_4000/improvements/current_setting_display/docs/potentiometer_2x1k.png" width="30%" >


## Schemat układu
Schemat nowego potencjometru nastawy wraz z wyświetlaczem panelowym poniżej:

<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/concepts/08_magnum_power_vip_4000/improvements/current_setting_display/schematic.png" width="75%" >

**P1/2** to ślizgacz potencjometru wmontowanego bezpośrednio w spawarce zamiast orginalnego potencjometru. Ponieważ użyty przeze mnie potenjometr podwójny ma wartość **1k** (a orginalny
ma wartość **830** ohm), używam potencjometru VR3 o wartości **500** ohm by dostosować charakterystykę nowego potencjometru do tego orginalnego. Chodzi o to by przy minimalnej nastawie
uzyskać napięcie czarnego przewodu na poziomie 0.00V a przy maksymalnej nastawie uzyskać napięcie około 6.60V.

Potencjometr **P1/1** i rezystory nastawne **VR1** i **VR2** służą do regulcaji i wyświetlania napięcia na woltomierzu panelowym. VR1 i VR2 należy tak wyregulować aby:
* przy minimalnej nastawie woltomierz pokazywał **0.20** V
* przy maksymalnej nastawie woltomierz pokazywał **2.00** V

Montaż układu jest prosty:
* VR1 ustawić na wartość maksymalną 10k
* VR2 ustawić na wartość minimalną 0 ohm
* P1/1 ustawić na wartość maksymalną 1k
* VR3 ustawić na wartośc maksymalną 500 ohm
* podłączyć odpowiednio wyjścia złącza JP1 do przewodów w spawarce (zielony, czarny i czerwony). Zasilanie 15.8V znaleźć w spawarce za pmoocą woltomierza.
* podłączyć odpowiednio woltomierz panelowy do złącza LCD


## Kalibracja trymera VR3:
1. uruchomić spawarkę
2. ustawić maksymalną nastawę prądu (200A)
3. zmniejszać wartość trymera VR3 aż do uzyskania napięcia na czarnym przewodzie na poziomie 6.60V
4. ustawić minimalną wartość nastawy prądu; napięcie na czarnym przewodzie powinno wynosić 0V

<br/>

## Kalibracja wyświetlacza:
1. uruchomić spawarkę
2. ustawić maksymalną nastawę prądu (200A)
3. zmieniać (generalnie zmniejszać) wartość trymera VR1 aż woltomierz pokaże 2.00V
4. ustawić minimalną nastawę prądu spawania (20A)
5. zmieniać (generalnie zwiększać) wartośc trymera VR2 aż woltomierz pokaże 0.20V
6. powtórzyć kroki od 2 do 5 kilka razy (zwykle 3 razy są wystarczające)
7. przy minimalnej nastawie woltomierz powinien pokazać 0.20 a przy maksymalnej nastawie powinien pokazać 2.00

W tym momencie wyświetlacz jest skalibrowany i powinien działać poprawnie. Mi przeszkadzała jeszcze kropka dziesiętna w woltomierzu panelowym. Aby jej nie wyświetlać to należy
przeciąć nóżkę sterującą (pin 3) w wyświetlaczu siedmiosegmentowym i złatwione (schemat [tutaj](https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/concepts/08_magnum_power_vip_4000/improvements/current_setting_display/docs/3_digits_display.jpg)).
Z kropką dziesiętną wyświetlacz pokazuje tak:

<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/concepts/08_magnum_power_vip_4000/improvements/current_setting_display/display_with_dot.jpg" width="30%" >

natomiast bez kropki jest już o niebo lepiej:

<img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/inverter-welder/concepts/08_magnum_power_vip_4000/improvements/current_setting_display/display_without_dot.jpg" width="30%" >


## Niedoskonałość skali
Jeszcze jedna uwaga o pewnej niedoskonałości całego rozwiązania: mianiowicie wskazania wyświetlacza nie pokrywają się ze wskazaniami orginalnej skali potencjometru. Wynika to z tego, że zastosowany
przeze mnie potenjometr ma większy kąt obrotu niż potencjometr orginalny. Być może można by coś w tej sprawie polepszyć, np. zastosować jakiś mechaniczny ogranicznik kątu obrotu uniemożliwiający dokonanie
pełnej nastawy potencjometru. Ponadto zastosowany potencjometr ma "ząbkowaną" oś (patrz zdjęcie powyżej) a gałka potencjometru zaciskana jest na śrubkę, w efekcie czego dokręcając ową śrubkę gałka 
zawsze przekręca się o pewien mały kąt i chce by śrubka dociskała się zawsze pomiędzy dwa sąsiednie ząbki.

<br/>

## Materiały dodatkowe:
 * [schemat w formacie EAGLE](https://github.com/wmarkow/sandbox/tree/master/inverter-welder/concepts/08_magnum_power_vip_4000/improvements/current_setting_display/sch)
 * [symulacje układu w LTspice XVII](https://github.com/wmarkow/sandbox/tree/master/inverter-welder/concepts/08_magnum_power_vip_4000/improvements/current_setting_display/sim)

