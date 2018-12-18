# Vektors un vector&lt;T&gt;

Vektors ir lineāra masīvam līdzīga datu struktūra. Vektors strādā kā saraksts, kurā var pielikt elementus klāt, tādā veidā palielinot tā izmērus no abiem galiem, bet vienlaikus ir iespējams tā elementiem piekļūt ar [] operatora palīdzību, kā masīvā. Tiesa, jāuzmanās ar ievietošanu un dzēšanu vektora sākumā, jo tādā gadījumā datu struktūra tiek pabīdīta uz vienu vai otru pusi (visiem elementiem mainās indeksi). Tā rezultātā darbība no konstantas var kļūt par lineāru atkarībā, cik tuvu sākumam tiek veikta elementa pievienošana vai dzēšana.

![Vektors](/media/theory/vector.png)

**1. attēls** - vektora darbības.

Vektora darbību sarežģītība ir:

- Elementa meklēšana **O(1)**. Dēļ [] operatora, kurš tiek realizēts vektoros konstantā laikā, piekļuve ir konstanta.
- Elementa ievietošana **O(1)** pašās beigās un **O(N)** sākumā. Ievietojot elementu vektora vidū, sarežģītība variē intervālā no O(1) līdz O(N). 
- Elementa izņemšana **O(1)** pašās beigās un **O(N)** sākumā. Ievietojot elementu vektora vidū, sarežģītība variē intervālā no O(1) līdz O(N). 

### STL bibliotēka vector

vector bibliotēkā ir realizēta vektora funkcionalitāte. Tās lietošanas piemērs ir apskatāms 1. programmā.

```cpp
#include <iostream>
#include <vector>
using namespace std;

void print(const vector<int> &v)
{
    for (int i = 0; i < v.size(); ++i)
    {
        cout << v[i] << " ";
    }
    cout << endl;
}

int main ()
{
    // Izveidojam vektora mainīgo.
    // <> iekavās tiek likts tips (elementārs vai komplekss), kura vērtības tiks glabātas.
    vector<int> v;

    // Ieliekam sākotnējos elementus.
    v.push_back(3);
    v.push_back(0);
    print(v);

    // Ieliekam beigās 9.
    v.push_back(9);
    print(v);

    // Ieliekam 0. pozīcijā 1.
    v.insert(v.begin(), 1);
    print(v);

    // Ieliekam beigās 4.
    v.push_back(4);
    print(v);

    // Ieliekam 1. pozīcijā 8.
    v.insert(v.begin() + 1, 8);
    print(v);

    // Izņemt no 0. pozīcijas.
    v.erase(v.begin());
    print(v);

    // Izņemt no beigām.
    v.pop_back();
    print(v);

    // Izņemt no 2. pozīcijas.
    v.erase(v.begin() + 2);
    print(v);

    return 0;
}
```

**1. programma** - vektoru bibliotēkas lietojums.

Vairāk metodes var apskatīt zemāk esošajā informācijas avotā.

<a href="http://www.cplusplus.com/reference/vector/" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>