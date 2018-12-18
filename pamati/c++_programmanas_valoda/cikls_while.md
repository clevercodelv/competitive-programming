# Cikls while

Cikls programmēšanā ir kaut kā atkārtošana līdz kaut kādam notikumam. Vienkāršs cikls būtu, kad tiek veikta kāda darbība atkārtoti, līdz kāda nosacījuma izpildei, piemēram, mizojam kartupeļus, kamēr spainī ir kartupeļi. Apskatīsim šādu algoritmu.

1. Ielasām spainī esošo kartupeļu skaitu. 
1. Pārbaudām, vai spainī ir kāds kartupelis (jo varbūt mums iedeva sākumā tukšu spaini).
1. Ja spainī ir vēl kartupeļi, tad paņemam vienu un nomizojam (spainī paliek par 1 kartupeli mazāk) un dodamies uz 2. soli.
1. Citādi beidzam mūsu ciklu.
1. Beidzam darbu.

Algoritms ir realizēts 1. programmā.

```
#include <iostream>
using namespace std;

int main()
{
    int kartupeli;
    cin >> kartupeli; // Ielasām spainī esošo kartupeļu skaitu.
    
    while (kartupeli > 0) // Pārbaudām, vai spainī ir kāds kartupelis.
    {
        kartupeli = kartupeli - 1; // Ja spainī ir vēl kartupeļi, tad paņemam vienu un nomizojam.
    }

    // Citādi beidzam mūsu ciklu.
    cout << "Kartupeli nomizoti" << endl;

    return 0; // Beidzam darbu.
}
```

**1. programma** - kartupeļu mizošanas algoritms ar while ciklu.

No angļu valodas tulkojot while nozīmē, **kamēr**. Tātad, kamēr izpildās mūsu nosacījums (kurš var sastāvēt no vairākiem likumiem), atņemam kartupeļu skaitam 1, ar to domājot, ka esam to nomizojuši. \{\} iekavas, gluži kā if-then-else gadījumā nozīmē, apzīmē bloku ar kodu, kuru izpildīt, katrā cikla iterācijā. Par **iterāciju** sauc katru reizi, kad cikls izpildās, jo nosacījums ir patiess jeb true.

<a href="http://www.cplusplus.com/doc/tutorial/control/" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>