# Orden Superior
Son funciones de orden superior aquellas que pueden tomar otras funciones como argumentos o devolver funciones como resultado. Esto es una característica fundamental de Haskell y permite una gran flexibilidad en la programación.

## all

```haskell
all :: (a -> Bool) -> [a] -> Bool
```
La función `all` toma una función que devuelve un booleano y una lista, y devuelve `True` si la función devuelve `True` para todos los elementos de la lista.

## any

```haskell
any :: (a -> Bool) -> [a] -> Bool
```
La función `any` toma una función que devuelve un booleano y una lista, y devuelve `True` si la función devuelve `True` para al menos un elemento de la lista.

## map 

```haskell
map :: (a -> b) -> [a] -> [b]
```
La función `map` toma una función que transforma un tipo `a` en un tipo `b` y una lista de elementos de tipo `a`, y devuelve una lista de elementos de tipo `b` aplicando la función a cada elemento de la lista.

Tiene algo que ver con transformaciones lineales

## filter

```haskell
filter :: (a -> Bool) -> [a] -> [a]
```
La función `filter` toma una función que devuelve un booleano y una lista, y devuelve una lista que contiene solo los elementos de la lista original para los cuales la función devuelve `True`.

## sum

```haskell
sum :: Num a => [a] -> a
```
La función `sum` toma una lista de números y devuelve la suma de esos números.
