#Masīva manipulācijas

C++ programmēšanā pašā pamatā patiesībā eksistē tikai viendimensiju masīvi, jo jebkurš divdimensiju masīvs ir viendimensiju masīvs, kur katrs elements ir masīvs. **Tāpat katrs n dimensiju masīvs ir patiesībā n - 1 dimensiju masīvs, kur katrs n - 1 dimensiju masīva elements ir masīvs.** Šis tika apskatīts nodaļā par masīviem, vienīgi šeit tiek dota vispārīga definīcija.

Pamatā šajā nodaļā tiks apskatīti 1 dimensiju masīvi, klasiskas darbības, kuras ar tiem varētu izdarīt un varbūt bibliotēkas, ar kurām to var izdarīt veiklāk. Pamatā tiks apskatīti int tipa masīvi. Šīs darbības eksistē algorithm bibliotēkā, lai labi apgūtu šo manipulāciju ātrāku pierakstu, ir ieteicams izlasīt nodaļai pievienoto informācijas saiti.

###Minimālā / maksimālā masīva vērtība

Ideja ir vienkārša, izejam cauri visam masīvam un pieglabājam lielāko vai mazāko vērtību. Piemēram skatīt 1. programmu. Bibliotēkā algorithm ir ekvivalentas divas funkcijas max_element un min_element.

```
#include <iostream>
#include <algorithm>
using namespace std;

int main()
{
    int mas[] = {1, -5, 9, 0, 4};

    // Min cikls.
    int maz = 2000000000;
    for (int i = 0; i < 5; ++i)
        if (mas[i] < maz) maz = mas[i];
    cout << maz << endl;

    // Max cikls.
    int liel = -2000000000;
    for (int i = 0; i < 5; ++i)
        if (mas[i] > liel) liel = mas[i];
    cout << liel << endl;

    //Min funkcija.
    cout << *min_element(mas, mas + 5) << endl;

    //Max funkcija.
    cout << *max_element(mas, mas + 5) << endl;

    return 0;
}
```

<center>**1. programma** - mazākā / lielākā elementa algoritms.</center>

###Sakārtotu masīvu apvienošana

Mērķis ir divus sakārtotus masīvus salikt vienā tā, lai tie būtu sakārtoti. Ideja ir tāda, ka jaunajā masīvā, kura izmērs ir abu masīvu izmēru summa, saliek visus elementus no abiem masīviem, visu laiku liekot mazākos pirmos.

```
#include <iostream>
#include <algorithm>
using namespace std;

int main()
{
    int len1 = 5;
    int len2 = 6;
    int mas1[] = {-1, 0, -3, 2, 4};
    int mas2[] = {-4, 5, 0, -1, 2, 3};
    int *mas = new int[len1 + len2];
    sort(mas1, mas1 + len1);
    sort(mas2, mas2 + len2);

    // Paša rakstīts kods
    for (int i = 0, pos1 = 0, pos2 = 0; i < len1 + len2; ++i)
    {
        if (pos1 == len1) mas[i] = mas2[pos2++];
        else
            if (pos2 == len2) mas[i] = mas1[pos1++];
            else
                if (mas1[pos1] < mas2[pos2]) mas[i] = mas1[pos1++];
                else
                    mas[i] = mas2[pos2++];
    }

    // Izvadām rezultātu.
    for (int i = 0; i < len1 + len2; ++i)
        cout << mas[i] << " ";
    cout << endl;

    delete[] mas;
    mas = new int[len1 + len2];

    // Bibliotēkas funkcija
    merge(mas1, mas1 + len1, mas2, mas2 + len2, mas);

    // Izvadām rezultātu.
    for (int i = 0; i < len1 + len2; ++i)
        cout << mas[i] << " ";
    cout << endl;

    return 0;
}
```

<center>**2. programma** - masīva apvienošana.</center>

###Masīva elementu nodalīšana

Masīva elementu nodalīšana ir algoritms, kā pēc kādas īpašības var sadalīt elementus divās daļās. Piemēram, ja ir dots masīvs ar dažādie pāra un nepāra skaitļiem, tad, kā izdarīt tā, lai visi pāra skaitļi atrastos masīva priekšā un nepāra skaitļi atrastos masīva aizmugurē. Piemēru var apskatīt 3. programmā.

