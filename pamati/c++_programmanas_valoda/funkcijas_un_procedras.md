# Funkcijas un procedūras

Funkcija ir komandu grupa, kura tiek iekļautas \{\} iekavās. Funkcijai ir nosaukums un tai var padot parametrus jeb mainīgos. Funkcijas forma ir šāda **<tips> <nosaukums>(<parametrs 1>, <parametrs 2>, ...) { <komandas> }**. Viens funkcijas piemērs ir main funkcija, kur:

- **<tips>** ir int. Bet citām funkcijām <tips> var būt jebkurš tips, elementārs vai komplekss.
- **<nosaukums>** ir main. Var būt jebkurš derīgs nosaukums. Funkciju nosaukumiem ir tie paši ierobežojumi, kas mainīgo nosaukumiem.
- **<parametrs x>** nav. Citām funkcijām var būt vairāki parametri. Katram parametram ir jānorāda tā tips un nosaukums. Parametrs būs pieejams tikai funkcijas ietvarā.
- **<komandas>** ir viss starp \{\} iekavām.

Apskatīsim piemēru 1. programmā.

```cpp
#include <iostream>
using namespace std;

// <tips> ir int.
// <nosaukums> ir sum.
// <parametrs 1> ir a ar tipu int.
// <parametrs 2> ir b ar tipu int.
int sum(int a, int b)
{
    // Ja funkcijas tips nav void, tad funkcijai ir jāatgriež kāda vērtība.
    // Atgriešanu veic ar komandu return un aiz return uzrakstot kādu vērtību, mainīgo vai izteiksmi.
    return a + b;
}

int main ()
{
    int a = 10;
    // Funkcijām var padot vērtību jebkādā formā.
    // Padotā argumenta tipam ir jābūt tādam pašam, kā konkrētajam parametram vai
    // jāspēj konvertēties no padotā tipa uz parametra tipu. Piemēram 5.0 ir float.
    // Float tips var konvertēties uz int - pazūd skaitļa daļa aiz komata.
    cout << sum(5.0, a) << endl;
    cout << sum(a, a) << endl;

    // Kā parametrs var tikt padota jebkāda izteiksme, kas beigās atgriež uz parametra tipu konvertējamu vērtību.
    int rez = sum(a, a * a) + sum(5, sum(5, a));

    cout << rez << endl;

    return 0;
}
```

**1. programma** - funkcijas piemērs.

Apskatīsim dažus terminus:

- **Funkcijas izsaukums** - sum(5, a) iekš main funkcijas ir funkcijas izsaukums.
- **Funkcijas arguments** - sum(5, a) izsaukumā 5 un a ir argumenti. To secība ir svarīga, jo šajā gadījumā parametrs a kļūs par 5 un parametrs b ieņems argumenta a vērtību. Lai būtu otrādi, var apmainīt argumentu secību - sum(a, 5).
- **Funkcijas rezultāts** - iekš sum funkcijas tā vērtība, ko atgriež return ir funkcijas rezultāts. return ir jāatgriež tāda vērtība, kas var tik pārveidota uz funkcijas tipu.

### Funkcijas ar void tipu

Citās programmēšanas valodās ir tāds jēdziens, kā procedūra, kas parasti ir līdzīga funkcijai ar vienīgo atšķirību, ka procedūra neko neatgriež, bet izdara kādu darbību. C++ procedūras neeksistē, bet eksistē funkcijas ar void tipu. Ja funkcijai tiek izmantots void tips, tā var neatgriezt vērtību ar return. Piemēram skatīt 2. programmu.

```
#include <iostream>
using namespace std;

int skaits; // Mainīgie definēti ārpus funkcijām vienmēr būs 0.

void palielinat_skaits()
{
    skaits++;
}

int main ()
{
    cout << skaits << endl; // Izvada 0.

    // Funkcijas var nekam arī nepieškirt. Tas ir īpaši lietderīgi procedūru gadījumā.
    palielinat_skaits();
    cout << skaits << endl; // Izvada 1.

    for (int i = 0; i < 10345; ++i)
        palielinat_skaits();

    cout << skaits << endl; // Izvada 10346.

    return 0;
}

```

**2. programma** - void funkcijas jeb procedūras piemērs.

### Funkcijas main komanda return

Kad programmētājs sāk strādāt pie lielām sistēmām, šīs sistēmas bieži vien var nesastāvēt no viena faila, vienas programmas, viena procesa. Process vienkārši sakot ir vairākas palaistas programmas (var būt arī vienādas). Kad kāda programma izsauc citu programmu, šai citai programmai beidzoties, izsaucēja var gribēt zināt, kā noritēja tās izpilde - veiksmīgi, neveiksmīgi, cits stāvoklis? Neiedziļinoties pārāk procesos, laba prakse C++ programmas main funkcijas beigās ir pielikt return 0; komandu, lai dators zinātu, ka programma bija veiksmīga.

