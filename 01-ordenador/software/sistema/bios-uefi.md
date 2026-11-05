---
titulo: "BIOS/UEFI"
slug: bios-uefi
rama: software
categoria: sistema
nivel: 4
prerequisitos: [firmware]
conduce_a: [sistema-operativo]
alias: ["BIOS", "UEFI"]
estado: borrador
fuentes: [FTE-0003]
---

# BIOS/UEFI

## Idea central
BIOS/UEFI es el [[firmware]] principal de un ordenador: el programa grabado en la placa base que se ejecuta al encender el equipo, reconoce y prepara el [[hardware]] y localiza el programa que cargará el [[sistema-operativo]]. Sin él, el procesador no sabría qué dispositivos existen ni de dónde debe continuar el arranque.

## Antes de empezar
- [[firmware]]: el software grabado en el propio dispositivo, que actúa antes del sistema operativo. BIOS/UEFI es un caso concreto de firmware, el de la placa base.
- [[sistema-operativo]]: el programa que BIOS/UEFI debe encontrar y cederle el control para que administre el ordenador.

## Explicación
Al encender el ordenador, el procesador comienza ejecutando instrucciones guardadas en la propia placa base, no en un disco ni en la [[memoria-ram]]. Ese primer programa es BIOS/UEFI. Su nombre reúne dos generaciones de una misma función: el sistema básico de entrada/salida (Basic Input/Output System, BIOS), el esquema clásico, y la interfaz unificada extensible de firmware (Unified Extensible Firmware Interface, UEFI), su sucesora desarrollada por el foro UEFI. En ambos casos, el trabajo de fondo es el mismo y es el que se describe aquí; la diferencia de arquitectura interna entre uno y otro queda fuera de esta nota.

Su primera tarea es comprobar que el hardware esencial está presente y responde: procesador, memoria, dispositivos de almacenamiento y de entrada y salida. A esta comprobación inicial se la conoce como autoprueba de encendido. Si algún componente esencial falla, el equipo puede detenerse o avisar del error antes de continuar. Superada la comprobación, BIOS/UEFI inicializa la comunicación básica entre los componentes y aplica la configuración guardada por el usuario, como el orden preferido de arranque o la hora del sistema.

La segunda tarea, y la que lo conecta con el resto del software, es encontrar el sistema operativo. BIOS/UEFI consulta la configuración para saber de qué dispositivo debe arrancar —normalmente un disco— y busca en él el cargador de arranque, el pequeño programa que prepara el sistema operativo para su ejecución. Cuando lo localiza, le cede el control: a partir de ahí ya no es BIOS/UEFI quien gobierna el equipo, sino el sistema operativo, que asume la gestión general a través de su [[nucleo-kernel]].

En resumen, BIOS/UEFI ocupa el intervalo entre el encendido eléctrico y la entrada del sistema operativo. No administra aplicaciones ni organiza archivos: reconoce el hardware, lo deja en un estado mínimo utilizable y entrega el mando al siguiente programa.

## Cómo se conecta con lo anterior y lo siguiente
Desde [[firmware]] se pasa a su instancia principal en un ordenador: el firmware de la placa base que despierta con el equipo. BIOS/UEFI cumple esa función de puente, cerrando la etapa de preparación del hardware y abriendo la del [[sistema-operativo]], al que localiza y carga mediante su cargador de arranque. El orden queda así: primero el firmware prepara, después BIOS/UEFI reconoce y entrega, y solo entonces el sistema operativo toma el control general del ordenador.

## Límites de esta explicación
Esta nota no desarrolla la arquitectura interna de UEFI —sus protocolos, servicios de gráficos, arranque seguro o módulos en ejecutables portables—, ni el funcionamiento interno del cargador de arranque, ni cómo el [[nucleo-kernel]] gestiona los recursos una vez que el sistema operativo ya está en marcha. Cada uno de esos temas requiere su propia nota; aquí solo se explica el papel de BIOS/UEFI como eslabón entre el hardware y el sistema operativo.

## Referencias
Sin referencias registradas en `_registro/fuentes.md`. No se han añadido fuentes a esta nota.
