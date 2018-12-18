# Simbolu virknes apakšvirknes meklēšana

Simbolu virknes meklēšana nozīmē atrast pirmo pozīciju lielākā virknē, kurā atrodas meklējamā simbolu virkne. Piemēram, ja ir dota simbolu virkne "abra ka dabra" un tiek meklēts "a da", tad rezultātā vajadzēti iegūt 6. Šo risinājumu var izmantot arī jebkura veida masīvam.

Lai gan eksistē optimāli algoritmi, kas ir lineāri, tie ir pietiekami sarežģīti, lai tos apskatītu advancēto algoritmu nodaļā. Šeit tiks apskatīta kvadrātiskā rupjā spēka metode un lineārā algorithm bibliotēkas funkcija. Piemērus var apskatīt 1. programmā.

```
#include <iostream>
#include <algorithm>
#include <string.h>
using namespace std;

int meklet(char mas[], char pattern[])
{
    int len1 = strlen(mas);
    int len2 = strlen(pattern);

    for (int i = 0; i < len1 - len2; ++i)
    {
        bool is_ok = true;
        for (int j = 0; j < len2 && is_ok; ++j)
            if (mas[i + j] != pattern[j])
                is_ok = false;

        if (is_ok) return i;
    }

    return -1;
}

int main()
{
    char mas[] = "abra ka dabra";
    char pattern[] = "a da";

    // Paša veidota programma.
    cout << meklet(mas, pattern) << endl;

    // Algorithm bibliotēka.
    cout << search(mas, mas + strlen(mas), pattern, pattern + strlen(pattern)) - mas << endl;

    return 0;
}
```

<center>
**1. programma** - simbolu virknes meklēšana.
</center>

<a href="http://www.cplusplus.com/reference/algorithm/" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>