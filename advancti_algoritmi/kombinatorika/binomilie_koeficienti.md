# Binomiālie koeficienti

Binomiālie koeficienti ir visi varianti, kā m priekšmetus var paņemt no n priekšmetiem. Piemēram, no:

- 0 priekšmetiem var paņemt 0 priekšmetus.
- 1 priekšmeta var paņemt 0 un 1 priekšmetu.
- 2 priekšmetiem var paņemt 0, 1 un 2 priekšmetus.
- u.t.t.

Binomiālos koeficientus var apvienot Paskāla trijstūrī, kuru var uzrakstīt matricā (skatīt 1. attēlu). Var redzēt vienu kopīgu lietu šiem skaitļiem ar kombinācijām - veidu skaits, kā m priekšmetus var paņemt no n priekšmetiem ir kombināciju definīcija. 

<center>
<img alt="Paskāla piramīda" src="/media/theory/pascal_pyramid.png" />
**1. attēls** - Paskāla trijstūris.
</center>

Paskāla piramīdu ir viegli izveidot. Ja matricu apzīmē ar M masīvu, tad katrs Paskāla piramīdas skaitlis M[i][j] = M[i - 1][j - 1] + M[i - 1][j], izņemot M[i][0] = 1 un M[j][j] = 1.

Šādi spējot ģenerēt Paskāla piramīdas matricu un zinot, ka M[i][j] apzīmē, cik veidos var paņemt j priekšmetus no i priekšmetiem, var ļoti veikli uzģenerēt paskāla trijstūri un iegūt kombināciju C(i, j), vai arī uzģenerēt daudzas kombinācijas un izmantot tās pēc vajadzības. Piemēram var skatīt 1. programmu.

```
#include <iostream>
using namespace std;

int M[11][11];

void calc_pascal(int M[][11], int N)
{
    for (int i = 0; i <= N; ++i)
    {
        M[i][0] = 1;
        M[i][i] = 1;
        for (int j = 1; j < i; ++j)
            M[i][j] = M[i - 1][j - 1] + M[i - 1][j];
    }
}

int C(int n, int m)
{
    return M[n][m];
}

int main()
{
    calc_pascal(M, 11);

    // Ja ir 10 bumbas un ir nepieciešams uzzināt, cik veidos var paņemt 4 bumbas no 10.
    cout << C(10, 4) << endl;

    return 0;
}
```

<center>
**1. programma** - Paskāla trijstūra aprēķināšana.
</center>

Interesants pielietojums Binomiālajiem koeficientiem ir kāpinot a + b vērtības pakāpē. Piemēram (a + b)^2 = a^2 + 2ab + b^2. Viegli ir arī noteikt (a + b)^3 = a^3 + 3*a^2*b + 3*a*b^2 + b^3, jeb jebkuru izteiksmi (a + b)^N. Ja paskatās uz Paskāla piramīdu, tad 3 rindā koeficienti ir 1, 3, 3, 1 jeb tās pašas vērtības, kuras saskaitāmajiem priekšā (a + b)^3.

<a href="http://en.wikipedia.org/wiki/Binomial_coefficient" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>