### Varianza

Dem./
Para demostrar la segunda fórmula de la varianza, partimos de la definición original:
$$Var(X) = E[(X - E[X])^2]$$
Expandiendo el cuadrado, tenemos:
$$Var(X) = E[X^2 - 2X E[X] + (E[X])^2]$$
Utilizando la linealidad de la esperanza, podemos separar los términos:
$$Var(X) = E[X^2] - 2E[X]E[X] + E[(E[X])^2]$$
Dado que $E[X]$ es una constante, $E[(E[X])^2] = (E[X])^2$. Por lo tanto, la expresión se simplifica a:
$$Var(X) = E[X^2] - 2(E[X])^2 + (E[X])^2$$
Finalmente, obtenemos:
$$Var(X) = E[X^2] - (E[X])^2$$