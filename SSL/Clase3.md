parametro a la hora de definir la funcion

argumento a la hora de llamar a la funcion

El operadore `sizeof` se calcula en tiempo de compilacion, salvo para arreglos de largo variable.


## Punteros genéricos

Sirve para simular sobrecarga y/o templates

### Programación genérica
Hago una funcion sin tipos para pasarle al compilador una" receta para generar codigo".
En el template le pasas un argumento el tipo de dato para que luego el compilador cree el código.

Sirve para no duplicar logica (por ejemplo un sort)

No podes desreferenciar directamente un `void*` . Da error de compilacion.
Aritmetica de punteros no aplica para `void*` si adheris estrictamente al estandar.

Podes asignar un puntero CONCERTO a un VOID o viceversa **SIN CASTING**.

`&var` es la direccion de `var`

Para la función `qsort()` el criterio ha de definirse asi:

```c
bool criterio(void* a, void* b){
    int ia = *(int*)a;

    [...]
}

```

Dependiendo el contexto donde llamas a la funcion, casteas el resultado del puntero void dependiendo del tipo de dato que necesitas usar.

### Punteros y Arreglos

`nullptr`

