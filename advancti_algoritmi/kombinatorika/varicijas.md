# Variācijas

Variācijas ir veids, kā izvēlēties m priekšmetus no n, ja svarīga ir secība. Piemēram, ja ir dotas 4 bingo bumbas numurētas no 0 līdz 3, un ir jāuzzina, cik veidos var paņemt 2 no 4 bumbām ar nosacījumu, ka paņemot 1, 2 un 2, 1 ir dažādi paņemšanas veidi, tad to var aprēķināt, kā ir redzams 1. attēlā. Piemēru visiem gadījumiem var redzēt tālāk:

```cpp
1. 01
2. 02
3. 03
4. 10
5. 12
6. 13
7. 20
8. 21
9. 23
10. 30
11. 31
12. 32
```

Aprēķinot pēc formulas, var iegūt rezultātu V(4, 2) = 4! / (4 - 2)! = 4! / 2! = 1 * 2 * 3 * 4 / (1 * 2) = 3 * 4 = 12, kas ir tāds pats, kā piemērā.

<img alt="Variācijas formula" src="/media/theory/variations.gif" />
**1. attēls** - variācijas formula.

<a href="http://www.uzdevumi.lv/ExerciseRun/RunExercise?exerciseId=d9737daf-3d32-44c9-9ab9-efcdea7db0ae&parentType=VirtualSchool&parentId=574" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>