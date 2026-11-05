# Mapa de cobertura - El Computador

> Orquestador. Estados: `pendiente | asignado | borrador | redactado | revisado`. `[[slug]]` = nota canónica. Ninguna nota hoja está redactada aún (§13.4: validación previa).

## 0. Raíz
- [[ordenador]] — pendiente
- [[hardware]] — pendiente (legado: `Hardware.md` vacío en raíz)
- [[software]] — borrador (reescrito según §5/§11, pendiente fuentes)

## 1. Hardware (visible → físico)
- Procesador
  - [[procesador]] — pendiente → [[cpu-amd-ryzen-7-5700g]] (caso del autor, ver decisiones D-003) — pendiente
  - [[arquitectura-x86-64]] — pendiente
  - [[ciclo-de-ejecucion]] — pendiente
  - [[registros-y-unidad-de-control]] — pendiente
  - [[unidad-aritmetico-logica-alu]] — pendiente
- Memoria
  - [[memoria-ram]] — pendiente (legado: `La memoria.md`)
  - [[memoria-cache]] — pendiente
  - [[memoria-virtual]] — borrador (legado en hardware, rama software)
  - [[espacio-de-usuario]] — borrador (no privilegiado)
  - [[espacio-de-kernel]] — borrador (privilegiado)
  - [[bus-de-memoria]] — pendiente
- Almacenamiento
  - [[almacenamiento]] — pendiente
  - [[hdd]] — pendiente (caso: disco 931,51 GB)
  - [[ssd]] — pendiente (caso: disco 953,85 GB)
  - [[gpu]] — pendiente (caso: RTX 5050 8 GB)
- Placa base
  - [[placa-base]] — pendiente (caso: PRIME B350M-A)
  - [[buses]] — pendiente
  - [[chipset]] — pendiente
- Periféricos
  - [[perifericos-de-entrada]] — pendiente
  - [[perifericos-de-salida]] — pendiente
  - [[fuente-de-alimentacion]] — pendiente
  - [[refrigeracion]] — pendiente
- Fundamento eléctrico / físico (común a todo hardware)
  - [[circuitos-combinacionales]] — pendiente
  - [[circuitos-secuenciales]] — pendiente
  - [[puertas-logicas]] — pendiente
  - [[algebra-de-boole]] — pendiente
  - [[transistor-mosfet]] — pendiente
  - [[transistor-como-interruptor]] — pendiente
  - [[semiconductores]] — pendiente
  - [[bandas-de-energia]] — pendiente
  - [[fisica-del-solido]] / [[fisica-cuantica-del-solido]] — pendiente
  - [[silicio-dopado]] — pendiente
- Comunicaciones
  - [[red-buses-internos]] — pendiente (comparar con red)

## 2. Software (visible → físico)
- Sistema
  - [[software-de-sistema]] — borrador (reescrito panorama 4 subgrupos)
  - [[firmware]] — borrador (panorama)
  - [[bios-uefi]] — borrador (arranque placa base)
  - [[sistema-operativo]] — borrador (entorno integral)
  - [[nucleo-kernel]] — borrador (centro siempre activo)
  - [[gestion-de-recursos]] — borrador (ciclo solicitud/concesión/espera)
  - [[gestor-de-procesos]] — borrador (turnos CPU, prioridades)
  - [[gestor-de-memoria]] — borrador (reparto memoria)
  - [[sistema-de-archivos]] — borrador (persistencia)
  - [[controladores-drivers]] — borrador (traducción dispositivo)
  - [[estructuras-de-datos]] — borrador (organización en memoria)
  - [[formatos-de-archivos]] — borrador (representación en disco)
  - [[memoria-virtual]] — borrador (espacio ampliado)
  - [[proceso]] — borrador (programa en ejecución)
  - [[planificador]] — borrador (política de turnos)
  - [[cambio-de-contexto]] — borrador (guardar/cargar estado)
  - [[llamadas-al-sistema]] — borrador (petición-respuesta)
  - [[interrupciones]] — borrador (señal hardware)
  - [[paginacion]] — borrador (páginas fijas)
  - [[segmentacion]] — borrador (segmentos variables)
  - [[herramientas-de-sistema]] — borrador (diagnóstico, shell, backup)
  - [[cargador-de-arranque]] — borrador (puente BIOS/UEFI → SO)
  - [[tipos-de-sistema-de-archivos]] — borrador (ext4/NTFS/FAT32)
  - [[permisos-de-archivos]] — borrador (leer/escribir)
  - [[journaling]] — borrador (diario de cambios)
  - [[pila]] — borrador (LIFO)
  - [[cola-fifo]] — borrador (FIFO)
  - [[arbol]] — borrador (jerarquía)
  - [[tabla-hash]] — borrador (clave)
  - [[tabla-de-paginas]] — borrador (correspondencia)
  - [[fallo-de-pagina]] — borrador (carga bajo demanda)
  - [[funcion-de-dispersion]] — borrador (clave→posición)
  - [[colision-en-tabla-hash]] — borrador (dos claves misma posición)
  - [[usuario-de-sistema]] — borrador (cuenta, grupos)
  - [[shell]] — borrador (intérprete de órdenes)
  - [[copia-de-seguridad]] — borrador (completa/incremental/diferencial)
  - [[diagnostico-de-sistema]] — borrador (observar–comparar–localizar)
  - [[hilos-concurrencia]] — borrador (hilos en proceso)
  - [[multitarea]] — borrador (varios procesos a la vez)
  - [[modo-privilegiado]] — borrador (acceso sin permiso)
  - [[comprobacion-de-consistencia]] — borrador (fsck)
  - [[bloque-de-control-de-proceso]] — borrador (ficha PCB)
