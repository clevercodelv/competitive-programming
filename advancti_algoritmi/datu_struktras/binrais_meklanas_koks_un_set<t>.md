# Binārais meklēšanas koks un set&lt;T&gt;

Binārai meklēšanas koks ir datu struktūra, kurā var glabāt, dzēst un ātri atrast vērtības. Šādam kokam atšķirībā no parastā binārā koka ir viena īpašība - virsotnes kreisajā apakškokā visi elementi ir mazāki par virsotnes elementu un labajā apakškokā visi elementi ir lielāki par virsotnes elementu. Binārā meklēšanas koka struktūra tiek veidota ar C++ struktūras palīdzību un katrs struktūras tipa mainīgais ir binārā koka virsotne, tādēļ katram šim mainīgajam ir jāsatur norādes uz kreiso, labo virsotni jeb bērniem un pati virsotnes vērtība. Piemēru šādai struktūrai var apskatīt 1. programmā. Mērķis šādam binārajam meklēšanas kokam ir tāds, ka ievietojot vērtību binārajā kokā, notiek sekojošs rekursīvs algoritms.

1. Sāk ar koka sakni.
1. Ja saknes vērtība ir vienāda ar ievietojamo, tad pārtrauc darbu.
1. Ja saknes vērtība ir lielāka par ievietojamo, tad iet pa kreisi,
1. Citādi iet pa labi.
1. Ja tajā zarā, kurā būtu jāiet, nav norāde uz virsotni, tad.
    1. Rezervē jaunu virsotnes tipa atmiņas apgabalu.
    1. Piešķir jaunajai virsotnei ievietojamo vērtību.
    1. Norāda norādi uz jauno virsotni.

Meklēšana notiek līdzīgi, kā ievietošana, bet dzēšot virsotni, ja abi zari satur virsotnes, tad atbrīvo dzēšamās virsotnes atmiņu un pievieno pa jaunu labējo un kreiso virsotni. C++ struktūra izskatās, kā zemākajā piemērā.

```cpp
struct node
{
    node *left = NULL, *right = NULL;
    int item;
};
```

Eksistē arī **bināri balansēta koku** struktūra, jo, piemēram, ievietojot sakārtotu sarakstu šādā struktūrā izveidosies koks, kurš līdzināsies sarakstam, kas nebūs pārāk efektīvi. Balansētie binārie koki šādu problēmu risina.

<a href="http://en.wikipedia.org/wiki/Binary_search_tree" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>

### STL set&lt;T&gt;

C++ programmēšanas valodā ir tips, kurā var glabāt mainīgos, izdzēst un meklēt O(log(N)) laikā. Darbības ar šo struktūru ir ļoti līdzīgas, kā binārajam meklēšanas kokam - find, lower_bound, upper_bound, insert, erase. Piemēru set izmantošanai var redzēt 1. programmā.

```
#include <iostream>
#include <set>
#include <string>
using namespace std;

int main()
{
    string cmd;
    set<string> s;

    do
    {
        cin >> cmd;
        if (cmd == "insert")
        {
            cin >> cmd;
            s.insert(cmd);
            cout <<"\"" << cmd << "\" inserted." << endl;
        } else if (cmd == "find")
        {
            cin >> cmd;
            if (s.find(cmd) != s.end())
                cout <<"\"" << cmd << "\" found." << endl;
            else
                cout <<"\"" << cmd << "\" not found." << endl;
        } else if (cmd == "erase")
        {
            cin >> cmd;
            s.erase(cmd);
            cout <<"\"" << cmd << "\" erased." << endl;
        }
    } while(cmd != "exit");

    return 0;
}
```

**1. programma** - STL set piemērs.

<a href="http://www.cplusplus.com/reference/set/set/" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>