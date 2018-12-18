# Skalārais reizinājums

Par divu vektoru a un b skalāru reizinājumu sauc šo vektoru moduļu reizinājumu ar kosinusu no leņķa starp šiem vektoriem. Skalārā reizinājuma formulu var apskatīt 1. attēlā.

<img alt="Skalārais reizinājums" src="/media/theory/dot_product.gif"/>
**1. attēls** - skalārais reizinājums.

Šo formulu daudz kur var izmantot, lai noteiktu leņķi un konkrētās situācijās noteiktu kādas īpašības vai veiktu aprēķinus. Skalāro reizinājumu var uzrakstīt arī diviem vektoriem ar koordinātēm. Piemēram A=(x1, y1), B=(x2, y2) skalārais reizinājums ir A * B = x1 * x2 + y1 * y2.

Zinot šīs divas lietas, ir iespējams iegūt skalāro reizinājumu no divām koordinātēm A un B, un aprēķināt leņķi starp šiem diviem vektoriem. 

```cpp
Piemēram, ja ir doti divi vektori A=(1, 3) un B=(4, 3). Tad leņķa kosinusu starp šiem diviem vektoriem var aprēķināt sekojoši.

Aprēķinām A * B = 1 * 4 + 3 * 3 = 4 + 9 = 13.
No 1. attēlā redzamās formulas ir redzams, ka skalāro reizinājumu dalot ar vektoru garumu reizinājumu var iegūt kosīnusu.
|A| = 1 * 9  = 10 un |B| = 16 + 9 = 25.
cos(A, B) = 13 / (10 * 25) = 0.052
```

<a href="http://community.topcoder.com/tc?module=Static&d1=tutorials&d2=geometry1" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>