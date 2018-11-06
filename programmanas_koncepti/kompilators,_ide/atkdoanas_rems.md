#Atkļūdošanas režīms

Programmēšanā izmantojot IDE jeb izstrādes lietotni, ir iespējams izpildīt programmu dažādos režīmos. Citi IDE piedāvā dažādus režīmus - profilēšana, izstrāde, atkļūdošana u.c. Līdz šim tika runāts par izpildes režīmu, tas ir režīms, kurā lietotājs spēj izpildīt savu kodu, kompilēt to un izmantot tālākai lietošanai. Bet ir vērts apskatīt arī atkļūdošanas režīmu. Apskatāmā vide ir Code::Blocks, bet principi ir ļoti līdzīgi citos IDE.

Atkļūdošanas režīmā ir iespējams likt kodam apstāties tā izpildes laikā, lai, piemēram, apskatītos kādu vērtību kādā programmas daļā. Lai apstādinātu kodu konkrētā vietā, var izmantot pārtraukuma punktus uzklikšķinot vienu (vai citreiz divas) reizi kreisajā sānā tajā rindā, kurā ir jāapstājas. Pārtraukuma punktu piemērs ir apskatāms 1. attēlu.

![Pārtraukuma punkti](/media/theory/debug_breakpoint.png)

<center>**1. attēls** - pārtraukuma punkti.</center>

Atkļūdošanas vadībai tiek izmantotas vairākas pogas. Veicot atkļūdošanu, atrašanās vietu kodā var redzēt ar dzelteno bultu kreisajā sānā. Sekojošas darbības ir iespējams veikt:

1. Sākt atkļūdošanu. <img src="/media/theory/dbg_start.png" />
1. Pārvietoties uz nākamo pārtraukuma punktu. <img src="/media/theory/dbg_next_bp.png" />
1. Pārvietoties uz nākamo rindu - funkcijās netiek iekāpts iekšā. <img src="/media/theory/dbg_next_row.png" />
1. Iekāpt funkcijā - ja atkļūdošanas režīma rindā ir funkcijas izsaukums, ir iespējams ieiet funkcijā un pārvietoties pa to. <img src="/media/theory/dbg_step_in.png" />
1. Izkāpt no funkcijas - ja ir iekāpts funkcijā, tad jebkurā mirklī var atgriezties pie tās izsaukuma un turpināt iet tālāk. <img src="/media/theory/dbg_step_out.png" />
1. Pārtraukt atkļūdošanu - beidz programmas izpildi un atkļūdošanu. <img src="/media/theory/dbg_stop.png" />

###Pārtraukuma punkti ar nosacījumiem

Ja ir uzlikts kāds pārtraukuma punkts, tam ir iespējams pievienot nosacījumu. Nosacījums ir C++ nosacījums (līdzīgi, kā if izteiksmē), kura izpildīšanās gadījumā (kad tas ir true) programma apstājas šajā pārtraukuma punktā. Atšķirība no parastajiem pārtraukuma punktiem ir tāda, ka programma apstājas vienmēr, ja sasniedz parasto pārtraukuma punktu. Piemēram, ja programma ģenerē N-to Fibonačī virknes numuru, kur i tiek izmantots, kā cikla skaitītājs, ir iespējams uzlikt i > 10 nosacījumu pārtraukuma punktam, lai programma apstātos katru reizi uz pārtraukuma punktu, kamēr i > 10. Vēl viens nosacījuma piemērs varētu būt i > 10 && i < 15.

Lai pievienotu pārtraukuma punktam nosacījumu, ir jāveic sekojošas darbības:

1. Jāspiež uz to kreisajā sānā ar labo peles pogu.
1. Jāspiež "Edit breakpoint". 
1. Jāieķeksē "Break when expression is true:".
1. Zem uzraksta logā ir jāieraksta nosacījums - var izmantot visus tajā pārtraukuma punkta vietā pieejamos mainīgos.
1. Spiež OK un nosacījums ir pievienots.

###Vērtību skatīšanās atkļūdošanas laikā

Atkļūdošanas laikā, apstājoties pie kāda pārtraukuma punkta, ir iespējams apskatīties mainīgo vērtības izmantojot **Debug > Debugging windows > Watches**. To izdarot parādās logs, kā 2. attēlā. Logam tabulā apakšējā rinda ir tukša. Šajā rindā kreisajā šūnā ierakstot mainīgā nosaukumu, ir iespējams redzēt tā vērtību atkļūdošanas laikā, pārtraukuma punktā. Šajā tabulā var pievienot ne tikai elementāros tipus, bet arī kompleksos un masīvu elementus. Dažus kompleksos tipus vērtību skatīšanās var nespēt pilnīgi attēlot.

![Vērtību skatīšanās](/media/theory/debug_watch.png)

<center>**2. attēls** - vērtību skatīšanās.</center>

<a href="http://wiki.codeblocks.org/index.php?title=Debugging_with_Code::Blocks" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>