### Noklusētās vērtības

Funkcijas parametriem var tikt definētas noklusētās vērtības. Noklusētā vērtība nozīmē, ka, ja netiek padots parametrs ar noklusēto vērtību, dators nevis izmetīs kļūdu, bet piešķirs parametram noklusēto vērtību. Piemēru var skatīt 3. programmā.

```
#include <iostream>
using namespace std;

// Ja 2. parametrs netiks padots funkcija izsaukumā, b būs 10.
int sum(int a, int b = 10)
{
    return a + b;
}

int main ()
{

    cout << sum(5, 5) << endl; // 5 + 5 = 10

    cout << sum(5) << endl; // 5 + 10 = 15

    return 0;
}
```

**3. programma** - funkcijas parametra noklusētā vērtība.

### Argumenta padošana pēc vērtības un norādes

Iepriekš padodot argumentu funkcijai, tā vērtība tika kopēta parametrā. Piemēram, ja mums ir programma ar parametriem, kas varētu aizņemt daudz atmiņu, piemēram simbolu virknes (string), tad iespējams garie parametri tiks kopēti un var notikt atmiņas pārpildīšanās. Piemēram skatīt 4. programmu.

```
#include <iostream>
#include <string>
using namespace std;

string salimet(string a, string b)
{
    return a + b;
}

int main ()
{

    string s1 = "1", s2 = "2";

    // Uzģenerējam milzīgas divas simbolu virknes garumā 2^25.
    for (int i = 0; i < 25; ++i)
    {
        s1 = s1 + s1;
        s2 = s2 + s2;
    }

    // Padodot tās kā argumentus, s1 tiks kopēta uz a un s2 tiks kopēta uz  b.
    string s3 = salimet(s1, s2);

    return 0;
}

```

**4. programma** - funkcijas argumenti tiek kopēti.

Lai no šīs problēmas izvairītos, ir iespējams panākt, lai parametru mainīgie nevis aizņem jaunu atmiņas apgabalu, bet norāda uz argumentu mainīgo atmiņas apgabaliem. Tam ir jāizmanto **& operators** Skatīt 5. programmu.

```
#include <iostream>
#include <string>
using namespace std;

string salimet(string &a, string &b)
{
    return a + b;
}

int main ()
{

    string s1 = "1", s2 = "2";

    // Uzģenerējam milzīgas divas simbolu virknes garumā 2^25.
    for (int i = 0; i < 25; ++i)
    {
        s1 = s1 + s1;
        s2 = s2 + s2;
    }

    // Padodot tās kā argumentus, s1 tiks kopēta uz a un s2 tiks kopēta uz  b.
    string s3 = salimet(s1, s2);

    return 0;
}

```

**5. programma** - funkcijas argumenti tiek padoti pēc norādes.

Savukārt 5. programmā uzrodas jauna problēma. Ja mēs varam padot argumentus tagad pēc norādes (parametri rāda uz to pašu atmiņas apgabalu, kur argumenti), tad palabojot parametrus, mēs netīšām varam negribot sabojāt argumentu vērtības. Lai no tā izvairītos jeb drīzāk aizsargātos, var definēt funkciju mainīgos, kā nelabojamus. Šādā gadījumā, ja arī notiks labošana jeb rakstīšana atmiņā, programma izmetīs kļūdu un netīšām neieviesīsies šī nevēlamā uzvedība - izdomāsim citu variantu, kā uzrakstīt risinājumu. Parametrus, kā nelabojamus definē ar const operatoru priekšā parametra tipam. Piemēru var skatīt 6. programmā.

```
#include <iostream>
#include <string>
using namespace std;

// a un b nevar tagad labot. Iesaku pamēģināt, lai pārliecinātos.
string salimet(const string &a, const string &b)
{
    return a + b;
}

int main ()
{

    string s1 = "1", s2 = "2";

    // Uzģenerējam milzīgas divas simbolu virknes garumā 2^25.
    for (int i = 0; i < 25; ++i)
    {
        s1 = s1 + s1;
        s2 = s2 + s2;
    }

    // Padodot tās kā argumentus, s1 tiks kopēta uz a un s2 tiks kopēta uz  b.
    string s3 = salimet(s1, s2);

    return 0;
}
```

**6. programma** - const operatora lietojums parametriem.

<a href="http://www.cplusplus.com/doc/tutorial/functions/" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>