#Rinda un queue&lt;T&gt;

Rinda ir lineāra datu struktūra, kurā elementi tiek ielikti no viena gala un ņemti ārā no otra gala. Vēl uz šo struktūru var paskatīties tā, ka tas elements, kurš ātrāk tiks ielikts, ātrāk tiks izņemts, angliski to sauc FIFO jeb First in first out. Vizuālu rindas piemēru var apskatīt 1. attēlā.

![Rinda](/media/theory/queue.png)

<center>**1. attēls** - rindas darbības.</center>

Rindas darbību sarežģītība ir:

- Elementa meklēšana **O(N)**. Lai atrastu kādu elementu rindā, nāksies izņemt pirms tā ievietots un vēl neizņemtos elementus. Sliktākajā gadījumā meklējamais elements būs rindas beigās jeb pēdējais ievietotais.
- Elementa ievietošana **O(1)**. Pieliekam elementu tajā rindas galā, kurā tiek likti elementi.
- Elementa izņemšana **O(1)**. Izņemam elementu no tā rindas gala, no kura tiek izņemti elementi.

###STL bibliotēka queue

queue bibliotēkā ir realizēta rindas funkcionalitāte. Tās lietošanas piemērs ir apskatāms 1. programmā.

```
#include <iostream>
#include <queue>
using namespace std;

int main ()
{
    // Izveidojam rindas mainīgo.
    // <> iekavās tiek likts tips (elementārs vai komplekss), kura vērtības tiks glabātas.
    queue<int> q;

    // Ieliekam sākotnējos elementus.
    q.push(2);
    q.push(4);
    q.push(2);
    q.push(1);
    q.push(9);
    q.push(0);
    q.push(3);

    // Izņemt.
    q.pop();
    cout << q.front() << endl;

    // Izņemt.
    q.pop();
    cout << q.front() << endl;

    // Ielikt 4.
    q.push(4);
    cout << q.front() << endl;

    // Ielikt 8.
    q.push(8);
    cout << q.front() << endl;

    // Izņemt.
    q.pop();
    cout << q.front() << endl;

    // Izņemt.
    q.pop();
    cout << q.front() << endl;

    return 0;
}
```

<center>**1. programma** - rindas bibliotēkas lietojums.</center>

Vairāk metodes var apskatīt zemāk esošajā informācijas avotā.

<a href="http://www.cplusplus.com/reference/queue/queue/" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>

##Uzdevumi

* Kartupelis (kartupelis)
* Pēterītis un datu struktūras (rinda2)
