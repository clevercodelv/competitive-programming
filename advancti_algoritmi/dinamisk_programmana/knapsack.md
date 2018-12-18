# Knapsack

Knapsack problēma ir sekojoša. Zaglim ir mugursoma un tas ielaužas mājā. Mājā ir dažādu izmēru priekšmeti ar dažādām vērtībām. Mērķis ir ielikt somā priekšmetus ar pēc iespējas lielāku kopējo vērtību.
Problēmu klasiski mēdz risināt ar 0/1 knapsack vai DP knapsack algoritmu. Ir, protams, iespējamas algoritmu modifikācijas. 

### 0/1 knapsack

0/1 knapsack risinājums ir diezgan neoptimāls, bet risinājuma ideja ir lietderīga un varbūt pat intuitīvāka par DP algoritmu. Ideja ir apskatīt visus variantus, kādos iespējams somā ielikt priekšmetus. Ideja nāk no kombinatorikas pasaules. To var izdarīt visās kombinācijās katram priekšmetam piekārtojot 0 vai 1.

* 0 - priekšmets netiek paņemts.
* 1 - priekšmets tiek paņemts.

Ja ir N priekšmeti, tad katru priekšmetu var paņemt vai nepaņemt un tas veido 2^N dažādus priekšmetu paņemšanas kombinācijas. To ir iespējams izdarīt ar skaitļu palīdzību, jo 0 un 1 ir divi bita stāvokļi un skaitļi sastāv no bitiem. Tā kā katrā no 2^N kombinācijām ir jāapskata kombinācijas N biti, tad algoritma sarežģītība ir O(2^N * N). Pēc sarežģītības var secināt, ka pārāk daudz elementus algoritms nespēs apstrādāt. Patiesībā, atkarībā no skaitļojamās mašīnas, algoritms izpildīsies sekundes laikā, ja N būs vidēji 21. Veids, kā apskatīt visus bitu kombinācijas ir apskatīt visus skaitļus ar tālāko zīmīgo bitu (bitu 1) mazākā, kā N pozīcijā (ja pieņem, ka bitus sākam skaitīt ar 0. pozīciju). No tā var secināt, ka ejot ciklā no 0 līdz 2^N - 1 un apskatot katra skaitļa N pirmos bitus tiks apskatītas visas 0/1 bitu kombinācijas. Rezultātā veidojas sekojošs algoritms:

1. Iet ciklā i = 0 -> 2^N - 1.
1. Apskata pirmos N bitus no i.
1. Ja k-tais bits ir 1, tad priekšmets tiek ielikts somā.
1. Ja ielikto priekšmetu tilpums nepārsniedz somas tilpumu un priekšmetu vērtības ir līdz šim lielākā atrastā, tad tiek pieglabāts rezultāts un skaitlis, lai izvadītu priekšmetus.
1. Izvada tilpumu, lielāko vērtību un priekšmetus.

Sekojošais piemērs 1. programmā attēlo aprakstīto algoritmu C++ valodā.

```
#include <iostream>
#define INF ((1LL << 31) - 1)
using namespace std;

int n, v, cnt;
int bestV = INF, bestVal, tmpV, tmpVal, bestI;
int a[21], b[21];

int main()
{
    cin >> n >> v;
    /* Aprēķinām 2^N */
    cnt = (1 << n);

    /* Ielasām tilpumus un vērtības */
    for (int i = 0; i < n; ++i)
    {
        cin >> a[i] >> b[i];
    }

    /* Ejam cauri 2^N kombinācijām */
    for (int i = 0; i < cnt; ++i)
    {
        /* Ejam cauri N bitiem */
        tmpV = tmpVal = 0;
        for (int j = 0; j < n; ++j)
        {
            if (i & (1 << j))
            {
                tmpV += a[j];
                tmpVal += b[j];
            }
        }

        /* Ja atrastais rezultāts ir labāks, uzlabojam to */
        if (tmpV <= v && (tmpVal > bestVal || (tmpVal == bestVal && tmpV < bestV)))
        {
            bestVal = tmpVal;
            bestV = tmpV;
            bestI = i;
        }
    }

    /* Izvadām labāko tilpumu un vērtību */
    cout << bestV << " " << bestVal << endl;

    /* Izvadām visus rezultātā izvēlētos priekšmetus */
    for (int i = 0; i < n; ++i)
    {
        if (bestI & (1 << i))
        {
            cout << i + 1 << endl;
        }
    }

    return 0;
}
```

**1. programma** - 0/1 knapsack

### DP knapsack

Šī problēma var parādīties dažādās interpretācijās. Piemēram <a href="http://uva.onlinejudge.org/index.php?option=com_onlinejudge&Itemid=8&category=8&page=show_problem&problem=615" target="_blank">**UVa 674 - Coin Change**</a> problēma ir līdzīga, kā problēma par zagli - ir dota vērtība, kura jāatgriež ar konkrēta nomināla monētām (ne obligāti superaugoša nomināla). Jautājums ir, cik veidos var izdot šādu summu M. Monētu problēmu ar knapsack var risināt izveidojot masīvu DP[], kur i ir monētu kopsumma un DP[i] ir i summas izdošanas veidu skaits. Ja šādu masīvu izdodas izveidot, tad pie konkrētas vērtības M jāizvada tikai DP[M]. DP masīvu var izveidot pēc sekojoša algoritma.

1. DP[0] = 1. (summu 0 var iegūt 1 veidā, nepaņemot nevienu monētu).
1. Apskata katru nominālu N.
    1. Iet ciklā i = N -> DP beigām.
        1. Ja DP[i - N] > 0, tad DP[i] += DP[i - N].
1. Ielasa katru M.
    1. Izvada DP[M].

Realizācija programmai ir redzama 2. programmā.

```
#include <iostream>
#include <cstdio>
#define SIZE 7500
using namespace std;

int coins[] = {1, 5, 10, 25, 50, -1};
int dp[SIZE] = {1};

int main()
{
    for (int i = 0; coins[i] != -1; ++i)
        for (int j = coins[i]; j < SIZE; ++j)
            if (dp[j - coins[i]] > 0) dp[j] += dp[j - coins[i]];

    int n;
    while (scanf("%d", &n) > 0)
    {
        cout << dp[n] << endl;
    }

    return 0;
}
```

**2. programma** - DP knapsack

<a href="http://en.wikipedia.org/wiki/Knapsack_problem" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>

## Uzdevumi

* Gardie dzērieni (gardie)
