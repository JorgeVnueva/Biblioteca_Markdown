# Decimales

Dirección Lógica / Tamaño de página = Nro Página

2045 / 1024 = 1 (resto 1021)

 página 1 - offset 1021

La página 1 tiene V = 1

y se encuentra en el marco 6

DF ()

# Bits

2045(decimal) -> 1111111101 (binario)

1  / 1111111101 -> offset

Esta página es la 1 y tiene V= 1. Se encunetra en el marco 6 (110) 

DF

| Nro Marco | Offset dentro de pag (10 bits) |                  |
| --------- | ------------------------------ | ---------------- |
| 110       | 1111111101                     | 7165 (decimales) |

Tabla de páginas pesaría megas y la CPU no podría cargar eso en un registro.

Quien traduce dirección es la CPU (no se programa la cuenta del número de páginas ya que está dado por el mismo hardware)

# Full teoría (TP)

Guarda el marco y el V de la página 

caché de TLB

La CPU tiene una caché me identifica 9 páginas. Si la página ya está traducida busco en la TLB el número de página y voy al frame number (Esto se llama TLB hit).

Si no está, va a TLB miss. Va a memoria y ¿revisa? la tabla de página.

El procesador hace esto al mismo tiempo. Pero en nuestro caso creo que primero va al TLB hit y luego al TLB miss 

# Memoria Compartida

Para ahorrar espacio y no quedar tan vacío hacen que 1 página sea grande y esté fragmentado en varios marcos donde puedo dejar datos de varios procesos.

Paginar la tabla de página
