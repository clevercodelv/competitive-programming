# Cikls do while

Šis cikls darbojas ļoti līdzīgi, kā while cikls, tikai nosacījuma pārbaude notiek nevis pirms koda izpildes, bet pēc. Tas nozīmē, ka kods \{\} iekavās vienmēr izpildīsies vismaz vienu reizi. Dažās situācijās šāda uzvedība ir ļoti nepieciešama, piemēram, uztaisīsim nelielu programmu, kas klausās mūsu komandas un atkarībā no tām mums pasaka kaut ko, algoritms ir šāds:

1. Ielasām komandu.
1. Ja komanda ir "smiletome", tad izvadām ":)".
1. Citādi, ja komanda ir "blinktome", tad izvadām ";)".
1. Citādi, ja komanda ir "exit", tad atzīmējam, ka gribam iziet no cikla.
1. Citādi izvadām "Komanda nav atpazita!".
1. Ja nav atzīmēts, ka gribam iziet no cikla, tad ejam uz 1. rindu.
1. Beidzam darbu.


Algoritma realizācija ir redzama 1. programmā.

```
#include <iostream>
#include <string>
using namespace std;

int main()
{
    string komanda;
    bool iziet_no_cikla = false;

    do {
        cin >> komanda; // Ielasām komandu.
        if (komanda == "smiletome")
        {
            cout << ":)" << endl; // Ja komanda ir "smiletome", tad izvadām ":)".
        } else {
            if (komanda == "blinktome")
            {
                cout << ";)" << endl; // Citādi, ja komanda ir "blinktome", tad izvadām ";)".
            } else {
                if (komanda == "exit")
                {
                    iziet_no_cikla = true; // Citādi, ja komanda ir "exit", tad atzīmējam, ka gribam iziet no cikla.
                } else {
                    cout << "Komanda nav atpazita!" << endl;
                }
            }
        }
    } while (!iziet_no_cikla); // Ja nav atzīmēts, ka gribam iziet no cikla, tad ejam uz 1. rindu.

    return 0; // Beidzam darbu.
}
```

<center>
**1. programma** - komandas lasoša algoritma realizācija.
</center>

<a href="http://www.cplusplus.com/doc/tutorial/control/" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>