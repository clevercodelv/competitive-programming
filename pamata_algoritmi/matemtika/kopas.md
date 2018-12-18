# Kopas

Kopas programmēšanā noder kā abstrakcijas veids. Par problēmām var domāt kopu līmenī un caur kopu darbībām, kā arī var izskaidrot risinājumu vai ideju kādam citam ar kopu palīdzību.

Kopas ir veids, kā matemātikā apzīmēt grupu ar elementiem. Piemēram, var iztēloties divas kopas - pāra skaitļi un nepāra skaitļi. Kopām ir nosacījums, ka kopas ietvarā eksistē tikai unikāli elementi, tādēļ, ja būtu kopa ar visu veselu skaitļu (..., -2, -1, 0, 1, 2, ...) absolūtajām vērtībām, tad kopā neeksistētu divi skaitļi 1, 2, ..., bet gan viens skaitlis no katra eksemplāra. Kopu tālāk apzīmēsim šādi {1, 2, 3}. Kopā nav svarīga nozīme secībai, piemēram {1, 2, 3} == {2, 1, 3} u.t.t.

**Multikopa** - multikopa ir kopa, kurā var eksistēt vairāki vienādi elementi, piemēram, {1, 1, 2, 3} nav kopa, bet ir multikopa.

**Apakškopa** - daļa no kādas kopas ir tās kopas apakškopa. Piemēram, {1, 2} ir apakškopa no {1, 1, 2, 3}, kā arī {} ir apakškopa no {1, 1, 2, 3}. Katra kopa ir nestingra apakškopa pati sev. Ja saka, ka A ir stingra apakškopa B, tad B var būt vienāds ar A. Ja saka, ka A ir nestingra apakškopa B, tad B var būt vienāds ar A.

**Tukšā kopa** - kopa, kura nesatur nevienu elementu ir tukšā kopa {}.

**Visuma kopa** - kopa, kura satur visus kontekstā esošos elementus. Piemēram, ja runa iet par veseliem skaitļiem, tad visuma kopa satur visus veselos skaitļus un jebkura cita kopa ir apakškopa no visuma kopas.

**Venna diagramma** - kopas matemātikā mēdz vizuāli attēlot ar Venna diagrammu. Piemēru Venna diagrammām var redzēt kopu darbību nodaļā.

<a href="http://en.wikipedia.org/wiki/Set_(mathematics)" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>

**Kortežs** - ja multikopā nav svarīga secība, tad kortežs ir kaut kas līdzīgs kopai, bet tajā ir svarīga secība. Kortežus apzīmē ar nedaudz citām iekavām (1, 1, 2, 3). Piemēram, (1, 1, 2, 3) != (1, 2, 1, 3), bet {1, 1, 2, 3} == {1, 2, 1, 3}.

<a href="http://www.cplusplus.com/reference/tuple/" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>

### Kopu darbības

Kopas programmēšanā var iztēloties kā masīvus. C++ algorithm bibliotēkā ir realizētas funkcijas kopu darbībām, kuras izmanto masīvus, lai tās veiktu. Kopu darbības ir sekojošas:

**Apvienošana** - ja apvieno divas kopas A un B, tad rezultātā veidojas jauna kopa C, kas iekļauj visus A un B elementus.

<img alt="Apvienošana" src="/media/theory/kopa_apvienosana.png"/>
**1. attēls** - kopu apvienošana.

**Šķelšana** - ja šķeļ divas kopas A un B, tad rezultātā iegūst kopu C, kurā atrodas visi elementi, kas ir gan A, gan B.

<img alt="Apvienošana" src="/media/theory/kopa_skelsana.png"/>
**2. attēls** - kopu šķelšana.

**Atņemšana** - ja atņem no kopas A kopu B, tad rezultātā iegūst kopu C, kurā ir visi elementi no kopas A, kuri nav kopā B.

<img alt="Apvienošana" src="/media/theory/kopa_atnemsana.png"/>
**3. attēls** - kopu atņemšana.

**Negācija** - ja veic negāciju kopai A, tad iegūst visus elementus no visuma kopas, kuri nav A kopā.

<img alt="Negācija" src="/media/theory/kopa_negacija.png"/>
**4. attēls** - kopu negācija.

**Izslēdzošais vai** - visi elementi, kas atrodas tikai A vai tikai B kopās. 

<img alt="Izslēdzošais vai" src="/media/theory/kopa_dekarta_reizinajums.png"/>
**5. attēls** - kopu izslēdzošais vai.

<a href="http://www.cplusplus.com/reference/algorithm/" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>