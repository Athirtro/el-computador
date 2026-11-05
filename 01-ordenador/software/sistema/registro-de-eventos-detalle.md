---
titulo: "Registro de eventos — detalle"
slug: registro-de-eventos-detalle
rama: software
categoria: sistema
nivel: 7
prerequisitos: [registro-de-eventos]
conduce_a: []
alias: ["formato de entrada de registro", "niveles de gravedad del registro", "filtrado del registro de eventos"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Registro de eventos — detalle

## Idea central
El detalle del [[registro-de-eventos]] consiste en qué contiene cada entrada, cómo se gradúa su importancia y cómo se recorre el conjunto para encontrar la secuencia que explica un fallo. Sin esos tres elementos, el registro sería una lista de textos sin criterio de lectura.

## Antes de empezar
- [[registro-de-eventos]]: qué es el registro como memoria cronológica del [[sistema-operativo]] y para qué sirve en el [[diagnostico-de-sistema]].

## Explicación
Cada entrada del registro responde, en una sola línea de información, a las preguntas mínimas de un hecho ya ocurrido: cuándo ocurrió, quién lo originó y qué ocurrió. El momento queda anotado con la hora del sistema, de modo que el orden de las entradas no depende del orden en que se lean, sino del orden en que sucedieron los hechos. El origen identifica al componente que generó el aviso —el [[nucleo-kernel]], uno de sus [[controladores-drivers]] o un servicio del sistema—, de modo que un mismo mensaje no significa lo mismo si proviene de un componente central o de uno periférico. El contenido describe el hecho en sí: qué operación se intentó, qué respondió el componente y, cuando procede, qué identificador o recurso estaba implicado.

A esos tres datos se añade la gravedad, que gradúa la importancia del hecho y convierte una lista plana en una jerarquía de atención. En el extremo inferior se sitúan los avisos informativos, que dejan constancia de una actividad normal sin señalar ningún problema. Por encima están las advertencias, que señalan una condición anómala que no impidió la operación pero que conviene vigilar, porque puede anunciar un fallo próximo. A continuación se encuentran los errores, que registran una operación que no pudo completarse, y en el extremo superior las condiciones críticas, que indican que una parte del sistema quedó incapacitada para seguir funcionando. La escala exacta y sus nombres varían según el sistema, pero la función es la misma en todos: permitir que quien diagnostica distinga, de un vistazo, lo que es ruido informativo de lo que exige acción.

Con la entrada y su gravedad definidas, el registro se consulta mediante filtrado: la selección de un subconjunto de entradas según uno o varios de sus datos. Filtrar por gravedad descarta el ruido informativo y deja visible lo que exige atención. Filtrar por origen acota el problema a un componente y descarta los avisos de los demás. Filtrar por ventana de tiempo aísla la secuencia de hechos que rodea a un síntoma, que es precisamente la evidencia que el diagnóstico necesita. Los tres filtros se combinan: ante un fallo, primero se acota el tiempo, luego se atiende a los errores y avisos críticos de esa ventana, y finalmente se ordena por origen para reconstruir qué componente falló primero y cuáles reaccionaron después. Ese recorrido es el que convierte el registro en evidencia, en lugar de una acumulación de textos.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[registro-de-eventos]] se sabía que el [[sistema-operativo]] anota los hechos con su momento, su origen y su importancia, y que el [[diagnostico-de-sistema]] los lee para contrastarlos con el estado actual. Esta nota abre esa afirmación: explica qué datos componen cada entrada, cómo se gradúa su gravedad y cómo se filtra el conjunto para reconstruir una secuencia. No conduce a ninguna nota posterior: es una rama terminal, porque la sintaxis concreta de cada herramienta de consulta pertenece a la práctica de uso y no a un peldaño nuevo de abstracción.

## Límites de esta explicación
Esta nota no trata la función general del registro, ya cubierta en [[registro-de-eventos]], ni la sintaxis, las opciones ni la ubicación del archivo de registro de ninguna herramienta concreta, que pertenece a [[herramientas-de-sistema]]. Tampoco trata otros registros con finalidad distinta, como el de usuarios, que se trata en [[registro-de-usuarios]].

## Referencias
- FTE-0001 (Operating Systems: Three Easy Pieces, Arpaci-Dusseau y Arpaci-Dusseau): la observación del estado del sistema como servicio que el [[sistema-operativo]] ofrece al diagnóstico.
- FTE-0002 (Modern Operating Systems, Tanenbaum): los servicios del sistema que registran la actividad del [[nucleo-kernel]] y sus [[controladores-drivers]].
