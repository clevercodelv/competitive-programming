#Algoritms

Matemātikā un datorzinātnē, pat reālajā dzīvē algoritms nozīmē darbību secību un to izpildi. Piemēram, lai nopirktu kaut ko veikalā, algoritms varētu būt sekojošs:

1. Uzvilkt jaku.
1. Iziet laukā.
1. Aiziet uz veikalu.
1. Ielikt grozā preci.
1. Samaksāt par precēm.
1. Aiziet mājās.


Paskatoties no matemātikas puses, mēs varētu izdomāt arī algoritmu, lai izrēķinātu kaut ko, piemēram, skaitli 2 pakāpē 4:

1. Sākam ar x = 1.
1. Pareizinam x ar 2. x = x * 2 = 2
1. Esam piereizinājuši x divnieku 1 reizi. Turpinām darbu.
1. Pareizinam x ar 2. x = x * 2 = 4
1. Esam piereizinājuši x divnieku 2 reizes. Turpinām darbu.
1. Pareizinam x ar 2. x = x * 2 = 8
1. Esam piereizinājuši x divnieku 3 reizes. Turpinām darbu.
1. Pareizinam x ar 2. x = x * 2 = 16.
1. Esam piereizinājuši x divnieku 4 reizes. Beidzam darbu.


Un esam ieguvuši, ka x = 16 ar šo algoritmu. Lai pirmajā mirklī nemulsinātu, kas ir x, tad tas ir vienkārši izvēlēts burts, kuru var iztēloties, kā matemātikas vienādojumos izmantotos burtus, piemēram, x = y + 3.

Datorzinātnēs algoritmus mēdz aprakstīt ar modeļiem. Modeļi visā savā būtībā ir vienkāršas diagrammas, jeb gluži kā domu zirneklis, kuru mēdz uzzīmēt, lai plānotu kaut ko. Modelis ir kaut kas, ko var uzzīmēt ļoti viegli uz papīra, lai aprakstītu algoritmu jau līdzīgā veidā, kā to varētu pierakstīt programmas kodā. Piemēram, 2 kāpināšanu 4 pakāpē modeli var redzēt 1. attēlā.

<center>

![Algoritms](/media/theory/algorithm.png)

**1. attēls** - algoritma modelis.

</center>

Sekojoši apzīmējumi tiek izmantoti šajā modelī:

- **Tukšais aplis** - algoritma sākums.
- **Taisnstūris** - darbība, piemēram, kaut kas, kas notiek, vai tiek izdarīts, tiek rakstīts taisnstūrī.
- **Rombs** - apzīmē nosacījumu. Ja nosacījums ir patiess (ja varam uz to atbildēt ar jā), tad sekojam Jā bultai, citādi sekojam Nē bultai.
- **Bulta** - bultas ir tādi kā ceļi, kuriem ir jāseko, lai saprastu, kā algoritms strādā. Algoritms strādā pareizi, ja sākot sekot bultām no modeļa sākuma elementa jeb tukšā apļa, mēs nonākam modeļa beigu elementā jeb pilnajā aplī (melnajā).
- **Pilnais aplis** - algoritma beigu elements. Veiksmīga algoritma izpildes gadījumā, sekojot bultām, mēs nonāksim beigu elementā.


<a href="http://en.wikipedia.org/wiki/Algorithm" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>