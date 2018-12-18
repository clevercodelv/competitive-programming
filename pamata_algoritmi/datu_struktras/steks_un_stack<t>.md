# Steks un stack&lt;T&gt;

Steks ir lineāra datu struktūra, kurā katru vērtību var ielikt tikai vienā no galiem un no tā paša gala var tikai izņemt. Tas nozīmē, ka, ja kādai vērtībai A ir uzlikta vērtība B, lai izņemtu vērtību A, ir jāizņem vērtība B. Steku var iztēloties kā ķieģeļu kaudzi, ķieģeļus var likt tikai augšpusē, un, ja gribam tikt klāt kādam ķieģelim, no sākuma ir jānoņem virsējie ķieģeļi. Šo principu labi attēlo 1. attēls.

![Steks](/media/theory/stack.png)

<center>
**1. attēls** - steka darbības.
</center>

Struktūras darbību sarežģītība ir:

- Elementa meklēšana ir **O(N)**, jo, lai atrastu elementu, ir jāizņem visi priekšā esošie elementi.
- Elementa pievienošana **O(N)**. Pieliekam pašā augšā.
- Elementa izņemšana **O(N)**. Izņemam no augšas.

### STL bibliotēka stack

stack bibliotēkā ir realizēta steka funkcionalitāte. Tās lietošanas piemērs ir apskatāms 1. programmā.

```
#include <iostream>
#include <stack>
using namespace std;

int main ()
{
    // Izveidojam steka mainīgo.
    // <> iekavās tiek likts tips (elementārs vai komplekss), kura vērtības tiks glabātas.
    stack<int> s;

    // Ieliekam sākotnējos elementus.
    s.push(7);
    s.push(6);
    s.push(1);
    s.push(0);
    s.push(9);
    s.push(8);
    s.push(5);
    s.push(2);

    // Izņemt.
    s.pop();
    cout << s.top() << endl;

    // Izņemt.
    s.pop();
    cout << s.top() << endl;

    // Izņemt.
    s.pop();
    cout << s.top() << endl;

    // Ielikt 7.
    s.push(7);
    cout << s.top() << endl;

    // Ielikt 2.
    s.push(2);
    cout << s.top() << endl;

    // Ielikt 3.
    s.push(3);
    cout << s.top() << endl;

    return 0;
}
```

<center>
**1. programma** - steka bibliotēkas lietojums.
</center>

Vairāk metodes var apskatīt zemāk esošajā informācijas avotā.

<a href="http://www.cplusplus.com/reference/stack/stack/" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>

## Uzdevumi

* Balansēta iekavu izteiksme (iekavas6)
* Monētu steks (steks)
