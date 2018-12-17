# Rekursija

Programmēšanas valodās ir viegli izsaukt funkciju. Kas notiktu, ja funkcija izsauktu pati sevi? To sauc par rekursiju. Ja uztaisa programmu tā, lai funkcija apstājās, kad kaut kāds rezultāts ir iegūts, tad var izveidot programmu, kas nepārpildīs steku un vienlaikus atrisinās kādu problēmu.

Matemātikā arī eksistē rekursijas jēdziens. Piemēram, ja grib apskatīt Fibonači skaitļu problēmu, tad matemātikā risinājumu tai var pierakstīt rekursīvā formā. Piemēram, ir dota funkcija F(i), kur F(i) = F(i - 1) + F(i - 2) jeb iepriekšējo divu Fibonači skaitļu summu. Tiesa, lai funkcija neizpildītos bezgalīgi, ir nepieciešams kāds nosacījums, kurš apstādinātu rekursiju, piemēram, ka F(0) == F(1) == 1, kurš ir zināms no Fibonači skaitļu virknes definīcijas, ka virkne sākās ar 1 un 1. Rekursīvas funkcijas pierakstu matemātikā var skatīt 1. attēlā un realizāciju var skatīties 1. programmā.

<center><img alt="Fibonači rekursīva funkcija" src="/media/theory/rec_fib.gif" /></center>

<center>**1. attēls** - Fibonači rekursīvā funkcija matemātikā.</center>

```
#include <iostream>
using namespace std;

int F(int i)
{
    if (i == 0 || i == 1) // Speciālais gadījums, lai funkcija neizpildītos bezgalīgi.
        return 1;
    else
        return F(i - 1) + F(i - 2); // Funkcija izsauc pati sevi.
}

int main()
{
    cout << F(13) << endl; // Atgriež 13 Fibonači skaitli.

    return 0;
}
```

<center>**1. programma** - Fibonači rekursīvā funkcija C++ programmā.</center>

<a href="http://en.wikipedia.org/wiki/Recursion_(computer_science)" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>