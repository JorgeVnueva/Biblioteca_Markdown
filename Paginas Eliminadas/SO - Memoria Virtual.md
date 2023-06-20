Direcciones ya traducidas. No necesitan traducir en tiempo de ejecución.

¿Cuáles de las siguientes afirmaciones son correctas sobre Particiones Fijas?

- Puede generar fragmentación **interna**

- Toda la imagen del proceso es alojado en una partición contigua

- Se requiere saber al base o número de cada partición

- Limita el grado multiprogramación (y tamaño de los procesos)
  
  Nota: aquí ya hay un límite de partición conocido (fijo). Hay que tenerlo en cuenta, el profe dijo que abría que cambiar la propocisión para que sólo se aplique al otro

¿Cuáles de las siguientes afirmaciones son correctas sobre Particiones Dinámica?

- Puede generar fragmentación **externa**

- Toda la imagen del proceso es alojado en una partición contigua

- Se requiere saber al base o número de cada partición

- Se requiere saber el límite de cada partición 

Nota: cuidado, genera un tamaño exacto para el proceso.

Dirección de memoria: en hexadecimal

Frames: En Bytes

---

Memoria Virtual

 Si todo el proceso tuviera que estar cargao en la RAM para poder ejecutar nos limitaría el tamaño máximo del proceso.

En su momento el proceso estaba partido en varias partes llamadas overlay y una sección principal. Overlay driver, sección principal, overley (i).

Por paginación

- Puede estar cargado en diferentes partes según el momento

- Puete estar en Memoria Principal (MP) o en disco (swap o área de swapping)

Memoria principal / Real (RAM) + Disco SWAP (almacenamiento secundario) -> Memoria Virtual

Nota: La instrucción que se ejecuta debe estar en RAM.

### Paginación bajo demanda

- La pagina se carga a memoria sólo cuando se necesita 

- El swapping es "lazy": mueve *páginas* entre MP y SWAP

- El tiempo de carga de los procesos disminuye

Viene la explicación de cómo haríamos las actividades en tablas. 

| n  ° pag | Frame | P(presencia) | M (modificado) |
| -------- | ----- | ------------ | -------------- |
|          |       |              |                |

SI se referencia una pag con P=0 (no está en RAM o mejor dicho MP) => Interrupción por fallo de página (PF o PAGE FAULT)

Si no tiene frame quiere decir que no fue cargada a memoria física

Hacer una rama de pp.

![](C:\Users\litig\AppData\Roaming\marktext\images\2023-06-06-16-47-03-image.png)

I - La CPU ejecuta una instrucción que referencia a una página

- Se busca en la TLB - MMU
  
  - TLB HIT (está en la TLB). Nos da la dirección física
  
  - TLB MISS. Se busca en la tabla de pags - MMU
    
    - P = 1 Se agrega entrada a TLB
    
    - P = 0 Se lanza interrupción PF - MMU
      
      - Se atiende la Interrupción - SO
        
        - Fuera del espacio de direcciones. Fin del Proceso || devuelve un error - SO
        
        - Pág válida (en disco). Buscar frame libre - SO
          
          - Hay frame libre. Se dispara operación de lectura + Se marca frame como ocupado 
            
            - Interrupción __ Fin IO - DMA 
              
              - Se marca página presente - SO
                
                - Se agrega entrada a TLB - MMU
                  
                  - Se vuelve a ejecutar la instrucción - I
          
          - No hay frames libres. Se elige un frame víctima - SO (Para esto es necesario un algorítmo + Política de sustitución de página)
            
            - M = 0. Se marca frame como libre + página ausente (Esta parte no es tan necesario)
              
              - Ahora hay frame libre por lo tanto Se dispara ope...
            
            - M = 1. Se dispara operación de escritura 
              
              - Interrupción __ Fin IO

Si está modificado (M=1) se tiene que escribir en Disto SWAP y luego se elimina.

En paginación se puede crear un bitmap, nos dice cuales frames tenemos libres y cuales no.

"El proceso está en SWAP"

### Asiganación, Sustitución de Frames

Políticas

- Asignación
  
  - Fija -> Un proceso tiene asignado un número fijo de frames
  
  - Dinámico -> el número de frames que tiene asignado un proceso puede aumentar o disminuir

- Sustitución (La víctima)
  
  - Local -> la víctima debe estar dentro del conjunto de frames asignados al proceso
  
  - Global -> la víctima puede ser cualquier frame (de cualquier proceso)

Algoritmos de sustitución de páginas - FIFO

- Siempre es la mejor forma de aprender algo y aquí pasa lo mismo. No anoté nada pero la práctica es sencilla con fifo

Algoritmos de sustitución de páginas - Óptimo

- Futurología - Sabemos qué páginas nos van a pedir y cuales no por lo que es la mejor pero vos tienes que poner de tu parte porque vos tienes que ver cual es el mejor para sacar.

Algoritmos de sustitución de páginas - LRU

- En un entorno, vemo cual es la página referenciada más alejada en el tiempo.  Se puede guardar la última referencia de la página

Algoritmos de sustitución de páginas - Clock

- Agrega un componente que sería el "Bit de USO". Como dice su nombre si la página se usó el bit se pone en 1 y a la hora de sustituir si el bit está en 1 lo deja en 0 y pasa a intentar sustituir al siguiente, sería como una vida que le das a la víctima. Su comportamiento es como el FIFO sólo que con vidas.

Algoritmos de sustitución de páginas - Clock modificado

- Es distinto a los anteriores porque no intenta ahorrarse PF sino que intenta ahorrarse accesos a disco por lo que le da otra vida extra a la víctima (Uso Modifcado). Primero busca a los (0, 0) y luego a los (0, 1) si es que tienen U=1 los pone en U=0 y sigue buscando.

### Paginación mala

Thrashing / sobrepaginación | no habrá en el TP

Asignación fija - Sustitución local

No tiene suficientes frames el proceso para poder ejecutar la instrucción - 

Asignación dinámica - Sustitución global 

Tengo un proceso muy grande pero quiero que este proceso se ejecute junto a todos los otros procesos por lo que si no tiene espacio le va tomar el espacio a otro proceso y este se lo quitará a otro y así seguirá. Esto se debe a que para que un proceso pueda robar un frame hace un PF (se bloquea pero no sé si pasaría al estado block) y mientras hace esto otro proceso intenta ejecutarse pero al no tener espacio intenta hacer lo mismo y así otro y otro. Esto se debe a la simultaneidad del PF y la ejecución de instrucciones.

Mucha actividad MMU -> proceso bloqueados -> bajo uso CPU -> SO aumenta nivel multiprogramación

Solución. No exagerar con el grado multiprogramación pero tampoco reducirlo a 1.

### Page Buffering

No sé lo que es