```
#include <iostream>
#include <algorithm>
#include <queue>
using namespace std;

bool is_pair(const int sk)
{
    // Boolean tips arī ir skaitlis, viss, kas ir 0, ir false un pārējais ir true.
    return !(abs(sk) % 2);
}

void print(int *mas, int len)
{
    for (int i = 0; i < len; ++i)
        cout << mas[i] << " ";
    cout << endl;
}

int main()
{
    int len = 11;
    int mas1[] = {-1, 0, -3, 2, 4, -4, 5, 0, -1, 2, 3};
    int mas2[] = {-1, 0, -3, 2, 4, -4, 5, 0, -1, 2, 3};

    // Paša rakstīts algoritms.
    queue<int> q;
    for (int i = 0; i < len; ++i)
        if (is_pair(mas1[i]))
        {
            if (!q.empty())
            {
                swap(mas1[i], mas1[q.front()]);
                q.pop();
                q.push(i);
            }
        } else {
            q.push(i);
        }

    print(mas1, len);

    // Iebūvētā funkcija.
    partition(mas2, mas2 + len, is_pair);
    print(mas2, len);

    return 0;
}
```

<center>**3. programma** - Masīva elementu nodalīšana.</center>

###Citas komandas

Ar šiem piemēriem vajadzētu tapt skaidrai vienai lietai, ka vērtīgi ir mācēt manipulēt ar masīviem, jeb uzrakstīt efektīvu programmu, kas veic kādu darbību vai pārbaudi, vai transformāciju. Bet vēl vērtīgāk ir apzināt ātras vienas rindas komandas, kas var aizvietot garu programmēšanu un atkļūdošanu sacensību laikā un ikdienā. Tiesa, svarīgi ir saprast šo funkciju ātrdarbību, kas patiesībā dotajā informācijas resursā ir pieejama katras funkcijas aprakstā. Šajos piemēros apskatītā sarežģītība līdzīgi, kā vairumā algorithm bibliotēkas masīvu funkciju, ir lineāra.

```
#include <iostream>
#include <algorithm>
#include <string.h>
using namespace std;

void print(const int mas[], int garums)
{
    for (int i = 0; i < garums; ++i)
        cout << mas[i] << " ";
    cout << endl;
}

int square(int sk)
{
    return sk * sk;
}

int main()
{
    // Atrod masīva apakšvirkni. O(N)
    char seq[] = "Big brown fox ate my cake";
    char srch[] = "fox";
    cout << srch << " atrodas pozicija ";
    cout << search(seq, seq + strlen(seq), srch, srch + strlen(srch)) - seq << endl;

    // Atrod elementa pozīciju masīvā. O(N)
    cout << "a atrodas pozicija ";
    cout << find(seq, seq + strlen(seq), 'a') - seq << endl;

    // Saskaita elementa parādīšanās reižu skaitu. O(N)
    cout << "a paradas " << count(seq, seq + strlen(seq), 'a') << " reizes" << endl;

    // Pārbauda, vai divi simbolu masīvi ir vienādi. O(N)
    cout << "virknes ir " << (equal(seq, seq + strlen(seq), srch) ? "vienadas" : "atskirigas") << endl;

    // Kopē no masīva uz masīvu. O(N)
    int sk1[] = {1, 2, 3, 4};
    int sk2[3];
    copy(sk1 + 1, sk1 + 4, sk2);
    print(sk2, 3);

    // Apmaina masīva vērtības ar citām masīva vērtībām. O(N)
    swap_ranges(sk1, sk1 + 3, sk2);
    print(sk2, 3);

    // Pārveido visu masīvu un iekopē resultāta masīvā. O(N)
    transform(sk1, sk1 + 3, sk2, square);
    print(sk2, 3);

    // Iazvieto masīvā vērtību ar citu vērtību. O(N)
    replace(sk1, sk1 + 4, 4, 9);
    print(sk1, 4);

    // Aizvieto masīvu ar vērtību. O(N)
    fill(sk2, sk2 + 3, 0);
    print(sk2, 3);

    // Apgriež masīvu otrādi. O(N)
    reverse(sk1, sk1 + 4);
    print(sk1, 4);

    // Rotē masīvu, lai 3 arguments atrastos 1. pozīcijā. O(N)
    rotate(sk1, sk1 + 2, sk1 + 4);
    print(sk1, 4);

    return 0;
}
```

<center>**4. programma** - algorithm funkciju piemēri.</center>

<a href="http://www.cplusplus.com/reference/algorithm/" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>