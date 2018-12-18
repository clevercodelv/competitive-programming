# Datu struktūra

Datu struktūra ir veids, kā glabāt datus programmā. Vienkāršs variants ir masīvs, sarežģītāks variants būtu izmantot masīvu un definēt likumus, pēc kuriem drīkst pievienot, dzēst, iegūt vērtību no tā. C++ programmās ne tikai masīvi var veidot datu struktūras, bet arī, piemēram, norādes.

C++ valodā ir tāds jēdziens, kā struktūra. Struktūras piemēru var skatīties 1. programmā.

```
#include <iostream>
#include <string>
#include <cmath>
using namespace std;

struct kordinates {
    int x;
    int y;
};

int main ()
{
    kordinates kord1;
    kord1.x = 13;
    kord1.y = 2;
    cout << kord1.x * kord1.y << endl;

    kordinates* kord2 = new kordinates();
    kord2->x = 13;
    kord2->y = 2;
    cout << kord2->x * kord2->y << endl;

    return 0;
}
```

**1. programma** - struktūras lietojums.

Struktūras ir ļoti līdzīgas iepriekš minētajām klasēm. Struktūra definē tipu, kuru var izmantot mainīgajiem. Struktūra sevī ietver mainīgos jeb atribūtus. Ja tiek izveidots mainīgais ar struktūras tipu, tad ir iespējams ar punkta palīdzību piešķirt vai piekļūt mainīgā vērtībai. Ja tiek izveidota norāde ar struktūras tipu un rezervēta atmiņa ar **new** tā tipa mainīgajam, tad atribūtiem jāpiekļūst ar **->** palīdzību.

### Struktūras atribūts kā norāde

Ja struktūras atribūts ir kā normāls mainīgais, tad tā tips varētu būt arī norādes tips. Piemēram, ja būtu vajadzība veidot C++ realizāciju 1. attēlā attēlotajai diagrammai, kur:

- Kastes ar uzrakstiem Galva un Aste ir norādes mainīgie uz datu struktūras sākuma atmiņas apgabalu un beigu atmiņas apgabalu.
- Kastes ar numuriem nozīmē rezervētu atmiņas apgabalu.
- Bulta apzīmē norādi no struktūras mainīgā atribūta uz atmiņas apgabalu, kur varētu glabāties tās pašas struktūras cita vērtība.

Realizācija ir parādīta 2. progrmmā.

![Saraksts](/media/theory/list.png)

**1. attēls** - diagramma.

```
#include <iostream>
#include <string>
#include <cmath>
using namespace std;

struct elements {
    int sk;
    elements* next;
};

elements* galva = NULL;
elements* aste = NULL;

void pielikt_skaitli(int sk)
{
    elements* tmp = new elements();
    tmp->sk = sk;
    if (galva == NULL)
    {
        galva = tmp;
        aste = tmp;
    } else {
        aste->next = tmp;
        aste = tmp;
    }

    aste->next = NULL;
}

int main ()
{
    pielikt_skaitli(2334);
    pielikt_skaitli(9876);
    pielikt_skaitli(33);
    pielikt_skaitli(9);
    pielikt_skaitli(2230);
    pielikt_skaitli(0);

    elements* tmp = galva;
    while (tmp != NULL)
    {
        cout << tmp->sk << endl;
        tmp = tmp->next;
    }

    return 0;
}
```

**2. programma** - diagrammas datu struktūras realizācija.

Lai gan sporta programmēšanas sacensībās šo tehniku neizmanto pārāk plaši vai praktiski nemaz, tā ir lietderīga, lai saprastu, kā nākamajās nodaļās strādā skaidrotās lineārās datu struktūras. Katru no tām var uzrakstīt ar struktūrām un atribūtiem kā norādēm.

<a href="http://www.cplusplus.com/doc/tutorial/structures/" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>