---
titulo: "Cliente-servidor"
slug: cliente-servidor
rama: software
categoria: aplicacion
nivel: 5
prerequisitos: [protocolo-de-red]
conduce_a: [servidor]
alias: ["relación cliente-servidor", "modelo cliente-servidor", "client-server"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Cliente-servidor

## Idea central
El modelo cliente-servidor describe una aplicación con red como un reparto de papeles: un programa, el cliente, inicia una solicitud y presenta el resultado a la persona, y otro programa, el servidor, atiende esa solicitud y responde con los datos pedidos. La distinción no es de naturaleza de los programas, sino de función en cada intercambio.

## Antes de empezar
- [[aplicacion-con-red]]: qué es una aplicación con red, la dirección del equipo remoto y la necesidad de un protocolo de red, es decir, un conjunto acordado de reglas que ambas partes entienden para formular la solicitud y la respuesta.

## Explicación
Desde [[aplicacion-con-red]] se sabe que una parte de la tarea ocurre en otro ordenador y que el sistema operativo transmite los datos. El presente peldaño ordena ese intercambio en dos papeles. El cliente es el programa que toma la iniciativa: decide qué pedir, lo formula según el protocolo común y muestra la respuesta o el error a la persona. El servidor es el programa que permanece a la espera de solicitudes, las atiende y responde con los datos, con un resultado o con un aviso de error; el detalle de cómo está construido el servidor queda para la nota siguiente, sin desarrollarlo aquí.

La comunicación es, en su forma mínima, una petición seguida de una respuesta. La persona actúa sobre el cliente, por ejemplo al pedir una página, enviar un mensaje o solicitar un archivo, y el cliente traduce esa intención en una solicitud dirigida a la dirección del equipo remoto. El servidor recibe la solicitud, la procesa con los datos de los que dispone y devuelve la respuesta. Solo cuando llega la respuesta el cliente puede actualizar lo que muestra; si el servidor no responde o responde con error, el cliente lo presenta como tal. Nada de esto ocurre en un solo ordenador: el que solicita y el que responde son procesos diferenciados por función, aunque puedan ejecutarse en la misma máquina en pruebas o en servicios locales.

Los papeles son relativos al intercambio. Un mismo programa puede ser cliente en una solicitud y servidor en otra, y un servidor puede atender a muchos clientes, mientras que cada cliente suele esperar la respuesta de su propia solicitud. Tampoco implican una jerarquía permanente entre personas o aparatos: el cliente es quien inicia y quien interactúa con la persona en esa sesión, y el servidor es quien conserva o procesa la información compartida. Por eso el navegador web, como cliente, pide contenido, y el programa que lo envía actúa como servidor en ese intercambio, sin que ninguno de los dos deje de ser una aplicación en el sentido de [[software-de-aplicacion]].

Este reparto explica por qué una aplicación con red depende de otro proceso para completar su tarea: si el servidor deja de responder, el cliente no puede inventar la respuesta. Explica también la concentración de datos y de lógica en el servidor frente a su presentación en el cliente, aunque esa organización interna del servidor no se desarrolla en esta nota.

## Cómo se conecta con lo anterior y lo siguiente
El salto desde [[aplicacion-con-red]] es mínimo: allí se establece que la aplicación intercambia datos con otro equipo mediante dirección y protocolo, y aquí se clasifica ese intercambio en papeles de cliente y servidor. El paso siguiente, con detalle pendiente de la nota de servidor, consiste en explicar cómo el servidor escucha, organiza las solicitudes y mantiene los datos que responde.

## Límites de esta explicación
Esta nota no describe la estructura interna del servidor, ni cómo escucha solicitudes, ni cómo guarda los datos que sirve; eso se trata en la nota de servidor, aún pendiente y sin enlace válido en `cola-listos.md`. Tampoco desarrolla los protocolos concretos, la dirección y localización de equipos, la seguridad de las comunicaciones ni la presentación gráfica de los resultados; esos temas pertenecen a sus notas propias, como [[aplicacion-grafica]] y [[navegador-web]] para la presentación y [[seguridad-aplicacion-con-red]] para la protección en tránsito.

## Referencias
- FTE-0001: Operating Systems: Three Easy Pieces, Remzi H. Arpaci-Dusseau y Andrea C. Arpaci-Dusseau. Respalda el papel del sistema operativo en transmitir datos y entregar la respuesta a la aplicación.
- FTE-0002: Modern Operating Systems, 4th ed., Tanenbaum con Bos. Respalda la organización de procesos y la capa de sistema que sostiene la comunicación entre aplicaciones.
