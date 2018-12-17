# Programmas struktūra

Lai gan C++ programmas var izskatīties dažādi. Tās var būt sarežģītas un ļoti īsas. Tās var sastāvēt no vairākiem failiem, kas ir apvienoti kopīgā direktoriju struktūrā, ko sauc par projektu. Bet pirmkārt mēs apskatīsim tikai programmas, kuras atrodas vienā failā, un otrkārt mūsu programmām būs vienota struktūra. Šo struktūru mēs jau apskatījām Hello world programmā. Atminēsimies, kā tā izskatījās apskatot 1. programmu.

```
#include<iostream>;

int main()
{
    std:cout << "Hello world" << std:endl;
    return 0;
}
```

<center>**1. programma** - Hello world programma.</center>

Programmas izpildās pa vienai rindiņai. Ja tiek izpildīta viena rinda, tad dators pāriet pie nākamās. To var iztēloties, kā grāmatas lasīšanu - arī cilvēks izlasa vienu rindiņu un pāriet pie nākamās.

**\#include&lt;iostream&gt;;** - rinda sākas ar \# zīmi. To apstrādā pirms kompilācijas preprocesors. Šī konkrētā rinda pasaka, ka programmā ir jāiekļauj bibliotēka priekš datu izvades uz ekrāna. 

**int main()** - šajā vietā sākās programmas darbības. int main(){} sauc par funkciju, līdzīgi, kā f() matemātikā. Kad programma sākas, pirmā tiek izpildīta main() funkcija. Tas, kas ir rakstīts starp {} iekavām pēc int main() tiek izpildīts, ja tiek izsaukta main() funkcija. Gluži kā funkcijas matemātikā, arī programmēšanā tām ir jāatgriež kāda vērtība, tādēļ starp {} ir return 0; komanda, kas saka, ka main() atgriež 0, bet tas pašlaik nav svarīgi.

Programmā nr. 1 mēs varam izdarīt vienu lietu, kas mums ļoti atvieglos dzīvi, ja kods kļūs liels. Pierakstot rindu using namespace std; mēs varam izvairīties no std: rakstīšanas priekšā cout, endl vai jebkur citur. Jauno programmu var skatīt 2. progrmmas piemērā.

```
#include<iostream>;
using namespace std;

int main()
{
    cout << "Hello world" << endl;
    return 0;
}
```

<center>**2. programma** - Hello world programma ar using namespace std;.</center>

Analizējot Hello world kodu varam uztaisīt vispārīgi izmantojamu šablonu (skatīt 3. programmu). Kad ir nepieciešams uzrakstīt kādu programmu, var komentāru aizvietot ar sintaktiski pareizu un semantiski sakarīgu kodu, un darbināt to.

```
#include<iostream>;
using namespace std;

int main()
{
    //Izpildāmās komandas
    return 0;
}
```

<center>**3. programma** - programmas šablons.</center>

<a href="http://www.cplusplus.com/doc/tutorial/program_structure/" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>