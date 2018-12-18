# Mainīge un tipi

Lai gan Hello world programma pilnībā atbilst programmas definīcijai, tomēr tā nav pārāk lietderīga. Patiesībā daudz ātrāk mums būtu pašiem uzrakstīt Hello world tekstu kur nu mums to vajag. Bet programmēšana neaprobežojas tikai ar teksta izvadīšanu uz ekrāna. Patiesībā programmēšana ir spējīga arī atcerēties kaut ko, piemēram, skaitļus. Līdzīgi, kā piemērā ar 2 kāpināšanu, mēs varam atcerēties skaitli x. Šādus skaitļus vai cita veida vērtības sauc par mainīgajiem. Mainīgie ir kā kastītes ar nosaukumiem, kurās glabājas vērtības.

Apskatīsim piemēru šādam algoritmam 1. programmā:

1. Piešķiram mainīgajam a skaitli 4.
1. Piešķiram mainīgajam b skaitli 3.
1. Aprēķinam a * b un piešķiram rezultātu result1 mainīgajam.
1. Aprēķinam (a - 1) * (b - 1) un piešķiram rezultātu result2 mainīgajam.
1. Izdrukājam uz ekrāna result1.
1. Izdrukājam uz ekrāna result2.
1. Beidzam darbu.


```
#include <iostream>
using namespace std;

int main()
{
    int a = 4; // Piešķiram mainīgajam a skaitli 4.
    int b = 3; // Piešķiram mainīgajam b skaitli 3.
    int result1 = a * b; // Aprēķinam a * b un piešķiram rezultātu result1 mainīgajam.
    int result2 = (a - 1) * (b - 1); // Aprēķinam (a - 1) * (b - 1) un piešķiram rezultātu result2 mainīgajam.
    
    cout << result1 << endl; // Izdrukājam uz ekrāna result1.
    cout << result2 << endl; // Izdrukājam uz ekrāna result2.

    return 0; // Beidzam darbu.
}
```


**1. programma** - mainīgo izmantošanas piemērs.


Pāris novērojumi, kurus varam izdarīt ir:

- Mainīgo nosaukumiem nav obligāti jābūt 1 simbolu gariem. Piemēram **result1** ir pilnībā derīgs mainīgā nosaukums.
- Mainīgo nosaukumi var saturēt ciparus. Patiesībā ir vēl labāk. Mainīgo nosaukumi var saturēt lielos, mazos latīņu burtus (vienkārši sakot, tie ir burti bez garumzīmēm), ciparus un _ simbolu. Pārējie simboli nav atļauti. Nevar arī izmantot nelielu skaitu speciālus vārdus kā mainīgo nosaukumus, kurus izmanto citām vajadzībām programmā. Ir jāatceras viena lieta, ka vienādi mainīgie ar dažādiem lielajiem burtiem ir divi dažādi mainīgie, piemēram, result1 un Result1 ir divi dažādi mainīgie.

### Mainīgo tipi

Mainīgā jēdziens ir plašs. Līdz šim mēs ar mainīgajiem, piemēram, result1 apzīmējām skaitli jeb result1 saturēja skaitli. Bet mainīgā jēdziens ir vēl plašāks. Tas var saturēt ne tikai skaitli, bet arī cita veida vērtības, piemēram simbolu virkni jeb tekstu. Bet lai nodrošinātu šādu funkcionalitāti, datoram ir jāzina, kas glabāsies šajā mainīgajā. Tādēļ mēs to datoram pateiksim. To var izdarīt pierakstot, pirms pirmo reizi izmantojam mainīgo, priekšā tipu. 1. tabulā var apskatīt visbiežāk izmantotos, elementāros mainīgo tipus.

