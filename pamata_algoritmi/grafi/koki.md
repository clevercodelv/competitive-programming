# Koki

Koks ir neorientēta grafa speciāls paveids, kurā starp jebkurām divām virsotnēm eksistē tieši viens ceļš, pretējā gadījumā grafs nav koks. Kokiem ir dažādas interesantas īpašības. Piemēram skatīt 1. attēlu.

<center>
<img alt="Koks" src="/media/theory/grafs_koks.png" />
**1. attēls** - koks.
</center>

**Vecāku bērnu attiecība** - koku virsotnēm mēdz noteikt savstarpējās attiecības jeb bērnu vecāku attiecības. Koku pēc šīm attiecībām var arī hierarhiski uzzīmēt. Piemēram, 1. attēlā 1 virsotnes bērni ir 2 un 3, 2 bērni ir 4 un 5. Virsotņu vecāki ir tās virsotnes, kurām virsotnes ir bērni, piemēram, 2 virsotnei vecāks ir 1, 5 virsotnei vecāks ir 2.

**Koka sakne** - sakne ir virsotne, kurai nav vecāka. Parasti šo virsotni zīmē koka augšā (šie koki aug ar saknēm uz augšu). 1. attēlā sakne ir virsotne 1.

**Koka līmenis** - var redzēt, ka virsotne veidojas līmeņos. Līmeņus vēl varētu saukt par dziļumiem - ja virsotne atrodas 3. līmenī, tā atrodas dziļumā 3. 1. attēlā ir šādi līmeņi:

1. līmenis satur virsotnes 1;
2. līmenis satur virsotnes 2, 3;
3. līmenis satur virsotnes 4, 5, 6, 7.


**Binārs koks** - koks, kur katrai virsotnei ir maksimums divi bērni (1. attēlā ir binārs koks).

**K-ārs koks** - koks, kurā katrai virsotnei ir masksimums K bērni (1. attēlā K == 2).

**Koka īpašības** - ja kokam ir konkrēta struktūra (binārs, k-ārs u.c.), tad tam atkarībā no struktūras var izsecināt vairākas īpašības, piemēram, binārā kokā, ja sanumurē virsotnes, kā tas ir izdarīts 1. attēlā, tad zinot kādas virsotnes numuru, piemēram 7, var pateikt, kāds numurs ir vecāka virsotnei 7 / 2 == 3. Tāpat var noteikt katra vecāka bērnus, piemēram, virsotnei 3 bērni ir 3 * 2 == 6 un 3 * 2 + 1 == 7. Šīs un vēl dažādas īpašības var padarīt vispārīgas un izmantot programmā, piemēram, var secināt, ka k-ārā grafā, ja virsotnes numurs ir n, tad vecāku var iegūt ar n / k formulu un bērnus ar n * k, n * (k + 1), ..., n * (k + k - 1).

<a href="http://en.wikipedia.org/wiki/Tree_(graph_theory)" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>