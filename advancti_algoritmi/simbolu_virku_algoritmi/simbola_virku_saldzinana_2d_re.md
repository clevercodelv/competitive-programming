# Simbola virkņu salīdzināšana 2D režģī

Problēma bieži vien definējas kā - ir dota 2D matrica ar simboluiem, ir jāatrod simbolu virkne šajā matricā. Bieži vien uzdevuma nosacījumi var būt sarežģīti, piemēram, simbolu virkne drīkst būz itliekta pa diagonālēm, horizontāli un vertikāli (2, 4, 8 virzienos). Piemēru var skatīt 1. attēlā.


<img alt="2D simbolu matrica ar 8 virzienu meklējamo simbolu virkni" src="/media/theory/2d_array.png" />
**1. attēls** - 2D simbolu matrica ar 8 virzienu meklējamo simbolu virkni.


Variants, kā risināt šo problēmu, ir rupjš spēks. Rekursīvi apstaigājot katru variantu tik dziļi, cik dziļa ir simbolu virkne, var atrast pareizo variantu šādā veidā. Ja kāds no simboliem meklēšanas procesā nesakrīt, tad notiek kāpšanās atpakaļ rekursijā un skatīšanās citā virzienā. Piemēram, meklējot WALDO 1. attēlā un nonākot masīvā līdz vietai, kur ir W burts, rekursīvā funkcija search() varētu tikt izsaukta uz koordinātēm i, j, kur atrodas 'W' - search(i, j, 0). Ja burts šajā šūnā sakrīt ar 0. simbolu meklējamajā simbolu virknē, tad notiek virzīšanās tālāk uz (atkarībā no uzdevuma) kādu no pusēm - augšu, pa labi, apakšu, pa kreisi. Virzīšanās ir atkal rekursīvs izsaukums. Lai patrenētos šo problēmu, var atrisināt <a href="" target="_blank">UVa 10010  - Where`s Waldorf</a>.