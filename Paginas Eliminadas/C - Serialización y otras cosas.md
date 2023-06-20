
TAD: Tipo abstracto de dato
1. tener info
2. tener operaciones asociadas

Streams: Flujos de datos
1. indefinido

Void * : Tipo de datos que no sabes que son. Pero puedes usarlos porque los leemos como bytes, por lo que tranquilamente los podemos transformar

transformo por memcpy() - transformamos a bytes y también cuardamos el tipo de mensaje y le damos un tamaño. 

 PELIGRO!! char(40) *  sizeof(0), en este caso no guardará un espacio de memoria ya que piensa que es tá vacío

{__atribbute packed__} no nos va a servir. 

Buffer
HEAP, STACK

Header {codigo} - size(username) {tamaño} - username - size(mensaje) - mensaje
hacer un sólo send

1kilobyte

## Hilos

#include <pthread.h>
#include <semaphore.h>
[GitHub - sisoputnfrba/threads-sincro-charla3: Ejemplos de la 3er charla de TP sobre Hilos y Sincronización con Semáforos](https://github.com/sisoputnfrba/threads-sincro-charla3)

vamos a recibir un dato

int pthread_create
int pthread_join
pthread_detach(); suspender por un tiempo la ejecución de un hilo
pthread_t tid[2];

sem_wait() = pthread_mutex_lock

sem_post()


Un semaforo puede ser un mutex pero no viceversa.

gcc thread.c -lpthread

./bin/memoria.out ./config/memoria.config

char. 4, 8, 16

