# Registro canónico de conceptos

> Única fuente de verdad (§6). Sin entradas duplicadas. Propuesta inicial pendiente de validación: los slugs de aquí son los canónicos tras migración D-001.

## ordenador
- Nota canónica: [[ordenador]]
- Alias que deben apuntar aquí: computador, equipo, máquina de cómputo
- Cubre: definición general, ramas hardware/software
- No cubre (se trata en): [[hardware]], [[software]]

## hardware
- Nota canónica: [[hardware]]
- Alias que deben apuntar aquí: hardware
- Cubre: componentes físicos
- No cubre (se trata en): [[software]]

## software
- Nota canónica: [[software]]
- Alias que deben apuntar aquí: software, programa
- Cubre: componente intangible, 4 grupos
- No cubre (se trata en): [[software-de-sistema]], [[software-de-aplicacion]], [[software-de-programacion]], [[software-malicioso]]

## software-de-sistema
- Nota canónica: [[software-de-sistema]]
- Alias que deben apuntar aquí: software de sistema
- Cubre: sistema operativo, núcleo, firmware, controladores
- No cubre (se trata en): [[sistema-operativo]], [[nucleo-kernel]]

## sistema-operativo
- Nota canónica: [[sistema-operativo]]
- Alias que deben apuntar aquí: sistema operativo, OS
- Cubre: entorno integral, kernel como centro
- No cubre (se trata en): [[nucleo-kernel]], [[gestion-de-recursos]]

## nucleo-kernel
- Nota canónica: [[nucleo-kernel]]
- Alias que deben apuntar aquí: kernel, núcleo
- Cubre: control directo del hardware, coordinación de recursos
- No cubre (se trata en): [[gestion-de-recursos]]

## gestion-de-recursos
- Nota canónica: [[gestion-de-recursos]]
- Alias que deben apuntar aquí: gestión de recursos, resource management
- Cubre: asignación de CPU, memoria, dispositivos
- No cubre (se trata en): [[memoria-virtual]]

## memoria-ram
- Nota canónica: [[memoria-ram]]
- Alias que deben apuntar aquí: memoria RAM, La memoria
- Cubre: memoria principal volátil
- No cubre (se trata en): [[memoria-virtual]], [[memoria-cache]]

## memoria-virtual
- Nota canónica: [[memoria-virtual]]
- Alias que deben apuntar aquí: memoria virtual
- Cubre: abstracción de memoria por SO
- No cubre (se trata en): [[espacio-de-usuario]], [[espacio-de-kernel]]

## espacio-de-usuario
- Nota canónica: [[espacio-de-usuario]]
- Alias que deben apuntar aquí: user space
- Cubre: zona de procesos de usuario
- No cubre (se trata en): [[espacio-de-kernel]]

## espacio-de-kernel
- Nota canónica: [[espacio-de-kernel]]
- Alias que deben apuntar aquí: kernel space
- Cubre: zona privilegiada del núcleo
- No cubre (se trata en): [[espacio-de-usuario]]

## estructuras-de-datos
- Nota canónica: [[estructuras-de-datos]]
- Alias que deben apuntar aquí: estructuras de datos
- Cubre: organización de datos en memoria
- No cubre (se trata en): [[formatos-de-archivos]]

## formatos-de-archivos
- Nota canónica: [[formatos-de-archivos]]
- Alias que deben apuntar aquí: formatos de archivo
- Cubre: representación en disco de datos
- No cubre (se trata en): [[estructuras-de-datos]]

## lenguajes-de-programacion
- Nota canónica: [[lenguajes-de-programacion]]
- Alias que deben apuntar aquí: lenguajes de programación
- Cubre: lenguajes de alto nivel, Python como ejemplo
- No cubre (se trata en): [[lenguajes-compilados]], [[lenguajes-interpretados]]

## lenguajes-compilados
- Nota canónica: [[lenguajes-compilados]]
- Alias que deben apuntar aquí: lenguajes compilados
- Cubre: C como ejemplo, traducción antes de ejecución
- No cubre (se trata en): [[compilacion]]

