5,6,7,11(pensar, sin herramientas aun),12

Si el lenguaje es finito, es regular.

La parte lexica de los lenguajes de programacion por definicion es regular.
El scanner de un compilador es un automata finito.

La concatenacion de lenguajes regulares es regular.




9)
S -> aaaRbbb 
R -> epsilon | aaRb

S -> aaaR | epsilon
R -> aabbb | aaRb

8)
cualquier orden
S -> aSa | bSb | c

primero a, dsp b 
S -> aSa | aRa | c
R -> bRb | c

10)
S -> aSd | aTd
T -> bTc | bc


22)
S -> Tb
T -> aTb | epsilon



0-
|
| - (a) -> 1 - (b) -> 3+
|
| - (b) -> 2 
           | - (a,b) -> 4+


2)
Funcion de trancision:
(0, a) = 1
(1, a) = 2+
(1, b) = 3+
(3+, a) = 3+

2.
    1. .
        i. Estoy en el estado 0
        ii. Voy por a, al estado 1.
        iii. voy por b, al estado 3+. 
        iv. finalizo. Cadena valida
    2. .
        i. Estoy en el estado 0
        ii. voy por a a 1.
        iii. 1 no es terminal. rechazo la cadena.


 3)
 | TT | a | b |
 | ---|---|---|
 | 0- | 1 | 2 |
 | 1  | - | 2 |
 | 2+ | 2 | - |       


 | TT | a | b |
 | ---|---|---|
 | 0- | 1 | 2 |
 | 1  | 3 | 2 |
 | 2+ | 2 | 3 |       
 | 3  | 3 | 3 |