# Garākā kopīgā apakšvirkne

Garākā kopīgā apaksvirkne no divām simbolu virknēm ir garākā no apakšvirknēm, kura ir apakšvirkne abās dotajās virknēs. Piemēram, ja ir dotas simbolu virknes "apple" un "people", tad kopīgā apakšvirkne ir "pple". Variants, kā ar rupjā spēka metodi risināt šo problēmu ir:

1. i = min(strlen(A), strlen(B)), kur A un B ir ielasītās simbolu virknes.
1. Kamēr i > 0.
1. Atrod visas A apakšvirknes garumā i.
1. Atrod visas B apakšvirknes garumā i.
1. Ja starp garumā i kāda A apakšvirkne eksistē B apakšvirknēs, tad izvada šo apakšvirkni kā rezultātu.
1. Ja nav atrasta apakšivrkne garumā >= 1, tad rezultātā ir jāizvada apakšvirkne garumā 0.

Šis algoritms nav pārāk optimāls, bet eksistē DP variants. Ja ir dotas divas virknes A garumā N un B garumā M, tad DP sarežģītība ir O(N * M). DP tiek definēta funkcija len(a, b), kur a ir pozīcija A masīvā un b ir pozicija B masīvā. Šo DP var realizēt bottom-up un top-down. Šeit tiks apskatīts top down, bet aprakstītās formulas var pielāgot arī bottom-up realizācijai. Top-down DP tiek izmantota memoizācija, lai atcerētos M[a][b] rezultātu un atgrieztu izsaucot atkārtoti len(a, b). Šis DP sastāv no:

**Bāzes stāvokļi:**

- len(0, b) = 0.
- len(a, 0) = 0.

**Rekursīvās funkcija:**

- Ja A[a] == B[b], tad len(a, b) = 1 + len(a - 1, b - 1).
- Ja A[a] != B[b], tad len(a, b) = max(len(a - 1, b), len(a, b - 1)).

Piemērs DP ir redzams 1. programmā, kas ir <a href="http://uva.onlinejudge.org/index.php?option=com_onlinejudge&Itemid=8&category=16&page=show_problem&problem=1346" target="_blank">UVa 10405 - Longest Common Subsequence</a> risinājums.

```
#include <iostream>
#include <string.h>
using namespace std;

int dp[1002][1002];
char A[1002], B[1002];
int lenA, lenB;

int len(int a, int b)
{
    // Atšķirībā no skaidrojuma, salīdzina ar -1, jo virknes ir intervālā [0, N - 1] nevis [1, N].
    if (a == -1 || b == -1) return 0;
    if (dp[a][b] > -1) return dp[a][b];

    if (A[a] == B[b])
        dp[a][b] = len(a - 1, b - 1) + 1;
    else
        dp[a][b] = max(len(a - 1, b), len(a, b - 1));

    return dp[a][b];
};

int main()
{
    while (cin.getline(A, 1001))
    {
        cin.getline(B, 1001);
        // -1, jo jāapskata virkne intervālā [0; strlen(A) - 1].
        lenA = strlen(A) - 1;
        lenB = strlen(B) - 1;

        // Ja garums ir 0 (garums - 1 < 0), tad rezultāts ir 0.
        if (lenA < 0 || lenB < 0) {
            cout << 0 << endl;
            continue;
        }

        for (int i = 0; i <= lenA; ++i)
            for (int j = 0; j <= lenB; ++j)
                dp[i][j] = -1;
        len(lenA, lenB);
        cout << dp[lenA][lenB] << endl;
    }


    return 0;
}

```

<center>
**1. programma** - kopīgā garākā apakšvirkne.
</center>