# Moduļu aritmētika

Moduļu aritmētikā aplūko veselu skaitļu atlikumus, dalot ar kādu naturālu skaitli \\(n\\). Uzdevumos bieži tiek prasīts izrēķināt atbildi pēc kāda moduļa, ja darbība notiek ar ļoti lieliem skaiļiem, lai izvairītos no <a href="http://www.clevercode.lv/#/theory/document/50">lielo skaitļu aritmētikas</a>. Citi pielietojumi bieži ietver skaitļu teorijas elementus.

Katram veselim skaitlim \\(a\\) varam piekārtot viņa atlikumu pēc moduļa \\(n\\), ko apzīmē ar \\(a \pmod n\\). Saka, ka veseli skaitļi \\(a\\) un \\(b\\) ir <i>kongruenti</i> pēc moduļa \\(n\\), ja tie dod vienādus atlikumus, dalot ar \\(n\\), t.i., \\(a \pmod n = b \pmod n\\). Tādā gadījumā lieto pierakstu \\(a \equiv b \pmod n\\). Ekvivalenti var teikt, ka \\(a\\) un \\(b\\) ir kongruenti, ja starpība \\(|a-b|\\) dalās ar \\(n\\) bez atlikuma.

Piemēram, ņemot \\(n = 6\\), ir spēkā $$3 \equiv 3 \pmod 6$$ $$5 \equiv 5 \pmod 6$$ $$0 \equiv 0 \pmod 6$$ $$6 \equiv 0 \pmod 6$$ $$7 \equiv 1 \pmod 6$$ $$15 \equiv 3 \pmod 6$$ $$20 \equiv 50 \pmod 6$$

Atlikums pēc moduļa \\(n\\) vienmēr ir vesels skaitlis robežās no 0 līdz \\(n-1\\). Tas izpildās, aplūkojot arī negatīvo skaitļu atlikumus pēc moduļa \\(n\\). Piemēram, $$-1 \equiv 5 \pmod 6$$ $$-4 \equiv 2 \pmod 6$$ $$-6 \equiv 0 \pmod 6$$ $$-14 \equiv 4 \pmod 6$$

Citiem vārdiem, skaitļa \\(a\\) atlikums pēc moduļa \\(n\\) ir tāds vesels skaitlis \\(r\\) no \\(0\\) līdz \\(n-1\\), ka \\(|r-a|\\) dalās ar \\(n\\) bez atlikuma.

Moduļu aritmētika ir saderīga ar parastajām veselo skaitļu saskaitīšanas, atņemšanas un reizināšanas operācijām. Tālāk ir doti piemēri moduļu aritmētikas realizācijai. Valodā C++ atlikuma ņemšanas operācija ir <code>%</code>.

## Operācijas

Saskaitīšana pēc moduļa:

```
int sum = (a + b) % n;
```

Atņemšana pēc moduļa:

```
int sub = (n + a - b) % n;
```

Reizināšana pēc moduļa:

```
int mul = (a * b) % n;
```

Ja skaitļi \\(a\\), \\(b\\) nav intervālā starp \\(0\\) un \\(n-1\\), tad pirms šīm darbībām vienmēr vajag tos pielīdzināt to atlikumiem, lai novērstu datu tipa pārpildīšanos: ```a %= n; b % = n;```

Savukārt skaitļu dalīšana pēc moduļa ir definēta tikai tad, ja \\(n\\) ir pirmskaitlis. Tā tiek aplūkota sadalā <a href = "http://www.clevercode.lv/#/theory/document/101">Fermā mazā teorēma</a>.