## compilacion
- Nota canónica: [[compilacion]]
- Alias que deben apuntar aquí: compilación, compile
- Cubre: C → ensamblador → código máquina
- No cubre (se trata en): [[lenguaje-ensamblador]], [[codigo-maquina]]

## lenguaje-ensamblador
- Nota canónica: [[lenguaje-ensamblador]]
- Alias que deben apuntar aquí: lenguaje ensamblador, assembly
- Cubre: instrucciones simbólicas
- No cubre (se trata en): [[codigo-maquina]]

## codigo-maquina
- Nota canónica: [[codigo-maquina]]
- Alias que deben apuntar aquí: código máquina, machine code
- Cubre: ceros y unos ejecutables
- No cubre (se trata en): [[conjunto-de-instrucciones-isa]]

## software-de-aplicacion
- Nota canónica: [[software-de-aplicacion]]
- Alias que deben apuntar aquí: software de aplicación, aplicaciones
- Cubre: programas para el usuario
- No cubre (se trata en): [[software-de-sistema]]

## software-de-programacion
- Nota canónica: [[software-de-programacion]]
- Alias que deben apuntar aquí: software de programación, herramientas
- Cubre: compiladores, intérpretes, IDEs
- No cubre (se trata en): [[compilador]], [[interprete]]

## software-malicioso
- Nota canónica: [[software-malicioso]]
- Alias que deben apuntar aquí: software malicioso, malware
- Cubre: clasificación técnica y defensa
- No cubre (se trata en): [[malware]], [[vulnerabilidades]]

## firmware
- Nota canónica: [[firmware]]
- Alias que deben apuntar aquí: firmware
- Cubre: software grabado en dispositivo, arranque previo a SO
- No cubre: [[bios-uefi]], [[controladores-drivers]]

## bios-uefi
- Nota canónica: [[bios-uefi]]
- Alias que deben apuntar aquí: BIOS, UEFI
- Cubre: firmware placa base, reconocimiento HW y carga SO
- No cubre: detalle UEFI avanzado

## sistema-de-archivos
- Nota canónica: [[sistema-de-archivos]]
- Alias que deben apuntar aquí: sistema de archivos, filesystem
- Cubre: organización persistente, archivos y carpetas, rutas
- No cubre: [[tipos-de-sistema-de-archivos]], [[formatos-de-archivos]]

## controladores-drivers
- Nota canónica: [[controladores-drivers]]
- Alias que deben apuntar aquí: controladores, drivers
- Cubre: enseñan al SO a manejar dispositivos
- No cubre: [[firmware]]

## herramientas-de-sistema
- Nota canónica: [[herramientas-de-sistema]]
- Alias que deben apuntar aquí: herramientas de sistema, utilidades de sistema
- Cubre: diagnóstico, backup, shell
- No cubre: [[shell]], [[copia-de-seguridad]]

## cargador-de-arranque
- Nota canónica: [[cargador-de-arranque]]
- Alias que deben apuntar aquí: cargador de arranque, boot loader, gestor de arranque
- Cubre: puente BIOS/UEFI → SO, carga SO en memoria
- No cubre: [[bios-uefi]], cargadores de programas

## tipos-de-sistema-de-archivos
- Nota canónica: [[tipos-de-sistema-de-archivos]]
- Alias que deben apuntar aquí: tipos de sistema de archivos, filesystem types
- Cubre: ext4, NTFS, FAT32 generales
- No cubre: [[journaling]], [[permisos-de-archivos]]

## permisos-de-archivos
- Nota canónica: [[permisos-de-archivos]]
- Alias que deben apuntar aquí: permisos de archivo, file permissions
- Cubre: quién puede leer/escribir, propietario
- No cubre: [[tipos-de-sistema-de-archivos]]

## journaling
- Nota canónica: [[journaling]]
- Alias que deben apuntar aquí: diario de cambios, journaling
- Cubre: diario de cambios para consistencia ante corte
- No cubre: detalle ext4/NTFS interno

