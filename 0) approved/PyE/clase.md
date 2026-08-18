- [Suma de Variables Aleatorias Normales Independientes](#suma-de-variables-aleatorias-normales-independientes)
  - [Suma de n Variables Aleatorias Normales Independientes](#suma-de-n-variables-aleatorias-normales-independientes)
- [Teorema Central del Límite](#teorema-central-del-límite)
- [Definiciones](#definiciones)
  - [Población](#población)
  - [Muestra](#muestra)
  - [Parámetro](#parámetro)
  - [Estimador](#estimador)
- [Propiedades de los Estimadores](#propiedades-de-los-estimadores)
  - [Insesgadez](#insesgadez)
    - [Demostración de que $\\bar{X}$ es un estimador insesgado de $\\mu$:](#demostración-de-que-barx-es-un-estimador-insesgado-de-mu)
  - [Eficiencia relativa](#eficiencia-relativa)
  - [Error cuadrático medio](#error-cuadrático-medio)


## Suma de Variables Aleatorias Normales Independientes

Sea $X \sim N(\mu_x, \sigma_x)$ e $Y \sim N(\mu_y, \sigma_y)$, entonces la suma de estas variables aleatorias, $Z = X + Y$, también sigue una distribución normal. La media y la varianza de $Z$ se pueden calcular de la siguiente manera:
- La media de $Z$ es la suma de las medias de $X$ e $Y$:
$$\mu_z = \mu_x + \mu_y$$
- La varianza de $Z$ es la suma de las varianzas de $X e $Y$ (ya que son independientes):
$$\sigma_z = \sqrt{\sigma_x^2 + \sigma_y^2}$$

### Suma de n Variables Aleatorias Normales Independientes

Sean: 
- $X_1 \sim N(\mu_1, \sigma_1)$
- $X_2 \sim N(\mu_2, \sigma_2)$
- $\ldots$
- $X_n \sim N(\mu_n, \sigma_n)$

Entonces, la suma de estas variables aleatorias, $Z = X_1 + X_2 + \ldots + X_n$, también sigue una distribución normal. La media y la varianza de $Z$ se pueden calcular de la siguiente manera:
- La media de $Z$ es la suma de las medias de todas las variables aleatorias:
$\mu_z = \mu_1 + \mu_2 + \ldots + \mu_n$
- La varianza de $Z$ es la suma de las varianzas de todas las variables aleatorias (ya que son independientes):
$\sigma_z = \sqrt{\sigma_1^2 + \sigma_2^2 + \ldots + \sigma_n^2}$

> [!TIP] En dificil
> $$ \sum_{i=1}^{n} X_i \sim N\left( \sum_{i=1}^{n} \mu_i, \sqrt{\sum_{i=1}^{n} \sigma_i^2} \right) $$


> [!NOTE] Si son iguales todas las X
> $$ \forall X_i \sim N(\mu, \sigma) $$
> $$ \sum_{i=1}^{n} X_i \sim N\left( n\mu, \sqrt{n}\sigma \right) $$  

> [!NOTE] Para el promedio de X
> $$ \bar{X} = \frac{1}{n} \sum_{i=1}^{n} X_i \sim N\left( \mu, \frac{\sigma}{\sqrt{n}} \right) $$


## Teorema Central del Límite

Sean $X_1, X_2, \ldots, X_n$ variables aleatorias independientes con la misma distribucion, con esperanza y varianza conocidas y finitas.

Entonces,
$$\bar{X} \xrightarrow{D} N\left( \mu, \frac{\sigma}{\sqrt{n}} \right)$$

cuando $n \to \infty$, el promedio se acerca a la distribucion normal.

> [!NOTE] Nota práctica
> En la practica, si $n > 30$ vamos a trabajar con la normal, aunque no se cumpla el teorema central del limite, ya que es una aproximacion bastante buena.


## Definiciones
### Población
Son todos los idnividuos en estudio.

### Muestra
Subconjunto de elementos en la poblacion.

$X_1, X_2, \ldots, X_n$ es una sucesion de variables aleatorias.

### Parámetro
Es una constante poblacional.

### Estimador
Es una funcion de la muestra alteatoria

$\hat{\theta}$ estima al parámetro $\theta$.

| Parámetro | Estimador |
| :---: | :---: |
| $\mu$ <br>Media Poblacional | $\bar{X}$<br>Media Muestral |
| $\sigma^2$<br> Varianza Poblacional | $S^2$<br> Varianza Muestral |
| $p$<br> Proporcion Poblacional | $\hat{p}$<br> Proporcion Muestral |



$\bar{X}$: Sumar todos los valores de la muestra y dividir por el número de elementos en la muestra.
$$\bar{X} = \frac{ \sum_{i=1}^{n} X_i}{n}$$

$S^2$: Sumar el cuadrado de la diferencia entre cada valor de la muestra y la media muestral, y dividir por el número de elementos en la muestra menos uno.
$$S^2 = \frac{ \sum_{i=1}^{n} (X_i - \bar{X})^2}{n-1}$$

$\hat{p}$: Es la p de la distribucion binomial, es decir, el numero de exito entre el numero de ensayos.
$$\hat{p} = \frac{\text{X}}{n}$$


## Propiedades de los Estimadores
### Insesgadez
Un estimador $\hat{\theta}$ es insesgado si y solo si su valor esperado es igual al parámetro que estima, es decir:
$$E(\hat{\theta}) = \theta. $$
o si el sesgo es cero:
$$\text{B}(\hat{\theta}) = E(\hat{\theta}) - \theta = 0. $$

> [!NOTE] Utilidad
> Si es insesgado, entonces el valor esperado del estimador es igual al parámetro que se está estimando. Esto significa que, en promedio, el estimador no sobreestima ni subestima el valor del parámetro.

#### Demostración de que $\bar{X}$ es un estimador insesgado de $\mu$:

$$ E(\bar{X}) = E(\frac{\sum_{i=1}^{n} X_i}{n}) = \frac{1}{n} \sum_{i=1}^{n} E(X_i) = \frac{1}{n} \sum_{i=1}^{n} \mu = \mu. $$

Entonces $\bar{X}$ es un estimador insesgado de $\mu$.

### Eficiencia relativa
Sean $\hat{\theta}_1$ y $\hat{\theta}_2$ dos estimadores insesgados de un mismo parámetro $\theta$. 

$\hat{\theta}_1$ es más eficiente que otro estimador $\hat{\theta}_2$ si su varianza es menor, es decir:
$$\text{Var}(\hat{\theta}_1) < \text{Var}(\hat{\theta}_2).$$

### Error cuadrático medio
$$ ECM(\hat{\theta}) = E[(\hat{\theta} - \theta)^2] = \text{Var}(\hat{\theta}) + [\text{B}(\hat{\theta})]^2. $$

> [!WARNING] Criterio
> A la hora de elegir entre dos estimadores, se prefiere el que tenga el menor error cuadrático medio, y el que tenga la mayor eficiencia relativa.
