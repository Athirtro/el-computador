---
titulo: "Componente web incorporado"
slug: componente-web-incorporado
rama: software
categoria: aplicacion
nivel: 6
prerequisitos: [aplicacion-hibrida]
conduce_a: [puente-nativo]
alias: ["componente web incorporado", "vista web incorporada"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Componente web incorporado

## Idea central
El componente web incorporado es un [[widget]] que incrusta el motor de un [[navegador-web]] dentro de una [[aplicacion-hibrida]] sin ser un navegador completo. Interpreta y presenta contenido web en un área reservada de la pantalla de la aplicación anfitriona, y es el peldaño que convierte la definición abstracta de «vista web» de la nota anterior en un objeto concreto de la interfaz.

## Antes de empezar
- [[aplicacion-hibrida]]: aplicación instalada cuya parte web necesita un componente que la renderice dentro de su propia ventana.

## Explicación
Desde [[aplicacion-hibrida]] se sabe que el programa anfitrión es un [[proceso]] más en [[espacio-de-usuario]], instalado y lanzado por el [[sistema-operativo]], y que dentro de él la parte web no se abre en un [[navegador-web]] independiente. El componente web incorporado es precisamente el lugar donde esa parte web se muestra: la aplicación anfitriona crea el componente, le asigna un rectángulo dentro de su [[ventana]] o pantalla, y a partir de ahí el componente se comporta como cualquier otro [[widget]], recibiendo [[eventos-de-interfaz]] y presentando su contenido en ese espacio.

Por dentro, el componente reutiliza el mismo motor que el [[navegador-web]] completo: interpreta un documento descrito con un [[lenguaje-de-descripcion-de-documentos]], ejecuta en su interior el código de un [[lenguaje-de-programacion-web]] mediante su [[interprete-del-navegador]], que construye un [[modelo-de-objetos-del-documento]] vivo que la aplicación puede recorrer. Puede cargar ese documento desde una [[direccion-web]] remota mediante el [[protocolo-http]], o desde un recurso incluido con la aplicación, y al mostrarlo lo hace sin añadir los elementos propios de un navegador completo: no tiene barra de direcciones, ni lista de pestañas, ni menú de navegación. Esas piezas, cuando existen, las aporta la aplicación anfitriona o no existen.

La diferencia con un navegador completo no está en el motor, sino en el control. En [[navegador-web]] el programa es el dueño de la ventana, de la navegación y de la carga; en el componente incorporado, el dueño es la aplicación anfitriona, que decide qué dirección cargar, cuándo recargar y qué parte de la pantalla ocupa el contenido. El componente, por sí solo, sigue siendo parte del mismo proceso de usuario y no accede a los recursos del equipo por su cuenta: todo acceso al sistema pasa por la envoltura de la aplicación anfitriona y, en última instancia, por las [[llamadas-al-sistema]] ordinarias.

## Cómo se conecta con lo anterior y lo siguiente
El paso desde [[aplicacion-hibrida]] es de concreción: la nota anterior nombra una vista web incorporada como mecanismo de renderizado, y esta nota la define como un [[widget]] con motor de navegador embebido, sin interfaz de navegador. El paso siguiente es el puente: una vez que el contenido web ya se renderiza y ejecuta dentro del componente, queda por explicar cómo ese contenido, que vive aislado dentro del proceso, pide a la parte nativa que realice operaciones del equipo y recibe la respuesta. Ese puente no se desarrolla aquí.

## Límites de esta explicación
Queda fuera el puente que comunica el contenido web del componente con las funciones nativas del equipo, que se trata en puente-nativo, siguiente peldaño de la cadena. También quedan fuera el navegador completo como aplicación independiente, tratado en [[navegador-web]], y la aplicación web que se ejecuta en ese navegador sin estar instalada, tratada en [[aplicacion-web]]. Tampoco se detallan las reglas de presentación visual del documento ni los mecanismos internos del motor de renderizado.

## Referencias
- [FTE-0001] Operating Systems: Three Easy Pieces — respalda que el componente vive dentro del mismo proceso de usuario de la aplicación anfitriona y queda sujeto a los servicios controlados del sistema operativo.
- [FTE-0002] Modern Operating Systems — respalda la distinción entre programa de usuario y núcleo, base para afirmar que el componente no accede directamente a los recursos del equipo.
