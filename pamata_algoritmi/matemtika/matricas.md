# Matricas

Matrica pēc idejas ir tabula ar skaitļiem. Matricas var glabāt 2 dimensiju masīvā, piemēram

```
1  2  3  4  5 
5  5  5 -1  0
4 -9  6 89 33
```

ir 5x3 izmēra matrica. Šo varētu saglabāt int mas[3][5]; masīvā.

<a href="http://en.wikipedia.org/wiki/Matrix_(mathematics)" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>

# Matricu saskaitīšana / atņemšana

Matricu saskaitīšana ir gaužām vienkārša. Saskaitīt var jebkuras divas vienādu dimensiju matricas. Piemēru var skatīt 1. attēlā.


<img alt="Matricu saskaitīšana" src="/media/theory/matrix1.gif"/>
**1. attēls** - matricu saskaitīšana.


Matricu atņemšana strādā tāpa, kā saskaitīšana, izņemot, ja matricas tiek atņemtas, 2. matricas skaitļiem pamaina visas zīmes uz otru pusi un saskaita tās.

<a href="http://en.wikipedia.org/wiki/Matrix_addition" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>

# Matricu reizināšana

Matricu reizināšana ir algoritms ar 3 cikliem un sarežģītību O(N^3). 2. attēls attēlo matricu reizināšanas algoritmu, tā realizācija ir redzama 1. algoritmā. Matricu reizināšanai no divu skaitļu reizināšanas ir viena atšķirība - ja divus skaitļus reizināšanā var mainīt vietām, tad divas matricas nevar, jo tas var mainīt rezultātu. Nosacījums, lai reizinātu divas matricas A un B, ir, ja matricai A ir izmērs NxM un B ir izmērs KxL, tad N == L. Šī nosacījuma dēļ matrica rezultātā sanāk MxK dimensijas liela.

```
#include <iostream>
using namespace std;

int main()
{
    int mx1[3][2] = {
        {0, -2},
        {2, 4},
        {3, 1}
    };

    int mx2[2][3] = {
        {9, 1, 9},
        {-1, 3, -2}
    };

    int res[3][3] = {{}, {}, {}};

    for (int i = 0; i < 3; ++i) // Ejam cauri 1. matricas rindām.
        for (int j = 0; j < 3; ++j) // Ejam cauri 2. matricas kolonnām.
            for (int k = 0; k < 2; ++k) // Ejam cauri 1. matricas rindas un 2. matricas kolonnas elementiem.
                res[i][j] += mx1[i][k] * mx2[k][j];

    for (int i = 0; i < 3; ++i)
    {
        for (int j = 0; j < 3; ++j)
            cout << res[i][j] << " ";
        cout << endl;
    }

    return 0;
}
```


**1. programma** - matricu reizināšana.



<img alt="Matricu reizināšana" src="/media/theory/matrix2.gif"/>
**2. attēls** - matricu reizināšana.


<a href="http://en.wikipedia.org/wiki/Matrix_multiplication" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>