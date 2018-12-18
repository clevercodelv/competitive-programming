# Norādes

Iepriekšējās nodaļās, lai piekļūtu vērtībām, mēs izmantojām mainīgos, kuriem ir nosaukumus. Šādā veidā mēs varam nedomāt par to, kur atmiņā glabājas mainīgo vērtības. Bet patiesībā visas šīs vērtības glabājas kaut kur atmiņā. Datora atmiņu var iztēloties, kā šūnu kopumu, kurās var glabāt vērtības jeb baitus. Piemēram, lai glabātu int mainīgo, mums vajag 4 baitus, tātad 4 šūnas atmiņā. Šīm atmiņas šūnām katrai ir sava adrese, kas ir skaitlis.

**Norādes operators (&)** - lai caur mainīgo varētu piekļūt vērtībai, programmai kaut kā ir jāspēj uzzināt vērtības adrese. Arī programmētājs var piekļūt vērtības adresei caur mainīgo ar norādes operatoru (skatīt 1. programmu). Norādes operators atgriež norādi. C++ valodā norādēm ir savi īpašie tipi - zvaigznīte (\*) plus jebkurš tipa nosaukums, piemēram, int\* vai char\*, u.t.t.

```
#include <iostream>
using namespace std;

int main ()
{
    int sk = 1432;
    int* address = &sk; // Saglabājam sk adresi norādes mainīgajā.
    cout << address << endl; // Izvadām adresi. Rezultātā iegūsim kādu heksadecimālu skaitli.

    return 0;
}
```

**1. programma** - norādes operators.

**Vērtības iegūšanas no norādes operators (\*)** - lai gan \* izmanto deklarējot norādes tipa mainīgo, tam ir vēl cita nozīme saistībā ar norādēm. To pieliekot priekšā norādes tipa mainīgajam vai adresei, var iegūt vērtību, uz kuru norāda adrese (skatīt 2. programmu).

```
#include <iostream>
using namespace std;

int main ()
{
    int sk = 1432;
    int* address = &sk; // Saglabājam sk adresi norādes mainīgajā.
    cout << address << endl; // Izvadām adresi. Rezultātā iegūsim kādu heksadecimālu skaitli.
    cout << *address << endl; // Iepriekšējā rindā izvadītajā adresē atrodas šajā rindā izvadītais skaitlis.

    return 0;
}
```

**2. programma** - vērtības iegūšana no adreses.

Norādes mainīgajiem ir sekojošas īpašības:

- Norādes mainīgos var savā starpā arī salīdzināt. Ja divi norādes mainīgie norāda uz vienu adresi, tie ir vienādi.
- Norādes mainīgos var arī inicializēt gluži kā int vai citus mainīgos, piemēram int* sk = &sk2;.

Norādēm ir liela nozīme masīvos, jo pateicoties tām, masīvi vispār pastāv. Pēc idejas masīvi ir atmiņas apgabals - virkne ar atmiņas šūnām. Mirklī, kad piekļūst kādam elementam, piemēram mas[5], notiek piekļuve mas mainīgā adresei ar 5 pozīciju nobīdi jeb mas adrese + 5 * mas baitu izmērs (skatīt 1. attēlu).

![Masīvs ar adresēm](/media/theory/masivs_address.png)

**1. attēls** - masīvs un tā adresācija.

Norādes mainīgie, kas norāda uz masīvu, var arī pārvietoties pa masīvu. Piemēru var apskatīt 3. programmā. Ja masīva viena elementa izmērs ir vairāki kilobaiti, pieskaitīšanas operators saprot, kas masīvam ir par tipu un pārvieto norādi pa tik baitiem, cik vajag.

```
#include <iostream>
using namespace std;

int main ()
{
    char mas[] = {'s', 'u', 'p', 'e', 'r', 'm', 'a', 'n'};
    char* p = mas;

    cout << *p; // 's'

    p++;
    cout << *p; // 'u'

    p += 3;
    cout << *p; // 'r'

    p -= 2;
    cout << *p; // 'p'

    cout << endl;

    return 0;
}
```

**3. programma** - pārvietošanās pa masīvu ar norādes mainīgo.

Ja ir vēlme vairāk apgūt par norādēm, būtu ieteicams palasīt papildus informāciju zemāk esošajā saitē.

<a href="http://www.cplusplus.com/doc/tutorial/pointers/" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>