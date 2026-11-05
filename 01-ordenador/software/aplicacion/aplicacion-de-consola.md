---
titulo: "Aplicación de consola"
slug: aplicacion-de-consola
rama: software
categoria: aplicacion
nivel: 4
prerequisitos: [software-de-aplicacion]
conduce_a: [terminal-de-texto]
alias: ["aplicación de consola", "console application", "aplicación de terminal"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Aplicación de consola

## Idea central
Una aplicación de consola es un programa de [[software-de-aplicacion]] cuya interacción con la persona se realiza principalmente mediante texto: recibe órdenes o datos escritos y responde con texto visible. No usa ventanas ni controles gráficos para su funcionamiento; su superficie de trabajo es una [[terminal-de-texto]].

## Antes de empezar
- [[software-de-aplicacion]]: qué es una aplicación y cómo se diferencia del [[software-de-sistema]] y del [[software-de-programacion]].

## Explicación
Desde [[software-de-aplicacion]] se sabe que una aplicación traduce una intención del usuario en operaciones ejecutadas por el sistema. En una aplicación de consola, esa traducción ocurre en forma de texto. La persona escribe una orden o un dato, pulsa una tecla de confirmación y la aplicación lee esa línea, la interpreta y muestra el resultado también como texto. Si necesita más información, vuelve a pedirla por el mismo medio; si detecta un dato incorrecto, responde con un mensaje de error en texto. La precisión de lo que escribe y de lo que lee es, por tanto, parte esencial de su funcionamiento.

Esto la distingue de la [[shell]]. La shell es el intérprete de órdenes: su tarea es recibir órdenes y decidir qué programas hay que ejecutar. Una aplicación de consola es uno de esos programas, con una tarea propia: editar un archivo, calcular un valor, copiar información o mostrar el estado de algo. Cuando esa tarea está en curso, la orden que la persona escribió ya no la interpreta la shell, sino la aplicación. Por eso una misma terminal puede servir para lanzar programas distintos sin cambiar la forma básica de interactuar con ellos.

La forma de la interacción tiene límites claros. Todo lo que la aplicación presenta debe ser representable como texto: instrucciones, respuestas, tablas sencillas y mensajes de error. No depende de imágenes, ventanas ni de señalar elementos con el ratón. A cambio, es un formato directo y legible, que permite ver exactamente qué se ha pedido y qué se ha recibido. La aplicación sigue apoyándose en los servicios del sistema para leer y escribir, gestionar archivos o terminar su ejecución: la consola es su interfaz, no el mecanismo que hace el trabajo.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[software-de-aplicacion]] se desciende a un tipo concreto de aplicación definido por su interfaz. Frente a una aplicación cuya interfaz se basa en elementos gráficos, la aplicación de consola realiza la misma función de aplicación, pero hablando con texto en una superficie de texto. El siguiente peldaño es [[terminal-de-texto]], porque para hablar con texto la aplicación necesita una superficie donde escribir y leer: sin ella, su modo de interacción no tendría dónde presentarse.

## Límites de esta explicación
Esta nota no trata las aplicaciones con ventana e interfaz gráfica, que se estudian en [[aplicacion-grafica]], ni las que su modo principal de trabajo es la comunicación con otros ordenadores, que se estudian en [[aplicacion-con-red]]. Tampoco explica cómo funciona la superficie de texto en sí: eso corresponde a [[terminal-de-texto]], ni cómo la shell interpreta las órdenes, que corresponde a [[shell]]. No se detallan programas concretos de consola ni sus órdenes concretas.

## Referencias
- FTE-0001: *Operating Systems: Three Easy Pieces*, de Remzi H. Arpaci-Dusseau y Andrea C. Arpaci-Dusseau. Respalda el marco general de los programas de usuario que solicitan servicios al sistema comportándose como [[proceso]] en espacio de usuario.
- FTE-0002: *Modern Operating Systems*, 4ª edición, de Andrew S. Tanenbaum (con Herbert Bos). Respalda el marco general de la relación entre programas de usuario, sistema operativo y gestión de recursos subyacente a cualquier aplicación, incluida la de consola.
