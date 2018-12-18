# Datora resursi

Dators balstās uz dažādām ierīcēm, kuras spēj saglabāt informāciju un apstrādāt komandas. Šajās ierīcēs ir gudri iestrādāti dažādi algoritmi, kas palīdz abstrahēties no tiem un domāt citā līmenī - programmēšanas valodas, procesi, virtuālā atmiņas. Sporta programmēšanā svarīgākie divi faktori ir laiks un atmiņa. Ja par laiku tika parunāts algoritmu sarežģītības nodaļā, tad par atmiņu tiek pastāstīts šeit.

### Atmiņa

Sporta programmēšanas uzdevumos un sacensībās parasti svarīgi ir divi aspekti - atmiņa un laiks. Šajā nodaļā tiks runāts par atmiņu. Atmiņa  datorā ir apskatāma no dažādām pusēm:

- **Fiziskā** - tā, kas glabājas reāli uz cietā diska, RAM u.c. ierīcēm.
- **Virtuālā** - tā, kas ir pieejama programmām un operētājsistēmām.

Virtuālā atmiņa, lai gan nosaukums var būt nedaudz maldinošs, patiesībā ir veids, kā abstrahēties no fiziskās atmiņas. Pateicoties virtuālajai atmiņai, var nodrošināt drošību starp programmām, lai vienas programmas nesāk rakstīt citas programmas atmiņā, un citus labumus.

Kad programma tiek startēta, tai tiek piešķirts konkrēts atmiņas daudzums - tas var mainīties. Pateicoties virtuālajai atmiņai, no programmas perspektīvas izskatās, ka tai pieder visa atmiņa, sākot no adreses 0x000000. Šo atmiņu iedala vairākos apgabalos:

- **Dati** - C++ valodā satur globālos un statiskos datus. Datu apgabalu var iedalīt divās daļās - lasāmā un lasāmā / rakstāmā. Lasāmajā daļā tiek glabāti tikai dati ar const priekšā, piemēram const int a;. Lasāmajā / rakstāmajā daļā rakstās visi pārējie statiskie un globālie datu.
- **Teksts** - lai operētājsistēma varētu izpildīt kodu, tam kaut kur ir jāglabājas. Izpildot programmu, tās teksts tiek glabāts teksta atmiņas apgabalā. Šim tekstam notiek virzīšanās cauri un komandu izpildīšana izmantojot pārējo atmiņu un datorā pieejamos resursus.
- **Kaudze** - C++ valodā šeit tiek glabāti dati rezervējot atmiņu. Jebkurš izsaukums ar new, malloc, realloc un citu rezervē atmiņu no kaudzes un delete, free to atbrīvo.
- **Steks** - C++ valodā šeit tiek glabāti dati izsaucot funkciju, nepieciešamie dati funkcijas izsaukumam un, lai atgrieztos atpakaļ uz izsaukuma vietu pēc izpildes. Piemēram, ja funkcijas izsaukumā tiek deklarēts mainīgais int, tad tas aizņems steka atmiņā 4 baitus. Steka un kaudzes atmiņas dala vienu atmiņas daudzumu, var iztēloties, ka tās aizpilda vienu apgabalu katra no sava gala. Ja tās sadurās, tad atmiņa ir pārpildīta.

<center>
<img alt="Procesa atmiņa" src="/media/theory/atmina.png"/>
**1. attēls** - procesa atmiņa.
</center>

<a href="http://en.wikipedia.org/wiki/Data_segment" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>