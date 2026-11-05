---
titulo: "Protocolo de red"
slug: protocolo-de-red
rama: software
categoria: aplicacion
nivel: 5
prerequisitos: [red-de-computadores]
conduce_a: [cliente-servidor]
alias: ["protocolo de comunicación", "network protocol"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Protocolo de red

## Idea central
Un protocolo de red es el conjunto de reglas que dos ordenadores aceptan de antemano para entenderse al intercambiar datos. Sin ese acuerdo, una aplicación puede enviar bytes a otro equipo, pero no puede pedir algo concreto ni interpretar con certeza lo que recibe.

## Antes de empezar
- [[red-de-computadores]]: los ordenadores están conectados y pueden enviarse datos; falta saber qué significan esos datos cuando llegan.

## Explicación
Desde [[red-de-computadores]] se sabe que el intercambio es posible, pero enviar datos no equivale todavía a comunicarse. Para comunicarse hacen falta reglas compartidas: qué puede pedir una parte, cómo se formula esa petición, cómo se reconoce que se ha recibido y qué significa la respuesta. Ese conjunto de reglas es el protocolo de red (network protocol), y debe ser conocido por ambas partes antes de que empiece el intercambio.

El protocolo ordena el intercambio en forma de petición y respuesta. La petición es el mensaje con el que una aplicación solicita algo concreto, y la respuesta es el mensaje con el que la otra parte entrega el resultado o indica que no ha podido hacerlo. La asimetría es esencial: quien solicita no decide por sí solo la respuesta, y quien responde debe poder distinguir el tipo de petición para saber qué se le está pidiendo. Por eso el protocolo fija el formato de ambos mensajes, los datos que cada uno lleva, las clases de petición permitidas y la manera de señalar un error.

También fija la secuencia. No todo vale en cualquier momento: una respuesta solo tiene sentido después de una petición, y si ambas partes hablaran a la vez con el mismo formato imprescindible, no sabrían cuál de los dos mensajes es la petición y cuál la respuesta. Al fijar quién inicia, qué sigue después y cómo se reconoce el final de un intercambio, el protocolo convierte una transmisión de datos en una conversación con significado.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[red-de-computadores]] se desciende a este peldaño por la pregunta que queda abierta: ya pueden viajar los datos, pero ¿cómo sabe cada parte qué le están pidiendo y qué debe responder? El protocolo responde a esa pregunta con reglas comunes. Una vez vistas, [[cliente-servidor]] describe el reparto de papeles que usa ese intercambio: qué programa solicita y cuál atiende, sin que esta nota tenga que entrar en cómo está construido por dentro el programa que atiende.

## Límites de esta explicación
Esta nota no desarrolla cómo son las redes por dentro ni cómo viaja físicamente la señal; esos temas pertenecen a [[red-de-computadores]]. Tampoco desarrolla el papel concreto de cliente y servidor, el detalle interno del programa que atiende las peticiones ni la protección de los datos en tránsito, que se tratan en [[cliente-servidor]] y en [[seguridad-aplicacion-con-red]].

## Referencias
- FTE-0001 y FTE-0002: respaldan solo el contexto de sistema operativo que sostiene el intercambio entre aplicaciones; ninguna de las dos cubre en concreto el contenido de un protocolo de red.
