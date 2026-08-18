## Recursos
- Criticos
- Contadores
- Dan orden de ejecucion

Grado de multiprocesamiento: Cuantos procesos pueden ejecutarse al mismo tiempo

Comunicacion asincrona: No se bloquea el proceso que envia el mensaje, el receptor lo recibe cuando puede
Comunicacion sincrona: El proceso que envia el mensaje se bloquea hasta que el receptor lo recibe

Operacion atomica: No se puede interrumpir, se ejecuta completamente o no se ejecuta

Espera activa: Dekker, Petersno, semaforo con spinlock


Mutex: Garantinza la mutua exlusion
Se inicializa en 1

Semaforo binario: Se inicializa en 1 o 0.

Semaforo contador: Se inicializa en un valor mayor a 1, permite que n procesos accedan a la vez, se decrementa al entrar y se incrementa al salir. 

Al hacer signal en un semaforo contador, se despierta a un proceso bloqueado, si hay alguno, y se incrementa el contador. Si no hay procesos bloqueados, solo se incrementa el contador.




### Ejercico 4
```c
mutex1 = 1;
mutex2 = 0;

void proceso1() {
    while (true) {
        wait(mutex1);
        // Seccion critica
        signal(mutex2);
    }
}

void proceso2() {
    while (true) {
        wait(mutex2);
        // Seccion critica
        signal(mutex1);
    }
}
```
En este ejemplo, el proceso1 y el proceso2 se alternan para acceder a la sección crítica. El proceso1 espera a que mutex1 esté disponible, entra a la sección crítica y luego señaliza mutex2 para que el proceso2 pueda entrar. El proceso2 hace lo mismo pero en orden inverso. Esto garantiza que ambos procesos puedan acceder a la sección crítica sin interferencias, evitando condiciones de carrera.


### Ejercico 5
```c

mutex1 = 1;
mutex2 = 0;
mutex3 = 0;

void procesoA() {
    while (true) {
        wait(mutex1);
        // Seccion critica
        signal(mutex2);
    }
}

void procesoB() {
    while (true) {
        wait(mutex2);
        // Seccion critica
        signal(mutex3);
    }
}


void procesoC() {
    while (true) {
        wait(mutex3);
        // Seccion critica
        signal(mutex1);
    }
}
```




#### Ejercico 6
```c
// BACA

mutex1 = 0;
mutex2 = 1;
mutex3 = 0;
mutex4 = 1;

void procesoA() {
    while (true) {
        wait(mutex1);
        // Seccion critica
        signal(mutex4);
    }
}

void procesoB() {
    while (true) {
        wait(mutex2);
        wait(mutex4);
        // Seccion critica
        signal(mutex3);
        signal(mutex1);
        

    }
}


void procesoC() {
    while (true) {
        wait(mutex3);
        wait(mutex4);
        // Seccion critica
        signal(mutex2);
        signal(mutex1);   
    }
}
```


### Ejercicio 1

```c
a = b = 1 // GLBOAL
mutex_a = mutex_b = 1; // SEMAFOROS

// PROCESO 0
variable_local d = 1;
While (TRUE){
    wait(mutex_a)
    a = a + d;
    signal(mutex_a);
    d = d * d;
    wait(mutex_b);
    b = b – d;
    signal(mutex_b);
}

// PROCESO 1
variable_local e = 2;
While (TRUE){
    wait(mutex_b);
    b = b * e;
    signal(mutex_b);
    e = e ^ e;
    wait(mutex_a);
    a++;
    signal(mutex_a);
}
```

> [!WARNING]
> Esta mal. Los wait tienen que estar al principio de cada proceso, sino no se garantiza la exclusión mutua en las variables compartidas.

### Ejercico 3

Dado un sistema con los siguientes tipos de procesos, sincronice su código mediante semáforos sabiendo que hay tres impresoras, dos scanners y una variable compartida. 
```c

s_impresora = 3;
s_scanner = 2;
m_variable_compartida = 1;

// PROCESO A
while (TRUE){
    wait(s_impresora);
    usar_impresora();
    signal(s_impresora);

    wait(m_variable_compartida);
    variable_compartida++;
    signal(m_variable_compartida);
}


// PROCESO B
while (TRUE){
    wait(m_variable_compartida);
    variable_compartida++;
    signal(m_variable_compartida);

    wait(s_scanner);
    usar_scanner();
    signal(s_scanner);
}


// PROCESO C
while (TRUE){
    wait(s_scanner);
    usar_scanner();
    signal(s_scanner);

    wait(s_impresora);
    usar_impresora();
    signal(s_impresora);
}
```