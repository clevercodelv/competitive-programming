# Dinamiskā programmēšana un memoizācija

Dinamiskajā programmēšanā ir divas pieejas:

- **Buttom-Up** - klasiskais DP rakstīšanas veids. Parasti izmanto 1 līdz N dimensiju masīvu apakšproblēmu risinājumu glabāšanai un iteratīvi risina problēmas.
- **Top-Down** - pieeja DP problēmām no otras puses jeb rekursīvi (kāpjoties atpakaļ tiek darīts kaut kas līdzīgi Bottom-Up metodei). Šī metode mēdz izmantot tabulu starprezultātu glabāšanai, lai izvairītos no daudziem liekiem rekursīviem izsaukumiem, ko sauc par memoizāciju.

### Memoizācija

Memoizācija ir aprēķināto apakšproblēmu rezultātu atcerēšanās ar nolūku, lai šīs vērtības nebūtu jāatceras atkal. Par piemēru tiek izmantota <a href="http://uva.onlinejudge.org/index.php?option=com_onlinejudge&Itemid=8&page=show_problem&problem=2750" target="_blank">**UVa 11703 - sqrt log sin**</a> problēma. Ideja ir katru aprēķināto x(i) pieglabāt memo[i], lai, ja tas ir jau aprēķināts, tad var atgriezt x(i) vērtību. Var redzēt, ka rekursija aprēķinās 1000000 vērtības un tad jebkurš i tiks atgriezts no memo[] masīva. Realizāciju var apskatīt 1. programmā.

```
#include <iostream>
#include <cmath>
#define MOD 1000000
using namespace std;

int memo[MOD + 1] = {1};

int x(int i)
{
    // Ja ir iepriekš aprēķināts x(i), atgriežam vērtību.
    if (memo[i]) return memo[i];

    // Aprēķina x(i).
    int res =  x(i - sqrt(i)) + x(log(i)) + x(i*pow(sin(i), 2));
    res %= MOD;

    // Pieglabā x(i).
    memo[i] = res;

    return res;
}

int main()
{
    int i;
    cin >> i;
    while (i != -1)
    {
        cout << x(i) << endl;
        cin >> i;
    }

    return 0;
}
```

**1. programma** - memoizācijas piemērs.

<a href="http://en.wikipedia.org/wiki/Memoization" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>