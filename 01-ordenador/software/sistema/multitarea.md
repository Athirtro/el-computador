---
titulo: "Multitarea"
slug: multitarea
rama: software
categoria: sistema
nivel: 7
prerequisitos: [gestor-de-procesos]
conduce_a: []
alias: ["multitarea", "multitasking"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Multitarea

## Idea central
La multitarea es la propiedad por la que varios programas avanzan a la vez compartiendo los recursos de un mismo ordenador, aunque un único procesador solo pueda ejecutar una instrucción en cada instante. Importa porque permite trabajar con varios programas abiertos sin que ninguno tenga que esperar a que termine otro.

## Antes de empezar
- [[gestor-de-procesos]]: el reparto de turnos de procesador entre procesos, con prioridades y con la separación entre procesos listos y procesos que esperan por otra causa.

## Explicación
El [[gestor-de-procesos]] reparte el procesador, pero la multitarea describe el efecto que ese reparto produce sobre el conjunto de los recursos. Cuando un [[proceso]] espera datos de un dispositivo, de un archivo o de la red, su procesador queda libre para otro proceso. Al entrelazar esos momentos de actividad y de espera, varios procesos progresan durante el mismo intervalo de tiempo aunque ninguno ocupe el procesador de forma continua. La multitarea consiste, por tanto, en ese solapamiento de avances, no solo en la existencia de turnos.

Ese solapamiento se aplica también a los demás recursos compartidos. Cada proceso dispone de su propia zona de memoria y accede a los dispositivos y al almacenamiento mediante el núcleo, de modo que lo que hace un proceso no destruye directamente el avance de otro. Si un proceso ocupa mucha memoria o retiene un dispositivo, el núcleo debe arbitrar el acceso, con los criterios generales de [[gestion-de-recursos]]. La multitarea bien arbitrada hace que cada programa pueda trabajar como si tuviera el ordenador entero a su disposición, mientras los recursos reales se reparten por turnos y por esperas.

El entrelazo puede organizarse de dos maneras. En la multitarea cooperativa, cada proceso cede voluntariamente el procesador cuando ya no lo necesita o cuando espera una respuesta. En la multitarea preventiva, el núcleo puede interrumpir a un proceso aunque este no ceda, como ocurre cuando el [[planificador]] decide cambiar de proceso mediante un [[cambio-de-contexto]]. La segunda forma protege al resto de procesos frente a un programa que nunca cede, pero exige guardar y restaurar el estado de cada proceso en cada cambio, con el coste que ya se vio en [[gestor-de-procesos]].

## Cómo se conecta con lo anterior y lo siguiente
Desde [[gestor-de-procesos]] se pasa del mecanismo concreto de turnos de procesador a la propiedad general de que varios procesos avanzan compartiendo procesador, memoria, dispositivos y almacenamiento. La multitarea es el resultado visible de alternar procesos listos y procesos en espera, y de arbitrar el resto de recursos entre ellos. Esta nota no avanza hacia un nuevo mecanismo concreto: deja el siguiente paso en el detalle de la concurrencia dentro de un mismo programa, que queda fuera de su alcance.

## Límites de esta explicación
Esta nota no trata cómo se reparten la memoria entre procesos ni cómo se organiza el espacio de cada uno; eso corresponde a [[gestor-de-memoria]] y a [[memoria-virtual]]. Tampoco trata la concurrencia dentro de un mismo programa, es decir, los hilos y su coordinación; eso se tratará en [[hilos-concurrencia]]. Las políticas concretas de ordenación de turnos quedan en [[planificador]].

## Referencias
- FTE-0001: Operating Systems: Three Easy Pieces, de Remzi H. Arpaci-Dusseau y Andrea C. Arpaci-Dusseau. Respalda la idea de varios procesos que avanzan sobre recursos compartidos y de las formas cooperativa y preventiva de alternarlos.
- FTE-0002: Modern Operating Systems, 4th Edition, de Andrew S. Tanenbaum (4ª ed. con Herbert Bos). Respalda la distinción entre multiprogramación, multitarea y arbitraje de recursos entre procesos.
