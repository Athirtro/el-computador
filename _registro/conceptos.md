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

## tabla-de-paginas
- Nota canónica: [[tabla-de-paginas]]
- Alias que deben apuntar aquí: tabla de páginas, page table
- Cubre: correspondencia página virtual → marco físico, bits presencia/protección
- No cubre: [[fallo-de-pagina]]

## fallo-de-pagina
- Nota canónica: [[fallo-de-pagina]]
- Alias que deben apuntar aquí: fallo de página, page fault
- Cubre: página no cargada, traer a marco
- No cubre: [[tabla-de-paginas]]

## funcion-de-dispersion
- Nota canónica: [[funcion-de-dispersion]]
- Alias que deben apuntar aquí: función de dispersión, hash function
- Cubre: clave→posición, reparto uniforme
- No cubre: [[colision-en-tabla-hash]]

## colision-en-tabla-hash
- Nota canónica: [[colision-en-tabla-hash]]
- Alias que deben apuntar aquí: colisión hash, hash collision
- Cubre: dos claves misma posición, resolución
- No cubre: [[funcion-de-dispersion]]

## usuario-de-sistema
- Nota canónica: [[usuario-de-sistema]]
- Alias que deben apuntar aquí: cuenta de usuario, user account
- Cubre: cuenta, grupos, propietario
- No cubre: [[permisos-de-archivos]]

## shell
- Nota canónica: [[shell]]
- Alias que deben apuntar aquí: intérprete de órdenes, shell
- Cubre: órdenes texto, scripting
- No cubre: sintaxis concreta

## copia-de-seguridad
- Nota canónica: [[copia-de-seguridad]]
- Alias que deben apuntar aquí: copia de seguridad, backup
- Cubre: completa/incremental/diferencial, restauración
- No cubre: [[journaling]]

## diagnostico-de-sistema
- Nota canónica: [[diagnostico-de-sistema]]
- Alias que deben apuntar aquí: diagnóstico de sistema, herramienta de diagnóstico
- Cubre: observar–comparar–localizar
- No cubre: reparación física

## hilos-concurrencia
- Nota canónica: [[hilos-concurrencia]]
- Alias que deben apuntar aquí: hilo, thread, concurrencia
- Cubre: hilos dentro de proceso, compartición memoria
- No cubre: [[multitarea]]

## multitarea
- Nota canónica: [[multitarea]]
- Alias que deben apuntar aquí: multitarea, multitasking
- Cubre: varios procesos a la vez, cooperativa/preventiva
- No cubre: [[hilos-concurrencia]]

## modo-privilegiado
- Nota canónica: [[modo-privilegiado]]
- Alias que deben apuntar aquí: modo privilegiado, privileged mode, modo kernel, modo supervisor
- Cubre: acceso sin permiso a memoria/hardware
- No cubre: detalle registros

## comprobacion-de-consistencia
- Nota canónica: [[comprobacion-de-consistencia]]
- Alias que deben apuntar aquí: file system check, fsck
- Cubre: fsck, fases de comprobación
- No cubre: [[journaling]]

## bloque-de-control-de-proceso
- Nota canónica: [[bloque-de-control-de-proceso]]
- Alias que deben apuntar aquí: bloque de control de proceso, process control block, PCB
- Cubre: ficha PCB, estado guardable
- No cubre: [[planificador]]

## sincronizacion-de-hilos
- Nota canónica: [[sincronizacion-de-hilos]]
- Alias: sincronización, synchronization, coordinación de hilos
- Cubre: exclusión mutua, cerrojo/semáforo
- No cubre: [[multitarea]]

## multitarea-cooperativa
- Nota canónica: [[multitarea-cooperativa]]
- Alias: multitarea cooperativa, cooperative multitasking
- Cubre: cesión voluntaria procesador
- No cubre: [[multitarea-preventiva]]

## multitarea-preventiva
- Nota canónica: [[multitarea-preventiva]]
- Alias: multitarea preventiva, preemptive multitasking
- Cubre: interrupción forzada por núcleo
- No cubre: [[multitarea-cooperativa]]

