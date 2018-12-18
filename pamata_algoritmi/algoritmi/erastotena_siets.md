# Erastotena siets

Pirms tiek stāstīts par Erastotena sietu, ir jāapskata, kā pārbauda, vai skaitlis ir pirmskaitlis? Ideja ir vienkārša, ja skaitlis N nav pirmskaitlis, tad tam ar kaut ko ir jādalās intervālā [2; N - 1]. Dalot N ar šo skaitli, vai nu pats skaitlis, vai dalījums ir mazāks par kvadrātsakni no N, jo pretējā gadījumā, ja dalītāji būtu A un B, tad A * B > N. Šo zinot, var iet ciklā līdz kvadrātsaknei no N un pārbaudīt, vai skaitlis ir pirmskaitlis. Piemēram skatīt 1. programmu.

```
#include <iostream>
#include <cmath>
using namespace std;

bool isPrime(int n)
{
    int up = sqrt(n);
    for (int i = 2; i < up; ++i)
        if (n % i == 0) return false;

    return true;
}

int main()
{
    int n;
    cin >> n;
    cout << n << " " << (isPrime(n) ? "ir" : "nav") << " pirmskaitlis" << endl;

    return 0;
}
```

<center>
**1. programma** - pirmskaitļa tests.
</center>

Erastotena siets izmanto ideju, ka visus skaitļus intervālā, kas dalās ar kādu pirmskaitli var iegūt sekojoši. Piemēram, ir dots pirmskaitlis 2, ar 2 dalās 2 * 2, 2 * 3, 2 * 4, 2 * 5, 2 * 6 u.t.t. Piemēru var apskatīt 2. programmā.

```
#include <iostream>
#include <cmath>
#include <string.h>
#include <vector>
#define LIMIT 200
using namespace std;

bool p[LIMIT];
int n;
vector<int> primes;

int main()
{
    n = LIMIT - 1;

    memset(p + 2, true, sizeof(bool) * (LIMIT - 2));

    for (int i = 2; i <= n; ++i)
        if (p[i])
        {
            for (int j = i * i; j <= n; j += i)
                p[j] = false;
            primes.push_back(i);
        }

    for (int i = 0; i < n; ++i)
        if (p[i])
            cout << i << " ir pirmskaitlis" << endl;

    return 0;
}
```

<center>
**2. programma** - Erastotena siets.
</center>

<a href="http://en.wikipedia.org/wiki/Sieve_of_Eratosthenes" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>