Condición de carrera: No nos devuelve el mismo resultado
- Tenemos varios procesos|hilos usando el mismo recurso, al menos 1 lo modifica y otro accede a él o lo necesita.
Región crítica: no hay que sobrecargarlo.

- Mutua exclusión: Hacer que accedan a la región crítica de un proceso a la vez
	- Progreso: 
	- Espera limitada: Hacer que todos los procesos vayan pudiendo entrar (que no esté eternamente esperando)
	- Velocidad de los procesos: 

Solución de peterson

Si es mi turno y no hay otro interesado. voy a la sección crítica.

Serializar: Ejecutar en sierto orden


instrucción atómicas: Preparado exclusivamene para las interrupciones

test and set 


Solución del SO: Semáforos

a partir de syscalls

a partir de un struct (nosotros usaremos un entero) nos indica quien esperaría y quien seguirá.

Sem = 1
Wait(Sem)
Sección crítica
Singal(Sem)

y a esto se le puede agregar  una forma de bloqueo.

Forma semáforo
Tengo un semáforo, entro al cpu, decremento el semaforo y hago el proceso necesario.

por el otro, yo habré terminado el while, me van a desbloquear



Claro, lo que sucede es que wait  es un ciclo eterno que espera a que le digan, puedes pasar. Cuando pasa ya 

En cambio el otro ya finalizó el wait pero está bloqueado por lo que en signal lo que pasa es que lo despiertan

Resuelve el problema de la exclusión mutua
pthreads_spinlock_t (wait)(lock)
pthreads_mutex_t (signal) (unlock) 1


contadores
Se unicializa en n (cantidad de instancias totales)

binarios

si valor >0 , semamforo
si valor <0, bloqueo

Contadores para limitar la cantidad de accesos
mutex para ordenarlos
y binario para el orden de ejecución??

semValor = 1
	wait (SemValor)
		valor++
	signal (semValor)

semContador = n
wait(semContador)
	usar recurso() //n-1
	.......
	n+1
	signal (semContador)

While(1){
	wait(semP1);
	printf("DOG")
	signal(semP2);
}

![[Pasted image 20230426125909.png]]

![[Pasted image 20230426130843.png]]
semP1 = 1 
semP2 = 0

