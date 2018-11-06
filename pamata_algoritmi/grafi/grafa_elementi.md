#Grafa elementi

Grafs pēc idejas ir diagramma, kura sastāv no specifiskām sastāvdaļām. Viens bieži izmantots piemērs ir domu zirneklis (skatīt 1. attēlā).

![Domu zirneklis](/media/theory/zirneklis.png)

<center>**1. attēls** - domu zirneklis par mašīnas sastāvdaļām.</center>

**Grafs** - šķautņu kopa (parasti apzīmē ar E) un virsotņu kopa (parasti apzīmē ar V), kur katra šķautne no E sasaista divas virsotnes no V. Piemēram, 1. attēlā bultas ir šķautnes un ovāli ir virsotnes.

**Šķautne** - elements no E kopas, kurš savieno divas virsotnes n, m, kur n un m pieder V kopai.

**Visotne** - elements no V kopas. Var saturēt kādu vērtību, var arī nesaturēt.

**Cilpa** - ja šķautnes n == m jeb šķautne savieno vienu un to paši virsotni, to sauc par cilpu (skatīt 2. attēlu).

<center><img alt="Domu zirneklis" src="/media/theory/cilpa.png"/></center>

<center>**2. attēls** - cilpa.</center>

**Orientēts grafs** - ja šķautnēm ir noteikts konkrēts virziens (to parasti attēlo kā bultu), kā 1. attēlā, tad grafs ir orientēts.

**Svērts grafs** - ja grafa šķautnēm, līdzīgi kā virsotnēm, katrai ir kāda vērtība, tad grafu sauc par svērtu grafu (skatīt 3. attēlu).

<center><img alt="Svērts grafs" src="/media/theory/grafs_sverts.png"/></center>

<center>**3. attēls** - svērts grafs.</center>

**Grafa komponentes** - pēc idejas grafs var būt sadalīts vairākās daļās. Katru šādu grafa daļu sauc par grafa komponenti (skatīt 4. attēlā).

<center><img alt="Grafa komponentes" src="/media/theory/grafs_komponentes.png"/></center>

<center>**4. attēls** - grafa komponentes.</center>

**Ceļš grafā** - šķautņu kopa no virsotnes n uz m (skatīt 5. attēlu). Ceļa garums ir ceļa šķautņu svaru summa, ja svars nav, tad var pieņemt, ka visas šķautnes sver vienādi, piemēram, 1. 5. attēlā ceļa garums būtu 4.

<center><img alt="Ceļš grafā" src="/media/theory/grafs_cels.png"/></center>

<center>**5. attēls** - ceļš grafā.</center>

**Cikls grafā** - cikls ir ceļš grafā, kurš ir garāks par 0, sākas un beidzas vienā un tajā pašā virsotnē. Ja grafā nav ciklu, to sauc par **aciklisku**.

**Virsotnes pakāpe** - neorientētā grafā virsotnes pakāpe ir virsotnei piesaistīto šķautņu skaits. Svērtā grafā var izšķirt ienākošo šķautņu virsotnes svaru un izejošo šķautņu virsotnes svaru, kur pirmais ir ienākošos šķautņu skaits un otrs ir izejošo šķautņu skaits.

<a href="http://en.wikipedia.org/wiki/Graph_theory" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>