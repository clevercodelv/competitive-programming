# Kombinācijas

Kombinācijas ir kaut kas līdzīgs permutācijām, bet sarežģītāks. Kombinācijas ir funkcija C(N, M), kas aprēķina, cik veidos no N lietām var paņemt M lietas. Funkciju var apskatīt 1. attēlā.


<img alt="Kombinācijas formula" src="/media/theory/combinations.gif" />
**1. attēls** - kombinācijas formula.


Piemēram, ja ir dotas 10 bingo bumbas un ir nepieciešams uzzināt, cik veidos var izvēlēties 4 bumbas no 10, tad to var aprēķināt C(10, 4) = 10! / (4! * 6!). Kā šo aprēķināt neaprēķinot katru faktoriāli? Kombinācijas vienmēr būs vesels skaitlis. Izvēršot faktoriāļus ir iespējams tos noīsināt. C(10, 4) = 1 * 2 * 3 * 4 * 5 * 6 * 7 * 8 * 9 * 10 / (1 * 2 * 3 * 4 * 1 * 2 * 3 * 4 * 5 * 6) = 7 * 8 * 9 * 10 / (1 * 2 * 3 * 4) = 7 * 3 * 10 = 210.

Vēl viena īpašība, kas jāpiemin, ir, ka faktoriālis strādā no abiem galiem jeb C(n, m) = C(n, n - m). Kāpēc tā? To ir viegli pierādīt. Ja C(n, m) = n! / (m! * (n - m)!), tad C(n, n - m) = n! / ((n - m)! * (n - (n - m))!) = n! / ((n - m)! * (n - n + m)!) = n! / ((n - m)! * m!). Acīm redzot izteiksmes ir ekvivalentas.

<a href="http://en.wikipedia.org/wiki/Combination" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>