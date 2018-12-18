# Fenvika koks

Fenvika koks jeb binārais indeksētais koks(BIK) ir datu struktūra, kura ļauj efektīvi aprēķināt un manipulēt ar skaitļu masīva prefiksu summām. 

Skaitļu masīva prefiksu summa ir skaitļu masīva ( sk[N] ) elementu summa sākot ar tā pirmo elementu līdz M-tajam elementam ( sk[1] + sk[2] + sk[3] + .. + sk[M] ). M<=N .  

Ja varam aprēķināt masīvu summu elementiem no 1 līdz X (apzīmēsim sum[X] ), tad varam aprēķināt jebkura intervāla summu elementiem no A līdz B ar formulu sum[B]-sum[A-1] .

Vienkāršākā gadījumā šo pašu problēmu varētu risināt veidojot prefiksu summu masīvu. Par piemēru ņemsim masīvu: sk = [3,9,1,2,8,5,4,9]. Šī masīva prefiksu summu masīvs būs sum = [3,12,13,15,23,28,32,41] . Un, piemēram, ja mēs gribētu noskaidrot intervāla summu no 3. elementa līdz 6. elementam tad mēs aprēķinātu sum[6] - sum[2] = 28 - 12 = 16 . Intervāla summas noteikšana var tikt veikta ar sarežģītību O(1), bet ja mēs vēlētos veikt šajā masīvā izmaiņas, piemēram, jāizmaina elements X, tad sum masīvā būtu jāmaina visi elementi no X līdz N, kas veido sarežģītību O(N) .

Ar BIK palīdzību ir iespējams aprēķināt jebkuru prefiksa summu ar sarežģītību O(log N) un tas ļauj veikt modifikācijas skaitļu masīvā, saglabājot struktūru ar sarežģību O(log N) . 

BIK sākotnējās būvēšanas sarežģītība ir O(n log n) . 

<h3>BIK struktūras principi</h3>

Katru pozitīvu veselu skaitli var izteikt kā divnieku pakāpju summu. BIK var glabāt atmiņā kā skaitļu masīvu, kuram ir tieši tik pat elementu, cik ir masīvā, kuru BIK apraksta. 

Ja P ir INDEKS binārā pieraksta pēdējā cipara numurs, tad BIK[IDX] glabāsies summa intervālam no (INDEKS - 2^P + 1) līdz INDEKS . 

Piemēri:

INDEKS ir 11 (binārajā pierakstā 1011), P = 0, jo pirmais cipars binārajā arī pirmais 1 . Tātad BIK[11] glabājas intervāla summa no 11 līdz 11 . (11 - 1(2^0) + 1) līdz 12
INDEKS ir 12 (binārajā pierakstā 1100), P = 2, jo trešais cipars binārajā ir pirmais 1 . Tātad BIK[12] glabājas intervāla summa no 9 līdz 12 . ( 12 - 4(2^2) + 1 ) līdz 12
 

Vizuāli tas izskatās šādi: 

<img alt="Divdaļīgs grafs" src="/media/theory/BIK.gif" />

Lietojot BIK struktūru sum[X] tiek aprēķināts sekojoši:

```cpp
RESULT = 0

WHILE (X>0)
RESULT = RESULT + BIK[X]
noņem X pēdējo bitu
ENDWHILE
```

Piemēram:

sum[13]   = BIK[13]   +  BIK[12]   + BIK[8] .
Ja rakstītu šos indeksus binārjā skaitīšanas sistēmā tas izskatīsies šādi:
sum[1101] = BIK[1101] +  BIK[1100] + BIK[1000]

Modificēt elementu no skaitļu virknes, lai struktūra saglabātu savas īpašības, var sekojoši:

Ir nepieciešams izmainīt visus BIK elementus, kur šī summa ir iekļauta. Piemēram, ja tas būtu INDEKS = 5, tad informāciju par šo elementu glabā BIK[5], BIK[6], BIK[8], BIK[16] . 

Programmā tas izskatītos šādi:

```
WHILE (X<N)
UPDATE (BIK[X])
pieskaita X pēdējo bitu
ENDWHILE
```