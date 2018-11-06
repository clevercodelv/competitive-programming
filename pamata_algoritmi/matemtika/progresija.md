#Progresija

Progresija ir skaitļu rinda, kur katrs nākamais skaitlis veidojas no kāda iepriekšējā skaitļa pēc kāda konkrēta likuma. Dažreiz sporta programmēšanā uzdevums var būt saistīts ar šīs formulas atrašanu un kāda skaitļa aprēķināšanu konkrētā pozīcijā. Šeit tiks paskatītas divu veidu progresijas - aritmētiskā un ģeometriskā.

###Aritmētiskā progresija

Aritmētiskā progresija ir skaitļu virkne, kura veidojas pēc kādas konkrētas formulas, kur katrs skaitlis ir atkarīgs no iepriekšējā skaitļa. Aritmētiskās progresijas formulu var raksturot ar 1. attēlā redzamo formulu. Piemēram, apskatot virkni 5, 7, 9, 11, 13, 15, var secināt, ka katrs elements ir pa 2 lielāks, kā iepriekšējais, jeb, ja 1. skaitlis atrodas pozīcijā 1, 2. skaitlis pozīcijā 2, u.t.t., tad katrs skaitlis ir 5 + 2 * (pozīcija - 1). Tāpēc šajā piemērā \\(a\_1 = 5\\), \\(d = 2\\), \\(n = \\) pozīcija.

<!--<center><img alt="Aritmētiskās progresijas vispārīgā formula" src="/media/theory/progression_arithmetic.gif" /></center>-->

$$a\_n = a\_1 + (n-1) \cdot d$$

<center>**1. attēls** - aritmētiskās progresijas vispārīgā formula.</center>


<a href="http://en.wikipedia.org/wiki/Arithmetic_progression" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>

###Ģeometriskā progresija

Ģeometriskā progresija ir skaitļu virkne, kur katrs nākamais elements veidojas no iepriekšējā, tam klāt piereizinot kādu skaitli. Universālu funkciju tai var redzēt 2. attēlā. Piemērs ģeometriskajai progresijai ir \\(1\\), \\(\frac 1 2\\), \\(\frac 1 8\\), \\(\frac{1}{16}\\) u.t.t., kur formulā redzamais \\(r = \frac 1 2\\), \\(a\_1 = 1\\) un \\(n =\\) pozīcija.

$$a\_n = a\_1 \cdot r^{n-1} \quad \text{vai} \quad a\_n = a\_{n-1} \cdot r$$

<center>**2. attēls** - ģeometriskās progresijas vispārīgā formula.</center>

<a href="http://en.wikipedia.org/wiki/Geometric_progression" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>