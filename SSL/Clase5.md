token: palabra -> coleccion de caracteres

Un lenguaje es un conjunto de cadenas o plabras sobre un determinado alfabeto
$$ L \subseteq \Sigma^* $$


## Definicion de conjuntos
### Extension
### Comprension
#### Frase Explicativa
#### Formula sobre las operaciones sobre cadenas
#### Constructivo
Una gramatica es un caso particular de un metodo constructuvo.




## Gramatica
Es una 4-upla

$$ G = (V_N, V_T, P, S) \quad o \quad G = (V_N, \Sigma, P, S) $$

$V_N$: Es el conjunto de NO terminales. Es decir, palabras que pueden estar sin finalizar.

$V_T$: Vocaublario terminal. Es el alfabeto del lenguaje. Pertenecen al lenguaje.

$$ V_N \cap V_T = \emptyset $$
$$ V = V_N \cup V_T $$
$$ S \in V_N $$
(Axioma o simbolo inicial)


P es el conjunto de producciones o reglas de produccion. Es un conjunto de pares ordenados de la forma $A \to \alpha$ donde $A \in V_N$ y $\alpha \in V^*$


'[S-Z]: no terminal

'[a-s]: terminal


## Producciones

P es un conjunto de pares ordenados que denotamos como
$$ \alpha \to \beta $$
(\alfa produce \beta)


