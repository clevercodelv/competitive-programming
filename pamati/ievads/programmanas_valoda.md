#Programmēšanas valoda

Iepriekš runājām par algoritma jēdzienu un programmēšanu. Ja cilvēkam saprotamā veidā mēs algoritmu aprakstījām ar saraksta palīdzību un modeļiem, tad datoram šāds formāts nav īsti saprotams. Šī iemesla dēļ nākas kaut kā savādāk paziņot komandas. Vislabākais veids protams būtu ar 0 un 1, bet šāds formāts ir pārāk nesaprotams cilvēkam. Meklējot kompromisu sākotnēji radās Asamblera programmēšanas valoda, jeb konkrētu komandu kopums, kuras cilvēks varēja saprast un varēja pārtulkot uz datoram saprotamu formātu. Laika gaitā veidojās jaunas programmēšanas valodas, kuras balstījās uz citām programmēšanas valodām vai tika tulkotas pa taisno uz datoram saprotamu formātu 0 un 1. 

Mūsdienās programmēšanas valodas ir izveidotas dažādiem nolūkiem un to principi mēdz atšķirties. Programmēšanas valodas izmanto mācībām, militāriem nolūkiem, dažādām biznesa vajadzībām. Svarīgi elementi programmēšanas valodās ir:


**Sintakse** - šis vārds arī daudzās citās jomās nosaka, kā precīzi pierakstīt tekstu kādas valodas ietvarā. Sintakse nosaka, kā jāizmanto punkti, iekavas un citi simboli, lai panāktu kaut kādu programmas funkcionalitāti. Zemāk ir redzams kods (skatīt 1. programmu), kurš ir tāds, kāds tas ir tieši dēļ sintakses.

```
#include<iostream>
using namespace std;

int main()
{
    int x = 1;
    int pakape = 4;
    while (pakape > 0)
    {
        x = x * 2;
        pakape = pakape - 1;
    }
    cout << x << endl;
}
```

<center>**1. programma** - 2 kāpināšana pakāpē 4 C++ programmēšanas valodā.</center>

**Semantika** - ja sintakse raksturo, kā pierakstīt programmu, tad semantika raksturo programmas nozīmi. Piemēram, 1. programmas koda izskatu nosaka C++ standarts, bet tā nozīmi raksturo semantika. Šīs programmas semantika ir 2 kāpināt 4 pakāpē.

<a href="http://en.wikipedia.org/wiki/Programming_language" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>