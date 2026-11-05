---
titulo: "Servidor"
slug: servidor
rama: software
categoria: aplicacion
nivel: 6
prerequisitos: [cliente-servidor]
conduce_a: []
alias: ["server"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Servidor

## Idea central
Un servidor es el equipo —ordenador y programa que en él actúa— que atiende las solicitudes que le envían otros equipos y responde con el dato o el resultado pedido. Es la otra cara de la relación cliente-servidor: sin él, la petición del cliente no tendría respuesta.

## Antes de empezar
- [[cliente-servidor]]: relación en la que un cliente solicita y un servidor responde.

## Explicación
Desde [[cliente-servidor]] se sabe que una aplicación con red reparte su trabajo entre varios ordenadores: el local, donde la persona actúa, y los remotos, donde se guarda o se procesa parte de la información. El servidor es el lado remoto de ese reparto.

En la práctica el servidor no es una pieza única. Es un ordenador con su [[sistema-operativo]], con almacenamiento y con memoria, en el que se ejecuta de forma permanente un programa —o varios— cuya única razón de ser es esperar solicitudes, atenderlas y contestar. Cada solicitud llega como un mensaje que identifica qué se pide y desde qué equipo, y el programa servidor la descifra, la trata como un [[proceso]] más que se ejecuta, obtiene el dato de su propio almacenamiento o de otro servicio local y devuelve la respuesta por la misma vía por la que llegó. Cuando el dato no existe o la petición no puede cumplirse, devuelve un aviso de error en lugar de un resultado, para que el cliente sepa que debe detenerse o mostrar un mensaje.

A diferencia de una aplicación como [[aplicacion-grafica]], que existe para uso directo de una persona sentada delante de un equipo, el servidor no está pensado para ser operado a mano. Su interfaz de uso es la red misma: se le interviene lo menos posible, se le mantiene encendido y disponible, y se vigila que siga respondiendo. Por eso un mismo ordenador puede actuar como cliente en un momento —cuando pide un dato— y como servidor en otro, cuando otro equipo le pide algo a él. No son naturalezas fijas, sino papeles que un equipo asume según el sentido de la comunicación.

Un servidor trabaja, en síntesis, en tres momentos sin pausa: escucha, atiende y responde. Escucha de forma continua en un punto de contacto conocido de la red; atiende cada solicitud como una tarea concreta que se ejecuta; y responde con el dato preparado o con el aviso de error. Si deja de escuchar o tarda demasiado en responder, el cliente no puede completar su tarea, aunque su propia aplicación funcione correctamente.

## Cómo se conecta con lo anterior y lo siguiente
El paso desde [[cliente-servidor]] a esta nota es concretar un papel de la relación: si aquélla describía que hay un solicitante y un respondedor, aquí se caracteriza con detalle quién es el respondedor, qué hace y cómo organiza su trabajo. La nota queda sin `conduce_a` posterior, como rama terminal del recorrido de [[aplicacion-con-red]]: a partir del servidor se iría hacia el detalle técnico de cómo se formulan las solicitudes, que pertenece a una nota de protocolo distinta.

## Límites de esta explicación
Esta nota no desarrolla cómo se formulan ni se interpretan las solicitudes: las reglas acordadas que permiten a cliente y servidor entenderse —es decir, el protocolo— quedan fuera deliberadamente y deben tratarse en una nota propia posterior. Tampoco desarrolla la red física que transporta los mensajes, ni la seguridad de la conversación, que corresponde a [[seguridad-aplicacion-con-red]].

## Referencias
- [FTE-0001, FTE-0002]: ambos textos describen la organización de los sistemas distribuidos en que un equipo central atiende las peticiones de otros, su ejecución como procesos permanentes y su dependencia de la red; respaldo general de la definición de servidor y de su papel frente al cliente.
