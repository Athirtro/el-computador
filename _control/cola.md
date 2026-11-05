# Cola - Temas pendientes en orden de prerequisitos

1. [[ordenador]] — prerequisitos: [] → conduce_a: [software, hardware]
2. [[software]] — prerequisitos: [ordenador] → conduce_a: [software-de-sistema, software-de-aplicacion, software-de-programacion, software-malicioso] (borrador entregado)
3. [[hardware]] — prerequisitos: [ordenador] → conduce_a: [procesador, memoria-ram]
4. [[software-de-sistema]] — prerequisitos: [software] → conduce_a: [sistema-operativo, firmware, bios-uefi, sistema-de-archivos, controladores-drivers] (borrador entregado, sin fuentes)
4b. [[software-de-aplicacion]] — prerequisitos: [software] → conduce_a: [aplicacion-grafica, aplicacion-con-red] (borrador entregado, sin fuentes)
4c. [[software-de-programacion]] — prerequisitos: [software] → conduce_a: [lenguajes-de-programacion, compilador, interprete] (borrador entregado, circularidad corregida: prerequisito solo [software])
4d. [[software-malicioso]] — prerequisitos: [software] → conduce_a: [malware, vulnerabilidades, exploits, defensa-malware] (borrador entregado, sin fuentes)
5. [[sistema-operativo]] — prerequisitos: [software-de-sistema] → conduce_a: [nucleo-kernel, sistema-de-archivos, controladores-drivers] (borrador entregado, sin fuentes)
5a. [[firmware]] — prerequisitos: [software-de-sistema] → conduce_a: [bios-uefi] (borrador entregado, sin fuentes)
6. [[nucleo-kernel]] — prerequisitos: [sistema-operativo] → conduce_a: [gestion-de-recursos] (borrador entregado, sin fuentes)
6a. [[bios-uefi]] — prerequisitos: [firmware] → conduce_a: [sistema-operativo] (borrador entregado, sin fuentes)
6b. [[sistema-de-archivos]] — prerequisitos: [sistema-operativo] → conduce_a: [estructuras-de-datos, formatos-de-archivos] (borrador entregado, sin fuentes)
6c. [[controladores-drivers]] — prerequisitos: [sistema-operativo] → conduce_a: [] (borrador entregado, rama terminal)
6d. [[estructuras-de-datos]] — prerequisitos: [sistema-operativo] → conduce_a: [formatos-de-archivos] (borrador entregado, sin fuentes)
7. [[gestion-de-recursos]] — prerequisitos: [nucleo-kernel] → conduce_a: [gestor-de-procesos, gestor-de-memoria] (borrador entregado, sin fuentes)
7a. [[formatos-de-archivos]] — prerequisitos: [estructuras-de-datos, sistema-de-archivos] → conduce_a: [] (borrador entregado, sin fuentes, rama terminal)
8. [[gestor-de-procesos]] — prerequisitos: [gestion-de-recursos] → conduce_a: [] (borrador entregado, sin fuentes)
8a. [[gestor-de-memoria]] — prerequisitos: [gestion-de-recursos] → conduce_a: [memoria-virtual] (borrador entregado, sin fuentes)
8b. [[memoria-virtual]] — prerequisitos: [gestor-de-memoria] → conduce_a: [espacio-de-usuario, espacio-de-kernel, paginacion, segmentacion] (borrador entregado, sin fuentes)
8c. [[proceso]] — prerequisitos: [gestor-de-procesos] → conduce_a: [planificador, cambio-de-contexto] (borrador entregado, sin fuentes)
8d. [[planificador]] — prerequisitos: [proceso] → conduce_a: [] (borrador entregado, sin fuentes)
8e. [[cambio-de-contexto]] — prerequisitos: [proceso] → conduce_a: [] (borrador entregado, sin fuentes)
8f. [[llamadas-al-sistema]] — prerequisitos: [nucleo-kernel] → conduce_a: [interrupciones] (borrador entregado, sin fuentes)
8g. [[interrupciones]] — prerequisitos: [llamadas-al-sistema] → conduce_a: []
8h. [[herramientas-de-sistema]] — prerequisitos: [software-de-sistema] → conduce_a: [] (borrador entregado, rama terminal)
8i. [[cargador-de-arranque]] — prerequisitos: [bios-uefi] → conduce_a: [sistema-operativo] (borrador entregado, sin fuentes)
8j. [[tipos-de-sistema-de-archivos]] — prerequisitos: [sistema-de-archivos] → conduce_a: [journaling] (borrador entregado, sin fuentes)
8k. [[permisos-de-archivos]] — prerequisitos: [sistema-de-archivos] → conduce_a: []
8l. [[journaling]] — prerequisitos: [tipos-de-sistema-de-archivos] → conduce_a: []
8m. [[paginacion]] — prerequisitos: [memoria-virtual] → conduce_a: [] (borrador entregado, sin fuentes)
8n. [[segmentacion]] — prerequisitos: [memoria-virtual] → conduce_a: [] (borrador entregado, sin fuentes)
8o. [[pila]] — prerequisitos: [estructuras-de-datos] → conduce_a: []
8p. [[cola-fifo]] — prerequisitos: [estructuras-de-datos] → conduce_a: []
8q. [[arbol]] — prerequisitos: [estructuras-de-datos] → conduce_a: []
8r. [[tabla-hash]] — prerequisitos: [estructuras-de-datos] → conduce_a: []
9. [[lenguajes-de-programacion]] — prerequisitos: [software-de-programacion] → conduce_a: [lenguajes-compilados, lenguajes-interpretados] (borrador entregado, sin fuentes)
9a. [[aplicacion-grafica]] — prerequisitos: [software-de-aplicacion] → conduce_a: [] (borrador entregado, rama terminal)
9b. [[aplicacion-con-red]] — prerequisitos: [software-de-aplicacion] → conduce_a: [] (borrador entregado, rama terminal)
9c. [[malware]] — prerequisitos: [software-malicioso] → conduce_a: [defensa-malware] (borrador entregado, sin fuentes)
9d. [[vulnerabilidades]] — prerequisitos: [software-malicioso] → conduce_a: [exploits] (borrador entregado, sin fuentes)
10. [[compilacion]] — prerequisitos: [lenguajes-compilados, compilador] → conduce_a: [lenguaje-ensamblador]
11. [[lenguaje-ensamblador]] — prerequisitos: [compilacion] → conduce_a: [codigo-maquina]
12. [[codigo-maquina]] — prerequisitos: [lenguaje-ensamblador] → conduce_a: [conjunto-de-instrucciones-isa]
13. [[conjunto-de-instrucciones-isa]] — prerequisitos: [codigo-maquina] → conduce_a: [arquitectura-x86-64]
14. [[arquitectura-x86-64]] — prerequisitos: [conjunto-de-instrucciones-isa] → conduce_a: [procesador]
15. [[procesador]] — prerequisitos: [arquitectura-x86-64] → conduce_a: [ciclo-de-ejecucion]
16. [[ciclo-de-ejecucion]] — prerequisitos: [procesador] → conduce_a: [registros-y-unidad-de-control]
17. [[registros-y-unidad-de-control]] — prerequisitos: [ciclo-de-ejecucion] → conduce_a: [unidad-aritmetico-logica-alu]
18. [[unidad-aritmetico-logica-alu]] — prerequisitos: [registros-y-unidad-de-control] → conduce_a: [circuitos-combinacionales]
19. [[circuitos-combinacionales]] — prerequisitos: [unidad-aritmetico-logica-alu] → conduce_a: [circuitos-secuenciales]
20. [[circuitos-secuenciales]] — prerequisitos: [circuitos-combinacionales] → conduce_a: [puertas-logicas]
21. [[puertas-logicas]] — prerequisitos: [circuitos-secuenciales] → conduce_a: [algebra-de-boole]
22. [[algebra-de-boole]] — prerequisitos: [puertas-logicas] → conduce_a: [transistor-mosfet]
23. [[transistor-mosfet]] — prerequisitos: [algebra-de-boole] → conduce_a: [transistor-como-interruptor]
24. [[transistor-como-interruptor]] — prerequisitos: [transistor-mosfet] → conduce_a: [semiconductores]
25. [[semiconductores]] — prerequisitos: [transistor-como-interruptor] → conduce_a: [bandas-de-energia]
26. [[bandas-de-energia]] — prerequisitos: [semiconductores] → conduce_a: [fisica-cuantica-del-solido]
27. [[fisica-cuantica-del-solido]] — prerequisitos: [bandas-de-energia] → conduce_a: [silicio-dopado]
28. [[silicio-dopado]] — prerequisitos: [fisica-cuantica-del-solido] → conduce_a: [] (cierre de la escalera)
# Resto de [[memoria-ram]], [[almacenamiento]], [[placa-base]], [[buses]], resto de software malicioso y periféricos se añaden a cola tras validar mapa.
8s. [[tabla-de-paginas]] — prerequisitos: [paginacion] → conduce_a: [fallo-de-pagina] (borrador entregado, con FTE-0001/0002)
8t. [[fallo-de-pagina]] — prerequisitos: [paginacion] → conduce_a: [] (borrador entregado, con FTE-0001/0002)
8u. [[funcion-de-dispersion]] — prerequisitos: [tabla-hash] → conduce_a: [colision-en-tabla-hash] (borrador entregado, sin fuentes)
8v. [[colision-en-tabla-hash]] — prerequisitos: [tabla-hash] → conduce_a: [] (borrador entregado, sin fuentes)
8w. [[usuario-de-sistema]] — prerequisitos: [permisos-de-archivos] → conduce_a: [] (borrador entregado, con FTE-0001/0002)
8x. [[shell]] — prerequisitos: [herramientas-de-sistema] → conduce_a: [] (borrador entregado, con FTE-0002)
8y. [[copia-de-seguridad]] — prerequisitos: [herramientas-de-sistema] → conduce_a: [] (borrador entregado, sin fuentes)
8z. [[diagnostico-de-sistema]] — prerequisitos: [herramientas-de-sistema] → conduce_a: [] (borrador entregado, sin fuentes)
8aa. [[hilos-concurrencia]] — prerequisitos: [proceso] → conduce_a: [] (borrador entregado, con FTE-0001/0002)
8ab. [[multitarea]] — prerequisitos: [gestor-de-procesos] → conduce_a: [] (borrador entregado, con FTE-0001/0002)
8ac. [[modo-privilegiado]] — prerequisitos: [espacio-de-kernel] → conduce_a: [] (borrador entregado, con FTE-0001/0002/0004)
8ad. [[comprobacion-de-consistencia]] — prerequisitos: [journaling] → conduce_a: [] (borrador entregado, sin fuentes)
8ae. [[bloque-de-control-de-proceso]] — prerequisitos: [proceso, cambio-de-contexto] → conduce_a: [] (borrador entregado, con FTE-0001/0002)
8af. [[sincronizacion-de-hilos]] — prerequisitos: [hilos-concurrencia] → conduce_a: [] (nuevo S-7)
8ag. [[multitarea-cooperativa]] — prerequisitos: [multitarea] → conduce_a: []
8ah. [[multitarea-preventiva]] — prerequisitos: [multitarea] → conduce_a: [interrupciones]
8ai. [[estado-de-proceso]] — prerequisitos: [proceso] → conduce_a: []
8aj. [[identificador-de-proceso]] — prerequisitos: [proceso] → conduce_a: []
8ak. [[tabla-de-paginas-multinivel]] — prerequisitos: [tabla-de-paginas] → conduce_a: []
8al. [[sustitucion-de-paginas]] — prerequisitos: [fallo-de-pagina] → conduce_a: []
8am. [[tlb]] — prerequisitos: [paginacion] → conduce_a: []
8an. [[entrada-de-pagina]] — prerequisitos: [tabla-de-paginas] → conduce_a: [bit-de-presencia]
8ao. [[bit-de-presencia]] — prerequisitos: [entrada-de-pagina] → conduce_a: []
8ap. [[encadenamiento-en-tabla-hash]] — prerequisitos: [colision-en-tabla-hash] → conduce_a: []
8aq. [[sondeo-en-tabla-hash]] — prerequisitos: [colision-en-tabla-hash] → conduce_a: []
8ar. [[inodo]] — prerequisitos: [sistema-de-archivos] → conduce_a: [mapa-de-bloques-libres]
8as. [[mapa-de-bloques-libres]] — prerequisitos: [inodo] → conduce_a: []
8at. [[registro-de-eventos]] — prerequisitos: [diagnostico-de-sistema] → conduce_a: []
8au. [[terminal-de-texto]] — prerequisitos: [shell] → conduce_a: []
8av. [[registro-de-usuarios]] — prerequisitos: [usuario-de-sistema] → conduce_a: []
8aw. [[pila-de-llamadas]] — prerequisitos: [pila] → conduce_a: []
8ax. [[cola-de-listos]] — prerequisitos: [planificador] → conduce_a: [cuanto-de-tiempo]
8ay. [[cuanto-de-tiempo]] — prerequisitos: [cola-de-listos] → conduce_a: []
8az. [[arbol-binario]] — prerequisitos: [arbol] → conduce_a: [arbol-equilibrado]
8ba. [[arbol-equilibrado]] — prerequisitos: [arbol-binario] → conduce_a: []
8bb. [[modo-no-privilegiado]] — prerequisitos: [espacio-de-usuario] → conduce_a: []
8bc. [[ejecucion-de-archivos]] — prerequisitos: [permisos-de-archivos] → conduce_a: []
8bd. [[ext4]] — prerequisitos: [tipos-de-sistema-de-archivos] → conduce_a: [inodo]
8be. [[ntfs]] — prerequisitos: [tipos-de-sistema-de-archivos] → conduce_a: []
8bf. [[fat32]] — prerequisitos: [tipos-de-sistema-de-archivos] → conduce_a: []
8bg. [[seguridad-aplicacion-con-red]] — prerequisitos: [aplicacion-con-red] → conduce_a: []
8af. [[sincronizacion-de-hilos]] — prerequisitos: [hilos-concurrencia] → conduce_a: [] (borrador entregado, con FTE-0001/0002)
8ag. [[multitarea-cooperativa]] — prerequisitos: [multitarea] → conduce_a: [] (borrador entregado, con FTE-0001/0002)
8ah. [[multitarea-preventiva]] — prerequisitos: [multitarea] → conduce_a: [interrupciones] (borrador entregado, con FTE-0001/0002)
8ai. [[estado-de-proceso]] — prerequisitos: [proceso] → conduce_a: [] (borrador entregado, con FTE-0001/0002)
8aj. [[identificador-de-proceso]] — prerequisitos: [proceso] → conduce_a: [] (borrador entregado, con FTE-0001/0002)
8ak. [[tabla-de-paginas-multinivel]] — prerequisitos: [tabla-de-paginas] → conduce_a: [] (borrador entregado, con FTE-0001/0002)
8al. [[sustitucion-de-paginas]] — prerequisitos: [fallo-de-pagina] → conduce_a: [] (borrador entregado, con FTE-0001/0002)
8am. [[tlb]] — prerequisitos: [paginacion] → conduce_a: [] (borrador entregado, con FTE-0001/0002)
8an. [[entrada-de-pagina]] — prerequisitos: [tabla-de-paginas] → conduce_a: [bit-de-presencia] (borrador entregado, con FTE-0001/0002)
8ao. [[bit-de-presencia]] — prerequisitos: [entrada-de-pagina] → conduce_a: [] (borrador entregado, con FTE-0001/0002)
8ap. [[encadenamiento-en-tabla-hash]] — prerequisitos: [colision-en-tabla-hash] → conduce_a: [] (borrador entregado, con FTE-0005)
8aq. [[sondeo-en-tabla-hash]] — prerequisitos: [colision-en-tabla-hash] → conduce_a: [] (borrador entregado, con FTE-0005)
8ar. [[inodo]] — prerequisitos: [sistema-de-archivos] → conduce_a: [mapa-de-bloques-libres] (borrador entregado, con FTE-0001/0002)
8as. [[mapa-de-bloques-libres]] — prerequisitos: [inodo] → conduce_a: [] (borrador entregado, con FTE-0001/0002)
8at. [[registro-de-eventos]] — prerequisitos: [diagnostico-de-sistema] → conduce_a: [] (borrador entregado, con FTE-0001/0002)
8au. [[terminal-de-texto]] — prerequisitos: [shell] → conduce_a: [] (borrador entregado, con FTE-0001/0002)
8av. [[registro-de-usuarios]] — prerequisitos: [usuario-de-sistema] → conduce_a: [] (borrador entregado, con FTE-0001/0002)
8aw. [[pila-de-llamadas]] — prerequisitos: [pila] → conduce_a: [] (borrador entregado, con FTE-0001/0002)
8ax. [[cola-de-listos]] — prerequisitos: [planificador] → conduce_a: [cuanto-de-tiempo] (borrador entregado, con FTE-0001/0002)
8ay. [[cuanto-de-tiempo]] — prerequisitos: [cola-de-listos] → conduce_a: [] (borrador entregado, con FTE-0001/0002)
8az. [[arbol-binario]] — prerequisitos: [arbol] → conduce_a: [arbol-equilibrado] (borrador entregado, con FTE-0005)
