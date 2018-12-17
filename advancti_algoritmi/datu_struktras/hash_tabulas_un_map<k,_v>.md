# Hash tabulas un map&lt;K, V&gt;

Hash tabulas ir asociatīva struktūra, kurā teorētiski var atrast, ielikt, dzēst elementu O(1) laikā. Bet tas ir ar vienu nosacījumu, ka hash funkcija tiek izvēlēta efektīva pret glabājamajiem datiem.

Programmēt hash tabulu var ar masīva palīdzību. Hash funkcija ir funkcija, kas hash masīva tipa mainīgos spēj pārvērst par kaut kādu skaitli, piemēram, ja ir jāglabā 2 pakāpes, tad hash funkcija var būt logaritms pie bāzes 2. Šādā veidā piemēram 1024 tiks glabāts masīva elementā H[10]. Protams, var gribēties glabāt komplicētākas vērtības H[]. Piemēram, simbolu virknes. Viens variants būtu saskaitīt simbolus un glabāt simbolu virkni iekš H[simbolu summa % H izmērs] elementa. Šī arī nav efektīva metode, bet tas pa lielam ir atkarīgs no glabājamo datu īpatnībām, jo neviena hash funkcija nav universāla. Kāpēc hash funkcija var nebūt universāla? Tādēļ, ka var gadīties divi dažādi argumenti, kas atgriež divas vienādas vērtības. Piemēram, minētajā funkcijā ar simbolu saskaitīšanu, derētu jebkura kādas simbolu virknes permutācija, lai funkcija atgrieztu vienādas vērtība - "aba", "baa", "aab" atgriezīs vienādu H[] masīva indeksu. Šī iemesla dēļ teorijā hash funkcijas darbības ir konstantas, bet ar nosacījumu, ka funkcija ir ideāla, bet tā kā tādu funkciju praksē ir grūti piemeklēt, tad improvizē un veido katru hash elementu kā sarakstu, kurš satur glabājamā tipa elementus. Hash darbībai var apskatīt 1. attēlu.

<center><img alt="Hash" src="/media/theory/hash.png" /></center>

<center>**1. attēls** - hash darbība.</center>

<a href="http://en.wikipedia.org/wiki/Hash_table" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>

### STL map&lt;K, V&gt;

C++ eksistē struktūra, kas var kalpot hash struktūras vietā - map&lt;K, V&gt, kur K ir atslēgas (jeb hash funkcija argumenta) tips un V ir glabājamās vērtības tips. Lai gan par map var domāt kā par hash struktūru, patiesībā iekšienē tur slēpjas cita struktūra, tādēļ darbības ir O(log(n)). Par map tipa mainīgo var domāt kā par masīvu, kur kā indeksu var izmantot K tipu. Piemēram var apskatīt 1. programmu.

```
#include <iostream>
#include <map>
#include <string>
using namespace std;

map<string, int> m;

int main()
{
    m["zero"] = 0;
    m["one"] = 1;
    m["two"] = 2;
    m["three"] = 3;
    m["four"] = 4;
    m["five"] = 5;
    m["six"] = 6;
    m["seven"] = 7;
    m["eight"] = 8;
    m["nine"] = 9;

    string cmd;
    do
    {
        cin >> cmd;
        if (m.find(cmd) != m.end())
            cout << m[cmd] << endl;
    } while (cmd != "exit");

    return 0;
}
```

<center>**1. programma** - STL map bibliotēka.</center>

<a href="http://en.wikipedia.org/wiki/Hash_table" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>