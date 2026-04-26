# Probabilidad

## Sucesos
- **Suceso**: Es un evento o resultado específico dentro de un experimento aleatorio.
  
Operaciones con sucesos:
- **Unión**: $A \cup B$ (suceso que ocurre si ocurre A o B).
- **Intersección**: $A \cap B$ (suceso que ocurre si ocurren A y B).
- **Complemento**: $\overline{A}$ (suceso que ocurre si no ocurre A).
- **Neutronidad**: $A \cup \overline{A} = E$ (donde E es el espacio muestral).
- **Absorción**: $A \cup E = E$ y $A \cap E = A$. 
- **Conunto vacío**: $A \cup \emptyset = A$ y $A \cap \emptyset = \emptyset$.
- **De Morgan**: $\overline{(A \cup B)} = \overline{A} \cap \overline{B}$ y $\overline{(A \cap B)} = \overline{A} \cup \overline{B}$.

## Cálculo de probabilidad
### Definicion clásica de probabilidad

$$ P(A) = \frac{\text{Número de casos favorables en A}}{\text{Número total de casos posibles}} $$

> [!NOTE]
> Esta definición asume que todos los casos posibles son igualmente probables y los elementos son finitos.

### Probabilidad frecuentista

$$ f_{r}(A) = \frac{\text{Número de veces que A ocurre}}{\text{Número total de ensayos}} $$ 
Sea $f_{r}(A)$ la frecuencia relativa de A.

- $f_{r}(A) >= 0$
- $f_{r}(E) = 1$
- $f_{r}(A \cup B) = f_{r}(A) + f_{r}(B)$ (si A y B son disjuntos)
- $lim_{n \to \infty} f_{r}(A) = P(A)$

### Definicion axiomatica de probabildiad
Sea $P$ una función que asigna a cada suceso A un número real entre 0 y uno $P(A)$, tal que:
1. $P(A) >= 0$ para todo suceso A.
2. $P(E) = 1$ donde E es el espacio muestral.
3. Si A y B son sucesos disjuntos, entonces $P(A \cup B) = P(A) + P(B)$.

Entonces se comprueban los siguientes teoremas:
#### $P(\overline{A}) = 1 - P(A)$
Demostración:
$$ P(E) = P(A \cup \overline{A}) = P(A) + P(\overline{A}) \Rightarrow P(\overline{A}) = 1 - P(A) $$

#### $A \subseteq B \Rightarrow P(A) \leq P(B)$
Demostración:
$$ P(B) = P(A \cup (B \cap \overline{A})) = P(A) + P(B \cap \overline{A}) \Rightarrow P(A) \leq P(B) $$ 

### Probaiblidad de la union de sucesos
$$ P(A \cup B) = P(A) + P(B) - P(A \cap B) $$
Demostración:
$$ P(A \cup B) = P(A) + P(B \cap \overline{A}) $$

Pensemos: 
$$ B = B \cap E = B \cap (A \cup \overline{A}) = (B \cap A) \cup (B \cap \overline{A}) $$
Aplicando probabilidad queda la defincion.

### Principio de la multiplicación

#### Permutaciones
Todos los ordenes que pueden formarse con n elementos distintos es $n!$.
#### Variaciones simples
El número de formas de elegir k elementos de un conjunto de n elementos, donde el orden importa, es $V(n, k) = \frac{n!}{(n-k)!}$.
#### Combinaciones simples
El número de formas de elegir k elementos de un conjunto de n elementos, donde el orden no importa, es $C(n, k) = \frac{n!}{k!(n-k)!}$.

### Probabilidad condicional
$$ P(A|B) = \frac{P(A \cap B)}{P(B)} $$
Entonces se cumple:
$$ P(A \cap B) = P(B)P(A|B) $$ 

$$ P(A \cap B) = P(A)P(B|A) $$

### Teorema de la probabilidad total
Si $B_1, B_2, ..., B_n$ son sucesos disjuntos que forman una partición del espacio muestral E, entonces para cualquier suceso A se cumple:
$$ P(A) = \sum_{i=1}^{n} P(B_i)P(A|B_i) $$

### Teorema de Bayes
Si $B_1, B_2, ..., B_n$ son sucesos disjuntos que forman una partición del espacio muestral E, y A es un suceso tal que $P(A) > 0$, entonces para cualquier i se cumple:
$$ P(B_i|A) = \frac{P(B_i)P(A|B_i)}{\sum_{j=1}^{n} P(B_j)P(A|B_j)} $$
