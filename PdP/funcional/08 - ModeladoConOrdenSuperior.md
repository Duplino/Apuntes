Lazy Evaulation =! Eager Evaluation

Evualacion Diferida


Patrones de listas
(x:y)
x: head
y: tail



foldl funcion semilla lista
:t foldl :: (b -> a -> b) -> b -> [a] -> b

foldl1 funcion lista
:t foldl1 :: (a -> a -> a) -> [a] -> a