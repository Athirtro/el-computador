---
titulo: "Códec"
slug: codec
rama: software
categoria: aplicacion
nivel: 6
prerequisitos: [reproductor-multimedia]
conduce_a: []
alias: ["códec", "codec", "codificador-decodificador"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Códec

## Idea central
Un códec es el método, junto con el programa que lo aplica, que comprime una pista de audio o de vídeo para guardarla ocupando menos espacio y la descomprime para poder reproducirla. Es el paso que permite que un [[reproductor-multimedia]] presente el contenido sin que el archivo tenga que guardar la imagen y el sonido sin comprimir.

## Antes de empezar
- [[reproductor-multimedia]]: qué hace un reproductor multimedia, cómo lee un archivo formado por pistas de audio y de vídeo y por qué necesita descomprimir los fragmentos antes de presentarlos.

## Explicación
El reproductor multimedia parte de [[software-de-aplicacion]]: es una aplicación que se apoya en los servicios del sistema para leer el archivo y para entregar la imagen y el sonido, sin gestionar directamente el hardware. Dentro de esa tarea, el reproductor no entiende por sí solo los fragmentos tal como están guardados. Los fragmentos llegan comprimidos, es decir, transformados mediante unas reglas que eliminan parte de la información repetida o apenas perceptible, y el reproductor necesita un códec para invertir esa transformación y recuperar los fragmentos en su forma presentable.

La palabra códec cubre, en realidad, dos operaciones complementarias. La primera es comprimir: codificar. Se realiza normalmente al crear el contenido o al prepararlo para distribuirlo, y consiste en recorrer la pista y producir una versión más pequeña que conserva lo necesario para reconstruirla después. La segunda es descomprimir: decodificar. Se realiza al reproducir, y consiste en aplicar las mismas reglas en sentido contrario sobre cada fragmento guardado para obtener la imagen o el sonido que el reproductor debe entregar en ese instante. Se habla de un mismo códec para ambas operaciones porque, aunque se ejecutan en momentos distintos y a veces en máquinas distintas, comparten las reglas de transformación: sin conocerlas no es posible pasar de la versión guardada a la versión presentable ni al revés.

La necesidad de comprimir nace del tamaño de la pista sin comprimir. Una pista de vídeo presenta muchas imágenes por segundo y una de audio muchas muestras por segundo, donde una muestra es un valor de sonido en un instante concreto; guardadas sin comprimir, ambas ocupan mucho más espacio y exigen mucha más lectura que lo que resultaría práctico para almacenar y distribuir. La compresión aprovecha que hay información redundante, es decir, información que se repite o que puede deducirse de lo que la rodea: en el vídeo, imágenes consecutivas suelen ser muy parecidas, y en el audio, sonidos próximos también guardan continuidad. En lugar de guardar cada fragmento de forma completa e independiente, el códec guarda diferencias y referencias entre fragmentos, de modo que el decodificador pueda reconstruirlos.

Esa reconstrucción puede ser exacta o aproximada, y la diferencia importa para entender qué se pierde al comprimir. En la compresión sin pérdida, el decodificador recupera exactamente los datos originales y el ahorro proviene solo de eliminar redundancia. En la compresión con pérdida, el códec descarta además información que considera menos perceptible, de modo que lo reconstruido no es idéntico a lo original, aunque resulte aceptable para quien lo escucha o lo mira. No se trata de dos códecs distintos por definición, sino de dos criterios posibles dentro de un mismo códec: cuánto ahorro se busca y cuánta fidelidad se exige a cambio.

Conviene distinguir el códec de otra cosa con la que se confunde a menudo: el contenedor, es decir, el formato de archivo que agrupa las pistas y les añade índices para localizarlas. El contenedor dice qué pistas hay y dónde empieza cada una; el códec dice cómo está comprimida cada pista y cómo debe descomprimirse. Un mismo contenedor puede llevar pistas comprimidas con códecs distintos, y un mismo códec puede aparecer dentro de contenedores distintos. Por eso el reproductor necesita saber dos cosas a la vez: en qué contenedor viene el archivo, para encontrar cada pista, y con qué códec está comprimida cada pista, para poder presentarla. En esta nota solo se trata de lo segundo.

La compresión y la descompresión no cuestan lo mismo ni tienen las mismas exigencias. Comprimir puede hacerse sin prisa, antes de distribuir el contenido, y admite dedicarle mucho tiempo de cálculo para lograr un buen ahorro. Descomprimir, en cambio, tiene que ocurrir al ritmo de la reproducción: cada fragmento debe estar listo cuando llega su instante, porque el reproductor lo presenta en tiempo real y no puede esperar. Por eso un códec se juzga también por lo exigente que es al decodificarlo, y no solo por lo pequeño que deja el resultado al comprimirlo.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[reproductor-multimedia]] se desciende a este peldaño porque aquella nota define al códec en una sola línea, como el método que el reproductor usa para descomprimir lo guardado, y deja su funcionamiento sin desarrollar. Esta nota desarrolla exactamente ese punto: qué comprime, qué descomprime y por qué el reproductor no puede presentar los fragmentos sin ese paso. No conduce a ningún otro slug en este momento, porque el detalle de los contenedores, de los códecs concretos y de la salida a dispositivos concretos pertenece a notas aún no registradas y no puede enlazarse todavía.

## Límites de esta explicación
Esta nota no trata la sincronía entre audio y vídeo: cuándo debe presentarse cada fragmento para que el sonido coincida con la imagen queda en [[reproductor-multimedia]]. Tampoco desarrolla el funcionamiento de ningún códec concreto, ni los estándares que los especifican, ni el formato del contenedor que agrupa las pistas, ni cómo se mide el ahorro logrado; esas cuestiones quedan para notas futuras dedicadas a cada aspecto y no se enlazan aquí porque aún no existen como conceptos registrados.

## Referencias
- FTE-0001 (Operating Systems: Three Easy Pieces, Arpaci-Dusseau y Arpaci-Dusseau): respalda únicamente la idea general de que la aplicación se apoya en los servicios del sistema operativo en lugar de gestionar directamente el hardware, aplicada aquí a la lectura del archivo y a la entrega de la imagen y el sonido; no contiene el detalle técnico de la compresión ni de códecs concretos.
- FTE-0002 (Modern Operating Systems, Tanenbaum y Bos): respalda la misma distinción entre el programa de aplicación y los servicios del sistema en que aquel se apoya; no contiene el detalle técnico de la compresión ni de códecs concretos.
