# Programmēšanas uzdevumu formāts

Viens no galvenajiem veidiem, kā sporta programmēšanā trenēties, ir pildīt sporta programmēšanas uzdevumus. Šie uzdevumi ir atjautīgi un bieži vien uz zināšanām balstīti. Uzdevuma mērķis ir sniegt programmētājam problēmu, kuru ir nepieciešams atrisināt ar programmēšanas palīdzību.

Eksistē diezgan daudz tiešsaistē pieejamas sistēmas, kurās var pildīt šos uzdevumus augšuplādējot savu programmu. Lai programma atrisinātu problēmu, tai ir jāatbilst pāris kritērijiem:

- Programmai ir jāprot nolasīt uzdevumā minētā formāta dati no ievaddatu faila vai ekrāna (atkarīgs no servera nosacījumiem).
- Programmai ir bez kļūdām un pareizi jāspēj aprēķināt uzdevumā prasītais rezultāts.
- Programmai ir jāprot ierakstīt uzdevumā minētajā formātā dati izvaddatu failā vai uz ekrāna (atkarīgs no servera nosacījumiem).
- Programmas izpildes ilgums nedrīkst pārsniegt noteikto limitu (parasti 1 - 2 sekundes).
- Programmas izpildes laikā patērētā atmiņa nedrīkst pārsniegt noteikto limitu (parasti 16 - 1024 megabaiti).


Uzdevuma problēmas apraksts sastāv no vairākām daļām:

- **Nosaukums un limiti** - var tikt atdalīti viens no otra, bet tas ir atkarīgs no formāta. Šajā nodaļā parasti ir uzdevuma nosaukums, citos serveros mēdz pievienot uzdevuma kodu, kā arī laiks un atmiņa atvēlēta vienas programmas izpildei uz viena testa piemēra.
- **Formulējums** - satur problēmas tekstuālo aprakstu. Dažreiz formulējumā var būt elementārs apraksts vai pat viens teikums. Citreiz formulējums var atrasties pat uz divām A4 lapām, kas notiek visai reti. Mērķis ir aprakstīt, kas ir jādara.
- **Ievaddatu apraksts** - tiek pastāstīts, kādā formātā dati atrodas ievaddatu failā, vai kādā formātā tie tiks padoti caur standarta ievadi.
- **Izvaddatu apraksts** - tiek pastāstīts, kādā formātā datus sagaida vērtēšanas sistēma. Parasti ievaddatu un izvaddatu aprakstos tiek doti arī failu nosaukumi datu lasīšanai / rakstīšanai, ja tas nenotiek standarta ievadē, izvadē.
- **Testu grupas** - tā kā programma tiek testēta pret vairākiem testu datiem, tad dažreiz uzdevumam klāt var tikt pievienots testu sadalījums par grupām. Var tikt aprakstīts, cik daudz procentuāli var iegūt punktus, ja atrisina uzdevumu ar konkrētu datu apjomu. Acīmredzot, jo lielāks datu apjoms, jo gudrāks algoritms ir jāizdomā.
- **Paraug dati** - parasti iekļauj 1 - 3 piemērus ar ievaddatiem un rezultātā iegūstamajiem izvaddatiem.
- **Pielikums** - šeit var tikt pievienoti attēli vai kāda paraug datu piemēra detalizēts skaidrojums.


Kā rēķina rezultātu? Pamatā ir divas pieejas:

- **Visu vai neko** - ja programma neatrisina kādu no testa datiem vai ir kļūda, vai pārsniegti resursu ierobežojumi, tad uzdevums ir neveiksmīgs, citādi veiksmīgs. Dažas sistēmas mēdz paziņot, vai uzdevums bija vienkārši neveiksmīgs, vai tika pārsniegts kāds ierobežojums, vai bija kļūda. Šī pieeja ir raksturīga tiešsaistes sacensībām un uzdevumiem.
- **Katrs tests skaitās** - šajā pieejā parasti par katru uzdevuma iesūtījumu skaita punktus. Piemēram, ja 7 no 10 testiem bija pareizi, tad ir iegūts 7/10 rezultāts. Dažreiz katram testam var tikti piekārtoti kādi punkti, piemēram, lai vienmēr rezultāts būtu kaut kas no 100, pat ja testi ir tikai 25. Šāda veida vērtēšana pārsvarā tiek izmantota oficiālajās olimpiādēs, kā Latvijas novada olimpiāde, LIO, BOI, IOI.


Sekojošajās vietnēs var apskatīt sporta programmēšanas uzdevumu piemērus un sākt kādu jau risināt:

- <a href="http://olimps.lio.lv/uzdevumi.php" target="_blank">**Olimps**</a> - dažu LIO organizētāju uzturēts servesi, kur ir pieejami vairāki iepriekšējo gadu uzdevumi. Visi tie ir latviešu valodā.
- <a href="http://www.spoj.com/" target="_blank">**Sphere Online Judge (SPOJ)**</a> - daudz uzdevumi angļu valodā. Izveido savu kontu un audzē reitingu.
- <a href="http://uva.onlinejudge.org/" target="_blank">**UVa Online Judge**</a> - arī satur daudz uzdevumus. Šai sistēmai ir veltītas vairākas grāmatas ar algoritmu skaidrojumiem un attiecīgajiem uzdevumiem pievienotiem par konkrēto algoritmu.
- <a href="http://en.wikipedia.org/wiki/Online_judge"  target="_blank">**Daudzas citas sistēmas**</a> - vikipēdija ir apkopojusi sarakstu ar uzdevumu sistēmām.