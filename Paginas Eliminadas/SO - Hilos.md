multithreaded programming

Proceso/tarea pero poco usados = programa en ejecución.

Multiples procesos cargados a memoria concurrentemente (paralelamente sería en 2 cores mientras que concurrente en 1) en ambos casos hay la misma cantidad de procesos cargando concurrentemente

Programa

Disco - Código


Proceso

RAM - Código Datos(estático, variables globales) Heap(memoria dinámica) Stack(memoria estática que se vá ejecutando, variables locales, automático) PCB

Hay un Proceso Control Block (PCB) por proceso - Siempre En RAM 



## Estados

new - no es ejecutable.
ready - 
running - 
(La máquina va cambiando rápidamente entre estos dos para hacer varias cosas)
terminated 

waiting - Sucede cuando el disco tarda un toque en leer el proceso.

## Swapping

Mover a Disco. Procesos bloqueados porque no los necesito de momento
Esto lo hace para que la RAM no se esté fijando en varios procesos en waiting así no desaprovechamos RAM. También puede ocurrir con procesos Ready. Así que pasa a un estado "suspendido en espera" y cunado está a punto de usarse se pone en suspendido listo (de ready pasa directamente a este último estado de ser necesario.)

## Planificadores

Copiar del PPT

Extra largo

Largo - RAM
Mediano - RAM Y DISCO
Corto - RAM


## Cambio de Contexto

Formato Pila u otros (en otros puede tener más costes pero es algo que quiero que pase).

==Overhead ==

## Creación de procesos

PID

- Un proceso crea a otra y vueden ejecutarse concurrentemente o a que su "hijo" finalice
- Espacio de direcciones del proceso, Clona el proceso pero tiene un PID distinto.



Sockets entre 
Para el tp no hay necesidad de poner un máximo de clientes

Una consola se conecta y se queda en Acept


- Hilos para esperar consolas nuevas. 
	- Listen acept  -Lista global de PCB's


Internamente cada uno se maneja con hilos. que sería PCB's para el TP's


Crear un PCB a cada una. 
PCB - Struct

No hacer fork, usar pile --- create

PID - 1
Instrucciones - Me las manda la consola 

registro - Vacíos

El resto vacío


PCB crea TCB's

Tolo lo que esté en me

Registros como strings y serán 12 y barra 0

El CPU debe interpretar las instrucciones como una lista continua y ordenada.

Mi kernel es capaz de esperar la conexion de una consola, esa consola me da su PCB y se la doy al CPU Y  hace algo y me lo devuelve.


**


-   Aprender a utilizar las Commons, principalmente las funciones para listas, archivos de configuración y logs.
    
-   Definir el Protocolo de Comunicación.
    
-   Todos los módulos están creados y son capaces de establecer conexiones entre sí.
    

**


File.system

Resolución de conflictos y escritura de archivos - Eliminar archivos


### Características de la forma entrega[​](https://docs.utnso.com.ar/primeros-pasos/normas-tp#caracteristicas-de-la-forma-entrega)

-   Para la evaluación, el grupo obtendrá su código fuente descargando la última versión disponible de su repositorio.
    
-   Será responsabilidad del grupo la obtención y descarga de todas las **dependencias** requeridas para el correcto funcionamiento del práctico.
    
-   La evaluación de los requerimientos se realizará en las **máquinas virtuales sin interfaz gráfica proporcionadas por la Cátedra**, que se encontrarán instaladas en el laboratorio de sistemas.

### Requisitos para la aceptación de la entrega[​](https://docs.utnso.com.ar/primeros-pasos/normas-tp#requisitos-para-la-aceptacion-de-la-entrega)

-   Contener un archivo makefile que ejecute correctamente.
-   Que no se produzcan errores de compilación.
-   Que no existan archivos ejecutables ni objetos[[1]](https://docs.utnso.com.ar/primeros-pasos/normas-tp#fn1).
-   Haber cumplido con los requerimientos técnicos y funcionales indicados en el enunciado del trabajo práctico.

### Aclaraciones sobre el desarrollo[​](https://docs.utnso.com.ar/primeros-pasos/normas-tp#aclaraciones-sobre-el-desarrollo)

El desarrollo de las funcionalidades del trabajo práctico debe ser codificado íntegramente utilizando el lenguaje de programación C y, cada uno de los programas que lo componen deben poder ser compilados utilizando el comando GCC. Sin embargo, es posible utilizar makefiles para automatizar el proceso de compilación y deploy del trabajo práctico. Siguiendo esta línea se sugiere utilizar makefiles creados por herramientas de desarrollo, como el IDE Eclipse, a fin de simplificar las tareas.

A excepción de la [Commons Library](https://github.com/sisoputnfrba/so-commons-library) y otras bibliotecas o herramientas desarrolladas por la cátedra, **no** está permitido que el código que compone el trabajo práctico utilice bibliotecas de terceros que no hayan sido instaladas previamente por la cátedra en las máquinas virtuales provistas para el desarrollo y pruebas del mismo.


Recordatorio: hay pautas para la entrega final. Leelas a su tiempo.



TP

Maquina virtual (VM). Descargue los recursos. Xubuntu y Server. Descomprimí los primeros archivos y verifiqué que el hash sea el mismo que dice en el documento "paso a paso" 
Bueno agregué las vdi y entré al que sería Xubuntu. De momento sólo se que le puedo "agregar un disco" y que la ventana es pequeña. Que puedo activar la terminal con Ctrl + Alt + T y lo que hago es ir a la dirección del "disco" e intento ejecutar el "VBoxLinuxAdditions.run" que no me deja porque necesito permiso de super usuario y para ello uso el comando "sudo" más lo que había tipeado antes "!!" y luego me pide contraseña que al tipear no te pone nada de lo que tipeas así que tienes que ser preciso
Agregué el compilador de C, aunque creo que no hacía falta. 
Agregué esa función del portapapeles y los archivos movibles. 
Y empecé con "mi primer proyecto C" que hayuda a entender cómo agregar una librería.

Sólo tendrá 512 M de memoria
