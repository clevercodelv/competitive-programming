# Uzdevumu testēšana

Dažreiz sacensību laikā vai pildot uzdevumu, lai pārliecinātos, ka kods ir pareizs vai, lai atrastu kļūdu, ir nepieciešams pašam patestēt, kā programma strādā. Piemēram, ja programma izvada i-to Fibonači skaitli, tad būtu vērtīgi programmu pārbaudīt ar ievaddatiem 0, 1, -1, 50, u.t.t. Tālāk tiek apspriests, kā ātri un labāk izvēlēties testa datus, lai pārbaudītu programmu. Praktizējoties uzdevumu pildīšanā, laika gaitā rodas pašam savi paņēmieni un tehnikas, kas var evolucionēt no kādiem zemāk uzskaitītajiem paņēmieniem.

### Sacensības un ierobežotais laiks

Pirms vispār apsvērt uzdevuma testēšanu, ir jāņem vērā laiks. Sekojošie apsvērumi ir noteikti jāpārdomā pirms izšķiršanās par testēšanas pieeju:

- Sacensību laikā veicot pārāk dziļu un lielu testēšanu no vienas puses var izvairīties no nepareiza vai daļēji nepareiza risinājuma.
- No otras puses ir jāuzmanās no pārāk lielas laika patērēšanas, jo testēšanas laiku var patērēt cita uzdevuma risināšanai vai domāšanai, kas var kopsummā dot labākus punktus. 
- Vēl viens apsvērums, kuru ir vērts ņemt vērā, ir, kāda ir sacensību vērtēšanas sistēma. Ja punktus dod tikai par pilnībā atrisinātu uzdevumu un par katru iesūtījumu samazina vērtējumu, noteikti vajadzētu patestēt uzdevumu pirms iesūtīšanas. Ja punktus dod arī par nepilnīgu risinājumu vai arī punktu skaits ir atkarīgs no iesūtīšanas laika kopš sacensību sākuma, tad vajadzētu apsvērt, vai tiešām uzdevumam ir nepieciešama testēšana.

### Ievaddatu paraugi

Sporta programmēšanā pārsvarā uzdevumam tiek doti līdzi ievaddatu paraugi. Kļūdīgi ir domāt, ka uzrakstot programmu, pietiek to patestēt ar šiem ievaddatiem un, ja tā strādās, tad programma būs pareiza. Patiesībā pārsvarā šie dati der tikai tam, lai pirmo reizi palaistu savu programmu un pārbaudītu, vai ievaddati tiek ielasīti pareizi. Lai pārbaudītu savu programmu, ir nepieciešams veikt nedaudz pārdomātāku testēšanu. Tiesa, ja apsvērumi ir par labu mazākai testēšanai un ir pietiekami liela pieredze, lai secinātu, ka uzdevums ir pareizs, tad var arī veikt minimālu testēšanu.

### Robežgadījumi, stūra gadījumi

Uzdevumiem parasti ir definēti kādi intervāli. Piemēram, ja mērķis ir noskaidrot, vai skaitlis ir pirmskaitlis, uzdevumā būs teikts, kādā intervālā pārbaudāmais skaitlis atrodas. Ja intervāls būtu [2, 1000], tad varētu definēt šādus testus vai daļu no tiem:

1. Intervāla galos - 2, 1000.
1. Pirms intervāla galiem - 5, 995. Šajās vērtībās mēdz būt biežāk kļūdas, kā intervālu galos.
1. Intervāla vidū un ap to - 450, 500, 635.

Par testu datiem var nākties domāt arī vairākās dimensijās gadījumos, ja ievaddatu parametri ir vairāk kā viens. Piemēram, uzdevumā, kur skaitlim N un M ir jānoskaidro lielākais kopīgais dalītājs, un 1 <= N, M <= 1000, var izšķirt šādus testa gadījumus priekš (N; M):

1. Stūra gadījumi: (1; 1), (1; 1000), (1000; 1), (1000; 1000).
1. Gandrīz stūra gadījumi: (4; 5), (5; 998), (998; 4), (998; 997).
1. Robežgadījumi: (1; 455), (453; 1); (1000; 455), (453; 1000).
1. Gandrīz robežgadījumi: (4; 455), (453; 5); (998; 455), (453; 995).
1. Intervālu vidū un ap to: (500; 500), (455; 498).

Var secināt, ka, augot ievaddatiem, arī rekomendējamo testpiemēru skaits augs. Kas notiks, ja ievaddatos tiks dota N * M matrica. Vai testpiemēros būs jāņem vērā arī katrs matricas skaitlis? Nu tas ir atkarīgs no testētāja, ja kādam ir vēlme gadiem testēt tādu programmu, tad jā, bet vajadzētu šādās situācijās izdomāt ko gudrāku, piemēram, testpiemēros ņemt vērā tikai N un M mainīgos, un ģenerēt gadījuma matricu. Patiesībā jau ar diviem mainīgajiem var sanākt pailga testēšana pēc šādas stratēģijas, it īpaši, ja nav pierasts pie šādas pieejas - to arī vajadzētu ņemt vērā. Dažreiz var izvēlēties neapskatīt visus konkrētās grupas gadījumus (stūrus vai robežas) vai izlaist kādu grupu.