## estado-de-proceso
- Nota canónica: [[estado-de-proceso]]
- Alias: estado de proceso, process state
- Cubre: listo/ejecución/bloqueado
- No cubre: [[planificador]]

## identificador-de-proceso
- Nota canónica: [[identificador-de-proceso]]
- Alias: identificador de proceso, process identifier, PID
- Cubre: PID único entre vivos
- No cubre: [[bloque-de-control-de-proceso]]

## tabla-de-paginas-multinivel
- Nota canónica: [[tabla-de-paginas-multinivel]]
- Alias: tabla de páginas multinivel, multi-level page table
- Cubre: tablas intermedias que indexan tablas
- No cubre: [[tlb]]

## sustitucion-de-paginas
- Nota canónica: [[sustitucion-de-paginas]]
- Alias: sustitución de páginas, page replacement
- Cubre: víctima óptima/FIFO/LRU, limpia vs modificada
- No cubre: [[tabla-de-paginas]]

## tlb
- Nota canónica: [[tlb]]
- Alias: TLB, translation lookaside buffer
- Cubre: caché traducciones
- No cubre: [[tabla-de-paginas]]

## entrada-de-pagina
- Nota canónica: [[entrada-de-pagina]]
- Alias: entrada de página, page table entry
- Cubre: marco + bits por entrada
- No cubre: [[tlb]]

## bit-de-presencia
- Nota canónica: [[bit-de-presencia]]
- Alias: bit de presencia, bit de validez, present bit
- Cubre: presencia/validez
- No cubre: [[tlb]]

## encadenamiento-en-tabla-hash
- Nota canónica: [[encadenamiento-en-tabla-hash]]
- Alias: encadenamiento, separate chaining
- Cubre: listas por posición
- No cubre: [[sondeo-en-tabla-hash]]

## sondeo-en-tabla-hash
- Nota canónica: [[sondeo-en-tabla-hash]]
- Alias: direccionamiento abierto, open addressing
- Cubre: siguiente posición libre
- No cubre: [[encadenamiento-en-tabla-hash]]

## inodo
- Nota canónica: [[inodo]]
- Alias: inode
- Cubre: metadatos por archivo
- No cubre: [[mapa-de-bloques-libres]]

## mapa-de-bloques-libres
- Nota canónica: [[mapa-de-bloques-libres]]
- Alias: mapa de bloques libres, free block bitmap
- Cubre: tabla bloques ocupados/libres
- No cubre: [[inodo]]

## registro-de-eventos
- Nota canónica: [[registro-de-eventos]]
- Alias: registro de eventos, event log
- Cubre: historia cronológica para diagnóstico
- No cubre: detalle herramientas

## terminal-de-texto
- Nota canónica: [[terminal-de-texto]]
- Alias: terminal, consola de texto
- Cubre: superficie texto para shell
- No cubre: [[shell]]

## registro-de-usuarios
- Nota canónica: [[registro-de-usuarios]]
- Alias: base de datos de usuarios, user database
- Cubre: persistencia cuentas/grupos
- No cubre: [[permisos-de-archivos]]

## pila-de-llamadas
- Nota canónica: [[pila-de-llamadas]]
- Alias: pila de ejecución, call stack
- Cubre: marcos, retorno, desbordamiento
- No cubre: [[pila]]

## cola-de-listos
- Nota canónica: [[cola-de-listos]]
- Alias: cola de listos, ready queue
- Cubre: competidores ordenados para planificador
- No cubre: [[cuanto-de-tiempo]]

## cuanto-de-tiempo
- Nota canónica: [[cuanto-de-tiempo]]
- Alias: cuanto de tiempo, time slice
- Cubre: intervalo de turno en rotativo
- No cubre: [[planificador]]

## arbol-binario
- Nota canónica: [[arbol-binario]]
- Alias: árbol binario, binary tree
- Cubre: 2 hijos izquierdo/derecho
- No cubre: [[arbol-equilibrado]]

