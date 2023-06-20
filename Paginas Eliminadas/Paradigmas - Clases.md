---
Nombre :: Pennella Valeria Verónica
E-mail :: vpennella@gmail.com
---
# Una clase

- Lazy evaluation

Reducción de expresiones -> los reemplazos equivalentes, como double x y x=2 entonces la función se reemplaza por 2+2

Transparencia referencial -> no hay forma de reemplazar una variable ya que es única.

Hay dos formas de reducción (lazy evaluation) de adentro hacia afuera y de afuera hacia adentro. Se supone que con ambos llegas al mismo resultado pero uno puede ser más rápido que otro.

La lista vacía no tiene cabeza head []

No hay overhead porque no hay memoria.

Función para modificar el animal (++ , "genio")

Eliminar de una lista filter.(\= string)

Función para lista vacía (const [ ])

replicate hace una lista con las repeticiones que hiciste

ecuación con guardas

head.filter f $ [1..]

Fold - MAP - ZIP puede ser
# 28/04

### Repaso
- Composición de funciones
	- Crear una nueva función
	- (.) - operador
- Currificación
	- Reciben los argumentos de a uno por vez
- Aplicación parcial
	- Permite poder crear nuevas funciones
- Expresión Lambda
	- Crear una función anónima.
- Tipos de tados propios
	- Usamos 'data'
- Funciones constantes
	- pedro = Persona 20  "pedro"
- Patter matching : coincidencia de patrones.
### Clase
Tipo de datos
- Conjunto de elementos con algunas carácteristicas en comun
- Conjunto de operaciones para manipular dichos elementos

'data' Identificador* = constructo{ ,}

Lista por compresión 
numerosPares numeros = [num | num <- numeros, even num]
> numerosPares [1..8]
> [2,4,6,8]

seleccionar :: (Number -> Bool) --función -> [Integer] -> [Integer] --lista de numeros 
seleccionar criterio numeros = [num | num <- numeros, criterio num]

Una función es de orden superior si recibe o devuelve una función
ejemplo filter

filter :: (a->bool) -> [a] -> [a]
filter criterio lista = [elemento | elemento <- lista , criterio elemento]

map :: (a->bool)-> [a] -> [b]
map criterio lista = [criterio elemento | elemento <- lista]

any :: (a -> bool) ->[a] -> bool
all :: (a -> bool) ->[a] -> bool


los tipos en mayuscula

cantidad[] = 0
cantidad ( __ : xs) = 1 + cantidad xs
>(7:6:[5,7])
>[7,6,5,7]

ultimo [x] = x
ultimo ( __ : xs) = ultimo xs



maximaFlorSegun g [] =
maximaFlorSegun canditadDemandada (x:xs)= Flor  cantidadDe 'max' 

# 21/04
## Paradigma Funcional
- Paradigma Declarativo
- Abstracción Principal 
	- Función
- [Transparencia Referencial](DiccionarioParadigma.md)
- [Patter Matching](DiccionarioParadigma.md)
- Función definida usando ecuaciones
	-  Ej: siguiente nro = nro + 1 (ecuacion orientada)
- [Tipos Propios](DiccionarioParadigma.md)
- Composición de funcones


# 14/04
## Paradigma Funcional
[[DiccionarioParadigma]]


# 31/03
## Imperativa
Conjunto de instrucciones que se ejecutan en orden y siguen un objetivo.

| Visión externa | Visión interna |
| --- | --- |
| Un ingenio de la maquina que resuelve un problema | Un algoritmo que resuelve un problema|

- Características
	- Deterministico: Siempre dará el mismo resultado
	- Conjunto de instrucciones que ejecutan en orden
	- Modular
	- **Variable:** Espacio de memoria para almacenamiento
		- Estado del programa
		- Asignación destructiva
	- Estructuras de datos
		- Listas | array
		- Árboles
		- Template
		- Pila | Cola
	- Estructuras de contol
		- Iteración
		- Secuencia
		- Selección

| Paradigama imperativo | Paradigama declarativo |
| --- | --- | 
| Conjunto de instrucciones que se ejecutan en un orden para resolver un problema | Describe las características del problema |
| Mayor ontrol sobre el algoritmo | Motor que se encarga de encontrar la solución = **Menor control** |
| Determinístico | No determinístico |
| Cambio de estados | --- |

Habitualmente el paradigma declarativo es más "legible" ya que muestra mayor "expresibidad". Por lo tanto: Declaratividad -> menos control

Ejemplo: esPar{función} unNumero = filter{función} even{critério} unNumero{variable}

>[!INFO]
>- Osea que mientras más funciones haya y estas se entiendan por cómo se llaman se considera más declarativo. Por eso es que también se lo llama "Paradiga funcional"



