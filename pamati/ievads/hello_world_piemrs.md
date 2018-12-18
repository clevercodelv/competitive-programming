# Hello world piemērs

Tagad, kad esam apskatījuši, kas ir programmēšanas valoda un uzstādījuši vidi, kurā grasāmies programmēt, tad izveidosim pirmo programmu. Parasti, kad sāk mācīties kādu programmēšanas valodu, tā tiek parādīta ar Hello world piemēru. Arī šajā nodaļā mēs uzrakstīsim Hallo world piemēru C++ valodā un izpētīsim, no kā mūsu nelielā programma sastāv. Nākamās programmas rakstot, šī var noderēt kā paša pamata šablons. Veicam sekojošus soļus.

1. Ieslēdzam Code::Blocks.
1. Ejam File > New > Empty file.
1. Saglabājam failu ar Ctrl+S un nosaucam par "hello.cpp". cpp faila paplašinājums nozīmē, ka fails saturēs C++ programmu, bet patiesībā tas ir vienkāršs teksta fails un to var atvērt ar Notepad lietotni.
1. Varam ievietot 1. programmu vai jebkuru citu programmu šajā failā.
1. Piespiežam F9 un programma tiks kompilēta un palaista. Šajā mirklī vajadzētu parādīties melnam logam ar uzrakstu Hello world. Apsveicu jūs izpildījāt savu pirmo programmu.


Sekojošā programma bez koda satur arī komentārus. Kodā ir iespējams rakstīt komentārus, viss, kas tiek rakstīts komentāros tiek ignorēts. Komentāri praktiski strādā tā, ka nav atšķirība starp kodu ar vai bez komentāriem. C++ ir divu veidu komentāri

- // Komentārs - viss, kam priekšā ir //, tiek ignorēts no // līdz rindas beigām.
- /\* Komentārs \*/ - viss, kas ir iekļauts /\* \*/ tiek ignorēts. Šis komentāra veids var tikt sākts vienā rindā un beigts citā.


```
#include<iostream>; // Bibliotēka, kas ļauj izmantot drukāšanu uz melnā ekrāna jeb cout, endl komandas
using namespace std; // Standarta lieta, kuru vajadzētu vienmēr pielikt, plašāk par to var palasīt citur

int main() // Šeit sākās komandas, kuras izpildīs dators
{
    cout << "Hello world" << endl; // Izvadam uz melnā ekrāna Hello world
    return 0; // Pasakām, ka programma beidzās, programma beigtos arī tad, ja tiktu līdz } iekavai.
}
```

<center>
**1. programma** - Hello world programma.
</center>