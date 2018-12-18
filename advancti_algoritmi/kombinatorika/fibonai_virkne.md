# Fibonači virkne

Fibonači skaitļu virkne ir skaitļu virkne, kura sākas ar skaitļiem 1 un 1 pozīcijās 0 un 1, un katrs nākamais Fibonači skaitlis ir uzrakstāms saskaitot divus iepriekšējos kopā. Rezultātā rodas rekursīva definīcija, kuru var apskatīt 1. attēlā. Piemērs Fibonači skaitļu virknei ir šāds:

```
1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, ...
```

<center>
<img alt="Fibonači rekursīva funkcija" src="/media/theory/rec_fib.gif"/>
**1. attēls** - Fibonači rekursīvā funkcija matemātikā.
</center>

Bet šo problēmu nebūtu pareizi risināt rekursīvi. Jo bez optimizācijas, programma būtu neoptimāla, pat eksponenciāla - O(2^N), ja N ir skaitļa pozīcija. Pareizais variants būtu to risināt dinamiski jeb ar dinamisko programmēšanu - pirms aprēķina i skaitli, aprēķina i - 1 un i - 2 skaitļus. Risinājums ir apskatāms 1. programmā.

```
#include <iostream>
using namespace std;

int F(int pos)
{
    // Katru reizi aprēķina jauno vērtību i - 3 pozīcijā.
    int mas[3] = {1, 1, 0};
    for (int i = 2; i <= pos; ++i)
        mas[i % 3] = mas[(i + 1) % 3] + mas[(i + 2) % 3];
    return mas[pos % 3];
}

int main()
{
    cout << F(13) << endl; // Atgriež 13 Fibonači skaitli.

    return 0;
}
```

<center>
**1. programma** - Fibonači dinamiskās programmēšanas risinājums.
</center>

<a href="http://en.wikipedia.org/wiki/Fibonacci_number" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>