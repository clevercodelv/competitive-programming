#Bibliotēku izmantošana

C++ valoda praktiski nav iedomājama bez bibliotēkām. Neizmantojot tās, ļoti daudz kas ir jāprogrammē pašam. Bibliotēku mērķis ir sniegt iespēju izmantot citu cilvēku izmantotu bibliotēku funkcionalitāti. Šajā nodaļā un vispār šīs mācību programmas ietvarā nerunāsim par to, kā rakstīt C++ bibliotēkas, bet apskatīsim, kā tās lietot un biežāk lietojamās no tām.

Iepriekš rakstītajā failu lasīšanas / rakstīšanas piemērā izmantojām #include <fstream> bibliotēku. Patiesībā šī ir macros komanda #include, kura pasaka, ka vēlamies izmantot fstream bibliotēku. Bibliotēkas nosaukums ir jāiekļauj <> iekavās. Ieteicams būtu #include komandas likt programmas sākumā. Dažreiz vienai bibliotēkai var būt dažādi nosaukumi, piemēram, cmath un math.h. Bibliotēkas dažreiz beidzās ar *.h paplašinājumu, jo tās tiek definētas **Header** failos, kurus paplašina ar .h, bet patiesībā tie ir tādi paši teksta faili, kā .cpp faili. Tajos tiek definēta visa bibliotēka, jeb tikai prototips tai un realizācija prototipam tiek atdalīta citā cpp failā. Bet par prototipiem ir iespējams plašāk izlasīt tīmeklī, tos neapskatīsim šeit.

Dažas populāras un noderīgas bibliotēkas tiek uzskaitītas 1. tabulā.

Bibliotēkas nosaukums | Apraksts
---|---
cmath | Satur matemātikas funkcijas, kā sin, cos u.c.
cstring | Simbolu masīvu apstrādes funkcijas.
cstdio | Funkcijas datu ievadīšanai un izvadīšanai.
cstdlib | C standarta rīku bibliotēka.
algorithm | Funkcijas darbam ar masīviem un atmiņas diapazoniem. Kārtošana, meklēšana.
string | Bibliotēka, lai izmantotu string tipu. Piedāvā arī funkcionalitāti string tipa mainīgo apstrādei.


<center>**1. tabula** - populāras C++ bibliotēkas sporta programmēšanai.</center>

<a href="http://www.cplusplus.com/reference/" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>