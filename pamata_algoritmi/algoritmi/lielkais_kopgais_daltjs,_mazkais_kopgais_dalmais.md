# Lielākais kopīgais dalītājs, mazākais kopīgais dalāmais

**Lielākais kopīgais dalītājs jeb LKD** ir lielākais skaitlis, kurš dala divus konkrētus skaitļus bez atlikuma. Piemēru, ja ir doti divi skaitļi 18 un 30, tad to LKD ir 6, jo nav lielāks skaitlis, kurš dala 18 un 30 bez atlikuma.

LKD problēmu var risināt ar **Eiklīda algoritmu**. Eiklīda algoritmu var iztēloties, kā funkciju LKD(A, B). LKD funkcija ir rekursīva. LKD algoritms strādā šādi (piemēru var skatīties 1. programmā):

1. Ja B == 0 tad LKD = A.
1. Citādi LKD = LKD(B, A % B).

```
#include <iostream>
#include <cstdio>
using namespace std;

int lkd(int a, int b)
{
    if (b == 0)
        return a;
    else
        return lkd(b, a % b);
}

int main()
{
    cout << lkd(30, 18) << endl; // Izvada 6.

    return 0;
}
```

<center>
**1. programma** - Eiklīda algoritms.
</center>

**Mazākais kopīgais dalāmais jeb MKD** ir mazākais skaitlis, kuru dala divi konkrēti skaitļi bez atlikuma. Piemēram, ja tiek doti divi skaitļi 18 un 30, tad MKD ir 90, jo nav mazāks skaitlis, kuru abi dala bez atlikuma.

MKD var aprēķināt no LKD, jeb MKD(A, B) = A * B /LKD(A, B). Piemēru var skatīt 2. programmā.

```
#include <iostream>
#include <cstdio>
using namespace std;

int lkd(int a, int b)
{
    if (b == 0)
        return a;
    else
        return lkd(b, a % b);
}

int mkd(int a, int b)
{
    return a * b / lkd(a, b);
}

int main()
{
    cout << mkd(30, 18) << endl; // Izvada 90.

    return 0;
}
```

<center>
**2. programma** - Eiklīda algoritms priekš MKD.
</center>

<a href="http://lv.wikipedia.org/wiki/Eikl%C4%ABda_algoritms" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>