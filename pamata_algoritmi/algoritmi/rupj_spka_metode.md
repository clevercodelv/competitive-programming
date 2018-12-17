# Rupjā spēka metode

Rupjā spēka metode parasti var attiekties uz vairākām lietām - meklēšanu, konkrēta algoritma izpildi, realizāciju. Tas nav konkrēts algoritms vai tehnika, bet drīzāk aptver tādus risinājumus, kuri nav īsti efektīvi un kuriem eksistē labāki risinājumi. Daži labumi parasti rupjā spēka metodēm ir:

- Rupjā spēka metodes risinājumi pārsvarā ir īsāki, vieglāk saprotami un vieglāk atkļūdojami.
- Tos ir viegli ātri uzrakstīt pareiza testpiemēra atbildes uzģenerēšanai.
- Ja sacensībās dod punktus par katru atrisināto testu, tad var problēmu risināt ar rupjā spēka metodi gadījumos, kad ir atlicis maz laika vai uzdevumu neizdodas atrisināt.
- Dažreiz īstais risinājums var slēpties aiz rupjā spēka risinājum ar optimizāciju, kuru izdomā pēc rupjā spēka uzrakstīšanas, bet šī pieeja nav uzticamam jo negarantē, ka optimizācija eksistē.


Tā kā rupjā spēka metodei īsti neeksistē konkrēts algoritms, tad var apskatīt piemēru 1. programmā un optimālo risinājumu 2. programmā. Problēma, kuru apskata risinājumi ir <a href="http://uva.onlinejudge.org/index.php?option=com_onlinejudge&Itemid=8&page=show_problem&problem=44">UVa 108 - Maximum sum</a>.

**Rupjā spēka risinājums** ir apskatīt katru taisnstūri matricā un aprēķināt tā summu. Ja summa ir labāka par līdz šim iegūto, tad to pieglabā. Šis risinājums strādā ar O(N^6) sarežģītību. Ar šo risinājumu nevar atrisināt problēmu serverī.

```
#include <iostream>
#include <cstdio>
using namespace std;

int mas[101][101], n;

int main()
{
    scanf("%d", &n);
    for (int i = 0; i < n; ++i)
        for (int j = 0; j < n; ++j)
            scanf("%d", mas[i] + j);

    int best = -2000000000;
    for (int i = 0; i < n; ++i)
        for (int j = 0; j < n; ++j)
            for (int k = i; k < n; ++k)
                for (int m = j; m < n; ++m)
                {
                    int sum = 0;
                    for (int x = i; x <= k; ++x)
                        for (int y = j; y <= m; ++y)
                            sum += mas[x][y];
                    if (sum > best) best = sum;
                }

    printf("%d\n", best);

    return 0;
}
```

<center>**1. programma** - rupjā spēka risinājums.</center>

**Efektīvā metode** ir aprēķināt horizontālo summu un vertikālo summu no horizontālo summu matricas. Tālāk apskatot katru kvadrātu vajag nevis saskaitīt kvadrāta summu, bet aprēķināt summu pēc formulas no vertikālās summas. Ar šo metodi var atrisināt problēmu serverī. Risinājumam sarežģītība ir O(N^4).

```
#include <iostream>
#include <cstdio>
using namespace std;

int mas[101][101], n;
int v[101][101];

int main()
{
    //freopen("in.in", "r", stdin);

    scanf("%d", &n);
    for (int i = 1; i <= n; ++i)
        for (int j = 1; j <= n; ++j)
            scanf("%d", mas[i] + j);

    for (int i = 1; i <= n; ++i)
        for (int j = 1; j <= n; ++j)
            v[i][j] = mas[i][j] + v[i][j - 1];

    for (int j = 1; j <= n; ++j)
        for (int i = 1; i <= n; ++i)
            v[i][j] += v[i - 1][j];

    int sum, best = -2000000000;
    for (int i = 0; i <= n; ++i)
        for (int j = 0; j <= n; ++j)
            for (int k = i + 1; k <= n; ++k)
                for (int m = j + 1; m <= n; ++m)
                {
                    sum = v[k][m] + v[i][j] - v[i][m] - v[k][j];
                    if (sum > best) best = sum;
                }

    printf("%d\n", best);

    return 0;
}
```

<center>**2. programma** - .</center>

<a href="http://en.wikipedia.org/wiki/Brute-force_search" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>