Tips | Izmērs | Apraksts
---|---|---
char | 1 baits | Viens simbols simbolu virknē.
unsigned char | 1 baits | Simbols, kur katru simbolu apzīmē ar pozitīvu veselu skaitli.
int | 4 baiti | Vesels skaitlis.
unsigned int | 4 baiti | Vesels pozitīvs skaitlis.
long long | 8 baiti | Vesels ļoti liels skaitlis.
unsigned long long | 8 baiti | Vesels pozitīvs, ļoti liels skaitlis.
float | 4 baiti | Skaitlis ar vērtību aiz komata.
double | 8 baiti | Skaitlis ar vērtību aiz komata un lielāku precizitāti, kā float.
bool | 1 baits | Loģiskais mainīgais, satur true vai false.
void | | Satur jebko. Var tikt izmantots, lai padotu jebkuru mainīgo, bet apstrāde kļūst sarežģītāka un nav ieteicams izmantot sporta programmēšanā, ja labi nepārzina šo tipu. Tiesa, šur tur to izmantosim tālākās nodaļās tehnisku iemeslu dēļ, bet pieņemsim, ka tam tā ir jābūt. Lai uzzinātu par šo tipu vairāk, ieteicams ir palasīt papildus materiālus.


**1. tabula** - biežāk izmantotie elementārie tipi.


Mainīgais nevar saturēt bezgalīgi lielu vērtību. Tips pasaka, cik liela vērtība mainīgajā var glabāties. 1. tabulā tipiem ir dažādi atmiņas izmēri baitos pielikti klāt. Šie atmiņas izmēri nosaka, cik lielas vērtības var saglabāt šāda tipa mainīgajos. 2. tabula apraksta, kāds atmiņas izmērs atbilst kādam skaitļa intervālam.

Atmiņas izmērs | Intervāls | Intervāls pozitīviem skaitļiem | Piezīme
---|---|---|---
1 baits | no -128 līdz 127 | no 0 līdz 255 | 2<sup>8</sup> vērtības.
2 baiti | no -32768 līdz 32767 | no 0 līdz 65535 | 2<sup>16</sup> vērtības
4 baiti | no -2147483648 līdz 2147483647 | no 0 līdz 4294967295 | 2<sup>32</sup> vērtības
8 baiti | no -9223372036854775808 līdz 9223372036854775807 | no 0 līdz 18446744073709551615 | 2<sup>64</sup> vērtības


**2. tabula** - atmiņas intervāli.


Piemērs mainīgo tipu norādīšanai ir redzams 1. un 2. programmā. Šajos piemēros var redzēt arī tādus jēdzienus, kā deklarācija un inicializācija.

- **Deklarācija** - ir mainīgā definēšana. Pasakot, ka mēs izmantosim mainīgo ar tipu int, mēs deklarējam šo mainīgo.
- **Inicializācija** - mainīgo deklarējot var piešķirt tam sākotnējo vērtību, bet var arī atstāt tukšu. Piešķirot mainīgajam pie deklarācijas vērtību, tas tiek inicializēts.


```
#include <iostream>
using namespace std;

int main()
{
    int a; // Deklarējam mainīgo a ar tipu int.
    a = 5; // Piešķiram a vērtību 5.
    
    int b = 4; // Deklarējam mainīgo a ar tipu int. Inicializējam b ar vērtību 4.
    b = a + 1; // Piešķiram b vērtību a + 1. a šajā mirklī ir 5, tad b pēc šīs komandas izpildes kļūs par 6.
    
    char c = 'i'; // Deklarējam mainīgo c ar tipu char. Inicializējam c ar simbolu 'i'. Simbolus ir jāliek 'i' parastajās pēdiņās.

    return 0; // Beidzam darbu.
}
```


**2. programma** - mainīgo deklarācija, inicializācija, vērtību piešķiršana.


### Ievads par simbolu virknēm

Pamata tipi sniedz iespēju glabāt programmas izpildes laikā elementāras vērtības, kā skaitļus, bet kompleksie tipi var saturēt jau sarežģītākus tipus, piemēram, simbolu virknes, kas sastāv no daudz char tipa mainīgajiem.

Simbola virkņu tipu var deklarēt ar string vārdu. Inicializēt mainīgā vērtību var piešķirot tekstu ieliktu " dubultajās pēdiņās (skatīt 3. programmu). Lai izmantotu string vārdu, ir nepieciešams pievienot vēl vienu bibliotēku programmai.

```
#include <iostream>
#include <string>
using namespace std;

int main()
{
    string s = "Hello world";
    cout << s << endl;
    return 0; // Beidzam darbu.
}
```


**2. programma** - Hello world programma.


<a href="http://www.cplusplus.com/doc/tutorial/variables/" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>