#Mainīgo redzamība

Redzamība apgabals programmēšanas valodās parasti nozīmē, kurā koda daļā kuri mainīgie ir redzami jeb izmantojami. Pa lielam C++ programmēšanas valodā mainīgie iedalās trīs daļās:

- **Lokālie** - šie mainīgie ir redzami konkrētajā redzamības apgabalā.
- **Globālie** - šie mainīgie ir redzami visur.
- **Statiskie** - tie paši globālie ar dažām niansēm.

Apskatot 1. programmu, var redzēt, kur tiek definēti vis veidu mainīgie. Pēc idejas jebkurš lokālais mainīgais ir mainīgais, kurš eksistē iekš funkcijas. Bet ir varianti, kad mainīgo var definēt, kā statisku, tādā gadījumā mainīgais ir globāls, bet redzams tikai faila ietvarā.

```
#include <iostream>
using namespace std;

int gvar; // Visi mainīgie ārpus funkcijām ir globāli.

void f()
{
    static int svar; // Visi mainīgie ar static priekšā ir globāli faila ietvarā.
}

int main ()
{
    int lvar; // Gandrīz visi mainīgie ir lokāli.
    f();

    return 0;
}

```

<center>**1. programma** - mainīgie ar dāžadiem redzamības apgabaliem.</center>

**Redzamības apgabals** - to veido \{\} iekavas. Ja mainīgais tiek definēts iekš \{\} iekavām, tad tas ir redzams tikai šo iekavu ietvarā un ir lokāls. Piemēram var skatīt 2. programmu.

```
#include <iostream>
using namespace std;

int main ()
{
    // Lokāli mainīgie.
    int a = 15;
    int b = 19;

    if (a == 15)
    {
        int b = 16; // Ir redzams tikai if {} iekavās.
        cout << b << endl; // Izvada 16.
    }

    cout << b << endl; // Izvada 19, jo int b = 16; beidza eksistēt pēc if } iekavas.

    return 0;
}
```

<center>**2. programma** - redzamības apgabul veidošanās ar \{\} iekavām.</center>