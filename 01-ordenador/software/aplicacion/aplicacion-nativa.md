---
titulo: "Aplicación nativa"
slug: aplicacion-nativa
rama: software
categoria: aplicacion
nivel: 5
prerequisitos: [aplicacion-de-escritorio]
conduce_a: []
alias: ["aplicación nativa", "app nativa", "native application"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Aplicación nativa

## Idea central
La aplicación nativa es una aplicación de [[aplicacion-de-escritorio]] que se distribuye como un paquete instalado en el dispositivo y que se ejecuta directamente en él, con código construido específicamente para su sistema operativo y su procesador. Importa porque su forma de ejecución determina qué servicios puede pedir al sistema, qué datos controla y con qué rapidez y autonomía trabaja.

## Antes de empezar
- [[aplicacion-de-escritorio]]: qué es una aplicación instalada y ejecutada localmente en un ordenador personal, como [[proceso]] en el [[espacio-de-usuario]] que accede a los recursos mediante [[llamadas-al-sistema]] solicitadas a [[nucleo-kernel]].

## Explicación
Desde [[aplicacion-de-escritorio]] se sabe que el programa vive en el equipo y se ejecuta en él. «Nativa» añade una precisión sobre cómo está construida y distribuida esa aplicación: su paquete se instala en el dispositivo —no se descarga en cada uso para correr dentro de otra aplicación—, y su código está preparado para la plataforma de destino, es decir, para el [[sistema-operativo]] concreto y para el procesador de ese equipo. La aplicación no necesita un intérprete alojado en un navegador ni un entorno genérico que la traduzca en tiempo de ejecución; cuando el usuario la lanza, el sistema carga directamente sus instrucciones como un proceso más.

Al correr como proceso en el [[espacio-de-usuario]], la aplicación nativa utiliza los servicios que [[sistema-operativo]] ofrece a los programas de usuario: reserva de memoria, acceso a archivos del [[sistema-de-archivos]] y comunicación con dispositivos a través de [[controladores-drivers]]. No accede por sí misma al hardware ni gestiona los recursos compartidos; los pide mediante [[llamadas-al-sistema]] y es el núcleo el que los reparte y protege. Por eso ser nativa no significa ser privilegiada: sigue siendo un programa sin acceso directo al hardware, pero con permiso para usarlo a través del sistema cuando lo necesita.

Esta forma de ejecución también implica instalación y actualización por paquetes: el usuario la instala, o la instala un administrador, en el almacén del dispositivo, y las actualizaciones sustituyen el paquete instalado. Al estar construida para una plataforma concreta, la misma función puede exigir un paquete distinto para otro sistema operativo, porque cada uno ofrece servicios y formatos de ejecución diferentes y el código nativo debe corresponder a ellos. El precio de esa adaptación directa es la pérdida de portabilidad automática: la aplicación se aprovecha de las características del equipo concreto, pero no corre sin cambios en otro sistema distinto.

## Cómo se conecta con lo anterior y lo siguiente
El paso desde [[aplicacion-de-escritorio]] a esta nota es de especialización dentro del mismo peldaño de abstracción: se pasa de «programa instalado y ejecutado en el ordenador personal» a «programa instalado cuya construcción responde a esa plataforma y que se ejecuta directamente en ella». Esta nota no abre un peldaño siguiente, por lo que `conduce_a` queda vacío; es una rama de aclaración sobre la forma de distribución y ejecución, mientras que la forma de presentar ventanas y controles se trata en [[aplicacion-grafica]] y el uso de la red en [[aplicacion-con-red]].

## Límites de esta explicación
Esta nota no trata las aplicaciones híbridas, que combinan una envoltura instalada en el dispositivo con la presentación de contenido web, porque combinan dos formas de ejecución que merecen una nota propia. Tampoco desarrolla la [[aplicacion-web]], que se ejecuta en un servidor y se usa a través de [[navegador-web]] sin instalarse en el dispositivo, ni la [[aplicacion-movil]], pensada para teléfonos y tabletas con pantallas táctiles y sistemas propios, ni cómo se construye el código nativo a partir de un [[lenguaje-de-programacion]], tema que pertenece a la rama de programación.

## Referencias
- [FTE-0001] Operating Systems: Three Easy Pieces — respalda que un programa de usuario se ejecuta como proceso en espacio de usuario y solicita servicios al sistema operativo mediante operaciones controladas.
- [FTE-0002] Modern Operating Systems — respalda la distinción entre el programa de usuario, que trabaja en espacio de usuario, y el núcleo, que gestiona los recursos del equipo en su nombre.
