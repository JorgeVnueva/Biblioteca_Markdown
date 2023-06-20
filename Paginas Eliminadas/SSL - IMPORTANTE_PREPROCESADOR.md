# Clase de codigo

Empezamos con un còdigo que se supone que sirve para transformar los grados Farenheit a Celcius
Hablaro de que C considera cualquier tipo de informaciòn true y considera el 0 false
Tambièn hablaron del tema de precedencia
\t es hacer un tab y sirve para hacer màs bonita la precentaciòn 

Complementos dados

--- 

asignamos una variable a otra

```c
int num = 3;
int num2 = num;
```

---

Acà estamos usando una constante

```c
#include NUM 5

int num2;
NUM <= num2 ;
```

La constante se le puede asignar de distinta manera

---

Con el còdigo siguiente podemos reconocer lo que hace el Pre-procesador

```cmd
gcc -E fahr.c > salida-pre-procesador.c 
```

---

El profe se puso a jugar con las funciones

```c
putchar(c) //
(char ) c //transforma a c (los bits que contiene) en char
```

y tenìa un programa que copiaba otros programas o archivos

Nos mostrò que el pre-procesador trata a los datos como una cadena de bits en cambio el compilador es el que los diferencia por tipo.

```c
i++; // post-incrementar, devuelve el valor y luego la suma
++i; // pre-incrementar, hace la suma y luego devuelve el valor
```

Archivos de binario vs archivos de texto

Los archivos binarios habrà que indicar de cuanto a cuanto tomar la cadena de bits
Los archivos de texto se pueden imprimir. Algunas caracterìstica: Se puede leer por linea, sus separaciones se pueden leer.

Compilador: Analizador lèxico.
