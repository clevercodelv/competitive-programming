# Nim spēle

Nim spēlē ir 2 spēlētāji un 3 (vai cits skaits) kaudzes ar akmeņiem. Spēles noteikumi ir tādi, ka katrā gājienā spēlētājs var paņemt jebkādu daudzumu (minimums 1) akmeņus no jebkuras kaudzes.

Nim spēles problēma ir mēģinājums uzzināt, vai spēlētājs, kam ir gājiens un akmeņi ir kādā konkrētā kompozīcijā, ir uzvarošā pozīcija un kādi gājieni jāveic, lai uzvarētu. Uzvarēšana nozīmē, ka spēlētājs paņem pēdējo akmeni, tiesa, var apskatīt arī pretēju uzvaras nosacījumu.

Lai uzzinātu, vai spēlētājs ir uzvarošajā pozīcijā, ir nepieciešams xor komandu izpildīt visiem kaudžu izmēriem. Ja rezultātā tiek iegūts skaitlis lielāks par 0, tad spēlētājs ir uzvarošā pozīcijā.

```
Piemēram, ja ir Nim spēle ar stāvokli - 3, 4, 5.
Tad tas ir binārajos skaitļos:

3 - 011
4 - 100
5 - 101

011
100 xor
---------
111

111
101 xor
----------
010

10 > 0, tātad stāvoklis 3, 4, 5 ir uzvarošs.
```

<a href="http://en.wikipedia.org/wiki/Nim" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>