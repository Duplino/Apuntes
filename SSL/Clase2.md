> [!NOTE] Arreglos y punteros en C
> Ver apunte en Aulas Virtuales

Alfabeto: utf-8, ascii?

## Mutabilidad
Si se puede cambiar o no.

Java tiene cadenas inmutables.

metodos estaticos: 

metodos de los objetos
```c++
Objeto.metodo(); # mutable
miCadena = Objeto.metodo(); # Inmutable pq se lo asigno a un nuevo elemento
```

First Class Citizen:  Si se trata el dato como primera. 
En el caso de los arrays, al pasarlo como parametro no se pasa un array sino el principio en la memoria. Entonces esto por ejemplo no permite que la funcion sepa de antemano el tamaño del arreglo.

ctype se puede usar para isDigit()




$$length: \Sigma^{*}  \to \mathbb{N}/length(s)= \begin{cases}0 &  s = \epsilon \\1 + length(t) &  h \cdot   t,h \in \Sigma \end{cases}$$

Para calcular el largo de una cadena, se puede usar un ciclo que recorra la cadena hasta encontrar el caracter nulo '\0' que indica el final de la cadena. 


## Assert
En C, la función `assert` se utiliza para verificar condiciones en tiempo de ejecución. Si la condición evaluada es falsa, el programa se detiene y muestra un mensaje de error que indica la línea donde ocurrió la falla. Esto es útil para detectar errores durante el desarrollo y depuración del código.

### Static assert
En C11, se introdujo la función `static_assert`, que permite realizar verificaciones en tiempo de compilación. Esto significa que si la condición evaluada es falsa, el programa no se compilará y se mostrará un mensaje de error. Esto es útil para garantizar ciertas condiciones antes de que el programa se ejecute, como verificar el tamaño de un tipo de dato o la compatibilidad de tipos.


Especificacionm matematica 
$$ \Sigma^{*} \to \Sigma^{*} $$



## Puntero a funcion

Un puntero a función es una variable que almacena la dirección de una función en memoria. Esto permite llamar a la función a través del puntero, lo que es útil para implementar callbacks, funciones de orden superior y para pasar funciones como argumentos a otras funciones.

```c
// ejemplo de puntero a funcion
#include <stdio.h>

// Declaración de una función
void saludo() {
    printf("¡Hola, mundo!\n");
}

int main() {
    // Declaración de un puntero a función
    void (*ptrSaludo)();

    // Asignación de la dirección de la función saludo al puntero
    ptrSaludo = &saludo;

    // Llamada a la función a través del puntero
    (*ptrSaludo)(); // o ptrSaludo();

    return 0;
}
```

En este ejemplo, `ptrSaludo` es un puntero a función que apunta a la función `saludo`. Al llamar a `(*ptrSaludo)()`, se ejecuta la función `saludo`, lo que imprime "¡Hola, mundo!" en la consola.


## Left value

Un left value (lvalue) es una expresión que se refiere a una ubicación de memoria y puede aparecer en el lado izquierdo de una asignación. En otras palabras, un lvalue es algo a lo que se le puede asignar un valor. Por ejemplo, en la expresión `x = 5`, `x` es un lvalue porque se le está asignando el valor 5. 
Tiene que ser una direccion de memoria y debe ser modificable.

### R value
Un rvalue es una expresión que no se refiere a una ubicación de memoria y no puede aparecer en el lado izquierdo de una asignación. En otras palabras, un rvalue es algo que no se le puede asignar un valor. Por ejemplo, en la expresión `5 + 3`, `5 + 3` es un rvalue porque no se le puede asignar un valor.

### X value
Un xvalue (expiring value) es un tipo de rvalue que representa un objeto que está a punto de ser destruido o que se puede mover. Un xvalue se refiere a un objeto que tiene una dirección de memoria, pero que no se puede modificar porque está en proceso de ser destruido o movido. Por ejemplo, en la expresión `std::move(x)`, `std::move(x)` es un xvalue porque se refiere a un objeto `x` que está siendo movido y no se puede modificar después de la operación de movimiento.

