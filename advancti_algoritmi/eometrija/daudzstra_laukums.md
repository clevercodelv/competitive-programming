# Daudzstūra laukums

Lai aprēķinātu jebkuram izliektam vai ieliektam daudzstūrim laukumu, var izmantot pseido skalāro reizinājumu un triangulāciju. Piemēram 1. attēlā redzamā daudzstūra triangulācijas rezultātā iegūtie trijstūri ir ABC, ACD, ADE. Aprēķinot |ABxBC + ACxCD + ADxDE|/2 var iegūt ABCDE laukumu. Piemēru var apskatīties 1. programmā.

<img alt="Daudzstūris" src="/media/theory/polygon_field.png"/>
**1. attēls** - daudzstūris.

```
#include <iostream>
#include <cmath>
using namespace std;

double cross_product(double x1, double y1, double x2, double y2)
{
    return x1 * y2 - x2 * y1;
}

int main()
{
    int x[] = {2, 5, 8, 4, 4};
    int y[] = {6, 9, 6, 3, 7};

    double S = 0.0;
    for (int i = 1; i < 4; ++i)
    {
        double x1 = x[i] - x[0];
        double y1 = y[i] - y[0];
        double x2 = x[i + 1] - x[0];
        double y2 = y[i + 1] - y[0];
        S += cross_product(x1, y1, x2, y2);
    }

    S = fabs(S) / 2;
    cout << S << endl;

    return 0;
}
```

**1. programma** - daudzstūra laukuma aprēķināšana.

<a href="http://community.topcoder.com/tc?module=Static&d1=tutorials&d2=geometry1" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>