#Quicksort

Quicksort ir skaldi un valdi algoritms, kurš katrā iterācijā sadala sakārtojamo masīvu uz pusēm un izpildot quicksort algoritmu uz katru masīva pusi apvieno tos kopā lineārā laikā. Tā kā tas ir skaldi un valdi algoritms, tad dalot intervālu uz 2 šādām dalīšanām jānotiek log(N) reizes. Katra divu pušu apvienošana ir lineārā, tādēļ sarežģītība algoritmam ir O(log(N) * N). Tiesa, efektīvāk ir izmantot sort funkciju. Realizāciju var apskatīt 1. programmā.

```
#include <iostream>
#include <algorithm>
using namespace std;

void quicksort(int *s, int *e)
{
    int len = e - s;
    if (len > 1)
    {
        // Pivot elements ir elements, kurš sadala masīvu divās daļās.
        int pivot = len / 2;

        // Sakārto masīva 1. pusi.
        quicksort(s, s + pivot);

        // Sakārto masīva 2. pusi.
        quicksort(s + pivot, e);

        // Savieno abus masīvus pagaidu masīvā un sakārtotos elementus ieliek orģinālajā masīvā.
        int *tmp = new int[len];
        merge(s, s + pivot, s + pivot, e, tmp);
        copy(tmp, tmp + len, s);
    }
}

int main()
{
    int mas[] = {9, 1, 10, -11, 6, 4, 2};
    quicksort(mas, mas + 7);

    for (int i = 0; i < 7; ++i)
    {
        cout << mas[i] << endl;
    }

    return 0;
}
```

<center>
**1. programma** - Quicksort realizācija.
</center>

<a href="http://en.wikipedia.org/wiki/Quicksort" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>