    Código
    Datos (globales)
    Heap
    Stack

- Estructuras y punteros: Se alojan en el Stack del proceso
- Memoria dinámica: Reserva en tiempo de ejecución. Alojada en el Heap del proceso (los datos apuntados por los punteros)
- Puntero: Dirección de un dato en memoria

## Malloc 

Almancena espacio en memoria pero tienes que darle el tamaño en bytes
```
malloc (4)
```
Siempre puesdes usar sizeof() para conocer el tamaño que tiene. Sea una variable o un tipo de dato (como en el ejemplo)
```
malloc(sizeof(int));
```

## `&` (ampersand):

Un operador muy importante es `&` (ampersand) el cual **nos devuelve la dirección en memoria de su parámetro**.

```c
#include <stdlib.h>
#include <stdio.h>

int main(void){
   int *p = malloc(sizeof(int));
   *p = 1;
   printf("p = %d\n", p);
   printf("&p = %p\n", &p);
   return 0;
}
```

-   `%d` está diciendo que en ésa parte de la línea va a imprimir un valor entero.
-   `%p` está diciendo que en ésa parte de la línea va a imprimir la dirección en memoria del dato, por ejemplo `0x7fff78c088d8`.

### Nota: esto sirve para una función que pide una dirección de memoria a un entero.

```c
void sumarUno(int *unaVariable){
	(*unaVariable) = (*unaVariable) + 1;  //esos parentesis son importantísimos. OJO
	printf("Dentro de la funcion, i vale: %d\n", *unaVariable);
}

int i = 1;

sumarUno(&i);
```


## Flechita:
Sirve en estructuras para ver cada dato individualmente sacando una flechita y preguntando por el la variable (p->nombre , p -> edad, etc). Es muy útil si hay una dirección a otra estructura ya que permite conocer los datos del hijo.

```c
typedef struct
{
   char[20] nombre;
   char[20] apellido;
   int edad;
   t_persona* hijo;  // Esta es la importante
} t_persona;

```

Si quisiéramos acceder al nombre del hijo, bastaría con tipear: `p->hijo->nombre`.

## Funciones que retornan punteros:
```c
char* copiar(char* palabra){
	char* tmp = malloc(sizeof(char) * strlen(palabra) + 1);
	memcpy(tmp, palabra, strlen(palabra));
	tmp[strlen(palabra)] = '\0';
	return tmp;
}
```
En este caso hace un nuevo puntero y almacena en memoria una copia al valor de palabra. Simplemente es un método para crear un nuevo valor y un nuevo puntero y cuando dejemos de usarlo hay que liberarlo.

### No olvides liberar tu memoria. Free()

En este caso que hay un puntero a un array que almacena bloques de memoria entonces hay que liberar los bloques de memoria

```c
char* copiar(char* palabra){
	char* tmp = malloc(sizeof(char) * strlen(palabra) + 1);
	memcpy(tmp, palabra, strlen(palabra));
	tmp[strlen(palabra)] = '\0';
	return tmp;
}

int main(void){
	char** nombres;
	//Grabo espacio para 4 punteros a nombres
	nombres = malloc(sizeof(char*) * 4);

	//Grabo cada una de las palabras
	nombres[0] = copiar("Joaquin");	//7 + 1 chars
	nombres[1] = copiar("Matias");	//6 + 1 chars
	nombres[2] = copiar("Santiago");	//8 + 1 chars
	nombres[3] = copiar("Gaston");	//6 + 1 chars

	int i;
	for(i=0; i<4; ++i)
		free(nombres[i]);
	free(nombres);
	return 0;
}
```
#### Otra forma de hacer lo de arriba pero con una forma aritmética

```c
char** nombres;
//Grabo espacio para 4 punteros a nombres
nombres = malloc(sizeof(char*) * 4);

//Grabo cada una de las palabras
nombres[0] = copiar("Joaquin");
*(nombres+1) = copiar("Matias");		//6 + 1 chars
*(nombres+2) = copiar("Santiago");		//8 + 1 chars
*(nombres+3) = copiar("Gaston");		//6 + 1 chars
```
## No lo voy a leer

### Otros alloc

`calloc(n, bytes)`: reserva memoria para un array de n elementos que ocupan un tamaño de x bytes cada uno, además inicializa los bytes con un `\0`. Por ejemplo, supongamos que queremos reservar memoria para un array de 5 enteros, entonces:

c

```
int *arrayEnteros = calloc(5, sizeof(int))
```

El equivalente, con la función `malloc`, sería:

c

```
int *arrayEnteros = malloc(5*sizeof(int))
```

`realloc(*unPuntero, bytes)`: cambia el tamaño del bloque de memoria apuntado por unPuntero a uno de x bytes. Devuelve un puntero al bloque con el tamaño indicado. Es importante saber que los datos no son alterados y se guardan en el nuevo bloque siempre y cuando le hayamos reasignado un tamaño mayor o igual al del bloque anterior. Los bytes agregados (es decir, si el tamaño total que le pasamos por parámetro es mayor al tamaño del bloque apuntado por unPuntero) no están inicializados. Debemos tener cuidado en los parámetros que le pasemos porque: Si unPuntero es `NULL`, la función se comporta como un `malloc(bytes)`. Si unPuntero no es `NULL` y `bytes = 0`, la función se comporta como un `free(unPuntero)`.

## La razón por la que el chico usó varios int64, int32. Aunque preferiblemente usar sizeof()

### El problema del tipo de dato "int"

Sin embargo, con el tipo de datos `int` hay un tema muy importante a considerar. Dependiendo de la arquitectura, sistema operativo, y del compilador en sí mismo, el tipo de dato `int` va a tener un tamaño u otro. Generalmente `int` tiene un tamaño equivalente al tamaño de la palabra del procesador. Por ende, si estamos en una arquitectura de 32 bits, la palabra tendrá un tamaño de 32 bits, `int` tendrá un tamaño de 32 bits o 4 bytes (8 bits = 1 byte). Si estamos en una arquitectura de 64 bits, la palabra tendrá un tamaño de 64 bits, `int` tendrá un tamaño de 64 bits o 8 bytes.

Entonces, si nosotros reservamos (malloc) 4 bytes para un tipo int en una máquina con un procesador de 32 bits no vamos a tener ningún problema pero si lo hacemos en una de 64 bits va a volar todo por los aires.

Para solucionar este problema podemos considerar dos opciones:

-   Recurrir a un tipo de datos que no dependa de la arquitectura de nuestro procesador, es decir, que tengan un tamaño fijo lo corramos donde lo corramos. Por ejemplo, `int32_t` o `int64_t`[[11]](https://docs.utnso.com.ar/guias/programacion/punteros#fn11).
-   Utilizar el operador el `sizeof()` para que se acople a la arquitectura en la que esté corriendo. Ej: malloc(sizeof int);

Normalmente vamos a optar por usar el operador `sizeof`, los tipos de dato entero de tamaño fijo los vamos a dejar para aquellos momentos en que no podemos dejar el tamaño del entero al criterio del sistema operativo. Un uso común para estos tipos de datos es cuando queremos realizar un intercambio de datos entre dos computadoras diferentes, pero eso lo veremos en el proximo capitulo.

## EXTRA: Punteros a Funciones
Lo dejo acá solo para que sepas que si en algún momento tienes que hacer un filtro por char e int y el código es el mismo. Podrías hacer una función pero con punteros que hará el trabajo de varias maneras.
