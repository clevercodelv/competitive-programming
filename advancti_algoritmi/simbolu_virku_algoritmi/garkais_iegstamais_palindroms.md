# Garākais iegūstamais palindroms

**Palindroms** ir simbolu virkne, kura no abām pusēm rakstās vienādi. Piemēram "abrarba" rakstās vienādi. **Garākā iegūstamā palindroma** problēma ir problēma, kad tiek dota netukša simbolu virkne, no kuras ir jāiegūst garākais iespējamais palindroms izmetot no tās kādus burtus. Viens problēmas paveids mēdz būt, ka ir jāaprēķina šāda garākā palindroma garums, bet otrs paveids ir, kad ir jāiegūst pats palindroms. Abi problēmas paveidi ir risināmi ar rupjā spēka metodi pēc šāda algoritma:

1. i = simbolu virknes garums.
1. Apskata visas simbolu virknes apaksvirknes garumā i.
1. Ja atrod kādu apakšvirkni, kura ir palindroms, tad risinājums ir atrasts.

```
Piemēram, ir dota simbolu virkne "ADAM".

i == 4
Apakšvirknes ir "ADAM".
Neviena no apakšvirknēm nav palindroms.

i == 3
Apakšvirknes ir "ADA", "ADM", "AAM", "DAM".
"ADA" ir palindroms.

Rezultātā ir iegūts 4 simbolus garš palindroms "ADA".
```

Bet šis algoritms ir neoptimāls un garākām simbolu virknēm strādās pārāk ilgi. Optimāls risinājums ir izmantot DP pieeju. Tālāk aprakstītā pieeja ir top-down, kura tiek definēta, kā rekursīvs algoritms, bet eksistē arī bottom-up pieeja. Tālāk algoritms tiek definēts ar rekursīvu funkciju len(l, r), kur l ir simbola virknes kreisās puses indeks un r ir simbolu virknes labās puses indeks. Piemēram, len(2, 15) ir jāatgriež garākā palindroma garums no simbolu virknes A apakšvirknes intervālā [2; 15]. Tiesa, len funkcija nav tikai iztēles auglis, tajā notiek sekojoši likumi:

**Bāzes stāvokļi:**

- Ja l == r, tad len(l, r) == 1. // Tas nozīmē, ka [l; r] apzīmē simbolu virkni viena simbola garumā un simbolu virkne ar vienu simbolu vienmēr ir palindroms.
- Ja l + 1 == r tad, ja (A[l] == A[r], tad len(l, r) == 2, citādi len(l, r) == 1. // Ja tiek apskatīta simbolu virkne garumā 2, kuras abi simbolu ir vienādi, tad virkne ir palindroms ar garumu 2.

**Rekursīvās funkcijas:**

- Ja A[l] == A[r], tad len(l, r) == 2 + len(l + 1, r - 1), // Abi simbolu virknes gala simboli ir vienādi.
- citādi len(l, r) = max(len(l, r - 1), len(l - 1, r)). // Paņem labāko rezultātu no varianta, kad kāds no abiem simboliem galos tiek nomests.


Kā jau DP top-down pieejā ir pieņemts, bez rekursijas eksistē arī memoizācijas daļa. Tā kā len(l, r) ir divargumentu funkcija un katram l, r unikālam komplektam len(l, r) atgriež vienu rezultātu, tad var izveidot masīvu memo[N][N], kur memo[l][r] == len(l, r). Atliek vienu reizi aprēķināt len(l, r) un, nākamreiz to mēģinot rēķināt, vērtību var ņemt no memo[l][r] elementa. Šādā veidā var secināt, ka DP algoritms strādā O(N^2) laikā. Kā piemērs tiek apskatīta <a href="http://uva.onlinejudge.org/index.php?option=com_onlinejudge&Itemid=8&category=23&page=show_problem&problem=2092" target="_blank">UVa 11151 - Longest Palindrome</a> problēma, kuras kods ir lasāms 1. programmā.

```#include <iostream>
#include <string.h>
#include <algorithm>
#include <cstdlib>
using namespace std;

char A[1001];
int memo[1001][1001];

int len(int l, int r)
{
    int res = 0;

    // Memoizācija.
    if (memo[l][r]) return memo[l][r];

    if (l > r) return 0;
    // Bāzes stāvokļi.
    if (l == r) res = 1;
    //Rekursīvās funkcijas.
    else if (A[l] == A[r])
        res = 2 + len(l + 1, r - 1);
    else
        res = max(len(l + 1, r), len(l, r - 1));

    memo[l][r] = res;
    return res;
}

int main()
{
    // Ielasa visu rindu, lai izvairītos no \n simbola nākamo reizi izmantojot getline.
    cin.getline(A, 1000);
    char* e = A + strlen(A);
    long int t = strtol(A, &e, 10);
    while (t--)
    {
        cin.getline(A, 1000); // getline tiek izmantots, jo var būt tukšā simbolu virkne.
        int l = strlen(A);

        // Speciālgadījums.
        if (l == 0) {
            cout << 0 << endl;
            continue;
        }

        for (int i = 0; i < l; ++i)
            memset(memo[i], 0, sizeof(int) * l);
        cout << len(0, l - 1) << endl;
    }

    return 0;
}
```


**1. programma** - garākā apakšpalindroma garuma meklēšana.


<a href="http://en.wikipedia.org/wiki/Quicksort" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>