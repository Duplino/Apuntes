```c

//START MODULE

//Conectar a los modulos y demas


while(1){
    // FETCH
    instruccion_raw = solicitarInstruccion();

    // DECODE
    instruction_t instruccion = parse_instruction(instruccion_raw);
    // EXECUTE
    
    execute_instruction(&instruccion);
    destroy_instruction(&instruccion);

    // CHECK INTERRUPT
    if(check_interrupt()){
        handle_interrupt();
    }

}

// END MODULE


```

La vida del proceso de CPU se puede dividir en tres etapas principales: INICIO, BUCLE PRINCIPAL y FIN.

En el Inicio se conecta al KS y KM y solicita los memory sticks hasta el momento (eventualmente pueden agregarse mas y eso se validara en el check_interrupt). 
Luego, se inicializan los registros del CPU y se solicita la primera instrucción al KS.

En el Bucle Principal, el CPU realiza un ciclo de ejecución que consta de las siguientes etapas:
1. FETCH: El CPU solicita la instrucción al KS utilizando la función `solicitarInstruccion()`, que devuelve la instrucción en formato raw.
2. DECODE: El CPU decodifica la instrucción utilizando la función `parse_instruction()`, que convierte la instrucción raw en una estructura de datos `instruction_t` que contiene los campos necesarios para su ejecución.
3. EXECUTE: El CPU ejecuta la instrucción utilizando la función `execute_instruction()`, que realiza las operaciones correspondientes según el tipo de instrucción.
4. CHECK INTERRUPT: El CPU verifica si hay alguna interrupción pendiente utilizando la función `check_interrupt()`. Si hay una interrupción, el CPU maneja la interrupción utilizando la función `handle_interrupt()`, que puede realizar acciones como cambiar el contexto del proceso, atender una solicitud de E/S, etc.