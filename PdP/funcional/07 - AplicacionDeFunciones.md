# Formas de aplicar funciones
- [Formas de aplicar funciones](#formas-de-aplicar-funciones)
  - [Aplicación Parcial de una función](#aplicación-parcial-de-una-función)
    - [Currficación](#currficación)
  - [Composicion de funciones](#composicion-de-funciones)
    - [Tipo del operador (.)](#tipo-del-operador-)
  - [Funcion Lambda](#funcion-lambda)
  - [Aplicacion de lista de funciones a un elemento](#aplicacion-de-lista-de-funciones-a-un-elemento)
    - [Precedencia](#precedencia)


## Aplicación Parcial de una función

Pasarle menos parametros de los que espera la funcion.

```haskell
suma :: Int -> Int -> Int
suma x y = x + y

-- Aplicacion parcial
> :t (suma 5)
> (suma 5) :: Int -> Int
```

Lo que hice es pasarle un unico parametro y eso me da una funcion que toma un parametro menos. Es decir, `suma 5` es una funcion que toma un `Int` y devuelve un `Int`, y lo que hace es sumar 5 a ese `Int`.

### Currficación
En Haskell decimos que todas las funcciones estan currificadas, lo que significa que todas las funciones toman un solo parametro y devuelven una funcion que toma el siguiente parametro, y asi sucesivamente.

Entonces por ejemplo

```haskell
suma :: Int -> Int -> Int
suma x y = x + y

-- es en realidad

suma :: Int -> (Int -> Int)
-- Es una funcion que va de INT a una funcion que va de INT a INT

funcionLoca :: a -> (b -> (c -> (a -> b)))
```

> Viene de el matematico Haskell Curry, y es una tecnica de transformacion de funciones que permite convertir una funcion que toma varios parametros en una funcion que toma un solo parametro y devuelve otra funcion que toma el siguiente parametro, y asi sucesivamente.



## Composicion de funciones
La composicion de funciones es una tecnica que permite combinar dos funciones para crear una nueva funcion. En Haskell, la composicion de funciones se hace con el operador `.`

```haskell
-- Verdadero si el nombre del destinatario tiene una cantidad par de letras
traeSuerte :: Paquete -> Bool
traeSuerte = even.length.destinatario
```

> [!NOTE]
> Se pueden componer funciones como
> ```haskell
> test :: Int -> Bool
> test = (<50).sum 5

### Tipo del operador (.)
```
> :t (.)
> (.) :: (b -> c) -> (a -> b) -> a -> c
```



## Funcion Lambda
Una funcion lambda es una funcion anonima, es decir, una funcion que no tiene un nombre. En Haskell, las funciones lambda se definen con la sintaxis `\parametros -> cuerpo`

```haskell
-- Funcion normal
suma :: Int -> Int -> Int
suma x y = x + y
-- Funcion lambda
sumaLambda :: Int -> Int -> Int
sumaLambda = \x y -> x + y

-- lambdas dentro de filter
> filter (\x -> x > 5) [1,2,3,4,5,6,7,8,9]
```


## Aplicacion de lista de funciones a un elemento
```haskell
map ($ elemento) [funcion1, funcion2, funcion3]
-- Es equivalente a
[funcion1 elemento, funcion2 elemento, funcion3 elemento]
```

> [!NOTE]
> El operador `$` es un operador de aplicacion de funciones, que tiene la menor precedencia de todos los operadores, lo que significa que todo lo que esta a la derecha del operador se evalua primero, y luego se aplica la funcion a la izquierda del operador. Es decir, `f $ x` es equivalente a `f x`, pero `f $ g x` es equivalente a `f (g x)`, lo que permite evitar el uso de parentesis.

### Precedencia
```haskell
> even.doble 5 
```
 No funciona porque el operador (.) tiene menor precedencia que la aplicacion de funciones, entonces se interpreta como (even.doble) 5, lo cual no tiene sentido porque even.doble no es una funcion.

```
> (even.doble) 5
> even.doble $ 5

```
Son equivalentes y funcionan porque el operador (.) se evalua primero, lo que da como resultado una funcion que es la composicion de even y doble, y luego se aplica esa funcion al 5.