# String bibliotēka

Jau apskatījām, ka string bibliotēka ļauj izmantot string tipu, lai veidotu simbolu virkņu jeb teksta mainīgos. Vērtīgi būt apskatīt, kādas darbības var veikt ar string tipa simbolu virknēm. 

### String metodes

C++ ļauj izmantot klases un iekš klasēm ir definētas metodes, šie ir termini no OOP jeb Objekt orientētās programmēšanas. OOP šeit mēs neapgūsim, bet, lai izmantotu string metodes, ir jāsaprot, ka string ir klase un jebkurš mainīgais ar string tipu ir objekts. Šī materiāla ietvarā aprobežosimies ar to, ka klases ir mainīgo tipi jeb kompleksie tipi (tie, kas nav elementārie tipi). Kompleksajiem tipiem ir iespēja pielietot kādu metodi, kas ir darbība, kura kaut ko izdara mainīgā kontekstā. Piemēram, ja vēlamies iegūt no string a = "sienazis"; apakšvirkni "azis", tad varam izmantot apakšvirknes metodi (skatīt 1. programmu).

```
#include <iostream>
#include <string>
using namespace std;

int main ()
{
    string str = "sienazis"; // Orģinālā simbolu virkne.
    // Apakšvirknes metode, lai iegūtu simbolu virkni "azis" no pozīcijas 4
    //(pozīcijas sākas ar 0) garumā 4 (jo "azis" satur 4 burtus).
    string str2 = str.substr(4, 4);
    cout << str2 << endl; // Metode substr no str izgrieza "azis" un ievietojam str2 mainīgajā. Rezulātā izvadās "azis".

    return 0;
}
```

**1. programma** - apakšvirknes iegūšana no simbolu virknes.

String tipa mainīgajiem ir vēl daudzas metodes. Visu metožu uzskaitījumu var apskatīt lapas apakšā esošajā norādē uz informācijas resursu, bet 2. programmas piemērā ir arī redzamas dažas populārākās metodes un to īss apraksts.

```
#include <iostream>
#include <string>
using namespace std;

int main ()
{
    string str = "sienazis";

    // Atgriež simbola virknes simbolu skaitu.
    int garums = str.length();
    cout << garums << endl;

    // Notīra simbolu virkni - tā kļūst par "".
    // Notīrītai simbolu virknei garums ir 0.
    str.clear();
    cout << str.length() << endl;

    // Ja simbolu virkne ir "", tad empty metode atgriež true, citādi false.
    if (str.empty())
        cout << "Tukss" << endl; // Izvadīs šo, jo tikko iztukšojām mainīgo.
    else
        cout << "Nav tukss" << endl;

    // += operators kreisajā pusē esošajam mainīgajam pieliek beigās klāt labajā pusē esošo vērtību.
    str = "sien";
    cout << str << endl;
    str += "aze";
    cout << str << endl;

    // [poz] operators izvada simbolu, kurš atrodas simbolu virknes pozīcijā poz (pozīcijas sāk skaitīt no 0 nevis 1).
    cout << str[0] << endl; // Izvada 's'.
    cout << str[str.length() - 1] << endl; // Izvada pēdējo simbolu 'e'. Ja pozīcijas sākas no 0, tad pēdējā pozīcija ir garums - 1.

    // Ieliek jebkurā no pozīcijām simbolu virkni. Viss no pozīcijas pa labi pabīdās.
    str.insert(4, "amais");
    cout << str << endl; // Izvada "sienamaisaze";

    // Nodzēš jebkuru fragmentu simbolu virknē. Pirmais arguments ir pozīcija, no kuras dzēs, otrais ir cik garu fragmentu dzēst.
    // Ja kaut kas paliek pāri pa labi, tas pārvietojas pa kreisi.
    str.erase(9, 3);
    cout << str << endl; // Izvada "sienamais".

    // Aizvieto simbolu virknes fragmentu ar simbolu virkni.
    // Aizvietojam 4 pozīcijā esošo 5 simbolus garo fragmentu "amais" ar "azis".
    str.replace(4, 5, "azis");
    cout << str << endl; // Izvada "sienazis".

    // Apmaina vietām simbola virknes saturu ar argumentā padoto simbola virknes saturu.
    string str2 = "lietussargs";
    str.swap(str2);
    cout << str << endl; // Izvada "lietussargs".
    cout << str2 << endl; // Izvada "sienazis".

    // Saliek kopā divas simbolu virknes.
    string str3 = str + " un " + str2;
    cout << str3 << endl; // Izvada "lietussargs un sienazis".

    // Atrod pozīciju meklējamajai simbolu virknei.
    int pos = str.find("sargs");
    cout << pos << endl; //Izvadīs 6.
    if (str.find("azis") == string::npos) // string::npos mainīgais satur vērtību, kuru atgriež find, ja pozīcija nav atrasta.
        cout << "Nav atrasts" << endl;
    else
        cout << "Ir atrasts" << endl;

    // Salīdzina divus string mainīgos.
    // Ja compare atgriež <0, tad str ir leksikogrāfiski mazāks par str2.
    // Ja compare atgriež 0, tad abas str un str2 ir vienādi.
    // Ja compare atgriež >0, tad str ir leksikogrāfiski lielāks par str2.
    cout << str.compare(str2) << endl;

    // Salīdzināšanas operatori < > <= >= strādā arī ar simbolu virknēm,
    // simbolu virknes tiek salīdzinātas leksikogrāfiski.
    if (str < str2)
        cout << str << " < " << str2 << endl;
    else
        cout << str << " > " << str2 << endl;

    return 0;
}
```

**2. programma** - string tipa mainīgo metodes.

<a href="http://www.cplusplus.com/reference/string/string/" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>