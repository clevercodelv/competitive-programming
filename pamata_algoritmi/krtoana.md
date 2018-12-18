# Kārtošana

Jēdzienu kārtošana parasti izmanto, lai pateiktu, ka kaut kas ir noteiktā secībā. Piemēram, skaitļi sakārtoti augošā secībā vai cilvēki sakārtoti pēc augumiem. Kārtošanā ir svarīgas divas lietas - secība un pēc kā kārtot. Programmēšanā arī var rasties vajadzība pēc kārtošanas, piemēram, ja ir ielasīti skaitļi masīvā un vajag tos izvadīt augošā secībā. Sarežģītāks variants būtu, ja tiktu ielasītas pārtikas preces un to cenas, un vajadzētu izvadīt preču nosaukumus sākot ar lētākajām līdz dārgākajām.

<a href="http://en.wikipedia.org/wiki/Sorting" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>

### Kārtošanas funkcija

C++ piedāvā kārtošanas funkcionalitāti, ja pievieno algorithm bibliotēku. Šī kārtošanas funkcija strādā ļoti ātri un droši vien vairumā gadījumu ir nevajadzīgi rakstīt savu kārtošanas funkciju, jo tik efektīvu un praktiski izmantojamu būs grūti izveidot, tiesa, dažreiz dēļ uzdevuma specifikas funkcija ir jāraksta pašam, bet tā gadās reti. Ko sort funkcija dara, tā saņem 3 argumentus, kur:

1. arguments ir masīva norāde, no kurienes sākt kārtot;
1. arguments ir masīva norāde, līdz kurai sākt kārtot + 1;
1. arguments ir funkcijas norāde (norāde ir pats funkcijas nosaukums), kuru izmantot, lai salīdzinātu divus mainīgos (neobligāts).

Vienkāršs sort funkcijas variants ir apskatāms 1. programmā.

```cpp
#include <iostream>
#include <algorithm>
#include <string.h>
using namespace std;

int main ()
{
    char mas[] = "sjdljksfnsdsljawq";
    // mas - simbolu virknes pirmā elementa adrese.
    // mas + strlen(mas) - simbolu virknes pirmā adrese nobīdīta pa tās garumu,
    // kas rezultātā iegūst nākamo adresi aiz masīva pēdējā elementa.
    sort(mas, mas + strlen(mas));
    cout << mas << endl; // Visi burti ir sakārtoti alfabētiskā secībā.

    return 0;
}
```

**1. programma** - simbolu masīva sakārtošana ar sort.

Tika minēts, ka 3 arguments ir funkcija. Funkcija var noderēt, piemēram, iepriekš minētās problēmas gadījumā par produktiem. Piemēram skatīt 2. programmu.

```
#include <iostream>
#include <algorithm>
#include <string>
using namespace std;

// Produkta struktūra.
struct produkts
{
    string nosaukums;
    double cena;
};

// Divu elementu salīdzināšanas funkcija kārtošanas procesā, lai katrā
// solī noteiktu, kurš elements ir lielāks par kuru.
bool salidzinasana(const produkts &a, const produkts &b)
{
    return a.cena < b.cena; // Salīdzinām elementus pēc cenām.
}

int main ()
{
    // Uztaisām produktu masīvu.

    string nosaukumi[] = {
        "maize",
        "saldejums",
        "ziepes",
        "cukurs",
        "kartupeli"
    };

    double cena[] = {
        1.12,
        2.50,
        0.41,
        1.00,
        0.55
    };

    produkts prod[5];

    for (int i = 0; i < 5; ++i)
    {
        prod[i].nosaukums = nosaukumi[i];
        prod[i].cena = cena[i];
    }

    // Sakārtojam produktus.
    sort(prod, prod + 5, salidzinasana);

    // Izvadām rezultātu.
    for (int i = 0; i < 5; ++i)
        cout << prod[i].nosaukums << " " << prod[i].cena << endl;

    return 0;
}
```

**2. programma** - produktu nosaukumu izvadīšana pēc cenas.

<a href="http://www.cplusplus.com/reference/algorithm/sort/" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>

### Kārtošanas algoritmi

Tika minēts, ka sort ir ļoti efektīvs un to realizēt ir pagrūti. Tas ir tāpēc, ka eksistē dažādi kārtošanas algoritmi un pieejas. Ir tādi, kas ir ļoti efektīvi konkrētās situācijās, ir tādi, kas ir universāli. Algoritmu sarežģītība variē ļoti plaši. Pa lielam varētu iedalīt kārtošanas algoritmus 4 daļās:

- **Ļoti neefektīvi un dažreiz paredzēti tikai kā joks.** Piemēram <a href="http://en.wikipedia.org/wiki/Bogosort" target="_blank">Bogosort</a>, kurš apskata virknes visas kombinācijas un, ja atrod tādu, kas ir sakārtota pēc vajadzīgā principa, tad to pieņem par atbildi. Šī algoritma sarežģītība ir O(N * N!), kas ir ļoti lēni - sacensību režīmā varētu vidēji 10 elementus tikai sakārtot efektīvi.
- **Kvadrātiski algoritmi** - parasti praksē netiek pielietoti, bet ir labs pamats kārtošanas algoritmu apguvei. Tiesa, ir daži kvadrātiski algoritmi, kuri konkrētās situācijās ir izmantojami.
- **Logaritmiski algoritmi** - šie pārsvarā ir universāli un efektīvi algoritmi, kuri savā starpā nedaudz atšķiras pēc ātrdarbības reālajā dzīvē, bet ne pārāk teorijā. sort funkcija izmanto šādus kārtošanas algoritmus un to kombinācijas. Šo algoritmu sarežģītība ir O(log(N) * N).
- **Lineāri algoritmi** - šie pārsvarā ir algoritmi, kas katrs ir pielietojams ierobežotiem ievaddatiem, dēļ pašu algoritmu darbības principiem. Daļa šo algoritmu iekrīt šajā kategorijā, jo izmanto faktu, ka lielā O notācija neizmanto konstantes. Tādēļ, piemēram, <a href="http://en.wikipedia.org/wiki/Radix_sort" target="_blank">Radix kārtošana</a>, kuras ātrdarbība ir N * bitu skaits skaitlī (int mainīgajiem tie būtu 32 biti) tiek kategorizēts zem lineāriem algoritmiem O(N), jo 32 ir konstante, bet tajā pašā laikā miljons skaitļus ātrāk sakārtotu O(N * log(N)) algoritms, kurš veiktu 1000000000 * 20 darbības.

Piemēram var apskatīt 3. programmā redzamo <a href="http://en.wikipedia.org/wiki/Bubble_sort" target="_blank">burbuļa kārtošanas</a> algoritmu.

```
#include <iostream>
#include <algorithm>
using namespace std;

void burbula_kartosana(int* sakums, int* beigas)
{
    int n = beigas - sakums;
    bool swapped;

    do
    {
        swapped = false;
        for (int i = 1; i < n; ++i)
            if (sakums[i - 1] > sakums[i])
            {
                swap(sakums[i - 1], sakums[i]);
                swapped = true;
            }
    } while (swapped);
}

int main ()
{
    int mas[] = {15, 3, 10, -9, -1, 0, 5, 4};
    burbula_kartosana(mas, mas + 8);
    for (int i = 0; i < 8; ++i)
        cout << mas[i] << endl;

    return 0;
}
```

**3. programma** - burbuļa kārtošanas metode.

<a href="http://en.wikipedia.org/wiki/Sorting_algorithm" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>