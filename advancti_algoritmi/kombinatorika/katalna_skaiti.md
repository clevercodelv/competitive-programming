# Katalāna skaitļi

Katalāna skaitļi ir skaitļu virkne, kuras n-to elementu apzīmē ar Cat(n) un Cat(n) ir unikālu bināro koku skaits ar n virsotnēm. Katalāna skaitļus var aprēķināt ar rekursīvu funkciju 1. attēlā. Programmas piemērs ir redzams 1. programmā.


<img alt="Katalāna skaitļu formula" src="/media/theory/catalan.gif" />
**1. attēls** - Katalāna skaitļu formula.


```
#include <iostream>
using namespace std;

int M[11];

void calc_catalan(int *M, int N)
{
    M[0] = 1;
    for (int i = 1; i <= N; ++i)
        M[i] = ((2 * (2 * N + 1)) / (N + 2)) * M[i - 1];
}

int Cat(int n)
{
    return M[n];
}

int main()
{
    calc_catalan(M, 10);

    // Cik unikālus bināros kokus var izveidot ar 10 virsotnēm.
    cout << Cat(10) << endl;

    return 0;
}
```


**1. programma** - Katalāna skaitļu formulas realizācija.


Katalāna skaitļiem ir vairāki pielietojumi, tie nav tikai unikālo bināro koku skaits, bet arī:

- Cik korektas iekavu izteiksmes var izveidot no N * 2 iekavām.
- Cik trijstūros var sadalīt N + 2 daudzstūri trijstūros novelkot taisnes starp virsotnēm, lai tās nekrustotos.
- Un citi pielietojumi, kurus var izlasīt zemākajā saitē.


<a href="http://en.wikipedia.org/wiki/Catalan_number" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>