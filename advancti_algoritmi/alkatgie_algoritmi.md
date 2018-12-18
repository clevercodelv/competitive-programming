# Alkatīgie algoritmi

**Alkatīgie algoritmi** ir plašs jēdziens, kurš tiek pielietot situācijās, kad algoritms neskatās uz kontekstu, bet veic konkrētajā situācijā izdevīgāko lēmumu. Piemēram, ja ir dots grafs un ir jāatrod īsākais ceļš, ne vienmēr atrodoties kādā virsotnē izdevīgākais būs doties uz tuvāko neapmeklēto virsotni. Bet ir situācijas, kad būt alkatīgam ir pareizi. Piemēram Prima, Kruskāla, Deikstras algoritmi izmanto alkatīgo pieeju un strādā lieliski. 

<a href="http://en.wikipedia.org/wiki/Greedy_algorithm" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>

Atlikuma izdošanas problēmas alkatīgā versija ir pašas problēmas apakšproblēma. Ja ir dots uzdevums ar noteikta nomināla naudu, piemēram, 1, 2, 5, 10, 20 izdot atlikumu no kādas summas, tad var izmantot alkatīgo pieeju gadījumos, kad nomināli ir superaugoša skaitļu virkne.

**Superaugoša skaitļu virkne ir sakārtota virkne, kur katrs nākamais elements ir lielāks par iepriekšējo elementu summu. Piemēram, 2 > 1, 5 > 2 + 1, 10 > 5 + 2 + 1, u.t.t.

Algoritms problēmai ir sekojošs:

1. Kamēr summa ir > 0.
    1. Atņem summai lielāko iespējamo nominālu.
    1. Izvada atņemto nominālu.
1. Visi atņemtie nomināli ir rezultāts.

```cpp
Piemēram, daudzums ir 345 un nomināli ir 1, 2, 5, 10, 20, 50, 100.

345 - 100 = 245
245 - 100 = 145
145 - 100 = 45
45 - 20 = 25
25 - 20 = 5
5 - 5 = 0

Rezultātā iegūst, ka minimālais monētu daudzums ir: 100, 100, 100, 20, 20, 5
```

<a href="http://en.wikipedia.org/wiki/Change-making_problem" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>