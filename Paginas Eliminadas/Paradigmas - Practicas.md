---
Nota: El objetivo de este documento es poner las dudas medio tontas o cosas de uso cotidiano que se me olvidan usar.
---

Para varias cosas sólo tienes que ir a [Guía Lenguajes 3.1.4 (google.com)](https://docs.google.com/document/d/e/2PACX-1vTlLkakSbp6ubcIq00PU4-Z96tg8CUSc8bO793_uftmiGjfkSn7Ug-F_y0-ieIWG6aWfuoHLJrRL8Fd/pub)

Para encontrar el tipo en GHCi

```ghci
> :t // Muestra el tipo
> :l // Abre un archivo haskell desde GHCI
> :r // Reabre el archivo haskell 
```

Para simplificar: elem verifica que la variable que le pasas se encuentre en la lista dada. Devuelve un Bool

```ghci
> elem "hate" ["hola","love"]
False
> elem "hola" ["hola","love"]
True
```