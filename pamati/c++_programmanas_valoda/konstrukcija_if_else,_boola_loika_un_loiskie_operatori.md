# Konstrukcija if else, boola loģika un loģiskie operatori

Šīs nodaļas ietvarā runāsim par to, kā pie konkrētiem nosacījumiem veikt darbības jeb pieņemt lēmumus. Piemēram, lai uzzinātu, vai programmas lietotājs ir ievadījis pāra vai nepāra skaitli. Algoritms varētu rīkoties sekojoši:

1. Ielasīt skaitli A.
1. Ja A % 2 == 0. *(Pārbaude vai atlikums A dalot ar 2 ir 0)
1. Izvada "Pāra".
1. Citādi izvada "Nepara".

Analizēsim algoritma soļus. Skaitļa ielasīšana tika apskatīta iepriekšējās nodaļās. Tālāk nākamajos divos soļos seko šāda konstrukcija "ja <kaut kas notiek>, tad <darām kaut ko>, citādi <darām kaut ko citu>" jeb **"ja-tad-citādi"**. Pierakstot šo konstrukciju angliski, mums sanāk **"if-then-else"**. Arī programmēšanā eksistē šāda konstrukcija. 1. programmā ir apskatāma algoritma realizācija.

```
#include <iostream>
using namespace std;

int main()
{
    int sk;
    cin >> sk; // Ielasām skaitli.

    if (sk % 2 == 0) // Šī ir if daļa no if-then-else.
    {
        // then daļa no if-then-else. Izvadīt "Para".
        cout << "Para" << endl;
    }
    else 
    {
        // Else daļa no if-then-else. Izvadīt "Nepara".
        cout << "Nepara" << endl;
    }

    return 0;
}
```

<center>**1. programma** - skaitļa paritātes noteikšanas programma.</center>

\{\} iekavas then un else daļā var apzīmēt vairākas koda rindas, gluži kā main() koda rindas ieliktas \{\} iekavās.

### Boola loģika un loģiskie operatori

Kā rakstīt if-then-else konstrukcijas if daļas nosacījumus. Kā pateikt datoram, lai pie kaut kādiem nosacījumiem tas veic komandas A un pie citiem nosacījumiem komandas B? Kā definēt šos **likumus**? Sākumā apskatīsim, kā likumi izskatās cilvēku valodā konkrētam algoritmam, kurš nosaka, vai skaitlis ir pāra un lielāks par 100 vai skaitlis ir nepāra un mazāks par 100:

1. Ielasīt skaitli.
1. Ja skaitlis ir pāra **un** lielāks par 100 **vai** skaitlis nepāra **un** mazāks par 100.
1. Tad izvadīt vārdu "Derigs".
1. Citādi izvadīt vārdu "Nederigs".


Šī algoritma if-then-else nosacījumi ir sekojoši:

- skaitlis ir pāra;
- skaitlis ir lielāks par 100;
- skaitlis ir nepāra;
- skaitlis ir mazāks par 100.


Var novērot, ka, apskatot kādu konkrētu skaitli, uz katru šo likumu var atbildēt ar **jā** vai **nē**. Iepriekš apskatījām tipu bool, kura mainīgie saturēja vērtības **true** vai **false**, kas ir tas pats jā vai nē. 

Likumus savā starpā saista un, vai operatori. Tos sauc par loģiskajiem operatoriem un C++ tie pierakstās ar && (un jeb and), \|\| (vai jeb or). Šie divi loģiskie operatori var saņemt divus likumus, kā operandus un atgriezt vērtību atkarībā no operandu vērtībām. Šos un dažus citus loģiskos operatorus var apskatīt 1. tabulā.

&& (and) | true | false | | &#124;&#124; (or) | true | false | | ! (not) | |
---|---|---|---|---|---|---|---|---|---|---
**true** | true | false | | **true** | true | true | | **true** | false |
**false** | false | false | | **false** | true | false | | **false** | true |

<center>**1. tabula** - loģisko operatoru darbība.</center>

```
#include <iostream>
using namespace std;

int main()
{
    int sk;
    cin >> sk;
    if ((sk % 2 == 0 && sk > 100) || (sk % 2 != 0 && sk < 100)) // Šādi izskatās algoritmā minētais nosacījums if daļā.
    {
        cout << "Derigs" << endl;
    } else {
        cout << "Nederigs" << endl;
    }

    return 0;
}
```

<center> **2. programma** - loģisko operatoru piemērs if-then-else konstrukcijā.</center>

<a href="http://www.cplusplus.com/doc/tutorial/control/" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>
