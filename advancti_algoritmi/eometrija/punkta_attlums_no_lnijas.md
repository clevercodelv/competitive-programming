# Punkta attālums no līnijas

Attāluma atrašana no punkta līdz līnijai ir bieži sastopama ģeometrijas problēma. Piemēram, ir doti trīs punkti A, B, C. Ir jāatrod attālums no punkta C līdz līnijai A, B (jāpiemin, ka līnija ir bezgalīga, punkti ir tikai paredzēti līnijas definēšanai). Algoritms ir sekojošs:

1. Apzināt vektorus AB un AC.
1. Aprēķina ABxAC.
1. Attālums ir (ABxAC)/|AB|.

Pamatojums tam, kādēļ tas strādā, ir vienkāršs. Ar ABxAC tiek aprēķināts paralelogramma laukums, kuru veido vektori AB un AC. Izdalot paralelogramma laukumu ar vienu no malām var iegūt augstuma garumu no pretējās malas līdz konkrētajai, kas ir arī meklētais attālums. Piemēru var apskatīt 1. attēlā.

<center>
<img alt="Attālums no punkta līdz virknei" src="/media/theory/point_line_distance.png"/>
**1. attēls** - attālums no punkta līdz virknei.
</center>

<a href="http://community.topcoder.com/tc?module=Static&d1=tutorials&d2=geometry1" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>