Clase pasada:
- Intro a Haskell
- Stateless programming
- Pure functions (definicion matematica)

"que es tal cosa"
```haskell
doble :: Int -> Int
doble x = 2 * x 
   -- QUE ES el doble de x. No que hacer
```

- [Estructuras de datos](#estructuras-de-datos)
  - [Listas](#listas)
    - [Operaciones con listas](#operaciones-con-listas)
      - [elem](#elem)
      - [reverse](#reverse)
      - [length](#length)
      - [(++)](#)
      - [(:)](#-1)
      - [drop](#drop)
      - [take](#take)
      - [head](#head)
      - [last](#last)
      - [tail](#tail)
      - [init](#init)
  - [Tuplas](#tuplas)
    - [Ejemplo](#ejemplo)
    - [Operaciones con tuplas](#operaciones-con-tuplas)
      - [`fst`](#fst)
      - [`snd`](#snd)
      - [Para mas elementos](#para-mas-elementos)
  - [Type Alias](#type-alias)
    - [Ejemplo](#ejemplo-1)
    - [\_ (Guión bajo)](#_-guión-bajo)
  - [data](#data)
    - ["Enum"](#enum)
    - [Record Syntax](#record-syntax)



# Estructuras de datos
## Listas
```haskell
-- Listas de enteros
[1, 2, 3, 4, 5]
-- Listas de caracteres
['a', 'b', 'c']
-- String
"Hola, mundo!" -- Es una lista de caracteres
```
> Las listas son estructuras de datos que contienen el mismo tipo de dato.

> [!WARNING]
> ```haskell
> [1, 2, 3, True]
> ```
> Esto no es una lista válida, ya que contiene diferentes tipos de datos (Int y Bool).
>
> ```haskell
> [[1, 2], [3, 4]]
> ```
> El tipo de dato es **lista de enteros**. No existe **lista**. Entonces no pudeo mezclar tipos de listas.

### Operaciones con listas

#### elem
Devuelve `True` si el elemento está en la lista, y `False` en caso contrario.

```haskell
elem 3 [1, 2, 3, 4] -- True
elem 5 [1, 2, 3, 4] -- False
```
#### reverse 
Devuelve una nueva lista con los elementos en orden inverso.
```haskell 
reverse [1, 2, 3] -- [3, 2, 1]
```
#### length
Devuelve el número de elementos en la lista.
```haskell
length [1, 2, 3] -- 3
```
#### (++)
Concatena dos listas.
```haskell
[1, 2] ++ [3, 4] -- [1, 2, 3, 4]
```
#### (:)
Devuelve una nueva lista con el elemento agregado al inicio de la lista.
```haskell
1 : [2, 3] -- [1, 2, 3]
```

#### drop
Devuelve una nueva lista con los primeros n elementos eliminados.
```haskell
drop 2 [1, 2, 3, 4] -- [3, 4]
```

#### take
Devuelve una nueva lista con los primeros n elementos de la lista.
```haskell
take 2 [1, 2, 3, 4] -- [1, 2]
```

#### head
Devuelve el primer elemento de la lista.
```haskell
head [1, 2, 3] -- 1
```
#### last
Devuelve el último elemento de la lista.
```haskell
last [1, 2, 3] -- 3
```

#### tail
Devuelve una nueva lista con todos los elementos excepto el primero.
```haskell
tail [1, 2, 3] -- [2, 3]
```
#### init
Devuelve una nueva lista con todos los elementos excepto el último.
```haskell
init [1, 2, 3] -- [1, 2]
```

## Tuplas
Una tupla es una estructura de datos que puede contener elementos de diferentes tipos. Se define utilizando paréntesis y comas para separar los elementos.
```haskell
-- tupla de tres elementos, representa una fecha
(2024, 6, 15) -- (año, mes, día)
-- tupla que representa una persona
("Alice", 30) -- (nombre, edad)
```
>[!NOTE]
> Las tuplas tienen cantidad fija de elementos.

### Ejemplo
Ver si una persona es mayor a 18
```haskell
pepita :: (String, Int)
pepita = ("Pepita", 20)

edad :: (String, Int) -> Bool
edad persona = snd persona

esMayorDeEdad :: (String, Int) -> Bool
esMayorDeEdad persona = edad persona > 18
```

### Operaciones con tuplas
#### `fst`
Devuelve el primer elemento de la tupla.
#### `snd`
Devuelve el segundo elemento de la tupla.
>[!WARNING]
> `fst` y `snd` solo funcionan con tuplas de dos elementos. No se pueden usar con tuplas de más de dos elementos.

#### Para mas elementos
PATTERN MATCHING
```haskell
nombre :: (String, Number, Number) -> String
nombre (nombre, edad, altura) = nombre
```
## Type Alias
Un type alias es una forma de dar un nombre a un tipo de dato. Se define utilizando la palabra clave `type`.
```haskell
type persona = (String, Number)

-- Entonces puedo hacer
pepita :: persona
pepita = ("Pepita", 20)

edad :: persona -> Number
edad persona = snd persona

esMayorDeEdad :: persona -> Bool
esMayorDeEdad persona = edad persona > 18
```
>[!TIP] 
> Es util para mejorar la legibilidad del código, ya que permite dar nombres más descriptivos a los tipos de datos. Saca ambiguedad de tipos. 
> Ademas, si el tipo de dato cambia, es más fácil cambiar el type alias que cambiar todas las ocurrencias del tipo de dato en el código.

### Ejemplo
Calcular el costo de entrada de una persona, que es la edad multiplicada por la longitud de su nombre menos su altura.

```haskell
type alias Persona = (String, Number, Number) -- (nombre, edad, altura)

altura :: Persona -> Number
altura (_, _, altura) = altura

edad :: Persona -> Number
edad (_, edad, _) = edad

nombre :: Persona -> String
nombre (nombre, _, _) = nombre

costoEntrada :: Persona -> Number
costoEntrada persona = (edad persona) * (length (nombre persona)) - (altura persona)
``` 
### _ (Guión bajo)
Puede signifcar *privado* o *ignorado*. Es una forma de decir "no me importa este valor". Se utiliza en pattern matching cuando no necesitamos usar un valor específico.

## data
`data` es una forma de definir un nuevo tipo de dato. Se utiliza para crear tipos de datos personalizados que pueden tener diferentes constructores.

```haskell
data Jovit = UnJovit{
    nombre :: String,
    estatura :: Number,
    fuerza :: Number,
    esDeLaComarca :: Bool
} deriving Show -- Esto es para que se pueda imprimir el jovit en la consola

bilbo :: Jovit
bilbo = UnJovit {
    nombre = "Bilbo",
    estatura = 125,
    fuerza = 20,
    esDeLaComarca = True
}

bilbo2 = UnJovit "Bilbo" 125 20 True
```
### "Enum"
```haskell
data Color = Rojo | Verde | Azul deriving Show 
colorFavorito :: Color
colorFavorito = Verde
```
Permite definir un tipo de dato con un conjunto finito de valores posibles. Es útil para representar categorías o estados específicos.

> [!CAUTION]
> En dos `datas` distintos no se puede usar el mismo nombre de atributo. 

### Record Syntax
La sintaxis de registro es una forma de definir un nuevo tipo de dato con campos nombrados. Esto permite acceder a los campos por su nombre en lugar de por su posición.

