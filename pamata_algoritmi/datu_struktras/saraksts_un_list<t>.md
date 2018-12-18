# Saraksts un list&lt;T&gt;

Saraksts ir lineāra datu struktūra, kuras katrs elements norāda uz elementu pa kreisi (skatīt 1. attēlu). Sarakstam ir sekojošas īpašības:

- Elementa meklēšana notiek **O(N)** laikā izejot cauri sliktākajā gadījumā visiem elementiem.
- Elementa dzēšana notiek **O(1)** laikā, jo, ja meklēšana ir veikta un elements ir atrasts, tad tā izdzēšana ir iepriekšējā elementa saites norādīšana uz nākamo elementu un atmiņas atbrīvošana.
- Elementa pievienošana notiek **O(1)** laikā, jo ar Astes norādi var noteikt pēdējā elementa atrašanās vietu, kurā pieglabā, ka nākamais elements ir jaunais elements un Astei piešķir jaunā elementa adresi.

![Vienvirziena saraksts](/media/theory/list.png)

**1. attēls** - saraksta diagramma.

<a href="http://en.wikipedia.org/wiki/Linked_list" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>

### STL bibliotēka list

list bibliotēkā ir realizēta saraksta funkcionalitāte. Tā lietošanas piemērs ir apskatāms 1. programmā.

```
#include <iostream>
#include <list>
using namespace std;

int main ()
{
    // Izveidojam saraksta mainīgo ar saraksta tipu.
    // <> iekavās tiek likts tips (elementārs vai komplekss), kura mainīgie glabājas sarakstā.
    list<int> l;

    l.push_back(2334);
    l.push_back(9876);
    l.push_back(33);
    l.push_back(9);
    l.push_back(2230);
    l.push_back(0);

    // list<int> pieliekot beigās ::iterator iegūst saraksta viena elementa norādes mainīgo.
    // Šīs norādes atšķirās no parastajām, jo patiesībā tās ir klases jeb kompleksie tipi,
    // bet par to var nemaz nedomāt.
    list<int>::iterator it;
    it = l.begin(); // Saraksta pirmā elementa norādi var iegūt šādi.
    while (it != l.end()) // Saraksta nākamā atmiņas apgabala adresi aiz pēdējā elementa var iegūt šādi.
    {
        cout << *it << endl; // Saraksta vienības vērtībai var piekļūt ar *
        it++; // Uz nākamo elementu var pāriet ar ++ operatoru.
    }

    return 0;
}
```

**1. programma** - list bibliotēkas lietojums.

Vairāk metodes var apskatīt zemāk esošajā informācijas avotā.

<a href="http://www.cplusplus.com/reference/list/list/" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>