Gadījumos, kad ievaddati ir īpatnēji, var mēģināt pielāgot šo pieeju kādam no netieši dotajiem parametriem. Piemēra, ja tiek dota simbolu virkne, par kuru ir jāpasaka, vai tas ir palindroms, var uztvert nevis pašu simbolu virkni par analizējamo parametru, bet tās garumu un veidot testa datus simbolu virknes garuma intervālam.

Var redzēt, ka runājot par 1 mainīgo ir viena vērtība testiem, runājot par diviem mainīgajiem, ir divas vērtības testiem, kas izskatās gandrīz kā koordinātes. Lai vieglāk būtu vizualizēt veidu, kā izvēlēties testpiemērus un testu grupas, 1 parametra gadījumā var iztēloties 1 dimensijas nogriezni, kas apzīmē parametra intervālu (skatīt 1. attēlu). Ja parametri ir 2 vai N, tad var iztēloties 2 vai N dimensiju ierobežotu figūru, kur katra figūras dimensija ir parametra intervāls (skatīt 2. attēlu). Stūra gadījumi šajos piemēros veidojas figūras stūros un robežgadījumi veidojas uz figūru šķautnēm.

<center>
<img alt="1 parametra testpiemēru vizualizācija" src="/media/theory/test_1_dimensija.png"/>
**1. attēls** - 1 parametra testpiemēru vizualizācija.
</center>

<center>
<img alt="2 parametru testpiemēru vizualizācija" src="/media/theory/test_2_dimensija.png"/>
**2. attēls** - 2 parametru testpiemēru vizualizācija.
</center>

### Speciālgadījumi

Programmēšanā speciālgadījumi ir testpiemēri, kas nav obligāti stūra gadījumi vai robežgadījumi, bet īpaši gadījumi, kas pārbauda kādu speciālu programmas funkcionalitātes daļu. Piemēram, ja programmai ir jāpārbauda, vai skaitlis ir pirmskaitlis, var to notestēt pret vērtību 1, kura atbilst definīcijai "dalās tikai pats ar sevi un 1", bet matemātikā šis ir pirmskaitļu izņēmums. Bieži vien speciālgadījumi var būt tukšas simbolu virknes, vērtība 0 un kādas citas īpatnējas vērtības, bet šeit nav viena vienota sistēma, kā pieiet testu veidošanai. Atkarībā no problēmas un tās specifikas ir jāpadomā, vai neeksistē kāds īpašs testpiemērs šai problēmai.

### Testu kopa

Mēdz gadīties uzdevumi, kuru ievaddati ir patiesībā testu kopa, jeb vairāki testi vienos ievaddatos. Šādā situācijā vērtīgi ir pamēģināt kopas ar vairākiem testiem un iespējams ar vienādiem testiem vienā kopā, lai redzētu, ka testi atgriež vienādus rezultātus.

### Testpiemēru ģenerēšana

Eksistē vairāki varianti, kā var uzģenerēt testpiemērus:

- **Uzzīmēt uz papīra** - piemēram, cenšoties izdomāt risinājumu un zīmējot uz papīra idejas var tīšām vai netīšām sazīmēt labus testpiemērus.
- **Uzprogrammēt ģeneratoru** - vienkāršiem ievaddatiem šo nevajadzētu izmantot, piemēram, ja ievaddatos ir viens skaitlis. Bet, ja programmas ievaddati ir apjomīgi, piemēram, līdz 1000x1000 matricas izmēriem, tad ir vērts izmantot šo pieeju. Tiesa, vajadzētu ģenerēt pēc iespējas "dumjākus" testa datus ar rupjā spēka pieeju, jo tas aizņems mazāk laika.
- **Excel un citas lietotnes** - Excel piedāvā lielisku funkcionalitāti ar savām funkcijām. Ja izdomā, kā testa datus saģenerēt ar Excel funkciju, tad to var izdarīt diezgan lieliem testa datiem. Piemēra, Fibonači rindu ir ļoti elementāri uzģenerēt. Iespējams ir pieejamas citas lietotnes, kas var palīdzēt testa datu ģenerēšanai - ir jāvadās pēc situācijas.


<a href="http://www.quora.com/Competitive-Programming/How-do-I-learn-to-quickly-write-test-cases-for-algorithm-competitions-like-TopCoder-SRMs-and-ACM-ICPC" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>