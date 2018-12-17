# Simbolu masīvi, ASCII kodējums

Par simbolu virknēm runājām, ka tie ir string tipa mainīgie, kas var saturēt tekstu un kur teksta simboliem var piekļūt ar [] operatoru. Tika minēts, ka string ir klase jeb kompleksais tips, bet jebkurš kompleksais tips pamatos balstās uz elementāro tipu vai šī tipa masīvu, vai struktūru. Simbola virkņu gadījumā var iztēloties, ka tas balstās uz simbola masīvu. Simbolu masīvs ir īpašs ar to, ka tam eksistē daudzas funkcijas tā apstrādei un to var, piemēram, izvadīt vai ielasīt no ekrāna / faila vienā komandā. Bet no kā tad simbolu masīvs sastāv? No simboliem jeb char tipa vērtībām. Piemēram var apskatīt 1. programmu.

```
#include <iostream>
using namespace std;

int main ()
{

    char mas[20]; // Deklarējam simbolu masīvu.

    cin >> mas; // Ielasām simbolu masīvu. Parastie masīvi šādi nestrādā.
    cout << "Ievadiji virkni: " << mas << endl; // Izvadām simbolu masīvu. Parastie masīvi šādi nestrādā.

    for (int i = 0; mas[i] != '\0'; ++i) // Ielasot simbolu masīvu, C++ pieliek beigās nulles simbolu '\0'.
        if (mas[i] >= '0' && mas[i] <= '9') // Šādi var pārbaudīt, vai simbols ir cipars.
            cout << "Ievadiji ciparu: " << mas[i] << endl; // Izvadām simbolu.

    return 0;
}
```

<center>**1. programma** - simbolu masīva piemērs.</center>

Apskatot 1. programmu, var redzēt pāris svarīgas lietas:

1. Simbolu masīvus atšķirībā no parastajiem masīviem var ielasīt ar 1 komandu un izvadīt ar 1 komandu.
1. Simbolos cipari ar salīdzināšanu salīdzinās tāpat, kā salīdzinot skaitļa tipa mainīgos, kas satur ciparus, tāpēc var pārbaudīt, vai simbols atrodas '0' - '9' intervālā.
1. Simbolu masīvam, to ielasot, beigās tiek pielikts '\0' simbols.


Jāpiemin, ka cin, ielasa simbolu masīvu, to nolasa tikai līdz pirmajai atstarpei vai, ja atstarpe nav, tad līdz rindas beigām.

<a href="http://www.cplusplus.com/doc/tutorial/ntcs/" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>

### ASCII simbolu tabula

Iepriekš redzējām, ka simbolus varēja salīdzināt ar < operatoru. To var izdarīt arī ar jebkuru citu operatoru, ar kuru var salīdzināt skaitļus. Kāpēc tā? Jo simboli patiesībā ir skaitļi. Katram simbolam ir savs skaitlis, kurš to reprezentē. Tipu nodaļā bija rakstīt, ka char tips ir 1 baitu. Patiesībā mainīgais ar char tipu ir skaitlis intervālā no -128 līdz 127. C++ zinot, ka tas ir char tips, izvada uz ekrāna to kā simbolu, bet, ja piešķirtu char tipa mainīgo int tipa mainīgajam un izvadītu, tad iegūtu simbola skaitlisko vērtību. Piemēram skatīt 2. programmu.

```
#include <iostream>
using namespace std;

int main ()
{

    // Jebkurš simbols ir patiesībā skaitlis. C++ veic konvertēšanu abos virzienos programmas vietā.
    char a = 'i';
    int nr = a;

    cout << a << endl; // Izvadīs 'i'.
    cout << nr << endl; // Izvadīs 105.
    cout << (int)a << endl; // Izvadīs 105.
    cout << (int)'i' << endl; // Izvadīs 105.

    return 0;
}

```

<center>**2. programma** - simbolu skaitliskās vērtības piemērs.</center>

ASCII tabula ir veids, kā šīm skaitliskajām vērtībām no -128 līdz 127 piemērot simbolu. 1. attēlā tiek parādīta ASCII tabula intervālā no 0 līdz 127.

![ASCII tabula](/media/theory/ascii.gif)

<center>**1. attēls** - ASCII tabula.</center>

### Leksikogrāfiskā salīdzināšana

Leksikogrāfiskā salīdzināšana ir divu tekstu, pieņemsim A un B, salīdzināšana. A ir lielāks par B, ja:

- Pirmais simbols, kurš A nav vienāds ar B ir lielāks par B. Piemēram, ja A un B satur tikai alfabēta burtus, tad burti tiktu salīdzināti tikai pēc to pozīcijas alfabētā.
- Ja B visi simboli ir vienādi ar A, bet A ir garāks.


