---
titulo: "Cola de listos"
slug: cola-de-listos
rama: software
categoria: sistema
nivel: 8
prerequisitos: [planificador]
conduce_a: [cuanto-de-tiempo]
alias: ["cola de listos", "ready queue"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Cola de listos

## Idea central
La cola de listos es el conjunto ordenado de [[proceso|procesos]] que el [[nucleo-kernel]] mantiene en espera de recibir el [[procesador]], sin estar ejecutándose ni bloqueados. Su importancia está en el orden: convierte un conjunto de procesos competidores en la secuencia concreta de turnos que aplica el [[planificador]].

## Antes de empezar
- [[planificador]]: componente del [[nucleo-kernel]] que decide, entre los procesos listos, cuál recibe el [[procesador]] a continuación y durante cuánto tiempo.

## Explicación
Un [[proceso]] en estado listo está preparado para ejecutarse: conserva su estado guardable, no necesita esperar ningún recurso externo y solo le falta el [[procesador]]. La cola de listos reúne a todos los procesos en esa situación en un mismo sitio para que el [[planificador]] pueda consultarlos en cada decisión. No forma parte de la cola el proceso que está en ejecución en ese instante ni el que está bloqueado a la espera de un recurso o de una operación, que el [[nucleo-kernel]] mantiene en otra lista.

Cada entrada de la cola no es el proceso entero, sino una referencia a su [[bloque-de-control-de-proceso]]: la ficha donde se guarda su estado y sus datos de control. Gracias a esa referencia, la cola puede reordenar procesos, sacar uno o añadir otro sin mover el contenido del proceso en sí.

El efecto práctico es la entrada y la salida de los procesos por dos motivos. Un proceso entra en la cola cuando pasa a estar listo: al crearse, al desbloquearse tras esperar un recurso o al ser retirado del [[procesador]] cuando termina su turno. Un proceso sale de la cola cuando el [[planificador]] lo elige para ejecutarse. La propia cola no decide por sí misma quién sale primero: la política del [[planificador]] interpreta el contenido de la cola. Como base, la cola respeta el orden de llegada que se estudia en [[cola-fifo]]; otras políticas pueden ordenarla por prioridades, por tiempo estimado o por turnos.

Como el [[planificador]] la actualiza en cada llegada, cada salida y cada fin de turno, la cola de listos es la representación viva de la competencia por el [[procesador]]. Mientras haya procesos en ella, el [[planificador]] tiene candidatos entre los que repartir turnos; cuando está vacía, no hay ningún proceso esperando el [[procesador]].

## Cómo se conecta con lo anterior y lo siguiente
Desde [[planificador]] ya se sabe que la política de turnos se aplica sobre un conjunto de procesos listos, pero no quién los reúne ni dónde esperan. Esta nota da ese paso: la cola de listos es esa reunión ordenada, con entradas que salen cuando el [[planificador]] las elige y que vuelven a entrar cuando un proceso vuelve a estar listo. El siguiente paso es cuánto tiempo puede permanecer en ejecución el proceso elegido antes de volver a la cola, que se trata en [[cuanto-de-tiempo]].

## Límites de esta explicación
Esta nota no explica cuánto tiempo dura cada turno ni cómo se fija su límite; eso se trata en [[cuanto-de-tiempo]]. Tampoco explica cómo se guarda y se restaura el estado de un proceso al salir de la cola para ejecutarse, que corresponde a [[cambio-de-contexto]], ni la organización interna de la cola como estructura de datos, que se estudia en [[estructuras-de-datos]], ni la creación de los procesos que entran en ella, que corresponde a [[gestor-de-procesos]].

## Referencias
- FTE-0001 (Operating Systems: Three Easy Pieces, Arpaci-Dusseau y Arpaci-Dusseau): cola de procesos listos y aplicación de políticas de planificación.
- FTE-0002 (Modern Operating Systems, 4ª ed., Tanenbaum): cola de listos y políticas de planificación.
