---
titulo: "Pila de llamadas"
slug: pila-de-llamadas
rama: software
categoria: sistema
nivel: 6
prerequisitos: [pila]
conduce_a: []
alias: ["pila de ejecución", "call stack"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Pila de llamadas

## Idea central
La pila de llamadas (call stack) es la pila concreta que usa un proceso para suspender temporalmente el trabajo de una función mientras otra función se ejecuta. Cada llamada activa queda registrada en un marco de pila propio, y al terminar, la función recupera de la cima el marco que le corresponde para regresar a quien la llamó. Sin esta organización, coexigirían dos funciones y ningún programa podría volver al punto exacto en que cedió el control.

## Antes de empezar
- [[pila]]: la estructura de datos que solo permite insertar y retirar elementos por la cima, en orden LIFO (last in, first out).

## Explicación
La pila de llamadas es la instanciación de una [[pila]] en la memoria del proceso: cada vez que el programa invoca a una función, se reserva un bloque en la zona de memoria destinada a las llamadas y se coloca en la cima. Ese bloque se llama marco de pila (stack frame) y es un registro contiguo asociado a una única activación de la función. En él se guardan los datos que distinguen esa activación de cualquier otra activación de la misma función: el punto de regreso, es decir, la dirección de la instrucción siguiente a la llamada dentro de la función que llamó, junto con los parámetros aún no consumidos y las variables locales del momento de la suspensión. Dos activaciones de la misma función conviven en la pila como dos marcos distintos, separados por su posición y por el punto de regreso que guarda cada uno.

El retorno sigue el mismo orden LIFO por construcción. Cuando la función invitada termina, retira su marco de la cima, restaura a partir de él el control que le correspondía y salta al punto de regreso allí guardado. La función que llamó nunca puede regresar antes que la invitada, porque su marco quedó cubierto por el de la invitada y solo se vuelve accesible cuando esta lo retira. Esta asimetría garantiza que la vuelta siempre deposite el control en el llamador correcto, aunque las funciones estén anidadas a tres, diez o mil niveles. La pila de llamadas, por tanto, no es un simple almacén de datos, sino el registro del orden de activación: la profundidad entera de funciones suspendidas queda codificada como una secuencia de marcos.

El límite de este mecanismo es su espacio finito. La zona de la pila dentro del espacio de memoria del proceso tiene un tamaño fijo, y cada marco ocupa una parte de él, de modo que una secuencia de llamadas sin un límite natural agota la zona. El caso extremo es la recursión, aplicación, cuando una función se llama a sí misma: cada llamada genera un marco nuevo sobre el anterior y nunca retira ninguno hasta que la cadena de llamadas alcanza un caso final. Si la cadena no alcanza ese caso, o si es simplemente muy larga, la pila se desborda: no cabe el marco siguiente y el programa no puede continuar la llamada. Esa situación es el desbordamiento de pila (stack overflow). Su consecuencia inmediata es la interrupción de la ejecución del proceso, porque el sistema operativo no encuentra marco donde alojar la llamada, pero su importancia va más allá del fallo: cualquier desbordamiento indica una invariante de anidamiento rota, ya sea por un caso final inalcanzable, por una cadena de llamadas mayor que la zona reservada o por una función que llama en bucle a otras sin regresar.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[pila]] se llega a la pila de llamadas al pasar de la regla general de la cima al uso concreto que la justifica: cada llamada activa necesita un registro propio y el retorno exige orden inverso al de llegada. La pila de llamadas aplica la disciplina LIFO a los marcos de activación, añadiendo el contenido de cada marco (punto de regreso, parámetros y locales) y el fenómeno del desbordamiento que aparece cuando la profundidad supera el espacio reservado. No hay un peldaño posterior asignado a esta nota.

## Límites de esta explicación
Esta nota no trata la estructura genérica de la pila, con sus operaciones de inserción y eliminación, que se estudia en [[pila]]. Tampoco detalla cómo el sistema operativo dimensiona la zona de la pila frente al resto de la memoria del proceso, descripción que corresponde a la gestión de memoria del proceso y a [[memoria-virtual]]. Los usos maliciosos del desbordamiento quedan fuera y se tratarán desde el punto de vista técnico y defensivo en las notas del grupo malicioso.

## Referencias
- FTE-0001 (Operating Systems: Three Easy Pieces, Arpaci-Dusseau y Arpaci-Dusseau): organización de la pila en la gestión de las llamadas y la ejecución de procesos.
- FTE-0002 (Modern Operating Systems, 4ª ed., Tanenbaum y Bos): pilas y marcos de activación en la gestión de procesos y llamadas del sistema.
