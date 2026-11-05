---
titulo: "Entorno de escritorio"
slug: entorno-de-escritorio
rama: software
categoria: aplicacion
nivel: 5
prerequisitos: [aplicacion-de-escritorio]
conduce_a: [aplicacion-grafica]
alias: ["entorno de escritorio", "desktop environment"]
estado: borrador
fuentes: [FTE-0001, FTE-0002]
---

# Entorno de escritorio

## Idea central
El entorno de escritorio es el conjunto organizado de [[ventana|ventanas]], menús, accesos e iconos con el que el [[sistema-operativo]] presenta las [[aplicacion-de-escritorio|aplicaciones de escritorio]] instaladas de forma coherente. No es una aplicación más: es el marco compartido que permite lanzarlas, verlas a la vez y pasar de una a otra.

## Antes de empezar
- [[aplicacion-de-escritorio]]: qué es una aplicación de escritorio y cómo se ejecuta como [[proceso]] en el [[espacio-de-usuario]] bajo control del [[sistema-operativo]].

## Explicación
El prerequisito establece que una aplicación de escritorio se instala en el equipo, se ejecuta directamente en él y recibe recursos del sistema. El entorno de escritorio es el peldaño siguiente: el sistema no se limita a ejecutar esas aplicaciones una a una en silencio, sino que les ofrece un marco visual común para convivir en pantalla. Ese marco es lo que esta nota describe a nivel de sistema, sin entrar en el diseño interno de cada aplicación.

Concretamente, el entorno combina tres piezas. La primera es la superficie de trabajo, a veces llamada simplemente escritorio, donde se colocan accesos directos a programas, carpetas y archivos. La segunda es el conjunto de ventanas de las aplicaciones en ejecución: cada [[ventana]] es un rectángulo delimitado que presenta una parte del estado de una aplicación, con su propio marco y barra de título, y el entorno decide cómo se apilan, se mueve y se activa cada una. La tercera es el panel o barra principal, desde el que se lanzan aplicaciones, se consultan menús de acceso y se cambia entre sesiones o escritorios virtuales. El conjunto forma parte de la [[interfaz-grafica-de-usuario]], pero tiene identidad propia: la interfaz gráfica describe los elementos visuales en general, mientras que el entorno de escritorio es la organización concreta de esos elementos para todas las aplicaciones a la vez.

Varias aplicaciones colaboran en ese marco. La [[gestion-de-ventanas]] se encarga de colocar las ventanas, mantener su orden de profundidad y entregar el foco a la que está delante. El [[gestor-de-archivos-grafico]] ofrece una ventana especializada para recorrer carpetas y archivos. El menú de inicio o de aplicaciones enumera los programas instalados. Ninguna de estas piezas trabaja sola: comparten criterios de presentación —botones, campos de entrada y otros [[widget|widgets]] con aspecto y comportamiento reconocibles— para que quien usa el equipo no tenga que reaprender cada aplicación desde cero. Esa uniformidad es precisamente la función del entorno: ofrecer un lenguaje visual y de interacción estable sobre el que cada aplicación construye su contenido.

Todo lo anterior se ejecuta como cualquier otro programa de usuario: es un [[proceso]] que vive en el [[espacio-de-usuario]] y solicita servicios al núcleo mediante [[llamadas-al-sistema]]. El entorno no gestiona directamente el hardware; pide memoria, entradas de teclado y ratón y salida gráfica al sistema, que los reparte en su nombre como con cualquier otro proceso.

## Cómo se conecta con lo anterior y lo siguiente
El paso desde [[aplicacion-de-escritorio]] al entorno de escritorio es de marco: la aplicación individual adquiere un escenario compartido donde sus ventanas se presentan junto a otras y se conmutan sin perder el contexto. El paso siguiente es hacia [[aplicacion-grafica]], donde se trata el funcionamiento de las ventanas y los controles que el entorno organiza, pero desde el punto de vista de la aplicación que los crea y los atiende.

## Límites de esta explicación
Esta nota no trata el detalle de cada [[ventana]] ni de cada [[widget]], que pertenecen a sus notas canónicas, ni la gestión fina de apilamiento y foco, propia de [[gestion-de-ventanas]]. Tampoco trata aplicaciones concretas como editores de texto o navegadores, ni los entornos de escritorio de sistemas móviles o de consola, fuera del ordenador personal de escritorio.

## Referencias
- [FTE-0001] Operating Systems: Three Easy Pieces — respalda que el entorno se ejecuta como proceso en espacio de usuario y solicita recursos al sistema mediante operaciones controladas.
- [FTE-0002] Modern Operating Systems — respalda la distinción entre el programa de usuario y el núcleo: el entorno no accede al hardware, sino que el núcleo reparte los recursos en su nombre.
