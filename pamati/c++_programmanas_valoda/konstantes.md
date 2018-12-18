# Konstantes

Konstantes pa lielam ir burtiski vērtības, kuras mēs uzrakstām kodā. Piemēram, skaitlis 1 ir konstante, jo skaitlis 1 nevar būt nekas cits, kamēr mainīgais a nav konstante, jo a var būt dažādas vērtības.

### Literāļi

Literāļi ir burtiski uzrakstītas konstantes. Iepriekš runājām par skaitļu pieskaitīšanu vai piešķiršanu, deklarēšanu. Tās vērtības, kuras šajās operācijās rakstījām bez mainīgo palīdzības, ir literāļi. Piemēru literāļiem, var skatīties 1. programmā.

```
#include <iostream>
#include <string>
using namespace std;

int main()
{
    int a = 13; // Integer literālis.
    int hex = 0x1A; // Integer literālis sešpadsmitnieku sistēmā.
    int oct = 057; // Integer literālis astoņnieku sistēmā.
    
    float f = 13.456; // Peldošā punkta literālis.
    float norm = 2.4e3; // Peldošā punkta literālis 2.4 * 10 ^ 3.
    
    char c = 'i'; // Simbola literālis.
    
    string s = "Hello world"; // Simbolu virknes literālis.
    string ml = "Hello\
world"; // Ja grib, tad var sadalīt simbolu virkni vairākās rindās, katra rindas beigās, izņemot pēdējo, pieliekto \ simbolu.
    string cc = "Hello" " world"; //Ja uzraksta vairākus simbola virkņu literāļus secīgi, tie tiks salikti kopā.

    bool b = true; // Loģiskā tipa literālis.

    return 0;
}
```

**1. programma** - literāļu piemēri.

### Literāļi ar tipu

Ir iespējams norādīt literāļiem specifisku tipu. Piemēru skatīt 2. programmā.

```
#include <iostream>
#include <string>
using namespace std;

int main()
{
    unsigned int a = 13u; //Nenegatīva vesela skaitļa literālis.
    long long b = 13ll; //Vesela 8 baitu skaitļa literālis.
    unsigned long long c = 13ull; //Nenegatīva vesela 8 baitu skaitļa literālis.

    float d = 13.123f; // Peldošā punkta float tipa literālis.
    long double e = 13.123; //Peldošā punkta long double tipa literālis.

    return 0;
}
```

**2. programma** - literāļi ar tipiem.

### Speciālie simboli

Speciālie simboli ir simboli, kuri tiek attēloti savādāk tekstā. Dažreiz to attēlošanas veids ir atkarīgs no vides, kur tos attēlo, bet pārsvarā katram tādam simbolam ir īpaša nozīme. Speciālos simbolus var redzēt 1. tabulā.

| Simbols | Nozīme |
| --- | --- |
| \\n | Pārnes kursoru jaunā rindā. Strādā līdzīgi, kā enter piespiešana rakstot tekstu. |
| \\r | Kursora pārnešana rindas sākumā. Piemēram, "Hello to \\r world" izskatītos uz ekrāna, kā "world to", jo tiekot līdz \\r, kursors tiek novietots sākumā un tekstam Hello tiek pārrakstīts pāri world. |
| \\t | Tab taustiņa piespiešanas simbols. |
| \\v | Vertikālais tab. Šo simbolu senākos laikos izmantoja printeriem. |
| \\b | Backspace taustiņa piespiešana. |
| \\f | Agrākos printeros šo simbolu ieraugot, tika izdrukāta ārā iesāktā lapa un sākts viss drukāt uz nākamās lapas. |
| \\a | Izvadot šo ārā, piemēram, "Hello \\a world", ja datorā ir "pīkstulis", tas iepīkstās. Uz 8.1. Windows un varbūt citiem šis simbols rada pīkstienu. |
| \\' | Ignorē simbola nozīmi. Var šādā veidā piešķirt, kā simbolu char mainīgajam, piemēram, char c = '\\''; |
| \\" | Ignorē simbola nozīmi. Var šādā veidā ievietot simbolu virknē - "Hello \\"Peter\\"". |
| \\\\ | Ignorē simbola nozīmi. Šādā veidā ir iespējams,piemēram, simbola virknē ievietot \\ simbolu - "Hello \\world\\\\". |

**1. tabula** - speciālie simboli.

### Konstantes un definīcijas

Dažreiz ir ļoti vērtīgi literāļiem piešķirt vārdu un izmantot šo vārdu citur. Konstantes izskatās līdzīgas mainīgajiem, tikai tās pēc tam vairs nevar mainīt un to deklarācijai priekšā ir const atslēgas vārds.

Definīcijas līdzīgi, kā konstantes, dod vārdu kādam literālim, bet tās tiek apstrādātas pirms kompilācijas. Definīcijas definē ar #define <nosaukums> <literālis>. Definīcija tiek ievietota kodā pirms kompilācijas burtiski aizstājot to izmantošanas vietu ar definēto literāli.

```
#include <iostream>
#define NEWLINE '\n'
using namespace std;

const double pi = 3.14159;

int main()
{
    cout << pi << endl; // Izvadīs 3.14159.
    cout << NEWLINE << endl; // Izvadīs pāreju uz jaunu rindu.
    return 0;
}
```

**3. programma** - konstantes, definīcijas.

<a href="http://www.cplusplus.com/doc/tutorial/constants/" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>