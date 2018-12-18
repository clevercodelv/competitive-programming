# Dinamiskā atmiņa

Dinamiskā atmiņa tiek veidota rezervējot ar new operatoru atmiņu un atbrīvojot to ar delete. Rezervēto atmiņu nevar izmantot citas programmas. Rezervējot atmiņu, tā ir pareizi jāatbrīvo, citādi var tikt rezervēta tik daudz atmiņa, ka dators sāk bremzēt vai tiek izmesta kļūda. Piemēru atmiņas rezervēšanai var apskatīt 1. programmā.

```cpp
#include <iostream>
using namespace std;

int main ()
{
    int* norade = new int; // Deklarējam norādi un inicializējam to piešķirot norādi uz rezervēto atmiņu.

    *norade = 15; // Rezervētajā atmiņā ieliekam 15.
    *norade *= 4; // Rezervētajā atmiņā esošajam skaitlim piereizinām 4.
    cout << *norade << endl; // Izvada 60.

    delete norade; // Atbrīvojam atmiņu.

    return 0;
}
```

**1. programma** - dinamiskās atmiņas izveidošana.
 

### Dinamiskie masīvi

Iepriekš runājot par masīviem, tos deklarējot, nebija iespēja izmantot masīva vārdu cita masīva vajadzībām un norādīt tā izmēru ar mainīgo. Dinamiskā atmiņa jeb dinamiskie masīvi piedāvā šādu iespēju. Nodaļā par norādēm tika runāts par to, ka masīva nosaukums ir norāde uz atmiņu, kur glabājas masīva dati. Dinamiskie masīvi tiek veidoti pēc šī principa:

1. Tiek izveidota norāde konkrēta tipa masīvam.
1. Tiek pieprasīta atmiņa un atmiņas sākuma adrese tiek piešķirta norādei.
1. Varam ar norādi piekļūt dinamiskajam masīvam tāpat, kā parastajam masīvam.

Šis princips ir attēlots 2. programmā. delete[] nozīmē, ka tiek atbrīvots nevis mainīgais, bet masīvs.

```
#include <iostream>
using namespace std;

int main ()
{
    int garums = 10;
    int* mas = new int[garums]; // Ar new int rezervē masīva atmiņu ar izmēru garums jeb 10.

    for (int i = 0; i < garums; ++i)
        mas[i] = i * i; // Dinamisko masīvu varam izmantot kā parasto masīvu.

    for (int i = garums - 1; i >= 0; --i)
        cout << i << " kvadrata ir " << mas[i] << endl;
    cout << endl;

    delete[] mas; // Atbrīvo rezevēto atmiņu, lai varētu to rezervēt citas programmas.

    return 0;
}
```

**2. programma** - dinamiskā masīva izveidošana.
 

### Vairāku dimensiju dinamiskie masīvi

Lai saprastu, kā pareizi izveidot vairāku dimensiju dinamiskos masīvus, ir nepieciešams saprast to, ka jēdziens vairāku dimensiju masīvi patiesībā ir tas pats, kas masīvs, kurš satur masīvus, kurš satur masīvus u.t.t. (skatīt 1. attēlu). Lai labāk saprastu, kā tehniski veidot 2 dimensiju dinamiskos masīvus, var apskatīt 3. programmu.

![2 dimensiju dinamiskais masivs](/media/theory/masivs_dinamisks.png)

**1. attēls** - 2 dimensiju masīva norāžu diagramma.
 

```
#include <iostream>
#include <cstdlib>
#include <time.h>
using namespace std;

// Programma uzģenerē random izmēra 2 dimensiju masīvu ar random vērtībām tajā.
int main ()
{
    srand(time(NULL));

    int platums = rand() % 10 + 5;
    int augstums = rand() % 10 + 5;
    int** mas; // Norāde, kas norāda uz norādi, kas norāda uz int.

    mas = new int*[augstums]; // Rezervējam masīvu ar norādēm, kas norāda uz int.
    for (int i = 0; i < augstums; ++i)
        mas[i] = new int[platums]; // Katrs masīva elements ir norāde, kurai piešķiram norādi uz rezervēto atmiņu.

    for (int i = 0; i < augstums; ++i)
        for (int j = 0; j < platums; ++j)
            mas[i][j] = rand();

    for (int i = 0; i < augstums; ++i)
    {
        for (int j = 0; j < platums; ++j)
            cout << mas[i][j] << " ";
        cout << endl;
    }

    for (int i = 0; i < augstums; ++i)
        delete[] mas[i]; // Atbrīvojam katru 2. dimensijas norādes masīvu.

    delete[] mas; // Atbrīvojam 1. dimensijas masīvu ar norādēm.

    return 0;
}

```

**3. programma** - 2 dimensiju dinamiskā masīva izveidošana.
 

<a href="http://www.cplusplus.com/doc/tutorial/dynamic/" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>