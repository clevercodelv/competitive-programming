#Efektīva skaitļu kāpināšana

Cik ātri var uzcelt skaitli \\(a\\) pakāpē \\(n\\)? Algoritms, kas sareizina \\(a\\) ar sevi \\(n\\) reizes, strādā laikā \\(\mathcal O(n)\\) (lineāri). Šajā sadaļā aprakstīsim algoritmu, kas izrēķina \\(a^n\\) laikā \\(\mathcal O(\log n)\\) (logaritmiski).

Pamatdoma balstās uz sekojošām īpašībām:
<ul>
  <li>Ja \\(n\\) ir pāra, \\(n = 2k\\), tad \\(a^n = a^{2k} = a^k \cdot a^k\\).</li>
  <li>Ja \\(n\\) ir nepāra, \\(n = 2k+1\\), tad \\(a^n = a^{2k+1} = a \cdot a^{2k}\\).</li>
</ul>

Tāpēc varam realizēt rekursīvo procedūru, kas izrēķina \\(a^n\\):

```
int fastPow(int a, int n) {
	if(n == 0) {
		return 1;
	} else if(n%2 == 0) {
		int pow = fastPow(a, n/2);
		return pow*pow;
	} else {
		int pow = fastPow(a, n-1);
		return a*pow;
	}
}
```

Paliek jautājums, cik ātri strādā šis algoritms. Šis algoritms ir piemērs tā sauktajai <i>astes rekursijai</i>: katrs procedūras izsaukums izsauc sevi ne vairāk par vienu reizi. Piemēram, darbinot šo algoritmu ar \\(n = 13\\), tas mainās šādi:

<center><img alt="Efektīvās kāpināšanas izsaukums" src="/media/theory/bin_pow.png" height="70"/></center>

<center>**1. attēls** - efektīvās kāpināšanas izsaukums.</center>

Ja pakāpe ir pāra, tad nākamajā izsaukumā tā samazinās divkārt. Tāpēc izsaukumu skaits, kad pakāpe ir pāra, nevar būt lielāks par \\(\log\_2 n\\). No citas puses, ja pakāpe ir nepāra, tad tiek izpildīts rekursīvs izsaukums priekš tās mīnuss 1, kas ir pāra skaitlis. Tāpēc nav divu rekursīvo izsaukumu pēc kārtas ar nepāra pakāpi. Maksimālais izsaukumu ar nepāra pakāpi skaits būs tad, ja gan pirms, gan pēc katra izsaukuma ar pāra pakāpi ir izsaukums ar nepāra pakāpi. Tad kopējais izsaukumu skaits nepārsniedz \\(2\log_2 n+1 = \mathcal O(\log n)\\).

## Skaitļu kāpināšana pēc moduļa

Viegli pamanīt, ka algoritma ātrums būs noderīgs tad, ja \\(n\\) ir liels. Savukārt tādā gadījumā \\(a^n\\) noteikti pārsniegs datu tipa izmēru (notiks pārpildīšanās, overfow). Piemēram, ja jau \\(a = 3\\) un \\(n = 50\\), tad \\(a^n \approx 7\cdot10^{23}\\), bet pat 64 bitu veselo skaitļu tips (<code>long long</code> valodā C++) var saturēt tikai skaitļus līdz \\(\approx 9\cdot10^{18}\\). Tāpēc bieži uzdevumos prasa atrast tikai \\(a^n \pmod m\\), kādam veselam skaitlim \\(m\\) (modulim). Priekš tā vajag pamainīt algoritma implementāciju:

```
int fastPow(int a, int n) {
	if(n == 0) {
		return 1;
	} else if(n%2 == 0) {
		int pow = fastPow(a, n/2);
		return (pow*pow) % m;
	} else {
		int pow = fastPow(a, n-1);
		return (a*pow) % m;
	}
}
```

## Ātrāka realizācija

Aprakstīto algoritmu var uztvert arī mazliet citādā veidā. Aplūkosim \\(n\\) reprezentāciju binārā skaitīšanās sistēmā:
$$n = b\_0\cdot 1 + b\_1\cdot2 + b\_2\cdot 4 + \ldots + b\_k\cdot2^k$$
Tā kā \\(a^{p+q} = a^p \cdot a^q\\), tad \\(a^n\\) var izteikt kā
$$a^n = a^{b\_0\cdot 1} \cdot a^{b\_1\cdot2} \cdot a^{b\_2\cdot4} \cdot \ldots \cdot a^{b\_k\cdot2^k}$$
vai
$$a^n = a^{b\_0} \cdot (a^2)^{b\_1} \cdot (a^4)^{b\_2} \cdot \ldots \cdot (a^{2^k})^{b\_k}$$
Šeit \\(b\_i\\) ir \\(i\\)-tais bits skaitļa \\(n\\) binārā reprezentācijā. Ievērosim, ka ja \\(b\_i = 0\\), tad atbilstošais reizinātājs kļūst par 1 un nemaina rezultātu. Tāpēc ir jēga aplūkot tikai tos \\(b\_i\\), kas ir vienādi ar 1. Galarezultāts ir sekojoša realizācija:

```
int fastPow(int a, int n) {
	int res = 1;
	while(n > 0) {
		if(n%2==1) {
			res = (res * a) % m;
		}
		a = (a*a) % m;
		n /= 2;
	}
}
```

Pamatcikls pārlasa \\(n\\) bitus, sākot no pirmā uz pēdējo, jo katru iterāciju \\(n\\) tiek izdalīts ar 2. Tas faktiski nozīmē, ka skaitļa \\(n\\) binārā pierakstā mēs izsvītrojam pašu pirmo bitu (nākamais bits kļūst par jauno pirmo). Tāpēc, lai pārbaudītu, ka atbilstošais bits ir 1, pietiek paņemt skaitli \\(n\\) pēc moduļa 2 pašreizējā iterācijā.

No citas puses, \\(a\\) uzceļam kvadrātā katru iterāciju. Tas nozīmē, ka pēc \\(k\\)-tās iterācijas (skaitot no 1) \\(a\\) glabāsies skaitlis \\(a^{2^k}\\). Tāpēc, ja nākamajā iterācijā bits tiešām ir 1, tad rezultātam piereizinām \\(a^{2^k}\\) - tieši atbilstoši formulai.

Šī realizācija nav rekursīva: tā tikai satur vienu ciklu. Praktiski tas nozīmē mazliet ātrāku izpildes laiku.