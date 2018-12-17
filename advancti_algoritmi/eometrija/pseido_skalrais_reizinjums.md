# Pseido skalārais reizinājums

Par divu vektoru a un b pseido skalāru reizinājumu sauc šo vektoru moduļu reizinājumu ar sinusu no leņķa starp šiem vektoriem. Pseido skalārā reizinājuma formulu var apskatīt 1. attēlā.

<center><img alt="Pseido skalārais reizinājums" src="/media/theory/cross_product.gif"/></center>

<center>**1. attēls** - pseido skalārais reizinājums.</center>

Šo formulu daudz kur var izmantot, lai noteiktu leņķi un konkrētās situācijās noteiktu kādas īpašības vai veiktu aprēķinus. Pseido skalāro reizinājumu var uzrakstīt arī diviem vektoriem ar koordinātēm. Piemēram A=(x1, y1), B=(x2, y2) pseido skalārais reizinājums ir A * B = x1 * y2 - x2 * y1.

Zinot šīs divas lietas, ir iespējams iegūt pseido skalāro reizinājumu no divām koordinātēm A un B, un aprēķināt leņķi starp šiem diviem vektoriem. 

```
Piemēram, ja ir doti divi vektori A=(1, 3) un B=(4, 3). Tad leņķa sinusu starp šiem diviem vektoriem var aprēķināt sekojoši.

Aprēķinām A * B = 1 * 3 - 3 * 4 = 3 - 12 = -9.
No 1. attēlā redzamās formulas ir redzams, ka pseido skalāro reizinājumu dalot ar vektoru garumu reizinājumu var iegūt sīnusu.
|A| = 1 * 9  = 10 un |B| = 16 + 9 = 25.
cos(A, B) = -9 / (10 * 25) = -0.036
```

<a href="http://community.topcoder.com/tc?module=Static&d1=tutorials&d2=geometry1" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>