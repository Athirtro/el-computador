---
titulo: "Reproductor multimedia"
slug: reproductor-multimedia
rama: software
categoria: aplicacion
nivel: 5
prerequisitos: [software-de-aplicacion]
conduce_a: []
alias: ["reproductor multimedia", "media player"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Reproductor multimedia

## Idea central
Un reproductor multimedia es una aplicación que lee un archivo de audio, de vídeo o de ambos, y lo presenta en el tiempo al usuario con controles de reproducción. Su tarea distintiva no es guardar ni crear ese contenido, sino recorrerlo de forma sincronizada para que lo que se oye y lo que se ve correspondan al mismo momento de la grabación.

## Antes de empezar
- [[software-de-aplicacion]]: qué es una aplicación y cómo se diferencia del software de sistema y del software de programación.

## Explicación
El reproductor multimedia parte de [[software-de-aplicacion]]: es un programa ya creado que el usuario abre para cumplir una tarea concreta. Como toda aplicación, no gestiona directamente el hardware. Lee el archivo mediante los servicios que el sistema operativo ofrece para acceder a [[formatos-de-archivos]], y entrega la imagen y el sonido mediante los servicios de salida del sistema. Lo que lo distingue de otras aplicaciones es el tipo de tarea: mantener un ritmo de presentación en tiempo real, no solo mostrar un documento cuando el usuario lo pide.

Un archivo multimedia contiene, en general, una pista de audio y una pista de vídeo. Cada pista está formada por fragmentos ordenados en el tiempo, y cada fragmento lleva una marca que indica el instante de la grabación al que corresponde. Un códec es el método que permite comprimir esos fragmentos para guardarlos ocupando menos espacio y descomprimirlos al reproducirlos. El reproductor usa el códec adecuado para cada pista, sin que el usuario tenga que ocuparse de ese detalle: así puede reproducir contenidos guardados con métodos distintos con la misma interfaz de controles.

La dificultad propia del reproductor está en la sincronía entre audio y vídeo. El oído y la vista detectan con rapidez si una voz no coincide con los labios que la pronuncian o si un sonido llega antes o después de la imagen que lo causa. Para evitarlo, el reproductor mantiene una línea de tiempo común: lee los fragmentos de cada pista en el orden marcado por su instante, los prepara con una pequeña antelación y presenta cada uno cuando llega su momento. Si hay retraso en una pista, el reproductor puede esperar, acelerar o adelantar la otra dentro de límites discretos, porque el objetivo es que la presentación siga el ritmo de la grabación y no el ritmo irregular con que los datos llegan desde el almacenamiento o con que el procesador atiende otros programas.

En torno a ese núcleo giran las funciones visibles de la aplicación. El usuario puede iniciar, pausar y reanudar la reproducción, retroceder o avanzar a otro instante, ajustar el volumen y elegir qué pista o qué subtítulos presentar cuando el contenido los ofrece. La interfaz es la de una [[aplicacion-grafica]]: una ventana con la imagen en curso, una barra que muestra la posición dentro de la línea de tiempo y unos controles que traducen las órdenes del usuario en saltos o cambios de ritmo. Ninguna de esas funciones altera el archivo original; solo cambia el punto de la línea de tiempo que se está presentando.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[software-de-aplicacion]] se desciende a este peldaño por tipo de tarea: si aquella nota define la aplicación como el programa que el usuario usa para un fin concreto, el reproductor multimedia es el caso en que ese fin es presentar contenido de audio y vídeo en el tiempo. No conduce a ningún otro slug en este momento, porque su desarrollo posterior —el detalle de los códecs, de los formatos de contenedor y de la salida a dispositivos concretos— pertenece a notas aún no registradas y no puede enlazarse todavía.

## Límites de esta explicación
Esta nota no desarrolla cómo funcionan los códecs ni cómo se comprimen el audio y el vídeo; solo los define en una línea como el método que el reproductor usa para descomprimir lo guardado. Tampoco detalla los formatos concretos de archivo, la reproducción en red ni la salida a televisores o altavoces externos. Esas cuestiones quedan para notas futuras dedicadas a cada aspecto, y no se enlazan aquí porque aún no existen como conceptos registrados.

## Referencias
- FTE-0001 (Operating Systems: Three Easy Pieces, Arpaci-Dusseau y Arpaci-Dusseau): respalda la idea general de que las aplicaciones se apoyan en servicios del sistema operativo en lugar de gestionar directamente el hardware, aplicada aquí a la lectura de archivos y a la salida de datos.
- FTE-0002 (Modern Operating Systems, Tanenbaum y Bos): respalda la misma distinción entre el programa de aplicación y los servicios del sistema en que aquel se apoya.