Pretējā gadījumā A ir mazāks vai vienāds ar B. Piemēru leksikogrāfiskajai salīdzināšanai var redzēt 2. attēlā.

![Leksikogrāfiskā salīdzināšana](/media/theory/str_compare.png)

<center>**2. attēls** - leksikogrāfiskā salīdzināšana.</center>

Ja apskatām ASCII tabulā simbolus no '0' līdz '9', no 'a' līdz 'z' un no 'A' līdz 'Z', tad var redzēt, ka to secība arī skaitliskajā formā ir pareiza. Tā kā katrs simbols ir skaitlis, tad mēs, salīdzinot divas simbolu virknes vai masīvus, patiesībā salīdzinām divas skaitļu virknes - tā rezultātā notiek leksikogrāfiskā salīdzināšana. Piemēru var skatīt 3. programmā, kur tiek attēloti abi piemēri no 2. attēla.

```
#include <iostream>
#include <string>
using namespace std;

int main ()
{
    /* 1. piemērs no attēla */
    string A = "ABAVA";
    string B = "ABIE";

    if ( A > B ) cout << "A > B" << endl;
    if ( A == B ) cout << "A == B" << endl;
    if ( A < B ) cout << "A < B" << endl; // Izvadās, ka A < B.

    /* 2. piemēs no attēla */
    A = "ABAVA";
    B = "ABAV";

    if ( A > B ) cout << "A > B" << endl; // Izvadās, ka A > B.
    if ( A == B ) cout << "A == B" << endl;
    if ( A < B ) cout << "A < B" << endl;

    return 0;
}
```

<center>**3. programma** - simbolu virkņu salīdzināšana.</center>

### Darbības ar simbolu masīviem

Tāpat, kā simbolu virknēm eksistē metodes, ar kurām var veikt darbības ar simbolu virknēm jeb string, tad simbolu masīviem eksistē string.h bibliotēka, kurā ir funkcijas pieejamas darbam ar tiem. Skatīt 4. programmu šo funkciju piemēriem.

```
#include <iostream>
#include <string.h>
using namespace std;

int main ()
{
    char mas1[20] = "To be or not to be.";
    char mas2[20];

    strcpy(mas2, mas1); // Kopēt visus simbolus.
    cout << mas2 << endl; // Izvada "To be or not to be."

    strncpy(mas2, "Vini vidi vici", 5); // Kopēt pirmos 5 simbolus
    cout << mas2 << endl; // Izvada "Vini  or not to be.".

    char mas3[20] = "";
    strcat(mas3, "To"); // Pieliek otro simbolu masīvu pirmajam beigās.
    strcat(mas3, " be\0");
    cout << mas3 << endl; // Izvada "To be".

    // Pieliek konkrētu skaitu simbolu pirmajam masīvam beigās no otrā masīva.
    strncat(mas3, " or not to be.", 7);
    cout << mas3 << endl; // Izavad "To be or not"

    // Leksikogrāfiski salīdzina mas1 ar mas3. Ja atgriež:
    // >0, tad mas1 > mas3.
    // 0, tad mas1 == mas3.
    // <0, tad mas1 < mas3.
    cout << strcmp(mas1, mas3) << endl; // Izvada 1.
    // Salīdzina norādīto skaitu pirmos simbolus.
    cout << strncmp(mas1, mas3, 4) << endl; // Izvada 0.

    char* pos = strchr(mas1, 'e'); // Atrod adresi, kurā simbols atrodas pirmo reizi masīvā.
    // Atņemot savā starpā norādes, tiek atgriezta starpība, cik atmiņas šūnas ir starp adresēm.
    // Šādi iegūstot simbola adresi atmiņā var noteikt tā pozīciju masīvā.
    cout << pos - mas1 << endl; // Izvada 4.

    char mas4[] = "Lieliski134";
    char mas5[] = "9876543210";
    // Pozīcija mas4, kurā pirmo reizi ir atrodams kaut viens simbols no mas5.
    cout << strcspn(mas4, mas5) << endl; // Izvada 8.

    // Atrod norādi uz "liski" pirmās parādīšanās reizes sākumu.
    pos = strstr(mas4, "liski");
    cout << pos - mas4  << endl;

    cout << strlen(mas4) << endl; // Nosaka simbolu masīva garumu.

    return 0;
}

```

<center>**4. programma** - simbolu masīvu funkcijas.</center>

<a href="http://www.cplusplus.com/reference/cstring/" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>