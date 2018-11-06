#Ad Hoc

Ad Hoc kategorijā ietilpst uzdevumi kuriem nav savs algoritms, tādējādi tie ir samērā unikāli un nav citādi katigorizējami. Šīs grupas uzdevumi bieži vien ir vienkārši, bet mēdz būt arī viltīgi. Sacensībās parasti šos uzdevums mēģina atrisināt pirmos, un parasti ir vismaz viens ad hoc uzdevums.

##Kategorijas

Vairums Ad Hoc uzdevumu ir iespējams atrisināt bez sarežģītām datu struktūrām. Ir iespējami dažāda tipa uzdevumi, kuri vairums ir salīdzinoši viegli, bet ir arī pinķerīgāki gadījumi.

###Kārtis

Ir daudz Ad Hoc problēmas, kuras ietver atpazīstamas spēles, to skaitā kāršu spēles. Parasti notiek kāda veida ievadteksta apstrāde, lai atdalītu mastus no to vērtībām vai līdzīgi. Viena metode, kas atvieglo šos uzdevumus ir apzīmēt kārtis ar skaitliskām vērtībām:

* kārava 2 (D2) →  0;
* kārava 3 (D3) → 1;
* kārava dūzis (DA) → 12;
* kreiča 2 (C2) → 13;
* utt.

###Šahs

Šahs ir vēlviena populāra spēle, kas parādas programmēšanas uzdevumos. Daži no uzdevumiem ir Ad Hoc, daži ietver kombinatoriku, piemēram, klasisks uzdevums ir novietot 8 dāmas uz 8x8 šaha laukuma, lai neviena no tām nespētu nokaut otru.

###Citas spēles

Programmēšanas uzdevumos parādās arī ne tik klasiskas spēles, kā piemēram: 

* desas;
* akmens šķēres papīrīts;
* cirks;
* bingo;
* boulings;
* u.c. 

Zināt, kā šis spēles ir jāspēlē, varētu būt noderīgi, bet vairumā gadījumu noteikumi ir doti uzdevuma aprakstā, lai nebūtu negodīgas priekšrocības tiem, kas ar šīm spēlēm nav pazīstami.

###Palindromi

Palindroms ir vārds, kurš rakstītā formā no abām pusēm un lasās vienādi - ALA, ABCBA, Z. Vārds SULA nav palindroms, jo, lai gan no abām pusēm veidojas loģiski vārdi, šie vārdi ir dažādi.

Palindromu atrašana jeb pārbaudīšana ir klasisks teksta apstrādes uzdevums. Visvienkāršākā metode palindroma pārbaudīšanai ir cikliski pārbaudīt no vārda **pirmā** simbola, līdz vārda **vidum**, salīdzinot ar vārda simetriski pretējo burtu no beigām. Vārds **A**BCB**A** ir palindroms. Sarežģītākiem palindromu uzdevumiem ir nepieciešami dinamiskās programmēšanas risinājumi.

###Anagrammas

Anagramma ir vārds (vai teikums), kuram, mainot simbolu secību, tiek iegūts cits vārds vai teikums. Tāpat, kā ar palindromiem, šis ir klasisks teksta apstrādes uzdevums.

Vienkāršākais veids, kā pārbaudīt, vai viens vārds/teikums ir otra anagramma, ir izskaitīt, cik reizes katrs simbols atkārtojas. Ja simbolu skaits ir vienāds - tā ir anagramma, ja atšķiras - tā nav anagramma. Nedrīkst aizmirst pārbaudīt simbolus kuri vienā vārdā neatkārtojas.

* **abc** ir vārda **bca** anagramma.
* **msd** nav vārda **msdz** anagramma, jo otrajā vārdā ir burts **z**

###Problēmas no dzīves

Uzdevumi, kuri iekļauj reālās dzīves (IRL) problēmas, ir vieni no interesantākajiem. Šo problēmu atrisināšana dod papildus motivāciju.

###Datumi, laiki, kalendārs

Šie uzdevumi arī ir no kategorijas “problēmas no dzīves”. Kā pirms tam minēts, šīs problēmas ir interesantāk risināt. Vieglāk šādus uzdevumus mēdz būt risināt ar Java programmēšanas valodu dēļ iebūvētajām bibliotēkām. Java valodai ir arī citi praktiski pielietojumi, kuru dēļ to ir vērts apgūt. Un atrisināt ir iespējams arī ar jebkuru citu valodu.

###Laika tērēšanas uzdevumi

Laika tērēšanas uzdevumi ir īpaša Ad Hoc kategorija. Šie uzdevumi ir pinķerīgi ar garu risinājumu un vairākiem īpašiem gadījumiem. Sacensībās šādi uzdevumi izceļ visefektīvākos programmētājus - kāds, kurš var implementēt sarežģītu, bet pareizu kodu dotajā laikā.

Risinot šos uzdevumus, tiek trenēta ātra un pareiza koda rakstīšana, kas palīdz rakstot citus algoritmus.

##Ieteikumi uzdevumu risināšanai

Lai nebūtu jaatceras, kurā bibliotēkā bija kura funkcija, var izmantot 

    #include <bits/stdc++.h>

Bet mācīšanās nolūkos labāk sākotnēji izmantot bibliotēku nosaukumus un šo bibliotēku pielietot pirms sacensībām / sacensībās.

<a href="http://en.wikipedia.org/wiki/Ad_hoc" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>