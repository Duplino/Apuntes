## Probabilidad

## Variables Aleatorias

Una variable aleatoria es una función que asigna un valor numérico a cada resultado de un experimento aleatorio. Las variables aleatorias pueden ser discretas o continuas, dependiendo de si toman un número finito o infinito de valores.

$$ f: E \to \mathbb{R} $$
donde $E$ es el espacio muestral del experimento aleatorio.

$f(X)$ es la variable aleatoria que asigna un valor numérico a cada resultado del experimento. Por ejemplo, si lanzamos un dado, podemos definir una variable aleatoria $X$ que representa el número que sale en el dado. En este caso, $X$ puede tomar los valores 1, 2, 3, 4, 5 o 6.

### Variable Aleatoria Discreta

#### Esperanza
La esperanza de una variable aleatoria discreta $X$ se define como:
$$E[X] = \sum_{x} x P(X = x)$$

La esperanza, también conocida como valor esperado o media, representa el valor promedio que se espera obtener al realizar un experimento aleatorio muchas veces. Es una medida de tendencia central que indica el valor alrededor del cual se agrupan los resultados de la variable aleatoria. Es el centro de masa de la distribución de probabilidad de $X$.

La esperanza se encuentra en el intervalo $[min(X), max(X)]$, donde $min(X)$ y $max(X)$ son los valores mínimo y máximo que puede tomar la variable aleatoria $X$, respectivamente.

##### Propiedades de la Esperanza
1. **Linealidad**: Para cualquier variable aleatoria discreta $X$ y cualquier constante $a$ y $b$, se cumple que:
   $$E[aX + b] = aE[X] + b$$
2. **Esperanza de una función**: Para cualquier función $g$ y cualquier variable aleatoria discreta $X$, se cumple que:
   $$E[g(X)] = \sum_{x} g(x) P(X = x)$$
3. **Esperanza de la suma**: Para cualquier conjunto de variables aleatorias discretas $X_1, X_2, \ldots, X_n$, se cumple que:
   $$E[X_1 + X_2 + \ldots + X_n] = E[X_1] + E[X_2] + \ldots + E[X_n]$$


#### Varianza
La varianza de una variable aleatoria discreta $X$ se define como:
$$Var(X) = E[(X - E[X])^2]$$

La varianza mide la dispersión de los valores de la variable aleatoria alrededor de su esperanza. Un valor de varianza más alto indica que los valores de $X$ están más dispersos, mientras que un valor de varianza más bajo indica que los valores están más concentrados alrededor de la esperanza.

Se puede [demostrar](demostraciones.md#varianza) que la varianza también se puede calcular como:
$$Var(X) = E[X^2] - (E[X])^2$$

##### Propiedades de la Varianza
1. **No negatividad**: La varianza siempre es mayor o igual a cero, es decir, $Var(X) \geq 0$ para cualquier variable aleatoria discreta $X$.
2. **Varianza de una constante**: Si $c$ es una constante, entonces $Var(c) = 0$.
3. **Varianza de una función**: Para cualquier función $g$ y cualquier variable aleatoria discreta $X$, se cumple que:
   $$Var(g(X)) = E[(g(X) - E[g(X)])^2]$$
4. **Varianza de la suma**: Para cualquier conjunto de variables aleatorias discretas $X_1, X_2, \ldots, X_n$, se cumple que:
   $$Var(X_1 + X_2 + \ldots + X_n) = Var(X_1) + Var(X_2) + \ldots + Var(X_n) + 2\sum_{i < j} Cov(X_i, X_j)$$
donde $Cov(X_i, X_j)$ es la covarianza entre las variables aleatorias $X_i$ y $X_j$.

#### Desviación Estándar
La desviación estándar de una variable aleatoria discreta $X$ se define como la raíz cuadrada de la varianza:
$$\sigma_X = \sqrt{Var(X)}$$

La desviación estándar es una medida de dispersión que indica cuánto se desvían los valores de la variable aleatoria $X$ respecto a su esperanza. Al ser la raíz cuadrada de la varianza, tiene las mismas unidades que la variable aleatoria, lo que facilita su interpretación en comparación con la varianza. Un valor de desviación estándar más alto indica una mayor dispersión de los valores de $X$ alrededor de su esperanza, mientras que un valor más bajo indica una menor dispersión.

La desviación estándar se encuentra en el conjunto de  $\mathbb{R}_0^+$, ya que la varianza es siempre no negativa. Un valor de desviación estándar igual a cero indica que todos los valores de $X$ son iguales a su esperanza, lo que significa que no hay dispersión.
