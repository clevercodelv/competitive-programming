# Lielie skaitļi

Lielie skaitļi ir tādi paši skaitļi, kā parastie, tikai tie pārsniedz parasto int vai long long intervālu. Piemēram situācijā, kad taisām kalkulatoru, lietotājs var ievadīt 1000 ciparu numuru, bet neviens C++ tips neatbalsta šādu skaitli. Šajā situācijā mēdz ielasīt skaitļus char masīvā un veikt nepieciešamo darbību gluži kā "zem svītras".

### Saskaitīšana

Saskaitīšana notiek zem svītras. Algoritms ir sekojošs:

1. Ielasa skaitļus masīvos A[] un B[].
2. Ja B lielāks par A, tad apmaina A un B norādes otrādi.
3. Apskata garāko masīvu no beigām ciklā un veic 4. - 5. soli.
4. Katrā iterācijā saskaita A masīva ciparu ar pārnesi.
5. Ja B cipari nav izbeigušies (jo tas ir īsāks), pieskaita B ciparu.
6. Kad viss ir saskaitīts, ja ir pārnese (rezultātā iegūts garāks cipars par abiem), tad pievieno galā pēdējo ciparu.
7. Apgriež masīvu otrādi.

Jāpiemin, ka rezultātu vajag veidot no otras puses masīvā un tad apgriezt otrādi. Rezultātu var izvadīt pēc vajadzības. Piemēru skatīt 1. programmā.

### Atņemšana

Atņemšanas piemēru var skatīt 1. programmā. Atņemšanas algoritms ir šāds:

1. Ielasām skaitļus masīvos A[] un B[].
2. Ja B lielāks par A, tad apmaina A un B norādes otrādi.
3. Apskata garāko masīvu no beigām ciklā un izpilda 4. - 6. soļus.
4. Rezultāta ciparama pieskaita A ciparu.
5. Ja nav beigušies B cipari, atņem no rezultāta cipara.
6. Ja rezultāta cipars ir mazāks par 0, aizņemas no nākamā A cipara 1 un pieskaita 10.
7. Ignorējot 0 pieliek beigās -, ja cipari tika apmainīti vietām, un 0 simbolu beigās.
8. Apgriež masīvu otrādi.

### Reizināšana

Reizināšanas piemēru var skatīt 1. programmā. Algoritms ir šāds:

1. Ielasa skaitļus maīvā A[] un mainīgajā B.
2. Apskata katru B ciparu.
3. Piereizina ciparu masīvam A[] pieliekot cipara pozīcija skaitu 0 rezultātam galā.
4. Iegūto rezultātu 3. solī pieskaita rezultātam.

### Dalīšana ar parasto skaitli

Dalīšanas piemēru var skatīt 1. programmā. Algoritms ir šāds.

1. Ielasa masīvu A[] un mainīgo B.
2. Iet cipariem no vis nozīmīgākā uz maznozīmīgāko.
3. Pieskaita skaitītājam ciparu.
4. Pievieno rezultātam dalījumu skaitītājs / B.
5. Atlikumu sareizina ar 10.

### Modelis pēc parastā skaitļa

Modeļa piemēru var skatīt 1. programmā. Algoritms ir šāds.

1. Ielasa masīvu A[] un mainīgo B.
2. Iet cipariem no vis nozīmīgākā uz maznozīmīgāko.
3. Pieskaita skaitītājam ciparu.
4. Veido modeli pēc B.
5. Atlikumu sareizina ar 10.
6. Rezultātā iegūtais skaitlis ir < B, tādēļ varat atgriezt, kā int vai long long int.

