Vector de bytes -> Direcciones
Memoria Principal (física) | Memoria Virtual (lógica)

Programa ->| DS |-> Compilador -> |DR| ->Louder -> |DA| -> Memoria Principal (MP)


Reasignación:
- Tiempo de Compilación -> Dirección Lógica (DL) == Dirección Física (DF)
- Tiempo de Compactación -> DL == DF
- Tiempo de Ejecución -> DL != DF

CPU -> MMV -> PF

Re-alocar -> Kernel
Protección -> Espacio de Dirección de otro no se toca sin permiso
Compartir memoria -> Lo mismo que arriba
Organización Lógica -> Ordenamiento de los procesos accediendo a Memoria Principal
Organización Física -> Ordenamiento real en Memoria Principal

RAM -> Gran vector de Bits


Paginación | Segmentación

En qué marco está asignado

Nro. Página = DL/ Tamaño de Página

Cociente = DF y Resto = OFFSET

DF = Nro. Marco x Tamaño Marco + OFFSET

Marco = Lugar del Bitmap

| Posición | Marco | Nro. Proceso |
| --- | --- | --- |
| 0 | 5 | 1 |
| 1 | 6 | 1 |
| 2 | 2 | 1 |
| 3 | 8 | 2 |


Bitmap -> Lector de bits

| Bits | 0 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | 1 | 0 | 0 |
| -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- |  -- |
| Marco | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 |

$$nro. Páginas =nro. Frames = nro. Bytes = 2^{nro.Bits}$$