## gestor-de-procesos
- Nota canónica: [[gestor-de-procesos]]
- Alias que deben apuntar aquí: gestor de procesos, process scheduler
- Cubre: turnos CPU, prioridades
- No cubre: [[proceso]], [[gestion-de-recursos]]

## gestor-de-memoria
- Nota canónica: [[gestor-de-memoria]]
- Alias que deben apuntar aquí: gestor de memoria, memory manager
- Cubre: reparto memoria entre programas, recuperación
- No cubre: [[memoria-virtual]]

## proceso
- Nota canónica: [[proceso]]
- Alias que deben apuntar aquí: proceso, process
- Cubre: programa en ejecución con estado propio
- No cubre: [[planificador]], [[cambio-de-contexto]]

## planificador
- Nota canónica: [[planificador]]
- Alias que deben apuntar aquí: planificador, scheduler
- Cubre: política de ordenación de turnos
- No cubre: [[cambio-de-contexto]]

## cambio-de-contexto
- Nota canónica: [[cambio-de-contexto]]
- Alias que deben apuntar aquí: cambio de contexto, context switch
- Cubre: guardar/cargar estado al pasar procesos
- No cubre: [[planificador]]

## llamadas-al-sistema
- Nota canónica: [[llamadas-al-sistema]]
- Alias que deben apuntar aquí: system calls
- Cubre: petición-respuesta programa→núcleo
- No cubre: [[interrupciones]]

## interrupciones
- Nota canónica: [[interrupciones]]
- Alias que deben apuntar aquí: interrupt
- Cubre: señal hardware que suspende y cede control
- No cubre: detalle registros

## paginacion
- Nota canónica: [[paginacion]]
- Alias que deben apuntar aquí: paginación, paging
- Cubre: páginas fijas, tabla por programa, traducción
- No cubre: [[segmentacion]]

## segmentacion
- Nota canónica: [[segmentacion]]
- Alias que deben apuntar aquí: segmentación, segmentation
- Cubre: segmentos variables
- No cubre: [[paginacion]]

## pila
- Nota canónica: [[pila]]
- Alias que deben apuntar aquí: pila LIFO
- Cubre: LIFO, inserción/eliminación por cima
- No cubre: [[cola-fifo]], [[arbol]]

## cola-fifo
- Nota canónica: [[cola-fifo]]
- Alias que deben apuntar aquí: cola FIFO, first in, first out
- Cubre: FIFO, orden de llegada
- No cubre: [[pila]]

## arbol
- Nota canónica: [[arbol]]
- Alias que deben apuntar aquí: árbol
- Cubre: jerarquía padre/hijos/raíz/hojas
- No cubre: [[tabla-hash]]

## tabla-hash
- Nota canónica: [[tabla-hash]]
- Alias que deben apuntar aquí: tabla hash, tabla de dispersión, hash table
- Cubre: búsqueda por clave con dispersión
- No cubre: colisiones detalle

## aplicacion-grafica
- Nota canónica: [[aplicacion-grafica]]
- Alias que deben apuntar aquí: aplicación gráfica, graphical application
- Cubre: GUI, ventana, editor como ejemplo
- No cubre: [[aplicacion-con-red]]

## aplicacion-con-red
- Nota canónica: [[aplicacion-con-red]]
- Alias que deben apuntar aquí: aplicación en red, aplicación de red, network application
- Cubre: cliente-servidor, red mínima
- No cubre: [[aplicacion-grafica]]

## malware
- Nota canónica: [[malware]]
- Alias que deben apuntar aquí: programa malicioso, código malicioso
- Cubre: clasificación por propagación/ocultamiento/objetivo
- No cubre: [[vulnerabilidades]], [[exploits]]

## vulnerabilidades
- Nota canónica: [[vulnerabilidades]]
- Alias que deben apuntar aquí: vulnerabilidad, vulnerability
- Cubre: defectos que permiten uso no previsto
- No cubre: [[exploits]], [[malware]]
