# Variables Aleatorias Especiales

- [Variables Aleatorias Especiales](#variables-aleatorias-especiales)
  - [Variable Aleatoria Bernoulli](#variable-aleatoria-bernoulli)
    - [Propiedades](#propiedades)
      - [Esperanza](#esperanza)
      - [Esperanza del cuadrado](#esperanza-del-cuadrado)
      - [Varianza](#varianza)
    - [Ejemplo](#ejemplo)
  - [Variable Aleatoria Binomial](#variable-aleatoria-binomial)
    - [Ejemplo](#ejemplo-1)
    - [Funcion de probabilidad](#funcion-de-probabilidad)
    - [Teorema de Esperanza de Variable Aleatoria Binomial](#teorema-de-esperanza-de-variable-aleatoria-binomial)
      - [Hipotesis](#hipotesis)
      - [Tesis](#tesis)
      - [Demostracion](#demostracion)
    - [Teorema de Varianza de Variable Aleatoria Binomial](#teorema-de-varianza-de-variable-aleatoria-binomial)
      - [Hipotesis](#hipotesis-1)
      - [Tesis](#tesis-1)
      - [Demostracion](#demostracion-1)
    - [Ejercicio](#ejercicio)
      - [Solución](#solución)
  - [Variable hipergeométrica](#variable-hipergeométrica)
    - [Ejemplo](#ejemplo-2)
    - [Esperanza](#esperanza-1)
    - [Varianza](#varianza-1)
  - [Variable Aleatoria Poisson](#variable-aleatoria-poisson)
    - [Esperanza](#esperanza-2)
    - [Esperanza del cuadrado](#esperanza-del-cuadrado-1)
  - [Varianza](#varianza-2)
  - [Variable Aleatoria Uniforme Continua](#variable-aleatoria-uniforme-continua)
    - [Esperanza](#esperanza-3)
    - [Esperanza del cuadrado](#esperanza-del-cuadrado-2)
    - [Varianza](#varianza-3)



## Variable Aleatoria Bernoulli
Es dicotómica con un éxito (1) y un fracaso (0).

| X | P(X) |
|---|------|
| 0 | $1-p$ = q  |
| 1 | $p$    | 

donde $p$ es la probabilidad de éxito y $q = 1-p$ es la probabilidad de fracaso.

$$ X_i \sim Ber(p)$$

### Propiedades

#### Esperanza
La esperanza de una variable aleatoria Bernoulli se calcula como:
$$E(X) = 0 \cdot q + 1 \cdot p = p \Rightarrow E(X) = p$$

#### Esperanza del cuadrado
$$ E(X^2) = 0^2 \cdot q + 1^2 \cdot p = p $$

#### Varianza
La varianza de una variable aleatoria Bernoulli se calcula como:
$$Var(X) = E(X^2) - (E(X))^2 = p - p^2 = p(1-p) = pq$$

### Ejemplo
Arrojo un dado una ze y observo si sale 4.
$X = \begin{cases} 1 & \text{si sale 4} \\ 0 & \text{si no sale 4} \end{cases}$
| X | P(X) |
|---|------|
| 0 | $\frac{5}{6}$  |
| 1 | $\frac{1}{6}$  |

Entonces:
- Esperanza: $E(X) = \frac{1}{6}$
- Varianza: $Var(X) = \frac{1}{6} \cdot \frac{5}{6} = \frac{5}{36}$

## Variable Aleatoria Binomial
Proceso de Bernoulli.
- Se repite $n$ ensayos Bernoulli.
- la probabilidad de exito se mantiene constante en cada ensayo.
- Los ensayos son independientes entre sí.

### Ejemplo
Arrjoamos un dado 3 veces. 

$X$ = número de veces que sale 4.

$$ X \sim B(n = 3, p = \frac{1}{6})$$

| X | P(X) |
|---|------|
| 0 | $\left(\frac{5}{6}\right)^3$  |
| 1 | $3 \cdot \frac{1}{6} \cdot \left(\frac{5}{6}\right)^2$  |
| 2 | $3 \cdot \left(\frac{1}{6}\right)^2 \cdot \frac{5}{6}$  |
| 3 | $\left(\frac{1}{6}\right)^3$  |

Entonces:
$$ q = 1-p = \frac{5}{6} $$
$$ p = \frac{1}{6} $$
$$ \therefore q^3+3pq^2+3p^2q+p^3 = (p+q)^3 = 1 $$

### Funcion de probabilidad
$$ P (X= x) = \binom{n}{x} p^x q^{n-x} , \quad \text{para } x = 0,1,2,...,n $$

Donde $n$ es el numero de ensayos y $x$ es el numero de exitos.

### Teorema de Esperanza de Variable Aleatoria Binomial
#### Hipotesis
$$ X \sim B_i(n,p) $$
$$ X = \sum_{i=1}^{n} X_i $$
#### Tesis
$$ E(X) = np $$

#### Demostracion
$$ X = \sum_{i=1}^{n} X_i $$ 
por hipotesis
$$ E(X) = E\left(\sum_{i=1}^{n} X_i\right) $$ 
Aplicamos esperanza a ambos lados
$$ E(X) = \sum_{i=1}^{n} E(X_i) $$
Por lineralidad de la esperanza
$$ E(X) = \sum_{i=1}^{n} p $$
$$ E(X) = np $$


### Teorema de Varianza de Variable Aleatoria Binomial
#### Hipotesis
Las mismas que el [teorema de esperanza](#teorema-de-esperanza-de-variable-aleatoria-binomial).
#### Tesis
$$ Var(X) = npq $$
#### Demostracion
$$ X = \sum_{i=1}^{n} X_i $$
$$ Var(X) = Var\left(\sum_{i=1}^{n} X_i\right) $$
$$ Var(X) = \sum_{i=1}^{n} Var(X_i) $$
$$ Var(X) = \sum_{i=1}^{n} pq $$
$$ Var(X) = npq $$

> [!WARNING] Suma de varianzas
> Las varianza de una suma no siempre es la suma de las varianzas. Aqui se puede pues los ensayos son independientes entre si, segun la hipotesis de Bernoulli.

> [!TIP] Reconocer un ejercicio de variable aleatoria binomial
> Los ensayos son independientes y la probabilidad de exito es contante.

### Ejercicio 
La compañía de aviación GranJet ha determinado mediante un estudio estadístico que el 4 % de los pasajeros que reservan un viaje Buenos Aires - Misiones no se presentan a tomar el vuelo. Un día de mucha demanda de pasajes la empresa decide vender 72 pasajes de un vuelo con capacidad para 70 pasajeros. ¿Cuál es la probabilidad de que puedan viajar todos los pasajeros que se presentan a tomar el vuelo?

#### Solución
Definimos la variable aleatoria $X$ como el número de pasajeros que no se presentan a tomar el vuelo. Entonces, $X$ sigue una distribución binomial con parámetros $n = 72$ y $p = 0.04$.

Queremos calcular la probabilidad de que todos los pasajeros que se presentan puedan viajar, lo que significa que el número de pasajeros que no se presentan debe ser menor o igual a 2 (ya que el vuelo tiene capacidad para 70 pasajeros). Por lo tanto, necesitamos calcular $P(X \leq 2)$.

Calculamos esta probabilidad sumando las probabilidades de que $X$ tome los valores 0, 1 y 2:
$$ P(X \leq 2) = P(X = 0) + P(X = 1) + P(X = 2) $$

Calculamos cada una de estas probabilidades utilizando la fórmula de la distribución binomial:
$$ P(X = k) = \binom{n}{k} p^k (1-p)^{n-k} $$


## Variable hipergeométrica
$$ X \sim HG(n, N, M) $$
$$ P(X = x) = \frac{\binom{M}{x} \binom{N-M}{n-x}}{\binom{N}{n}} $$


Donde:
- $M$: los elementos elegidos a favor de una categoria.
- $N$: total de elementos.
- $n$: elementos que se extraen.

> [!WARNING] Diferencia entre binomial e hipergeometrica
> Aca la probabilidad de exito no es constante, pues no se reemplaza el elemento extraido. En cambio, en la binomial si se reemplaza el elemento extraido, por lo que la probabilidad de exito se mantiene constante.

### Ejemplo
$X$ es el numero de bolillas rojas.

Se tiene una urna con 4 bolillas rojas y 3 bolillas negras. Se extraen 2 bolillas.

Entonces, definimos:
- $M$ = 4 (bolillas rojas)
- $N$ = 7 (total de bolillas)
- $n$ = 2 (bolillas que se extraen)

Podemos entonces calcular P(X= 2) como:
$$ P(X = 2) = \frac{\binom{4}{2} \binom{3}{0}}{\binom{7}{2}} = \frac{6 \cdot 1}{21} = \frac{6}{21} = \frac{2}{7} $$


### Esperanza
$$ E(X) = n \cdot \frac{M}{N} $$
### Varianza
$$ Var(X) = n \cdot \frac{M}{N} \cdot \left(1 - \frac{M}{N}\right) \cdot \frac{N-n}{N-1} $$

## Variable Aleatoria Poisson
Las ocurrencias se cuentan en un espacio continuo, como el tiempo o la distancia. Pero la variable aleatoria sigue siendo discreta, pues se cuentan ocurrencias.

Por ejemplo:
- $X$ = Numero de fallas en 1000 metros de cable.
- $X$ = numero de bacterias en 100ml de solucion.
- $X$ = numero de llamadas telefonicas en 24hs.

$$ P(X = x) = \frac{\mu^x e^{-\mu}}{x!} \quad X \in \mathbb{N}_0 $$

> [!NOTE] Probability Calculator
> En vez de $\mu$ se puede usar $\lambda$.

Se cumple: $E(X) = Var(X) = \mu$.

$\mu = \lambda \cdot t$ donde $\lambda$ es la intendisdad por unidad de continuo y $t$ es el continuo.



### Esperanza
$$ E(X) = \Sigma_{x=0}^{\infty} x \cdot P(X = x) = \Sigma_{x=0}^{\infty} x \cdot \frac{\mu^x e^{-\mu}}{x!} $$

Como el primer termino siempre es 0, podemos empezar la sumatoria desde 1:
$$ E(X) = \Sigma_{x=1}^{\infty} x \cdot \frac{\mu^x e^{-\mu}}{x!} $$

Simplificando el termino $x$ con el factorial, tenemos:
$$ E(X) = \Sigma_{x=1}^{\infty} \frac{\mu^x e^{-\mu}}{(x-1)!} $$

Hacemos el cambio de variable $j = x-1$, entonces $x = j+1$ y la sumatoria queda:
$$ E(X) = \mu \Sigma_{j=0}^{\infty} \frac{\mu^{j} e^{-\mu}}{j!} $$

Como la sumatoria de todas las probabilidades es igual a 1, entonces:
$$ E(X) = \mu $$

### Esperanza del cuadrado
$$ E(X^2) = \Sigma_{x=0}^{\infty} x^2 \cdot \frac{\mu^x e^{-\mu}}{x!} $$
Hacemos el mismo cambio de variable que en la esperanza, entonces:
$$ E(X^2) = \Sigma_{x=1}^{\infty} x^2 \cdot \frac{\mu^x e^{-\mu}}{x!} $$
$$ E(X^2) = \Sigma_{x=1}^{\infty} \frac{\mu^x e^{-\mu}}{(x-1)!} + \Sigma_{x=1}^{\infty} \frac{\mu^x e^{-\mu}}{(x-2)!} $$

 Tomamos el primer termino y hacemos el cambio de variable $j = x-1$, entonces $x = j+1$ y del segundo termino hacemos el cambio de variable $k = x-2$, entonces $x = k+2$. Entonces, la sumatoria queda:
 
$$ E(X^2) = \mu \Sigma_{j=0}^{\infty} \frac{\mu^{j} e^{-\mu}}{j!} + \mu^2 \Sigma_{k=0}^{\infty} \frac{\mu^{k} e^{-\mu}}{k!} $$

$$ E(X^2) = \mu + \mu^2 $$

## Varianza
$$ Var(X) = E(X^2) - (E(X))^2 = \mu + \mu^2 - \mu^2 = \mu $$



## Variable Aleatoria Uniforme Continua
$$ X \sim U[a,b] $$

$$ f(x) = \begin{cases} \frac{1}{b-a} & \text{si } a \leq x \leq b \\ 0 & \text{en otro caso} \end{cases} $$
### Esperanza
$$ E(X) = \int_{-\infty}^{\infty} x f(x) dx = \int_{a}^{b} x \cdot \frac{1}{b-a} dx = \frac{1}{b-a} \int_{a}^{b} x dx =$$

$$ = \frac{1}{b-a} \left[ \frac{x^2}{2} \right]_{a}^{b} = \frac{1}{b-a} \cdot \frac{b^2 - a^2}{2} = \frac{b+a}{2} $$


### Esperanza del cuadrado
$$ E(X^2) = \int_{-\infty}^{\infty} x^2 f(x) dx = \int_{a}^{b} x^2 \cdot \frac{1}{b-a} dx = \frac{1}{b-a} \int_{a}^{b} x^2 dx $$
$$= \frac{1}{b-a} \left[ \frac{x^3}{3} \right]_{a}^{b} = \frac{1}{b-a} \cdot \frac{b^3 - a^3}{3} = \frac{b^2 + ab + a^2}{3} $$

### Varianza
$$ Var(X) = E(X^2) - (E(X))^2 = \frac{b^2 + ab + a^2}{3} - \left(\frac{b+a}{2}\right)^2 = \frac{(b-a)^2}{12} $$
