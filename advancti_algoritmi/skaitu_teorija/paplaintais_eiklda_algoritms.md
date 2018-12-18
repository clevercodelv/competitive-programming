# Paplašinātais Eiklīda algoritms

Paplašinātais Eiklīda algoritms ir praktiski tāds pats, kā parastais Eiklīda algoritms, izņemot bez dalījuma un atlikuma katrā solī tiek aprēķinātas vēl divas vērtības - Bezouta identitātes koeficienti. Bezouta identitāte jeb lemma skan diezgan vienkārši. Ja izteiksmē

$$ax + by = gcd(a, b)$$

$a$ un $b$ ir veseli ne nulles skaitļi, tad eksistē $x$ un $y$ veseli skaitļi, lai vienādība izpildītos. Cits jautājums ir, kā tos aprēķināt. Tādēļ tiek izmantota paplašinātā Eiklīda algoritms, kurš palīdz atrast šos koeficientus.

Piemēram, ir doti divi skaitļi 240 un 46. Ir nepieciešams atrast $x$ un $y$ izteiksmē $240x + 46y = 2$. 1. tabulā ir attēlota aprēķinu gaita.

Indeks ($i$) | Dalījums ($d\_i$) | Atlikums ($a\_i$) | $s\_i$ | $t\_i$
---|---|---|---|---
0 |  | 240 | 1 | 0
1 |  | 46 | 0 | 1
2 | 240 / 46 = 5 | 240 % 46 = 10 | | 
3 | 46 / 10 = 4 | 46 % 10 = 6 | |
4 | 10 / 6 = 1 | 10 % 6 = 4 | |
5 | 6 / 4 = 1 | 6 % 4 = 2 | |
6 | 4 / 2 = 2 | 4 % 2 = 0 | |

Lai no parastā Eiklīda algoritma aprēķinātu paplašinātā algoritma vērtības $s\_i$ un $t\_i$, skaitļošana ir jāsāk ar sākuma vērtībām

$$s\_0 = 1\ un\ s\_1 = 0$$
$$t\_0 = 0\ un\ t\_1 = 1$$

un katru nākamo $s$ un $t$ vērtību var aprēķināt ar sekojošām formulām

$$s\_i = s\_{i-2} - d\_i * s\_{i-1}$$
$$t\_i = t\_{i-2} - d\_i * t\_{i-1}$$

Patiesībā arī $a\_i$ var aprēķināt ar tādu pašu formulu

$$a\_i = a\_{i-2} - d\_i * a\_{i-1}$$

Tagad pārrakstot tabulu ar $s$ un $t$ aprēķinātu, kā arī $a$ aprēķinātu pēc jaunās formulas, tiek iegūts sekojošs rezultāts.

Indeks ($i$) | Dalījums ($d\_i$) | Atlikums ($a\_i$) | $s\_i$ | $t\_i$
---|---|---|---|---
0 |  | 240 | 1 | 0
1 |  | 46 | 0 | 1
2 | 240 / 46 = 5 | 240 - 5 * 46 = 10 | 1 - 5 * 0 = 1 | 0 - 5 * 1 = -5
3 | 46 / 10 = 4 | 46 - 4 * 10 = 6 | 0 - 4 * 1 = -4 | 1 - 4 * -5 = 21
4 | 10 / 6 = 1 | 10 - 1 * 6 = 4 | 1 - 1 * -4 = 5 | -5 - 1 * 21 = -26
5 | 6 / 4 = 1 | 6 - 1 * 4 = 2 | -4 - 1 * 5 = -9 | 21 - 1 * -26 = 47
6 | 4 / 2 = 2 | 4 - 2 * 2 = 0 | 5 - 2 * -9 = 23 | -26 - 2 * 47 = -120

Rezultātā izmantojot pirmspēdējās $s$ un $t$ vērtības vienādībā, sanāk, ka

$$x = -9$$
$$y = 47$$
$$240 * -9 + 46 * 47 = 2$$
$$-2160 + 2162 = 2$$
$$2 = 2$$

C++ programmas piemēru var apskatīt 1. programmā.

```
#include <queue>
#include <iostream>
#include <algorithm>
using namespace std;

void extended_euclidean(queue<int> &a, queue<int> &s, queue<int> &t)
{
    if (a.back() == 0)
    {
        return;
    }

    int d = a.front() / a.back();

    a.push(a.front() - d * a.back());
    a.pop();

    s.push(s.front() - d * s.back());
    s.pop();

    t.push(t.front() - d * t.back());
    t.pop();

    extended_euclidean(a, s, t);
}

int main()
{
    int a, b;
    cin >> a >> b;

    queue<int> ai;
    queue<int> si;
    queue<int> ti;

    ai.push(max(a, b));
    ai.push(min(a, b));

    si.push(1);
    si.push(0);

    ti.push(0);
    ti.push(1);

    extended_euclidean(ai, si, ti);

    cout << a << "x + " << b << "y = gcd(a, b)" << endl;
    cout << a << " * " << si.front() << " + " << b << " * " << ti.front() << " = " << ai.front() << endl;
    cout << a * si.front() << " + " << b * ti.front() << " = " << ai.front() << endl;
    cout << a * si.front() + b * ti.front() << " = " << ai.front() << endl;

    return 0;
}
```


**1. programma** - paplašinātā Eiklīda algoritma realizācija programmā.
