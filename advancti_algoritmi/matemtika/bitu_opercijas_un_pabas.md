# Bitu operācijas un īpašības

C++ programmēšanas valodā un vispār datoros katrs skaitlis glabājas atmiņā bitu formā. C++ valodā eksistē operatori, ar kuriem var mainīt vai nolasīt šos bitus. Piemēram, ja int sastāv no 32 bitiem, ar C++ operatoriem var manipulēt katru mainīgā bitu atsevišķi un visus kopā. Bitu operācijas ir:

**& (AND)** - no diviem operandiem atgriež trešo, kur tajā katrs bits ir iepriekšējo divu skaitļu katru divu bitu un & operācijas rezultāts.

```cpp
1000101001001
0010011001011
---------------
0000001001001
```

**| (OR)** - bitu or.

```
1000101001001
0010011001011
---------------
1010111001011
```

**^ (XOR)** - bitu izslēdzošais or.

```
1000101001001
0010011001011
---------------
1010110000010
```

**~ (NOT)** - bitu not.

```
1000101001001
---------------
0111010110110
```

**<< (LEFT SHIFT)** - bitu pārbīde pa kreisi. Biti tiek pabīdīti pa kreisi labajā galā pieliekot konkrētu skaitu 0 un kreisajā galā noņemot konkrētu skaitu bitu.

```
1000101001001 << 5
---------------
0100100100000
```

**<< (RIGHT SHIFT)** - bitu pārbīde pa labi.

```
1000101001001 >> 5
---------------
0000010001010
```

# Noderīgas operācijas

Ar bitiem var veikt dažādas interesantas darbības, kas var būt efektīvākas par līdzīgām loģiskajām darbībām.

#### Pārbaude, vai bits ir 1/0

* Lai noskaidrotu vai A 5. bits ir 1 jāveic sekojoša pārbaude: A & (1 << 5) != 0
* Attiecīgi, lai pārbaudītu, vai bits ir 0: A & (1 << 5) == 0

#### Pārveidot bitu uz 1/0.

* Lai pārveidotu A 5. bitu uz 1: A = A | (1 << 5)
* Lai pārveidotu A 5. bitu uz 0: A = A & (~(1 << 5))

#### Iegūt 2^N

Lai iegūtu 2^N: 1 << N
Piemēram:

* 1 << 0 == 1
* 1 << 1 == 2
* 1 << 2 == 4
* 1 << 3 == 8
* 1 << 4 == 16
* 1 << 5 == 32

#### Pārbaudīt paritāti

* Lai pārbaudītu, vai A ir pāra: A & 1  == 0 .
- Lai pārbaudītu, vai A ir nepāra: A & 1 != 0 .

#### Mainīt bita stāvokli uz pretējo

A ^ (1 << 5)

<a href="http://www.cplusplus.com/doc/tutorial/operators/" target="_blank">![Vairāk informācija](/media/theory/information.png)</a>