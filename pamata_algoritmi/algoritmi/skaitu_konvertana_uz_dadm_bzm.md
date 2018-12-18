# Skaitļu konvertēšana uz dažādām bāzēm

Lai pārveidotu jebkuru skaitli no tā bāzes uz citu bāzi, var izmantot pārveidošanā 10 bāzi. Ir jāvadās pēc sekojoša algoritma, pretējā gadījumā pietiek veikt tikai vienu algoritma soli:

1. Pārveido no bāzes A uz 10 bāzi.
1. Pārveido no bāzes 10 uz B.

Jebkuru bāzes skaitli uz 10 var pārveidot katram ciparam piereizinot klāt bāzi pakāpē, kas vienāda ar cipara pozīciju. Piemēram, ja skaitlis ir 0x1023, tad 10 sistēmā tas ir 1 * 16 ^ 3 + 0 * 16 ^ 2 + 2 * 16 ^ 1 + 3 * 16 ^ 0 = 4096 + 32 + 3 = 4131.

Jebkuru 10 skaitlis var pārveidot no 10 sistēmas uz jebkuru citu, dalot skaitli ar bāzi, un atlikumu pierakstot. Rezultātā iegūtā skaitļu virkne no otras puses ir rezultāts. Apskatot piemēru 4131, procedūra ir sekojoša:

```
4131 % 16 = 3
4131 / 16 = 258
258 % 16 = 2
258 / 16 = 1
1 % 16 = 1
1 / 16 = 0 // Beidzam darbu.
```

Ar moduļa darbību tika iegūti šādi skaitļi: 3, 2, 0, 1. Apgriežam tos otrādi un iegūstam rezultātu: 1, 0, 2, 3 jeb 1023, jeb 0x1023.

Piemēru realizācijai var apskatīt 1. programmā.

```
#include <iostream>
#include <string.h>
#include <string>
using namespace std;

// Pārveido uz desmitnieku sistēmas skaitli.
int uz_10(char sk[], int base)
{
    int garums = strlen(sk);
    int pakape = 1;
    int sk10 = 0;

    for (int i = garums - 1, j = 0; j < garums; --i, ++j)
    {
        sk10 += (sk[i] - '0') * pakape;
        pakape *= base;
    }

    return sk10;
}

// Pārveido uz rezultāta sistēmas skaitli.
const char* uz_X(int sk, int base)
{
    string skX = "";

    while (sk > 0)
    {
        skX += (char)(sk % base + '0');
        sk /= base;
    }
    // Apgriežam simbolu virkni otrādi.
    skX = string(skX.rbegin(), skX.rend());

    // No simbolu virknes iegūst simbolu masīvu.
    return skX.c_str();
}

// Pārveido no ievaddatu bāzes uz mērķa bāzi.
const char* convert(char sk[], int base1, int base2)
{
    int sk10 = uz_10(sk, base1);
    return uz_X(sk10, base2);
}

// Programma strādā tikai ar int intervāla skaitļiem.
int main()
{
    char sk[] = "1023";
    int base1 = 16;
    int base2 = 2;
    cout << convert(sk, base1, base2) << endl;

    return 0;
}
```

**1. programma** - skaitļu pārveidošana no vienas bāzes uz citu.

<a href="http://en.wikipedia.org/wiki/Positional_notation" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>