- Aplicación
  - [[software-de-aplicacion]] — borrador (panorama por finalidad)
  - [[aplicacion-grafica]] — borrador (GUI)
  - [[aplicacion-con-red]] — borrador (cliente-servidor)
- Programación
  - [[software-de-programacion]] — borrador (panorama lenguajes/traductores/IDE)
  - [[lenguajes-de-programacion]] — borrador (sintaxis/semántica)
  - [[lenguajes-compilados]] — pendiente (legado: `Lenguajes compilados.md`)
  - [[lenguajes-interpretados]] — pendiente
  - [[compilacion]] — pendiente (legado: `Compilación.md`)
  - [[compilador]] — pendiente
  - [[interprete]] — pendiente
  - [[ensamblador]] — pendiente
  - [[lenguaje-ensamblador]] — pendiente (legado: `Lenguaje ensamblador.md`)
  - [[codigo-maquina]] — pendiente (legado: `Código máquina.md` vacío)
  - [[conjunto-de-instrucciones-isa]] — pendiente → enlaza a [[arquitectura-x86-64]]
  - [[enlazadores]] — pendiente
  - [[cargadores]] — pendiente
- Malicioso
  - [[software-malicioso]] — borrador (panorama técnico/defensivo sin exploits detallados)
  - [[malware]] — borrador (clasificación)
  - [[vulnerabilidades]] — borrador (defecto)
  - [[exploits]] — pendiente
  - [[defensa-malware]] — pendiente

## 3. Cadena troncal de lectura (sin saltos)
[[ordenador]] → [[hardware]] → [[procesador]] → [[arquitectura-x86-64]] → [[ciclo-de-ejecucion]] → [[registros-y-unidad-de-control]] → [[unidad-aritmetico-logica-alu]] → [[circuitos-combinacionales]] → [[circuitos-secuenciales]] → [[puertas-logicas]] → [[algebra-de-boole]] → [[transistor-mosfet]] → [[transistor-como-interruptor]] → [[semiconductores]] → [[bandas-de-energia]] → [[fisica-cuantica-del-solido]] → [[silicio-dopado]]

Cadena software: [[software]] → [[sistema-operativo]] → [[nucleo-kernel]] → [[gestion-de-recursos]] → [[memoria-virtual]] → [[espacio-de-usuario]] / [[espacio-de-kernel]] → [[lenguajes-de-programacion]] → [[compilacion]] → [[lenguaje-ensamblador]] → [[codigo-maquina]] → [[conjunto-de-instrucciones-isa]] → ... (física)

