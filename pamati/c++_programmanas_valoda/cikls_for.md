# Cikls for

Cikls for ir veidots, lai atkārtotos konkrētu skaitu reizes. Cikla for var deklarēt un inicializēt mainīgo īpašā veidā. Uzrakstīsim iepriekš minēto kartupeļu mizošanas algoritmu ar for ciklu, to nedaudz papildinot (realizāciju skatīt 1. programmā).

1. Ielasām spainī esošo kartupeļu skaitu. 
1. Pārbaudām, vai spainī ir kāds kartupelis (jo varbūt mums iedeva sākumā tukšu spaini). Ja ir, turpinām darbu, citādi dodamies uz beigām.
1. Pasakām, cik spainī ir palikuši kartupeļi.
1. Nomizojam 1 kartupeli.
1. Dodamies uz 2. soli.
1. Beidzam darbu.


```
#include <iostream>
using namespace std;

int main()
{
    int kartupeli;
    cin >> kartupeli;

    for (int i = 0; i < kartupeli; ++i)
    {
        cout << "Spaini ir " << (kartupeli - i) << " kartupeli." << endl;
    }

    return 0; // Beidzam darbu.
}
```


**1. programma** - kartupeļu mizošanas programma ar for ciklu.


Kā redzam, tad piemērā ir \{\} iekavas, kurās atrodas kods, kurš katrā iterācijā tiek izpildīts, bet tagad ir interesanta for daļa nākusi klāt. Pats vārds for norāda, ka tas būs for cikls, bet tas, kas ir () iekavās, dalās trīs blokos, kur katru bloku atdala ; simbols. Bloku nozīme ir:

1. **int i = 0** - var deklarēt vienu līdz vairākiem mainīgajiem, kurus pēc cikla nevarēs izmantot.
1. **i &lt; kartupeli** - ir nosacījums, gluži kā while un do while ciklos. Šis nosacījums var izmantot 1. blokā deklarētos mainīgos.
1. **++i** - šis bloks izpildās pēc katras iterācijas. Šeit ir iespējams mainīt mainīgos, kas ir paredzēti iterāciju skaitīšanai, šajā gadījumā tas ir i.


<a href="http://www.cplusplus.com/doc/tutorial/control/" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>