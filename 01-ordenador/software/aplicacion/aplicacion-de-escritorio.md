---
titulo: "Aplicación de escritorio"
slug: aplicacion-de-escritorio
rama: software
categoria: aplicacion
nivel: 4
prerequisitos: [software-de-aplicacion]
conduce_a: []
alias: ["aplicación de escritorio", "app de escritorio", "desktop application"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Aplicación de escritorio

## Idea central
La aplicación de escritorio es un programa de [[software-de-aplicacion]] instalado y ejecutado localmente en un ordenador personal, pensado para ser usado por una persona sentada ante él. Se distingue de una aplicación web o móvil porque su código reside en el propio equipo y se ejecuta en él como un [[proceso]] del [[sistema-operativo]].

## Antes de empezar
- [[software-de-aplicacion]]: qué es el software de aplicación y qué lo diferencia del software de sistema y del software de programación.

## Explicación
Desde [[software-de-aplicacion]] se sabe que una aplicación traduce una intención del usuario en operaciones ejecutadas por el sistema y le devuelve el resultado. Una aplicación de escritorio es una forma concreta de esa idea: está instalada en el ordenador personal —sus archivos forman parte del equipo, no de un servidor ajeno—, se lanza desde el entorno del sistema operativo y trabaja sobre los datos locales de ese equipo. El entorno de escritorio es, en esta nota, simplemente el conjunto de ventanas, menús y accesos con los que el sistema operativo presenta los programas instalados a la persona; no se desarrolla aquí cómo funciona ese entorno.

Al ejecutarse, la aplicación de escritorio funciona como cualquier otro programa de usuario: es un [[proceso]] que vive en el [[espacio-de-usuario]], separado del núcleo, y solo accede a los recursos del equipo —memoria, archivos, dispositivos— mediante servicios que le ofrece el sistema. Para pedir esos servicios utiliza [[llamadas-al-sistema]], es decir, el mecanismo por el que un programa de usuario solicita a [[nucleo-kernel]] una operación que él no puede hacer por sí mismo. La aplicación no gestiona directamente el hardware ni compite por él: es el sistema el que reparte los recursos en su nombre.

Ser «de escritorio» no describe qué hace la aplicación, sino dónde vive y cómo se ejecuta. Un editor de texto, un reproductor multimedia o un programa de cálculo pueden ser aplicaciones de escritorio si están instalados en el ordenador personal y se ejecutan en él, aunque existan versiones web o para otros dispositivos del mismo tipo de programa. Lo definitorio es la ejecución local y nativa en ese equipo: el código que se ejecuta es el código instalado, preparado para ese sistema operativo, y no un código que se descarga y corre dentro de un navegador, ni un programa instalado en un teléfono.

## Cómo se conecta con lo anterior y lo siguiente
El paso desde [[software-de-aplicacion]] a esta nota es de especialización: se pasa de «programas para el usuario» en general a una clase de ellos definida por su lugar de ejecución, el ordenador personal, y por su relación directa con el sistema operativo local. Esta nota no abre un peldaño siguiente en la cola: es una rama terminal que aclara una forma de aplicación, mientras que la forma en que presenta ventanas y controles se trata en [[aplicacion-grafica]] y su funcionamiento en red en [[aplicacion-con-red]], notas ya registradas y enlazables desde aquí.

## Límites de esta explicación
Esta nota no trata las aplicaciones móviles, pensadas para teléfonos y tabletas con pantallas táctiles y sistemas propios, ni las aplicaciones web, que se ejecutan en un servidor y se usan a través de un navegador; ambas quedan fuera por su lugar de ejecución y se proponen como conceptos nuevos. Tampoco desarrolla la interfaz gráfica en sí, que pertenece a [[aplicacion-grafica]], ni la comunicación en red, propia de [[aplicacion-con-red]], ni el funcionamiento del sistema al que se apoya, que pertenece a [[software-de-sistema]] y [[software-de-programacion]] para la creación de programas como este.

## Referencias
- [FTE-0001] Operating Systems: Three Easy Pieces — respalda que un programa de usuario se ejecuta como proceso en espacio de usuario y solicita servicios al sistema operativo mediante operaciones controladas.
- [FTE-0002] Modern Operating Systems — respalda la distinción entre el programa de usuario, que trabaja en espacio de usuario, y el núcleo, que gestiona los recursos del equipo en su nombre.