## 2b. Sistema - expansión S-7 (auditoría)
- [[sincronizacion-de-hilos]] — borrador (exclusión mutua)
- [[multitarea-cooperativa]] — borrador (cesión voluntaria)
- [[multitarea-preventiva]] — borrador (interrupción forzada)
- [[estado-de-proceso]] — borrador (listo/ejecución/bloqueado)
- [[identificador-de-proceso]] — borrador (PID)
- [[tabla-de-paginas-multinivel]] — borrador (directorios)
- [[sustitucion-de-paginas]] — borrador (víctima FIFO/LRU)
- [[tlb]] — borrador (caché traducciones)
- [[entrada-de-pagina]] — borrador (marco + bits)
- [[bit-de-presencia]] — borrador (presencia/validez)
- [[encadenamiento-en-tabla-hash]] — borrador (listas por posición)
- [[sondeo-en-tabla-hash]] — borrador (direccionamiento abierto)
- [[inodo]] — borrador (metadatos por archivo)
- [[mapa-de-bloques-libres]] — borrador (bitmap/libre)
- [[registro-de-eventos]] — borrador (historia cronológica)
- [[terminal-de-texto]] — borrador (superficie texto)
- [[registro-de-usuarios]] — borrador (persistencia cuentas)
- [[pila-de-llamadas]] — borrador (marcos, retorno, overflow)
- [[cola-de-listos]] — borrador (competidores ordenados)
- [[cuanto-de-tiempo]] — borrador (intervalo de turno)
- [[arbol-binario]] — borrador (2 hijos)
- [[arbol-equilibrado]] — borrador (altura)
- [[modo-no-privilegiado]] — borrador (modo usuario)
- [[ejecucion-de-archivos]] — borrador (tercer permiso)
- [[ext4]] — borrador (Linux, journaling)
- [[ntfs]] — borrador (Windows, MFT)
- [[fat32]] — borrador (compatible)
- [[seguridad-aplicacion-con-red]] — borrador (autenticación/cifrado)

## 4. Software - huecos S-8 (pendientes)
- [[sincronizacion-entre-procesos]] — borrador (exclusión entre procesos)
- [[interbloqueo]] — borrador (espera circular)
- [[manejo-de-interrupciones]] — borrador (rutina + prioridades)
- [[instruccion-privilegiada]] — borrador (solo modo privilegiado)
- [[credenciales]] — borrador (secreto + custodia)
- [[autenticacion]] — borrador (contraste identidad)
- [[tabla-maestra-de-archivos]] — borrador (MFT)
- [[lista-de-control-de-acceso]] — borrador (ACL)
- [[extent]] — borrador (rango contiguo)
- [[registro-de-eventos-detalle]] — borrador (entradas, gravedad, filtro)

## Aplicación - 17 huecos A-E (S-A)
- [[aplicacion-de-escritorio]] — borrador (local nativa)
- [[aplicacion-movil]] — borrador (táctil, sensores)
- [[aplicacion-web]] — borrador (navegador/servidor)
- [[aplicacion-de-consola]] — borrador (texto en terminal)
- [[procesador-de-texto]] — borrador (formato)
- [[navegador-web]] — borrador (interpretar/presentar)
- [[reproductor-multimedia]] — borrador (audio/vídeo sincronizado)
- [[gestor-de-archivos-grafico]] — borrador (navegación jerárquica)
- [[ventana]] — borrador (rectángulo delimitado)
- [[widget]] — borrador (control en ventana)
- [[interfaz-grafica-de-usuario]] — borrador (conjunto elementos)
- [[gestion-de-ventanas]] — borrador (apilar/mover/activar/cerrar)
- [[eventos-de-interfaz]] — borrador (notificación usuario→app)
- [[red-de-computadores]] — borrador (ordenadores conectados)
- [[protocolo-de-red]] — borrador (reglas petición/respuesta)
- [[cliente-servidor]] — borrador (papeles)
- [[servidor]] — borrador (escucha/atiende/responde)
- [[sesion]] — borrador (periodo autenticado)
- [[autorizacion]] — borrador (permiso en sesión)

## Aplicación - Lote E (5 huecos)
- [[lenguaje-de-descripcion-de-documentos]] — borrador (marco)
- [[pestana-de-navegador]] — borrador (tab)
- [[protocolos-de-la-web]] — borrador (HTTP petición/respuesta)
- [[codec]] — borrador (compresión con/sin pérdida)
- [[manejador-de-eventos]] — borrador (respuesta/callback)

## Aplicación - 14 huecos A-E (S-A2)
- [[direccion-web]] — borrador (URL)
- [[protocolo-http]] — borrador (HTTP)
- [[servidor-web]] — borrador (especialización web)
- [[lenguaje-de-programacion-web]] — borrador (código en cliente)
- [[aplicacion-nativa]] — pendiente
- [[aplicacion-hibrida]] — pendiente
- [[sistema-operativo-movil]] — pendiente
- [[pantalla-tactil]] — pendiente
- [[sensor]] — pendiente
- [[dispositivo-movil]] — pendiente
- [[entorno-de-escritorio]] — pendiente
- [[propagacion-de-eventos]] — pendiente
- [[primitiva-grafica]] — pendiente
- [[dibuixado-en-pantalla]] — pendiente
- [[contenedor-multimedia]] — pendiente
- [[compresion-de-datos]] — pendiente
- [[formato-de-documento]] — pendiente
- [[certificados-digitales]] — pendiente
- [[criptografia-clave]] — pendiente
- [[confidencialidad-integridad]] — pendiente
