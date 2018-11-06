#Taišņu krustpunkts

Katru plaknes taisni var aprakstīt ar vienādojumu \\(ax+by = c\\). Kā divām taisnēm \\(a\_1x+b\_1y = c\_1\\) un \\(a\_2x+b\_2y = c\_2\\) aprēķināt krustojuma punktu?

Jebkurš šo taišņu krustpunkts ir atrisinājums sistēmai $$\begin{cases}a\_1x+b\_1y = c\_1\\\\ a\_2x+b\_2y = c\_2\end{cases}$$

To var atrisināt, izsakot \\(x\\) caur \\(y\\) no pirmās vienādības un aizvietojot otrajā vienādībā. Atrisinājumu sistēmai izsaka arī Kramera formulas, kur <i>determinants</i> \\(\begin{vmatrix} m\_{11} & m\_{12} \\\\ m\_{21} & m\_{22} \end{vmatrix}\\) izsaka vērtību \\(m\_{11}m\_{22}-m\_{12}m\_{21}\\):
$$x = \frac{\begin{vmatrix} c\_1 & b\_1 \\\\ c\_2 & b\_2 \end{vmatrix}}{\begin{vmatrix} a\_1 & b\_1 \\\\ a\_2 & b\_2 \end{vmatrix}} = { c\_1b\_2 - b\_1c\_2 \over a\_1b\_2 - b\_1a\_2}$$
$$y = \frac{\begin{vmatrix} a\_1 & c\_1 \\\\ a\_2 & c\_2 \end{vmatrix}}{\begin{vmatrix} a\_1 & b\_1 \\\\ a\_2 & b\_2 \end{vmatrix}} = { a\_1c\_2 - c\_1a\_2 \over a\_1b\_2 - b\_1a\_2}$$



<a href="http://en.wikipedia.org/wiki/Cramer%27s_rule" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>

Tālāk ir nepieciešams izšķirt, kurš no gadījumiem ir spēkā: taisnes ir paralēlas, bet dažādas; taisnes ir vienādas; taisnes krustojas vienīgā punktā.
<ul>
<li> Ja \\(\begin{vmatrix} a\_1 & b\_1 \\\\ a\_2 & b\_2 \end{vmatrix} = 0\\), tad sistēmai vai nu nav atrisinājuma, vai nu ir bezgalīgi daudz atrisinājumu. Tas nozīmē, ka taisnes ir paralēlas. Pirmajā gadījumā taisnes ir paralēlas, bet dažādas; otrajā gadījumā taisnes ir vienādas. Lai taisnes būtu vienādas, tad jābūt tādam reālam skaitlim \\(q\\), ka \\(a\_1 = qa\_2\\), \\(b\_1 = qb\_2\\), \\(c\_1 = qc\_2\\). Ja tāds \\(q\\) eksistē, tad \\(\begin{vmatrix} c\_1 & b\_1 \\\\ c\_2 & b\_2 \end{vmatrix} = \begin{vmatrix} a\_1 & c\_1 \\\\ a\_2 & c\_2 \end{vmatrix} = 0\\). Tātad taisnes sakrīt, ja visi trīs determinanti ir 0.
</li>
<li>
Ja \\(\begin{vmatrix} a\_1 & b\_1 \\\\ a\_2 & b\_2 \end{vmatrix} \neq 0\\), tad sistēmai ir vienīgs atrisinājums \\((x,y)\\). Tas atbilst gadījumam, kad taisnes krustojas vienā punktā.
</li>
</ul>

## Realizācija

```
#include<cmath>

double eps = 1e-9;

bool doublesEqual(double a, double b) {
	return fabs(a-b) < eps;
}

struct Point {
    double x, y;
};

struct Line {
	double a, b, c;
};

double det(double m11, double m12, double m21, double m22) {
	return m11*m22-m12*m21;
}

bool parallel(Line line1, Line line2) {
    return doublesEqual(det(line1.a, line1.b, line2.a, line2.b), 0);
}

bool equal(Line line1, Line line2) {
    return	parallel(line1, line2) &&
			doublesEqual(det(line1.c, line1.b, line2.c, line2.b), 0) &&
			doublesEqual(det(line1.a, line1.c, line2.a, line2.c), 0);
}

Point intersection(Line line1, Line line2) {
    Point point;
    double d = det(line1.a, line1.b, line2.a, line2.b);
    point.x = det(line1.c, line1.b, line2.c, line2.b)/d;
    point.y = det(line1.a, line1.c, line2.a, line2.c)/d;
    return point;
}
```

Deļ tā, ka reālo skaitļu tipam nav patvaļīgi lielas precizitātes, var uzkrāties mazas novirzes no patiesas skaitļa vērtības. Tāpēc uzskata, ka divi <code>double</code> skaitļi ir vienādi, ja tie viens no otra atšķiras par mazu absolūto vērtību, ko sauc par <i>epsilonu</i>. Šajā realizācijā par epsilonu ņemām vērtību \\(10^{-9}\\). Šī nav «vienīgā un pareizā» epsilona vērtība; atkarībā no uzdevuma ierobežojumiem var būt nepieciešamība izvēlēties lielāku vai mazāku epsilona vērtību.