## arbol-equilibrado
- Nota canónica: [[arbol-equilibrado]]
- Alias: árbol equilibrado, balanced tree
- Cubre: altura acotada
- No cubre: detalle rotaciones

## modo-no-privilegiado
- Nota canónica: [[modo-no-privilegiado]]
- Alias: modo no privilegiado, user mode, modo usuario
- Cubre: modo usuario
- No cubre: [[modo-privilegiado]]

## ejecucion-de-archivos
- Nota canónica: [[ejecucion-de-archivos]]
- Alias: permiso de ejecución, execute permission
- Cubre: tercer permiso, ejecutar frente a leer
- No cubre: [[permisos-de-archivos]]

## ext4
- Nota canónica: [[ext4]]
- Alias: sistema de archivos ext4, fourth extended filesystem
- Cubre: ext4 Linux, grandes, journaling
- No cubre: [[ntfs]], [[fat32]]

## ntfs
- Nota canónica: [[ntfs]]
- Alias: sistema de archivos NTFS, New Technology File System
- Cubre: NTFS Windows, MFT
- No cubre: [[ext4]]

## fat32
- Nota canónica: [[fat32]]
- Alias: File Allocation Table 32
- Cubre: FAT32 compatible, límite 4GB
- No cubre: [[ext4]], [[ntfs]]

## seguridad-aplicacion-con-red
- Nota canónica: [[seguridad-aplicacion-con-red]]
- Alias: seguridad en aplicación de red, seguridad en red a nivel de aplicación
- Cubre: autenticación/cifrado en tránsito
- No cubre: [[defensa-malware]]

## arbol-equilibrado
- Nota canónica: [[arbol-equilibrado]]
- Alias: árbol equilibrado, balanced tree
- Cubre: altura acotada
- No cubre: detalle rotaciones

## sincronizacion-entre-procesos
- Nota canónica: [[sincronizacion-entre-procesos]]
- Alias: coordinación entre procesos, interprocess synchronization
- Cubre: exclusión entre procesos vía núcleo
- No cubre: detalle interbloqueo

## interbloqueo
- Nota canónica: [[interbloqueo]]
- Alias: deadlock, bloqueo mutuo
- Cubre: esperas circulares, deadlock
- No cubre: sincronización general

## manejo-de-interrupciones
- Nota canónica: [[manejo-de-interrupciones]]
- Alias: manejador de interrupciones, interrupt handler
- Cubre: rutina + prioridades
- No cubre: detalle registros

## instruccion-privilegiada
- Nota canónica: [[instruccion-privilegiada]]
- Alias: instrucción privilegiada, privileged instruction
- Cubre: solo modo privilegiado
- No cubre: detalle registros

## credenciales
- Nota canónica: [[credenciales]]
- Alias: nombre de usuario y contraseña, credentials
- Cubre: secreto + custodia
- No cubre: [[autenticacion]]

## autenticacion
- Nota canónica: [[autenticacion]]
- Alias: autenticación de usuario, authentication
- Cubre: contraste identidad local/remota
- No cubre: autorización

## tabla-maestra-de-archivos
- Nota canónica: [[tabla-maestra-de-archivos]]
- Alias: Master File Table, MFT
- Cubre: MFT, entradas numeradas
- No cubre: detalle atributos

## lista-de-control-de-acceso
- Nota canónica: [[lista-de-control-de-acceso]]
- Alias: ACL, access control list
- Cubre: ACL, usuarios/grupos/acciones
- No cubre: detalle MFT

## extent
- Nota canónica: [[extent]]
- Alias: extensión contigua, extent
- Cubre: rango contiguo de bloques
- No cubre: detalle interno ext4

## registro-de-eventos-detalle
- Nota canónica: [[registro-de-eventos-detalle]]
- Alias: formato de entrada de registro, niveles de gravedad del registro, filtrado del registro de eventos
- Cubre: entradas, gravedad, filtro
- No cubre: sintaxis herramienta
