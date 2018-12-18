# Pirmreizinātāju atrašana

Skaitļa pirmreizinātāji ir unikāls pirmskaitļu komplekts, kurus savā starpā sareizinot, tiek iegūts šis skaitlis. Pirmreizinātājus var iegūt sekojoši.

1. Aprēķināt ar Erastotena sietu pirmskaitļus intervālā līdz sqrt(N), ja N ir sadalāmais skaitlis.
2. Iet katram pirmskaitlim cauri un dalīt to ar pirmskaitli, kamēr to vairs nevar izdarīt. Ja skaitlis dalās ar pirmskaitli, tad tik reizes, cik tas dala skaitli, tik tas reizes ir atrodams skaitlī kā pirmreizinātājs.


Piemēram, ja ir dots skaitlis 9350, tad sekojošas darbības varētu tikt veiktas (realizāciju var skatīt 1. programmā):

1. Kvadrātsakne no skaitļa ir 18.
1. Pēc Erastotena sieta, pirmskaitļi intervālā [2; 18] ir 2, 3, 5, 7, 11, 13, 17.
1. Dalot ar šiem pirmskaitļiem tiek iegūts sekojošais rezultāts.

```
9350 / 2 = 4675
4675 / 5 = 935
935 / 5 = 187
187 / 11 = 17
17 / 17 = 1

Pirmreizinātāji ir: 2, 5, 5, 11, 17.

Ja pēc visu pirmskaitļu dalīšanas skaitlis nav 1, tad skaitlis ir pēdējais pirmreizinātājs, piemēram: 22
Kvadrātsakne ir 4.
Pirmreizinātāji ir 2 un 11.
```

```
#include <iostream>
#include <cmath>
#include <vector>
#include <string.h>
using namespace std;

void get_primes(int n, vector<int> &primes)
{
    bool *p = new bool[n + 1];
    memset(p, 0, sizeof(bool) * (n + 1));

    for (int i = 2; i <= n; ++i)
        if (!p[i])
        {
            for (int j = i * i; j <= n; j += i)
                p[j] = true;
            primes.push_back(i);
        }
}

void prime_factors(int n, vector<int> &factors)
{
    vector<int> primes;
    get_primes(sqrt(n), primes);
    int pf_idx = 0, pf = primes[pf_idx];

    while (n != 1 && (pf * pf <= n)) {
        while (n % pf == 0) { n /= pf; factors.push_back(pf); }
        pf = primes[++pf_idx];
    }

    if (n != 1) factors.push_back(n);
}

int main()
{
    vector<int> v;
    prime_factors(1000000, v);

    for (int i = 0; i < v.size(); ++i)
        cout << v[i] << endl;

    return 0;
}
```


**1. programma** - pirmreizinātāju iegūšana.
