#Aritmētiskie operatori un to izpildes secība

Operatori ir paredzēti, lai veiktu dažādas darbības ar literāļiem un mainīgajiem.

**Piešķiršanas operators** - paredzēts, lai mainīgajam piešķirtu vērtību. Piemēru skatīt 1. programmā.

```
#include <iostream>
using namespace std;

int main()
{
    int a, b; // Deklarējam a un b. Atdalot ar komatu, varam deklarēt vairākus viena tipa mainīgos.

    a = 5; // Piešķiram a literāli 5.
    b = 4; // Piešķiram b literāli 4.
    b = a + 1; // Piešķiram b izteiksmi a + 1 jeb 6.

    //Piešķiram a + (b = b - a) jeb 5 + (b = 6 - 5). Tā pat, kā a + b patiesībā 
    //kļūst par šīs izteiksmes vērtību, tāpat katru vienādību var aizstāt ar kreisajā 
    //pusē esošā mainīgā vērtību pēc piešķiršanas. Tādēļ sanāk, 
    //ka a = 5 + (b = 11) jeb a = 5 + 11, jeb a = 16, kā arī šajā izteiksmē b kļuva par 11.
    a = a + (b = b - a);

    return 0;
}
```

<center>**1. programma** - piešķiršanas operators.</center>

**Aritmētiskie operatori** - skatīt 1. tabulu.

Operators | Piemērs | Paskaidrojum
---|---|---
+ | 4 + a | Saskaitīšana.
- | 4 - a | Atņemšana.
* | 4 * a | Reizināšana.
/ | 4 / a | Dalīšana.
% | 4 % a | Modulis. Modulis ir atlikums, ja kreisās puses operandu dalītu ar labās puses operandu. Operandi ir operatoru argumenti.

<center>**1. tabula** - aritmētiskie operatori.</center>

**Kombinētie operatori** - grupētie operatori veic divas darbības vienlaikus - aritmētisko darbību un piešķiršanu. Kombinētos operatorus var skatīt 2. tabulā.

Operators | Parastais variants | Paskaidrojum
---|---|---
a += 4 | a = a + 4 | Saskaitīšana un piešķiršana.
a -= 4 | a = a - 4 | Atņemšana un piešķiršana.
a *= 4 | a = a * 4 | Reizināšana un piešķiršana.
a /= 4 | a = a / 4 | Dalīšana un piešķiršana.
a %= 4 | a = a % 4 | Modulis un piešķiršana.

<center>**2. tabula** - kombinētie operatori.</center>

**Skaitļu palielināšana un samazināšana** - veselus skaitļus ir iespējams palielināt un samazināt par 1 ar speciāliem operatoriem. Šos operatorus var skatīt 3. tabulā.

Operators | Parastais variants | Paskaidrojum
---|---|---
a++ vai ++a | a = a + 1 | Palielināšana par 1.
a-- vai --a | a = a - 1 | Samazināšana par 1.

<center>**2. tabula** - kombinētie operatori.</center>

Ir svarīgi, kurā pusē tiek likts šis operators. Jo:

- Ja x = 3, tad veicot y = ++x darbību, y = 4 un x = 4.
- Ja x = 3, tad veicot y = x++ darbību, y = 3 un x = 4.

###Operatoru secība

Ir svarīgi, kādā secībā tiek izpildīti operatori, jo tie veic darbības ar datiem. Neapzinoties pareizu to izpildes secību, var panākt nevēlamu rezultātu. Ir viens variants, kā pašam kontrolēt operatoru izpildes secību - ar iekavām. Piemēram, mēs zinām, ka izpildot programmas rindiņu a = 5 + 3 * 4, mēs iegūsim rezultātā 17, bet pieliekot iekavas a = (5 + 3) * 4, + operators tiks izpildīts pirms * operatora un rezultātā a būs 32. Situācijās, kad ir grūti izdomāt, kurš operators izpildīsies pirms kura, ir ieteicams likt iekavas. Bet pašu operatoru prioritātes var apskatīt 3. tabulā.

Līmenis | Operators | Apraksts | Grupēšana
---|---|---|---
1 | :: | Tvērums. | No kreisās uz labo
2 | ++ -- [] () . -> | Unārie postfiksie operatori. | No kreisās uz labo
3 | ++ -- ~ ! + - & * new delete izeof (type) | Unārie prefiksie operatori. | No labās uz kreiso
4 | .* ->* | Norāde uz vienību. | No kreisās uz labo
5 | * / % | Aritmētika: mērogošana. | No kreisās uz labo
6 | + - | Aritmētika: pieskaitīšana. | No kreisās uz labo
7 | << >> | Bitu pārbīde. | No kreisās uz labo
8 | < > <= >= | Attiecība. | No kreisās uz labo
9 | == != | Vienādība. | No kreisās uz labo
10 | & | Bitu un. | No kreisās uz labo
11 | ^ | Bitu xor. | No kreisās uz labo
12 | \| | Bitu or. | No kreisās uz labo
13 | && | Loģiskais un. | No kreisās uz labo
14 | \|\| | Loģiskais vai. | No kreisās uz labo
15 | = *= /= %= += -= <<= >>= &= ^= \|= ?: | Piešķiršanas līmeņa izteiksmes. | No labās uz kreiso
16 | , | Virknēšana. | No kreisās uz labo

<center>**3. tabula** - operatoru izpildes secība.</center>

Ja vairākiem operatoriem ir vienāda prioritāte, tad tie tiek izpildīti atkarībā no grupēšanas veida secīgi - no kreisās uz labo vai no labās uz kreiso pusi.

<a href="http://www.cplusplus.com/doc/tutorial/operators/" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>