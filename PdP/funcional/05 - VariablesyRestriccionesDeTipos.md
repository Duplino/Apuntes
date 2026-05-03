# Variables y Restricciones de Tipos

## Tipo de dato

Un tipo tiene valores y una serie de operaciones relacionadas.

|Tipo | Valores | Operaciones |
|-----|---------|-------------|
| Numeros | `0, 1, 2, ...` | `+`, `-`, `*`, `/` |
| Booleanos | `True`, `False` | `&&`, `\|\|`, `not` |
| Strings | `"Hola"`, `"Mundo"` | `(++)`, head, length, reverse |
| Funcion | not, even, odd | Aplicacion, composicion |

> [!NOTE] 
> Las funciones no son comparables por igualdad, no se pueden ordenar, no se pueden mostrar como texto, etc.

## Inferencia de tipos

Haskell puede inferir el tipo de una función o expresión basándose en su definición. Por ejemplo, si definimos la función identidad:

```haskell
identidad x = x
```
En este caso, `identidad` es una función que toma un argumento `x` y lo devuelve sin modificarlo. Haskell puede inferir que el tipo de `x` es cualquier tipo, por lo que la función `identidad` tiene el tipo:

```haskell
identidad :: a -> a
```

En este caso `a` es una **variable de tipo**.

`:t` es un comando en GHCi que se utiliza para mostrar el tipo de una expresión o función. Por ejemplo:

```haskell
:t identidad
> identidad :: a -> a
``` 

Esto aplica tambien con varios parametros:

```haskell
quedateConElPrimero x y = x

> :t quedateConElPrimero
> quedateConElPrimero :: a -> b -> a
```
> [!NOTE] 
> `a` y `b` pueden ser iguales tambien.

## Restricciones de tipo o Typeclass

Una forma de agrupar tipos es a través de las typeclasses. Una typeclass es una colección de tipos que comparten ciertas operaciones. 

Agrupamos tipos, definimos interfaces y operaciones comunes a esos tipos.

Por ejemplo si hacemos una funcion between:

```haskell
between x y z = x <= y && y <= z

> :t between
> between :: (Ord a) => a -> a -> a -> Bool
```
En este caso, el tipo de x, y, z puede ser cualquier tipo, siempre y cuando sean Ordenables y el mismo tipo. 

> [!NOTE] Genericidad adecuada
> En Haskell, es importante escribir funciones de manera genérica para aprovechar al máximo la inferencia de tipos y las typeclasses. Esto permite que nuestras funciones sean más flexibles y reutilizables.
> 
> `between :: a -> a -> a -> Bool` es demasiado general, ya que no especifica ninguna restricción sobre el tipo de los argumentos. Esto significa que la función no puede realizar ninguna operación específica sobre los argumentos, como compararlos.

### Typeclasses 

| Tipo | Operaciones | Características |
|------|-------------|-----------------|
| `Eq` | `==`, `/=` | Implica que se pueden comparar por igualdad |
| `Ord` | `<=`, `<`, `>`, `>=` | Implica que se pueden ordenar. |
| `Show` | `show` | Es una función que permite convertir un valor a una cadena de texto. |




> [!NOTE] 
> El hecho de que los `Ord` tengan `<=` y `>=` implica que también tienen `==` y `/=`, por lo que `Ord` es una superclase de `Eq`. Esto significa que cualquier tipo que sea una instancia de `Ord` también es automáticamente una instancia de `Eq`. 


### Clases derivadas
Haskell permite derivar automáticamente instancias de ciertas typeclasses para tipos de datos personalizados. Esto se hace utilizando la palabra clave `deriving` al definir un nuevo tipo de dato. Por ejemplo:

```haskell
data Color = Rojo | Verde | Azul deriving (Eq, Show)
```
Esto permite que `Color` tenga automáticamente instancias de `Eq` y `Show`, lo que significa que podemos comparar colores por igualdad y convertirlos a cadenas de texto sin tener que escribir código adicional para estas operaciones.

