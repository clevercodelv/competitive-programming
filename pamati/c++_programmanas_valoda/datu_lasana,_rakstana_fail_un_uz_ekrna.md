# Datu lasīšana, rakstīšana failā un uz ekrāna

Datu lasīšana no ekrāna un failā notiek ļoti līdzīgi, patiesībā lasīšana no ekrāna un rakstīšana tajā ir tā pati lasīšana / rakstīšana failā, tikai speciāli tai ir izveidotas speciālas konstrukcijas, bet tajā neiedziļināsimies pārāk daudz.

### Pamata ievade un izvade

Izmantojot #include <iostream> bibliotēku, mēs varam izmantot cin, cout plūsmas un endl, lai izvadītu un ielasīt vērtības no ekrāna. Izmantojot cin, ekrānā kursors stāvēs un programma apstāsies, gaidot teksta ievadi. Tekstu ievadot un piespiežot enter, programma turpina darbību un teksts vai skaitlis ielasās mainīgajā līdz atstarpei vai rindas beigām. Skatīt 1. programmu.

```cpp
#include <iostream>
#include <string>
using namespace std;

int main()
{
    int a = 1234;
    string s = "Hello world";

    // Rakstīšana uz ekrāna.

    cout << s; // Izvadām uz ekrāna s vērtību. Kursors paliek tajā pašā rindā.
    cout << s << endl; // Izvadām s uz ekrāna tajā pašā rindā, kurā iepriekš izvadījām s un pārejam ar endl uz jaunu rindu jeb izvadām \n simbolu.
    
    string s2 = "Good night world";
    cout << s << " or " << s2 << a << endl; // Izvadām rindā "Hello world or Good night world1234" tekstu un pārejam nākamajā rindā.

    // Lasīšana no ekrāna.

    // Programma gaidīs, kamēr ievadīsim skaitli komandrindā. Ievadot ne skaitli, tik pavēstīts par kļūdu. Ja ievadītā teksta sākumā 
    // ir skaitlis un tad turpinās teksts, tad tiek ielasīta skaitļa daļa.
    cin >> a;
    cin >> s; // Programma gaidīs, kamēr kaut ko ievadīsim un spiedīsim enter. Pēc enter piespiešanas teksts no komandrindas atradīsies mainīgajā s.
    cin >> a >> s; // Īsāk pierakstītas divas iepriekšējās komandas.

    getline(cin, s); // Ielasa visu ievadīto rindu līdz rindas beigām mainīgajā s.

    return 0;
}
```

**1. programma** - cin / cout piemērs.

<a href="http://www.cplusplus.com/doc/tutorial/basic_io/" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>

### Ievade un izvade failā

Ievade un izvade failā ir līdzīga, kā ievade un izvade uz ekrāna. Vienīgi, lai kaut ko darītu ar kādu failu, tas ir jānorāda - jāatver un jāaizver. Darbam ar failiem ir līdzīga bibliotēka - #include <fstream>. Piemēru darbam ar failiem var redzēt 2. programmā.

Pieņemsim, ka mums ir teksta fails C:\test.txt ar šādu saturu:

12 Biskvits

```
#include <iostream>
#include <string>
#include <fstream>
using namespace std;

int main()
{
    int a;
    string s;

    ifstream fin; // Izveidojam faila mainīgo. ifstream norāda, ka fails tiek atvērts lasīšanai, tātad pašlaik rakstīšanu nevarēs veikt.
    fin.open("C:\test.txt"); // Atveram failu. Ne burtiski, bet programmas līmenī šādi var pateikt, ka gribam kaut ko darīt ar failu.
    fin >> a >> s; // Ielasām skaitli un tam sekojošo simbolu virkni
    cout << s << " " << a << endl; // Izvadām uz ekrāna "Biskvits 12".
    fin.close(); // Aizveram failu - paziņojam datoram, ka beigsim darbu ar to.

    ofstream fout; // Izveidojam faila mainīgo rakstīšanai failā. ofstream norāda, ka fails būs rakstīšanai.
    fout.open("C:\test.txt"); // Atveram failu. Atverot failu rakstīšanai, fails tiek iztīrīts jeb kļūst tukšs.
    fout << s << " " << a << endl; // Ierakstām failā, "Biskvits 12".
    fout.close(); // Aizveram failu.

    return 0;
}
```

**2. programma** - ievade / izvade failā.

<a href="http://www.cplusplus.com/doc/tutorial/files/" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>