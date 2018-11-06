#Greja kodi

Greja kodi ir virkne ar binārām virknēm, kur katra atšķiras no nākamās ar vienu bitu. Piemēram:

```
001
011
010
011
111
110
u.t.t.
```

Greja kodus var ģenerēt salīdzinoši vienkārši - ar rekursijas vai cikla palīdzību. Algoritms ir sekojošs (realizāciju var apskatīt 1. prgorammā).

1. Ielasām N, cik garus Greja kodus vajag ģenerēt.
1. Izveido sākotnējo masīvu M = {0, 1}.
1. N - 1 reizes izpilda.
1. M = M + reverse(M). reverse - apgriež masīvu otrādi.
1. M pirmajai pusei pieliek aizmugurē vai priekšā 0, otrajai pusei pieliek priekšā 1.


```
#include <iostream>
#include <string>
#include <vector>
#define SIZE 20
using namespace std;

void make_gray_codes(vector<string> &v, int N)
{
    if (!v.size())
    {
        v.push_back("0");
        v.push_back("1");
    }

    for (int i = 1; i < N; ++i)
    {
        int v_size = v.size();
        for (int i = v_size - 1; i >= 0; --i)
        {
            v.push_back(v[i] + "1");
            v[i] += "0";
        }
    }
}

int main()
{
    vector<string> v;

    make_gray_codes(v, SIZE);

    for (int i = 0; i < v.size(); ++i)
        cout << v[i] << endl;

    return 0;
}
```

<center>**1. programma** - Greja kodu ģenerēšana.</center>

<a href="http://en.wikipedia.org/wiki/Gray_code" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>