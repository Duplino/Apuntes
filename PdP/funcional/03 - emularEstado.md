# Como emular estado en Haskell

En Haskell, el estado se puede emular utilizando funciones puras y estructuras de datos inmutables. A continuación, se presentan algunas técnicas comunes para lograr esto.

Podes tener una instancia y una funcion que retorne una nueva instancia con el estado actualizado. En ese caso, estamos creando una copia de la instancia con el nuevo estado, pero no estamos modificando la instancia original.

```haskell
cambiarEstatura :: Jovit -> Number -> Jovit
cambiarEstatura jovit cambioDeAltura = jovit{estatura = estatura jovit+ cambioDeAltura}
```