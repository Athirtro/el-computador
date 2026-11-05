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
7. [[gestion-de-recursos]] — prerequisitos: [nucleo-kernel] → conduce_a: [gestor-de-procesos, gestor-de-memoria]
8. [[memoria-virtual]] — prerequisitos: [gestor-de-memoria] → conduce_a: [espacio-de-usuario, espacio-de-kernel]
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
