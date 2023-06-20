# Funcional
- **Transparencia referencial:** Con un valor determinado siempre llegaremos al mismo resultado
- **Variable:** Incógnita
- Patter Matching:
```Haskell
signo 0 = 0
signo nro   | nro < 0 = -1
			| otherwise = 1
```
Nota: es la habilidad de haskell de matchear las variables que le doy a una de las definiciones. Va de abajo hacia arriba así que si una se repite tomará la de arriba como la importante.

- Currificación: Toda aplicación parcial
```Haskell
suma :: Integer->Integer->Integer 
-- :t suma 7 = Integer -> Integer

suma' :: (Integer ; Integer) -> Integer
-- No hay currificación
```

- Tipo Propio
```Haskell
data Figura = Circulo {radio::Double} | Rectangulo {base::Double, altura::Double}
```
