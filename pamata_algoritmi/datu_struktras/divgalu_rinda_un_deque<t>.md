#Divgalu rinda un deque&lt;T&gt;

Divgalu rinda ir rinda, kurai abiem galiem var gan pievienot, gan izņemt elementus. Dažreiz šo struktūru sauc par galvas-astes saistīto sarakstu, jo tā strādā kā saraksts, pa kuru vienkārši nevar staigāt.

![Divgalu rinda](/media/theory/deque.png)

<center>**1. attēls** - divgalu rindas darbības.</center>

Divgalu rindas darbību sarežģītība ir:

- Elementa meklēšana **O(N)**. Lai atrastu kādu elementu rindā, nāksies izņemt pirms vai pēc tā ievietots un vēl neizņemtos elementus. Sliktākajā gadījumā meklējamais elements būs tādā pozīcijā, ka pirms tā sasniegšanas nāksies izņemt visus elementus.
- Elementa ievietošana **O(1)**. Pieliekam elementu vienā no galiem.
- Elementa izņemšana **O(1)**. Izņemam elementu no kāda gala.

###STL bibliotēka deque

deque bibliotēkā ir realizēta divgalu rindas funkcionalitāte. Tās lietošanas piemērs ir apskatāms 1. programmā.

```
#include <iostream>
#include <deque>
using namespace std;

int main ()
{
    // Izveidojam divgalu rindas mainīgo.
    // <> iekavās tiek likts tips (elementārs vai komplekss), kura vērtības tiks glabātas.
    deque<int> d;

    // Ieliekam sākotnējos elementus.
    d.push_back(0);
    d.push_back(3);

    // Ielikt sākumā 9.
    d.push_front(9);
    cout << d.front() << " " << d.back() << endl;

    // Ielikt sākumā 1.
    d.push_front(1);
    cout << d.front() << " " << d.back() << endl;

    // Ielikt beigās 4.
    d.push_back(4);
    cout << d.front() << " " << d.back() << endl;

    // Ielikt beigās 8.
    d.push_back(8);
    cout << d.front() << " " << d.back() << endl;

    // Izņemt no sākuma.
    d.pop_front();
    cout << d.front() << " " << d.back() << endl;

    // Izņemt no beigām.
    d.pop_back();
    cout << d.front() << " " << d.back() << endl;

    return 0;
}
```

<center>**1. programma** - divgalu rindas bibliotēkas lietojums.</center>

Vairāk metodes var apskatīt zemāk esošajā informācijas avotā.

<a href="http://www.cplusplus.com/reference/deque/" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>