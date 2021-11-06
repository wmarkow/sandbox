# 28.06.2021 Sztywność konstrukcji: stopa

Stopa wydaje sie być mocna ale niestety nie ma ona zbyt dobrej konstrukcji żeberkowej, przez co mam wrażenie że się ona odgina.
Postanowiłem dokonać ulepszenia i wspawać wzdłuż stopy dwa płaskowniki stalowe.

Zdjęcie orginalnej stopy:

<p align="center">
  <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/bench-drill/02/foot_before.jpg" width="60%" >
</p>

Płaskowniki o grubości 5mm i długości ok 32cm. Jeden z nich ma szerokość 40mm a drugi 25mm (akurat takie posiadałem pod ręką).
Zostały on przycięte na wymiar by jak najlepiej pasowały do blachy stopy.
Po zespawaniu wygląda to tak:
<p align="center">
  <img src="https://raw.githubusercontent.com/wmarkow/sandbox/master/bench-drill/02/foot_after.jpg" width="60%" >
</p>
Spoiny nie były nakładana na całej długości płaskowników. Nakładałem je na odcinkach o długości ok 2cm symetrycznie po obu stronach
każdego płaskownika.

Aby sprawdzić czy płaskowniki usztywniają kosnktrukcję, ponownie zbudowałem układ pomiarowy jak w 
[sztywność konstrukcji: stolik-kolumna](https://github.com/wmarkow/sandbox/tree/master/bench-drill/01/README.md)
a porównawczy wynik jest w poniżeszej tabelce:

| Siła nacisku na korbę [kG] | Odchylenie bez klocka [mm]| Odchylenie z klockiem [mm]| Odchylenie ze wzmocnioną stopą [mm]|
|---|---|---|---|
|  0 | -0.08 | -0.08 | |
|  1 |  0.00 |  0.00 | 0.00 |
|  2 |  0.18 |  0.06 | 0.12 |
|  3 |  0.45 |  0.21 | 0.24 |
|  4 |  0.72 |  0.38 | 0.35 |
|  5 |  0.95 |  0.58 | 0.46 |
|  6 |  1.18 |  0.73 | 0.58 |
|  7 |  1.40 |  0.86 | 0.70 |
|  8 |  1.61 |  1.07 | 0.79 |
|  9 |  1.86 |  1.17 | 0.85 |
| 10 |  2.03 |  1.23 | 0.91 |

Krótki komentarz do wyników:
 * przy zerowej sile nacisku wiertło nie naciskało porządnie na stolik. Wskazania czujnika nie zanotowałem.
 * przy sile nacisku 1kG (waga wskazuje masę 1kg) wiertło zaczyna wywierać mały ale stabilny nacisk na stolik.
 Wskazanie zegara jest 0.00mm.
 * przy sile nacisku 10kG odchylenie podpartego klockiem stolika ze wzmocnioną stopą wynosi ok. 0.9mm. Widać znaczną poprawę.
 * do siły nacisku 4kG nie widać żadnej poprawy a nawet lekkie pogorszenie. Jak to wytłumaczyć? Być może przy małym nacisku 
 stopa nie ugina się zbytnio? Może łatwiej ugina się kolumna lub kołnierz mocujący kolumne ze stopą? Być może zbudowany układ
 pomiarowy różni się nieco od tego poprzedniego (np. wystąpiła niedoskonałość montażu czujnika zegarowego)?
 * dla sił nacisku powyżej 4kG widać znaczną poprawę; największe ugięcie zostało zmniejszone o 0.32mm dzięki zastosowaniu dwóch 
 płaskowników wspawanych wzdłuż stopy.
 * podczas pomiarów zauważyłem, że kolumna również się odgina. W zasadzie to nie jestem pewien jak mocno ugina się sama kolumna,
 ale odnoszę wrażenie, że połączenie kolumny z kołnierzem stopy też jest kiepskie. Sam kołnierz jest wykonany z aluminium a kolumna wydaje
 się być tylko do niego mocno wciśnięta.

