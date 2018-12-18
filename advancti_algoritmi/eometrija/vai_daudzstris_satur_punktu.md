# Vai daudzstūris satur punktu

Ideja ir gaužām vienkārša. Tiek novilkts stars no punkta līdz kādai bezgalībai. Ja daudzstūrī tiek šķērsots nepāra skaits šķautņu, tad punkts ir daudzstūrī, citādi punkts ir ārpus daudzstūra. Lai pārbaudītu, vai daudzstūra šķautne krusto staru, var iztēloties, ka stars ir ļoti liels nogrieznis - pietiekami liels, lai krustotu visas krustojamās šķautnes. Kad tas ir izdarīts, pietiek pārbaudīt katru šķautni AB un noteikt, vai A ir vienā pusē un B ir otrā pusē no nogriežņa. To var izdarīt ar pseido skalāro reizinājumu. Ja leņķis ir < 180, tad sin > 0, ja leņķis ir > 180, tad sin < 0. Piemēru ar AB malu (atsevišķi izceltu) un punktu P var apkatīt 1. attēlā un realizāciju 1. programmā.

<center>
<img alt="Nogriežņu krustošanās noteikšana" src="/media/theory/segment_cross.png"/>
**1. attēls** - nogriežņu krustošanās noteikšana.
</center>

<a href="http://en.wikipedia.org/wiki/Point_in_polygon" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>