# Garākā augošā apakšvirkne

Garākās augošās apakšvirknes problēma jeb LIS (Longest Increasing Subsequence) ir viegli saredzama uz skaitļiem - tā ir secīga, augoša skaitļu virkne, kura ir atrodama iekļauta citas virknes elementiem pa vidu. Piemēram,

```cpp
Ir dota virkne: 1, 6, 4, 5, 3, 9, 9.

Garākā augošā apakšvirkne ir: 1, 4, 5, 9.
```

Ir vairāki varianti, kā to aprēķināt. Rupjā spēka variants strādā pēc šāda algoritma:

1. Izveido masīvu M[], kas ir virknes V[] garumā. M[i] apzīmē V[i] elementa pozīciju kādā augošajā apakšvirknē. 
1. No sākuma katrs M[i] = 1, jeb katrs elements ir apakšvirkne garumā 1.
1. Izejot katram elementam cauri ar i.
    1. Apskata katru iepriekš apskatīto elementu ar j.
        1. Ja M[i] > M[j] un V[i] <= V[j].
        1. Tad V[i] = V[j] + 1.
1. Lielākais V[i] elements L ir garākās augošās apakšvirknes garums un M[i] ir pirmais garākās apakšvirknes elements K no beigām.
1. Pieglabā K masīvā LIS[].
1. Iet no atrastā garākās apakšvirknes elementa - 1.
    1. Ja V[i] == L - 1 un M[i] < K.
    1. Tad L = L - 1 un K = M[i].
    1. Pieglabā K masīvā LIS[] beigās.
1. Apgriež masīvu LIS otrādi un izvada.

Realizāciju var apskatīt 1. programmā.

```
#include <iostream>
#include <vector>
#include <algorithm>
#define SIZE 7
using namespace std;

int M[] = {1, 6, 4, 5, 3, 9, 9};
int V[] = {1, 1, 1, 1, 1, 1, 1};
vector<int> LIS;

int main()
{
    int L = 1, pos = 0;
    for (int i = 0; i < SIZE; ++i)
        for (int j = 0; j < i; ++j)
        {
            if (M[i] > M[j] && V[i] <= V[j])
                V[i] = V[j] + 1;
            if (V[i] > L)
            {
                L = V[i];
                pos = i;
            }
        }

    LIS.push_back(M[pos]);
    for (int i = pos - 1; i >= 0; --i)
        if (V[i] == L - 1 && M[i] < M[pos])
        {
            L--;
            pos = i;
            LIS.push_back(M[pos]);
        }
    reverse(LIS.begin(), LIS.end());

    for (int i = 0; i < LIS.size(); ++i)
        cout << LIS[i] << " ";
    cout << endl;

    return 0;
}
```

**1. programma** - LIS meklēšana ar rupjā spēka metodi.

### Garākā augošā apakšvirkne DP

DP variants atšķirībā no rupjā spēka varianta, kurš strādā O(N^2) laikā, veic O(N * log(N)) darbības. Triks ir tajā, ka tiek uzturēti 2 masīvi, kuri ļauj katram elementa ar bināro meklēšanu piemeklēt līdz šim atrasto garāko apakšvirkni, kurai elements var tikt pielikts galā. Algoritmam ir jāuztur divi masīvi.

Ja ir dota simbolu virkne X[], tad **M[i]** elements satur X indeksu uz mazāko elementu, kurš atrodas apakšvirknes ar garumu i galā.

**P[i]** satur apakšvirknes elementa X[i] iepriekšējo apakšvirknes elementa indeksu.

Tiek uzturēts arī mainīgais **L**, kurš apzīmē līdz šim atrasto garāko apakšvirkni.

Var izdarīt secinājumu, ka X[M[0]], X[M[1]], ..., X[M[L]] ir augoša apakšvirkne, pretējā gadījumā rodas pretruna (pierādījums izriet no pretējā). Ja ir nepieciešams atrast X[j] elementa pozīciju pēc iespējas garākā apakšvirknē, tad var ar bināro meklēšanu meklēt skaitļu virknē X[M[0]], X[M[1]], ..., X[M[L]] lielāko elementu X[M[i]], kurš ir mazāks par X[j] un M[i] būs apakšvirknes garums, kurai X[j] tiek pielikts klāt, veidojot M[i] + 1 garuma apakšvirkni. Piemēru šī algoritma realizācijai var apskatīt 2. programmā.

```
#include <iostream>
#include <vector>
#include <stack>
#include <algorithm>
#define SIZE 7
using namespace std;

int X[] = {1, 6, 4, 5, 3, 9, 9};
int M[SIZE + 1], P[SIZE], L = 1;

// a == M[i], b == X[j] jeb meklējamo elementu.
bool cmp(const int &a, const int &b)
{
   return X[a] < b;
}

int main()
{
    for (int i = 0; i < SIZE; ++i)
        P[i] = -1;

    int pos;
    for (int i = 0; i < SIZE; ++i)
    {
        pos = lower_bound(M + 1, M + L, X[i], cmp) - M;
        if (pos == L)
            M[L++] = i;
        else if (X[M[pos]] > X[i])
            M[pos] = i;

        if (pos > 1)
            P[i] = M[pos - 1];
    }

    stack<int> st;
    pos = M[L - 1];
    while (pos != -1)
    {
        st.push(pos);
        pos = P[pos];
    }

    while (!st.empty())
    {
        cout << X[st.top()] << endl;
        st.pop();
    }

    return 0;
}
```

**2. programma** - optimizēta LIS meklēšana.

<a href="http://en.wikipedia.org/wiki/Longest_increasing_subsequence" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>