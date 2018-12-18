# Segmentu koks

Segmentu koks ir datu struktūra, kurā var glabāt un kurai var jautāt informāciju par diapazonu skaitļu virknes ietvaros. 

Piemēram, ar intervāla koku var risināt klasisko RMQ(range minimum query - minimuma atrašana diapazonā). Uzdevuma piemērs "Ir dota N skaitļu virkne. Ir doti M jautājumi par šo skaitļu virkni: kāda ir minimālā elementa vērtība intervālā [A,B]." 

Vienkāršākajā variantā atbildi uz RMQ(A,B) var atrast ar serežģītību O(K), kur K ir elementu skaits intervālā [A,B], ejot cauri katram skaitlim un saglabāt sastapto minimumu. Segmentu koks ļauj uz katru šo jautājumu atrast atbildi ar sarežģītību O(log N) . 

Šo uzdevumu varētu arī nedaudz sarežģīt un pievienot nosacījumu, ka var mainīt elementa vērtību. Ar segmenta koku šo darbību varētu veikt ar seržģītību O(log N). 

Segmenta koks ir binārais koks, kur katra virsotne glabā informāciju par kādu konkrētu intervālu [L, R]. Katrā virsotnē [L, R] jau glabājas maksimālā summa intervālā [L, R] . Saknes virsotne glabā informāciju par visu skaitļu virkni. Ja virsotne glabā informāciju par intervālu [L,R] tad katrs tās bērns glabā informāciju par [L, (L+R)/2] un [(L+R)/2+1, R], koka dziļums stiepjas līdz L = R . 

Atrast atbildi uz RMQ(i,i) ir vienkārši. Atbilde glabājas koka lapās. Bet, vispārīgā gadījumā ir nepieciešamas papildu darbības.

Visa meklēšana parasti sākas koka saknē. Pieņemsim, ka mūsu skaitļu virknē ir 8 skaitļi un mēs vēlamies noskaidrot atbildi uz RMQ(2,6) . 

3 9 1 2 8 5 4 9

Sākumā kokam tiek veikta inicializācija O(log N) laikā. Pēc inicializācijas koks izskatās šādi: 

<center>
<img alt="Initial" src="/media/theory/SK_initial.png"/></center>

Jautāšana segmentu kokam notiek rekursīvi. Vispirms sāk ar saknes virsotni un pārbaudes funkcija izskatās šādi:

```
BEGIN

minimums = infinity  // resultāts

segmenta_sākums = 2  // meklējamā segmenta sākums
segmenta_beigas = 5  // meklējamā segmenta beigas

pārbaude( virsotnes_nr, virsotnes_segmenta_sākums, virsotnes_segmenta_beigas )  BEGIN   // saknes virsotnes gadījumā - virsotnes_nr = 1, virsotnes_segmenta_sākums = 1, virsotnes_segmenta_beigas = 8

IF (segmenta_sākums >= virsotnes_segmenta_sākums AND segmenta_beigas <= virsotnes_segmenta beigas) begin  	 // ja virsotnes segments pilnībā pārklājas ar meklējamo segmentu, pārbaudam vai
if ( minimums > vērtības[ virsotnes_nr ] ) begin                                                  	 // nepieciešams uzlabot rezultātu, ja ir uzlabojam
minimums = vērtības[ virsotnes_nr ]
END
HALT	   	 // pārtraucam un dziļāk neejam
END

IF (virsotnes_segmenta_sākums == virsotnes_segmenta_beigas) begin
HALT
END


bērna_virsotnes_segmenta_sākums = virsotnes_segmenta_sākums	 // kreisā bērna virsotnes segmenta sākums
bērna_virsotnes_segmenta_beigas = (virsotnes_segmenta_sākums + virsotnes_segmenta_beigas) / 2	 // kreisā bērna virsotnes segmenta beigas

IF (bērna_virsotnes_segmenta_sākums <= segmenta_beigas AND bērna_virsotnes_segmenta_beigas >= segmenta_sākums) BEGIN  	// pārbaudam vai šis bērna segments pārklājas ar mums interesējošo segmentu
pārbaude( virsotnes_nr * 2, bērna_virsotnes_segmenta_sākums, bērna_virsotnes_segmenta_beigas)
END


bērna_virsotnes_segmenta_sākums = (virsotnes_segmenta_sākums + virsotnes_segmenta_beigas) / 2 + 1        	 // labā bērna virsotnes segmenta sākums
bērna_virsotnes_segmenta_beigas = virsotnes_segmenta_beigas                                             	 // labā bērna virsotnes segmenta beigas

IF (bērna_virsotnes_segmenta_sākums <= segmenta_beigas AND bērna_virsotnes_segmenta_beigas >= segmenta_sākums) BEGIN  	// pārbaudam vai šis bērna segments pārklājas ar mums interesējošo segmentu
pārbaude( virsotnes_nr * 2 + 1, bērna_virsotnes_segmenta_sākums, bērna_virsotnes_segmenta_beigas)	      	// pārbaudam šo virsotni	
END

END

final_result = minimums

END
```


Rekursīvi pa soļiem aprēķini izskatās šādi: 

Cipars rindas sākumā apzīmē virsotnes numuru. Tab nozīmē, ka ejam dziļāk kokā. 

1. Sākumā tiek meklēts saknē.
1. Ejam uz kreiso bērnu.
2.Ejam uz kreiso bērnu
4. Ejam uz labo bērnu
9. Intervāls pilnībā pārklājas - pārbaudam rezultāt. Virsotnes rezultāts = 0. Minimums = 9 .
2.Ejam uz labo bērnu
5. Intervāls pilnībā pārklājas - pārbaudam rezultātu. Virsotnes rezultāts = 1. Minimums = 1 . 
1. Ejam uz labo bērnu
3. Ejam uz keiso bērnu
6. Intervāls pilnībā pārklājas - pārbaudam rezultātu. Virsotnes rezultāts = 5. Minimums = 1 .

<center>
<img alt="Mekl" src="/media/theory/SK_mekl.png"/></center>

Intervāla koks rezultātā paņem mazāko virsotņu skaitu no koka tā, ka šo virsotņu atbilstošie intervāli kopā veido meklējamo intervālu. Šajā gadījumā tās bija virsotnes: 9. 5. 6. ar intervāliem [2,2] + [3,4] + [5,6] . Zinot labākos rezultātus no šīm virsotnēm un tos apvienojot, mēs zinām labāko kopējo rezultātu.


Ar segmentu koku var risināt daudz citas problēmas, piemēram atrast summu kādam skaitļu virknes segmentam. Tikai atšķirība būtu tāda, ka virsotnēs glabātos attiecīgā segmenta summa, un pārbaudes ifs attiecīgi mainītos uz

IF (segmenta_sākums >= virsotnes_segmenta_sākums AND segmenta_beigas <= virsotnes_segmenta beigas) begin
summa = summa + vērtības[ virsotnes_nr ]
HALT	   	
END

Kad programma beigs savu darbību, mainīgajā summa glabāsies prasītā intervāla summa.