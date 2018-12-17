# Algoritma sarežģītība

Algoritmu analīzes viens no galvenajiem mērķiem ir noteikt algoritma patērēto resursu daudzumu - laiku un atmiņu. Sporta programmēšanā par algoritma sarežģītību sauc funkciju ietvertu lielā O notācijā, kura abstrakti raksturo, cik daudz darbības algoritms veiks. Sporta programmēšanas uzdevumus ierobežo laiks un patērētā atmiņa, tādēļ tas ir tik svarīgi saprast, cik daudz algoritms patērē abus resursus.

Algoritmu sarežģītību varētu mērīt pie dažāda lieluma ievaddatiem ar hronometru, bet tas būtu apgrūtinoši. Otrs variants ir mērīt atkarībā no ievaddatu apjoma procesora izpildīto instrukciju skaitu un skatīties, cik ļoti instrukciju skaits palielinās atkarībā no ievaddatu apjoma, bet tas pie vienādiem ievaddatiem diviem dažādiem algoritmiem var dažreiz sniegt maldinošu priekšstatu (piemēram, polinomiāli un exponensiāli algoritmi var izskatīties līdzīgi pie maziem ievaddatiem). Universāls variants ir skaitīt ciklu skaitu programmā - for, while, do while cikli, rekursijas, tos aprakstīt ar funkciju un pateikt, ka šī funkcija raksturo algoritma sarežģītību. Piemēram, apskatīsim 1. programmu un saskaitīsim, cik reizes tajā izpildīsies cikls.

```
#include <iostream>
using namespace std;

int main ()
{
    int n;
    cin >> n;

    for (int i = 0; i < n; ++i)
        cout << i << endl;

    return 0;
}
```

<center>**1. programma** - lineāra programma.</center>

Tātad programmā ir viens cikls, kurš izpildīsies n reizes. n ir vērtība, kura tiks ielasīta kā ievaddati, var secināt, ka funkcijā izmantotie mainīgie vis ticamāk būs ievaddatu izmēriem izmantotie mainīgie, piemēram, šī algoritma sarežģītību raksturo funkcija n. Programmēšanā sarežģītībai mēdz izmantot dažādus apzīmējumus - labākais gadījums, sliktākais gadījums, vidējais gadījums. Pārsvarā tomēr ņem vērā sliktāko gadījumu, jo uzdevumu veidotāji bieži vien apzinās algoritmus, kuriem izveidotie dati nesasniedz sliktāko gadījumu un izveido speciālus datus, lai sliktākais gadījums tomēr notiktu.

```
#include <iostream>
using namespace std;

int main ()
{
    int n, k;
    cin >> n;

    for (int i = 0; i < n; ++i)
    {
        cin >> k;
        if (k % 2 == 1)
            for (int j = 0; j < n; ++j)
                cout << j << endl;
    }

    return 0;
}
```

<center>**2. programma** - kvadrātiska programma.</center>

Apskatot 2. programmu var redzēt, ka tā n reizes veic darbības, kur ir cikls ar n reizēm. Lai gan pirmajā mirklī šķiet, ka sarežģītība varētu būt n\*n, bet patiesībā dēļ if nav zināms, vai kaut reizi tas izpildīsies un 2. cikls tiešām izpildīsies n reizes vai if nekad neizpildīsies un 2. cikls līdz ar to ne reizi nenotiks. Šī iemesla dēļ ir sliktākā un labākā sarežģītība:

- **sliktākā sarežģītība** - apzīmē, kāds varētu būt potenciāli sliktākais izpildes laiks vai patērētā atmiņa. 2. programmas gadījumā sliktākais laiks būtu n ^ 2.
- **labākā sarežģītība** - apzīmē, kāds varētu būt potenciāli labākais izpildes laiks vai patērētā atmiņa. 2. programmas gadījumā labākais laiks varētu būt n.
- **vidējais laiks** - apzīmē, kāds varētu būt vidējais potenciāli vidējais izpildes laiks vai patērētā atmiņa. Parasti vidējo laiku noteikt ir samērā sarežģīti un to nevajadzētu darīt sacensību laikā.

Bez algoritma izpildes laika svarīgs resurss ir arī atmiņa. Lai gan sacensībās lielāko grūtību sagādā ātrdarbības problēmas, atmiņas problēmas arī mēdz būt klupšanas akmens. Programmas patērēto atmiņu pārsvarā nosaka divi faktori - izvēlētais algoritms, ievaddatu apjoms. Ja ir teikts, ka jāielasa n skaitļi un tos ielasa masīvā, tad atmiņas sarežģītība ir n. Ja ielasa datus 2 dimensiju masīvā, kur tās platums ir n un augstums ir m, tad atmiņas sarežģītība būs n * m. Tiesa, sporta programmēšanā masīvi parasti tiek taisīti tik lieli, cik tas varētu būt nepieciešams sliktākajā gadījumā, lai programma darbotos ar lielākajiem testa datiem.

### Lielā O notācija

Lielā O notācija raksturo algoritma sarežģītību. Tā ir funkcija, kurai kā arguments tiek dota sarežģītības funkcija. Piemēram, O(N * N). Lielā O notācija apzīmē sliktāko gadījumu un tai ir viena svarīga īpašība - tajā neraksta konstantes, kuras dala, reizina, pieskaita, atņem. Zemāk ir saraksts ar dažādiem lielā O notācijas piemēriem:

- **Konstants algoritms** - O(1), neietver sevī nekādus ciklus vai rekursiju, piemēram, matemātiska formula.
- **Lineārs algoritms** - O(N), iziešana cauri sarakstam;
- **Kvadrātisks algoritms** - O(N * N) = O(N ^ 2) = O(N * N / 2) = O(N * N + 100);
- **Kvadrātisks algoritms** - O(N * M), piemēram, matricas apstaigāšana;
- **Kubisks algoritms** - O(N ^ 3), piemēram, parasta matricu reizināšana;
- **Polinomiāls algoritms** - O(N^M), kur M varētu būt jebkāds skaitlis.;
- **Logaritmisks algoritms** - O(log(N)), piemēram, binārā meklēšana;
- **Logaritmisks algoritms** - O(N * log(M)) bieži vien ietver sevī meklēšanas algoritmu vai skaldi un valdi algoritmu;
- **Faktoriāls algoritms** - O(N!) parasti kombinatoriskos uzdevumos, piemēram, visu objektu kombināciju apskatīšana;
- **Eksponensiāls algoritms** - O(2 ^ N) sliktākie algoritmi, kuri pie nelieliem datiem izpildās ļoti ilgi. Tiesa, ir tādas problēmas, kurām nav 100% risinājuma un šāda veida algoritmi ir vienīgie, kas 100% tos atrisina visos variantos.

<a href="http://en.wikipedia.org/wiki/Analysis_of_algorithms" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>
<a href="http://bigocheatsheet.com/" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>