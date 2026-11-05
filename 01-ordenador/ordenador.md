---
titulo: "Ordenador"
slug: ordenador
rama: software
categoria: ""
nivel: 1
prerequisitos: []
conduce_a: [software]
alias: ["ordenador", "computador", "equipo", "máquina de cómputo"]
estado: borrador
fuentes: []
---

# Ordenador

## Idea central
El ordenador es una máquina de cómputo: un sistema físico que ejecuta instrucciones y datos según reglas precisas. Su interés está en el cómo: cada parte —física o lógica— se explica desde lo más visible hasta sus principios fundamentales, sin saltos.

## Antes de empezar
Sin prerequisitos. Esta es la nota de entrada del libro (§12).

## Explicación
El ordenador se divide en dos caras. Por un lado, lo físico: componentes con forma, que ocupan espacio y consumen energía. Por otro, lo lógico: instrucciones y datos que indican a esos componentes qué hacer. La primera cara se tratará en su rama propia; la segunda es el [[software]], el componente intangible que controla el hardware, ya en borrador en esta bóveda. Aquí no se enlaza a la rama física porque aún no existe como nota canónica en borrador (está en `cola-pendientes.md`, archivo de referencia aislado), sino que se define en una línea: hardware es el conjunto de circuitos, procesadores, memorias y dispositivos que ejecutan las instrucciones.

La descripción de un caso concreto ayuda a no perder el hilo general. El equipo del autor que sirve de ejemplo recurrente es:

| Componente | Dispositivo |
| ---------- | ----------- |
| CPU | AMD Ryzen 7 5700G with Radeon Graphics (4.3 GHz) |
| GPU | NVIDIA GeForce RTX 5050 (8 GB) |
| Memoria | 2 x 16 GB a 3200 MT/s A-DATA |
| Disco 0 | HDD de 931,51 GB |
| Disco 1 | SSD de 953,85 GB |
| Placa | ASUSTeK COMPUTER INC. PRIME B350M-A |

Ninguno de estos datos sustituye a la explicación general: cada componente se tratará como caso de una arquitectura general (x86-64, memoria principal, almacenamiento), no como una ficha aislada.

## Cómo se conecta con lo anterior y lo siguiente
Esta nota no tiene anterior. Desde aquí, el paso natural es el [[software]], ya redactado en borrador, que define la cara lógica. La cara física queda registrada como pendiente en `cola-pendientes.md` y no se enlaza hasta que existan sus notas canónicas en `cola-listos.md`.

## Límites de esta explicación
Esta nota no desarrolla el software ni el hardware; cada rama tiene sus notas canónicas en orden de prerequisitos. Tampoco entra en el detalle físico de los componentes.

## Referencias
Sin referencias registradas en `_registro/fuentes.md` para esta nota todavía.
