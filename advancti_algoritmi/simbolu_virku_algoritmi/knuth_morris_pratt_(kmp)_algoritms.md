# Knuth-Morris-Pratt (KMP) algoritms

Problēma skan tā - ir dotas divas simbolu viknes M = "ABCDABAABCABCDEABCDG" un W = "ABCDE". Uzdevums ir atrast, kurā pozīcijā simbolu virknē M pirmo reizi ir atrodama simbolu virkne W. Viens variants varētu būt apskatīt visus variantus jeb pielīdzināt W virknei M no pozīcijas 0 un 1, un 2, u.t.t. Piemēru var skatīt 1. programmā.

```
#include <iostream>
#include <string.h>
using namespace std;

int main()
{
    char M[] = "ABCDABAABCABCDEABCDG";
    char W[] = "ABCDE";
    int lenM = strlen(M);
    int lenW = strlen(W);
    int pos = -1;

    for (int i = 0; i < lenM - lenW && pos < 0; ++i)
    {
        bool isOk = true;
        for (int j = 0; j < lenW && isOk; ++j)
            if (M[i + j] != W[j])
                isOk = false;
        if (isOk) pos = i;
    }

    cout << pos << endl;

    return 0;
}
```

<center>**1. programma** - rupjā spēka simbolu virknes meklēšana.</center>

Var redzēt, ka algoritms sliktākajā gadījumā izpildīsies O((strlen(M) - strlen(W)) * strlen(W)). Tiesa, vidēji uz gadījuma tekstiem saržģītība būs tuvu O(strlen(M)), bet sliktākais gadījums var būt diezgan slikts. Eksistē efektīvāks algoritms, to sauc par KMP jeb Knuth-Morris-Pratt algoritmu. Tas sastāv no divām daļām.

1. Aprēķina palīgtabulu T priekš simbolu virknes W.
1. Aprēķina W pozīciju iekš M.

Masīvs T sastāv no elementiem, kur T[i] apzīmē garāko W prefiksa pēdējā elementa pozīciju W sākumā pozīcijā i iekš masīva W. Piemēram, ja W = "ABCDABACD", tad T[5] == 1, jo "AB" ir W prefiks garumā 2 un 'B' atrodas pozīcijā 1. Tiek pieņemts, ka T[0] = -1 un T[1] = 0. Piemēram, T = {-1, 0, 0, 0, 0, 1, 2, 0, 1, 0}. Šo masīvu var aprēķināt lineārā laikā (skatīt 2. programmas funkciju knp_table). T var izmantot, lai atšķirībā no rupjā spēka metodes ar if secinot, ka M[i + j] != W[j] nevis sāktu M salīdzināšanu ar W no jauna, bet zinot, ka tajā vietā, kur radās nevienādība T[j] apzīmē, cik garš prefiks jau ir vienāds līdz M[i + j] elementam, tādēļ i = i + j - T[j] un j = T[j] (piemēru skatīt 2. programmā).

```
#include <iostream>
#include <string.h>
using namespace std;

int T[100];
char M[] = "ABCDABAABCABCABCDABACDDEABCDG";
char W[] = "ABCDABACD";
int lenM;
int lenW;

void knp_table()
{
    T[0] = -1;
    T[1] = 0;
    int i = 0, j;
    for (int j = 2; j < lenW; ++j)
    {
        if (W[i] == W[j])
        {
            T[j] = i++;
        } else {
            i = 0;
            T[j] = i;
            if (W[i] == W[j])
                ++i;
        }
    }
};

int main()
{
    lenM = strlen(M);
    lenW = strlen(W);
    int pos = -1;

    int i = 0, j = 0;
    while (i + j < lenM && pos < 0)
    {
        if (W[j] == M[i + j])
        {
            if (j == lenW - 1)
                pos = i;
            j++;
        } else {
            if (T[i] > -1) {
                i = i + j - T[j];
                j = T[j];
            } else {
                j = 0;
                i++;
            }
        }
    }

    cout << pos << endl;

    return 0;
}
```

<center>**2. programma** - KMP simbolu virknes meklēšana.</center>

<a href="http://en.wikipedia.org/wiki/Knuth%E2%80%93Morris%E2%80%93Pratt_algorithm" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>