```
#include <iostream>
#include <string.h>
#include <algorithm>
#include <cstdio>
using namespace std;

bool is_greater_than(char *a, char *b)
{
    int lenA = strlen(a);
    int lenB = strlen(b);

    if (lenA != lenB)
        return lenA > lenB;

    for (int i = 0; i < lenA; ++i)
        if (a[i] != b[i]) return a[i] > b[i];

    return false;
}

/*
 * Saskaitīšana.
 */
void add(char *a, char *b, char res[])
{
    // Ja B lielāks par A, tad apmaina A un B norādes otrādi.
    if (is_greater_than(b, a)) swap(a, b);

    int lenA = strlen(a);
    int lenB = strlen(b);

    // Apskata garāko masīvu no beigām ciklā.
    int rem = 0;
    for (int i = 1; i <= lenA; ++i)
    {
        // Katrā iterācijā saskaita A masīva ciparu ar pārnesi.
        res[i - 1] = a[lenA - i] - '0' + rem;
        // Ja B cipari nav izbeigušies (jo tas ir īsāks), pieskaita B ciparu.
        if (i <= lenB) res[i - 1] += b[lenB - i] - '0';
        rem = res[i - 1] / 10;
        res[i - 1] = res[i - 1] % 10 + '0';
    }

    // Kad viss ir saskaitīts, ja ir pārnese (rezultātā iegūts garāks cipars par abiem), tad pievieno galā pēdējo ciparu.
    if (rem)
    {
        res[lenA] = rem + '0';
        res[lenA + 1] = '\0';
    } else {
        res[lenA] = '\0';
    }

    // Apgriež masīvu otrādi.
    reverse(res, res + strlen(res));
}

void sub(char *a, char *b, char res[])
{
    bool flag = false;

    // Ja B lielāks par A, tad apmaina A un B norādes otrādi.
    if (is_greater_than(b, a))
    {
        swap(a, b);
        flag = true;
    }

    int lenA = strlen(a);
    int lenB = strlen(b);

    // Apskata garāko masīvu no beigām ciklā un izpilda 4. - 6. soļus.
    for (int i = 1; i <= lenA; ++i)
    {
        // Rezultāta ciparama pieskaita A ciparu.
        res[i - 1] = a[lenA - i] - '0';
        // Ja nav beigušies B cipari, atņem no rezultāta cipara.
        if (i <= lenB) res[i - 1] -= b[lenB - i] - '0';
        // Ja rezultāta cipars ir mazāks par 0, aizņemas no nākamā A cipara 1 un pieskaita 10.
        if (res[i - 1] < 0) {
            res[i - 1] += 10;
            a[lenA - i - 1]--;
        }
        res[i - 1] += '0';
    }

    // Ignorējot 0 pieliek beigās -, ja cipari tika apmainīti vietām, un 0 simbolu beigās.
    int len = lenA;
    while (res[len - 1] == '0' && len > 1) --len;
    if (flag) res[len++] = '-';
    res[len] = '\0';

    // Apgriež masīvu otrādi.
    reverse(res, res + len);
}

void multiply_digit(char *a, int b, char *res, int delta)
{
    for (int i = 0; i < delta; ++i)
        res[i] = '0';

    int lenA = strlen(a);
    int rem = 0;
    for (int i = 0; i < lenA; ++i)
    {
        res[delta + i] = (a[lenA - i - 1] - '0') * b + rem;
        rem = res[delta + i] / 10;
        res[delta + i] = res[delta + i] % 10  + '0';
    }

    if (rem) {
        res[delta + lenA] = rem + '0';
        res[delta + lenA + 1] = '\0';
    } else {
        int len = delta + lenA;
        while (res[len - 1] == '0' && len > 1) --len;
        res[len] = '\0';
    }

    reverse(res, res + strlen(res));
}

void multiply(char a[], int b, char res[])
{
    res[0] = '0';
    res[1] = '\0';
    char *tmpRes = new char[strlen(a) + 3];
    char *tmpRes2 = new char[strlen(a) + 3];

    // Apskata katru B ciparu.
    for (int i = 0; b; ++i)
    {
        // Piereizina ciparu masīvam A[] pieliekot cipara pozīcija skaitu 0 rezultātam galā.
        int digit = b % 10;
        b /= 10;
        multiply_digit(a, digit, tmpRes, i);

        // Iegūto rezultātu 3. solī pieskaita rezultātam.
        add(res, tmpRes, tmpRes2);
        strcpy(res, tmpRes2);
    }
}

void divide(char a[], int b, char res[])
{
    int lenA = strlen(a);
    int tmp = 0;
    int len = 0;
    bool beginFlag = true;

    // Iet cipariem no vis nozīmīgākā uz maznozīmīgāko.
    for (int i = 0; i < lenA; ++i)
    {
        // Pieskaita skaitītājam ciparu.
        tmp += a[i] - '0';
        if (tmp >= b) beginFlag = false;
        // Pievieno rezultātam dalījumu skaitītājs / B.
        if (!(beginFlag && tmp < b)) res[len++] = tmp / b + '0';

        // Atlikumu sareizina ar 10.
        tmp = (tmp % b) * 10;
    }

    if (len == 0) res[len++] = '0';

    res[len] = '\0';
}

int mod(char a[], int b)
{
    int lenA = strlen(a);
    int res = 0;

    // Iet cipariem no vis nozīmīgākā uz maznozīmīgāko.
    for (int i = 0; i < lenA; ++i)
    {
        // Pieskaita skaitītājam ciparu.
        res += a[i] - '0';
        // Veido modeli pēc B.
        res %= b;
        // Atlikumu sareizina ar 10.
        res *= 10;
    }

    // Rezultātā iegūtais skaitlis ir < B, tādēļ varat atgriezt, kā int vai long long int.
    return res % b;
}

int main()
{
    char a[101], b[101], res[200];
    int sk;

    cin >> a >> b; //Ielasa skaitļus masīvos A[] un B[].
    add(a, b, res);
    cout << res << endl;

    cin >> a >> b; //Ielasa skaitļus masīvos A[] un B[].
    sub(a, b, res);
    cout << res << endl;

    cin >> a >> sk; // Ielasa masīvu A[] un mainīgo B.
    multiply(a, sk, res);
    cout << res << endl;

    cin >> a >> sk; // Ielasa masīvu A[] un mainīgo B.
    divide(a, sk, res);
    cout << res << endl;

    cin >> a >> sk; // Ielasa masīvu A[] un mainīgo B.
    cout << mod(a, sk) << endl;

    return 0;
}

```

**1. programma** - lielo skaitļu aritmētika.

<a href="http://en.wikipedia.org/wiki/Arbitrary-precision_arithmetic" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>