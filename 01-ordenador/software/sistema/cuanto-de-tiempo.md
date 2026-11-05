---
titulo: "Cuanto de tiempo"
slug: cuanto-de-tiempo
rama: software
categoria: sistema
nivel: 9
prerequisitos: [cola-de-listos]
conduce_a: []
alias: ["cuanto de tiempo", "time slice"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Cuanto de tiempo

## Idea central
El cuanto de tiempo es el intervalo máximo de ejecución continua concedido a un proceso dentro del turno rotativo antes de que el [[planificador]] pueda retirarlo y dar paso al siguiente de la cola. Su importancia está en el reparto: sin un límite temporal, un solo proceso podría ocupar el [[procesador]] indefinidamente y los demás quedarían bloqueados.

## Antes de empezar
- [[cola-de-listos]]: cola de procesos listos para ejecutarse en espera de turno.

## Explicación
El cuanto de tiempo es una duración, no una probabilidad ni un número de operaciones abstracto: mide cuánto tiempo puede permanecer un proceso concreto en ejecución en el [[procesador]] antes de que se le retire el turno. Al agotarse, el proceso no termina; se conserva su estado, se le coloca de nuevo al final de la [[cola-de-listos]] y el siguiente proceso en cola recibe su propio cuanto completo. Así, con un único [[procesador]], cada [[proceso]] listo avanza por turnos cortos y alternos.

Su puesta en marcha depende de un mecanismo de control temporal: el núcleo programa una interrupción con el intervalo de duración del cuanto y, al producirse, evalúa si el proceso que está en ejecución ha vencido. Si el proceso cede antes —por terminar, por esperar un recurso o por ayudar al núcleo—, el turno se entrega anticipadamente sin necesidad de esperar al vencimiento. Si, en cambio, el proceso agota su cuanto sin ceder, la interrupción fuerza la retirada. Esta es la diferencia práctica entre ceder voluntariamente y ser interrumpido: en ambos casos se entrega el [[procesador]], pero en el segundo caso la cesión está impuesta por el reloj del núcleo.

El valor elegido para el cuanto expresa un compromiso. Con un cuanto muy corto, la alternancia entre procesos es muy fina y todos avanzan con poca espera, pero se multiplican las retiradas y, con ellas, el costo de guardar y restaurar estado en cada cambio, además de la sobrecarga de evaluar el intervalo en cada turno. Con un cuanto muy largo, ese costo se reduce, pero el proceso que no cede monopoliza el [[procesador]] durante demasiado tiempo y los procesos que acaban de llegar esperan mucho antes de ejecutarse. El cuanto, por tanto, no es solo un límite: es el parámetro que gradúa cuánta consistencia se gana en respuesta inmediata y cuánta se pierde en trabajo útil.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[cola-de-listos]] se establece el conjunto de procesos que esperan turno en orden de llegada; desde [[planificador]] se conoce el criterio que decide cuál de ellos sale el siguiente. Esta nota añade el parámetro que faltaba para que ese orden opere en rotativo: cuánto tiempo puede durar cada turno antes de pasar al siguiente. Queda fuera de esta nota cómo se guarda físicamente el estado al retirar y cómo se carga el del siguiente.

## Límites de esta explicación
Esta nota no desarrolla cómo se conserva y restaura el estado del proceso al agotar el cuanto; eso se trata en [[cambio-de-contexto]]. Tampoco trata qué políticas de ordenación usan el turno rotativo ni cómo se comparan entre sí; eso corresponde a [[planificador]]. La estructura de la cola de procesos listos y su estado se estudian respectivamente en [[estructuras-de-datos]] y en [[proceso]].

## Referencias
- FTE-0001 (Operating Systems: Three Easy Pieces, Arpaci-Dusseau y Arpaci-Dusseau): definición y papel del cuanto de tiempo en el turno rotativo.
- FTE-0002 (Modern Operating Systems, 4ª ed., Tanenbaum): mecanismo del turno rotativo y costo de los cambios frecuentes de proceso.
