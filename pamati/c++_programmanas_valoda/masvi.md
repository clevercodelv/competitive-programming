# Masīvi

Iztēlojamies situāciju, ka mēs gribam ielasīt no komandrindas 5 skaitļus un izvadīt tos apgrieztā secībā. Pašlaik mums nāktos veidot 5 mainīgos un ielasīt skaitļus tajos, lai veiktu šo uzdevumu (skatīt 1. programmu).

```cpp
#include <iostream>
using namespace std;

// Šeit definējot mainīgos, tiem tiek automātiski piešķirta vērtība 0.
// Mainīgie šeit kļūst pieejami visā programmā.
int sk0, sk1, sk2, sk3, sk4;

int main ()
{
    cin >> sk0 >> sk1 >> sk2 >> sk3 >> sk4;
    cout << sk4 << " " << sk3 << " " << sk2 << " " << sk1 << " " << sk0 << endl;

    return 0;
}
```

**1. programma** - 5 skaitļu apgriešana ar 5 mainīgajiem.

Kas notiek, ja mēs 5 skaitļu vietā gribam šo pašu algoritmu izpildīt ar 100 vai 1 miljonu skaitļiem? Rakstīt 100 mainīgos būtu pārāk ilgi. Tā vietā var izmantot masīvus. Masīvus var iztēloties gluži kā tabulas, kur katrai šūnai var piekļūt ar indeksu jeb skaitli, kas raksturo pozīciju tabulā (skatīt 1. attēlu un 2. programmu).

![Masīvs](/media/theory/masivs.png)

**1. attēls** - masīvs.

```
#include <iostream>
#define SKAITS 5 // Izmantojam macros komandu, lai noteiktu ielasāmu elementu skaitu. Var būt pat 1 miljons.
using namespace std;

int sk[SKAITS]; // SKAITS pirms kompilācijas tiks aizvietots ar 5.

int main ()
{
    for (int i = 0; i < SKAITS; ++i)
    {
        // Masīva elementam katrā cikla iterācijā pozīcijā i ielasām skaitli.
        // Cikls ilgs SKAITS reižu un i mainīsies no 0 līdz 4 (jo 4 < 5).
        cin >> sk[i];
    }

    //Ejam no 4 līdz 0 un izvadām visus sk elementus.
    for (int i = SKAITS - 1; i >= 0; --i)
    {
        cout << sk[i] << " ";
    }
    cout << endl;

    return 0;
}
```

**2. programma** - 5 skaitļu apgriešana ar masīvu.

### Masīvu inicializācija

Masīva nosaukums patiesībā ir tāds pats mainīgais, kā aprasto mainīgo nosaukumi. Tāpat, kā mainīgos var inicializēt, tā var arī masīvus. Inicializēšana masīvu gadījumā nozīmē, ka masīva "tabulā" tiek ierakstītas vērtības (skatīt 3. programmu). Inicializējot masīvu bez norādīta masīva izmēra iekš [] iekavām, masīvs kļūst tik liels, cik elementu ir inicializācijā. Inicializējot fiksēta izmēra masīvu tikai ar {} iekavām, tas saturēs tikai 0 vērtības.

```
#include <iostream>
using namespace std;

int main ()
{
    int mas1[5] = {2, 4, 8, 16, 32}; // Inicializējam masīvu.
    // for ciklu var rakstīt bez {} iekavām. Ja tās nav,
    // tad tiek izpildīta tikai pirmā komanda aiz () iekavām.
    for (int i = 0; i < 5; ++i) cout << mas1[i] << " ";
    cout << endl;

    int mas2[] = {3, 9, 27}; // Inicializējam masīvu. Inicializācijā ir 3 elementi, tādēļ masīva izmērs ir 3.
    for (int i = 0; i < 3; ++i) cout << mas2[i] << " ";
    cout << endl;

    int mas3[6] = {}; // Inicializējot masīvu ar {}, masīva elementi ir 0.
    for (int i = 0; i < 6; ++i) cout << mas3[i] << " ";
    cout << endl;

    return 0;
}
```

**3. programma** - masīva inicializācija.

### Vairāku dimensiju masīvi

Vairāku dimensiju masīvs ir praktiski masīvs, kurš satur nevis skaitļus, bet citus masīvus. Piemēram, apskatīsim 2D masīvu. 2D masīvs ir vistiešākajā veidā tabula (skatīt 2. attēlu). 2D masīvi var glabāt, piemēram, skaitļu tabulu (skatīt 4. programmu).

![Masīvs](/media/theory/masivs_2d.png)

**2. attēls** - masīvs 2D.

```
#include <iostream>
using namespace std;

int mas[5][6]; // Katru dimensiju definē ar [] iekavām, kuras satur dimensijas izmēru.

int main ()
{
    // Cikls ciklā arī drīkst atrasties, jo cikls ir tāda pati programmas komanda, kā jebkas cits.
    for (int i = 0; i < 5; ++i)
    {
        for (int j = 0; j < 6; ++j)
        {
            cin >> mas[i][j]; // Masīva tabulas elementam jeb šūnai var piekļūt norādot abas dimensijas pozīcijas.
        }
    }

    cout << endl << "Tika ievadīta tabula: " << endl;

    for (int i = 0; i < 5; ++i)
    {
        for (int j = 0; j < 6; ++j)
        {
            cout << mas[i][j] << " ";
        }
        cout << endl;
    }

    return 0;
}
```

**4. programma** - 2D masīva lietojums.

Lai piekļūtu 2D masīva vienai šūnai, ir nepieciešams norādīt katru dimensiju. Ja mēs piekļūtu mas[1][2] elementam, tad vizuāli tas izskatītos tā, kā 3. attēlā.

![Masīvs](/media/theory/masivs_2d_access.png)

**3. attēls** - piekļūšana 2D masīva elementam.

<a href="http://www.cplusplus.com/doc/tutorial/arrays/" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>