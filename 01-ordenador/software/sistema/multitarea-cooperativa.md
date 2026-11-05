---
titulo: "Multitarea cooperativa"
slug: multitarea-cooperativa
rama: software
categoria: sistema
nivel: 8
prerequisitos: [multitarea]
conduce_a: []
alias: ["multitarea cooperativa", "cooperative multitasking"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Multitarea cooperativa

## Idea central
La multitarea cooperativa es la forma de [[multitarea]] en la que cada [[proceso]] deja el procesador por su propia voluntad cuando espera una respuesta o llega a un punto de cesión acordado. Importa porque permite que varios procesos avancen a la vez con un mecanismo muy simple, a cambio de confiar en que ninguno ocupe el procesador indefinidamente.

## Antes de empezar
- [[multitarea]]: la propiedad por la que varios procesos avanzan compartiendo los recursos de un mismo ordenador, aunque un único procesador solo pueda ejecutar una instrucción en cada instante.

## Explicación
En la multitarea cooperativa, la cesión del procesador procede del propio proceso, no de una interrupción decidida desde fuera. Un proceso que espera datos de un dispositivo, de un archivo o de la red no puede hacer ningún avance útil mientras tanto, así que deja el procesador libre para que otro proceso listo pueda trabajar. La cesión también puede ocurrir en un punto de cesión, es decir, un momento de su ejecución en el que el proceso decide voluntariamente dar paso a otro antes de continuar su propio trabajo.

Mientras lo hace, el proceso cooperante conserva su estado interno y su lugar de ejecución, de modo que puede retomar el trabajo cuando vuelva a recibir su turno. La cooperación se sostiene, por tanto, en una disciplina compartida: cada proceso cede antes de convertirse en un estorbo para los demás. Un editor que espera la siguiente tecla o un programa que espera una respuesta de la red no necesitan que nadie los detenga, basta con que dejen de ocupar el procesador hasta que la respuesta llegue.

La sencillez de este mecanismo tiene un precio. Si un proceso nunca espera y nunca llega a un punto de cesión, los demás procesos no reciben su turno aunque estén listos, porque nadie los retira del procesador. Por eso la multitarea cooperativa solo funciona bien cuando todos los procesos cumplen su parte y ceden con regularidad, y su riesgo principal es un proceso mal comportado o mal programado que monopoliza el procesador y bloquea el avance del resto.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[multitarea]] se pasa de la propiedad general de que varios procesos avanzan compartiendo recursos a uno de sus dos mecanismos concretos de alternancia. La multitarea cooperativa explica la alternancia por cesión voluntaria del procesador, mientras que la otra forma, en la que el núcleo puede retirar el procesador a un proceso que no cede, queda para una nota distinta. Esta nota no avanza hacia un nuevo mecanismo posterior: deja el contraste con esa otra forma de alternancia como siguiente paso.

## Límites de esta explicación
Esta nota no trata la alternancia en la que el núcleo interrumpe a un proceso aunque este no ceda; eso corresponde a [[multitarea-preventiva]]. Tampoco trata la concurrencia dentro de un mismo programa, es decir, los hilos y su coordinación; eso se tratará en [[hilos-concurrencia]]. Las políticas concretas de ordenación de los turnos quedan en [[planificador]].

## Referencias
- FTE-0001: Operating Systems: Three Easy Pieces, de Remzi H. Arpaci-Dusseau y Andrea C. Arpaci-Dusseau. Respalda la idea de que la alternancia entre procesos puede apoyarse en que cada proceso ceda el procesador de forma voluntaria.
- FTE-0002: Modern Operating Systems, 4th Edition, de Andrew S. Tanenbaum (4ª ed. con Herbert Bos). Respalda la distinción entre las formas cooperativa y preventiva de compartir el procesador entre varios procesos.
