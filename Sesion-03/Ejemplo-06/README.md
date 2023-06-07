[`Procesamiento de datos con Python`](../../Readme.md) > [`Sesión 03`](../Readme.md) > `Ejemplo 6`

# Ejemplo 6: Lambda

<div style="text-align: justify;">

## 1. Objetivos :dart:

- Aprender la sintaxis `lambda` para poderla aplicar en `map` y `filter`.

## 2. Requisitos :clipboard:

1. **PyCharm** instalado.

## 3. Desarrollo :rocket:

Una función lambda se define así:

```python
lambda x: x * 100
```
*Salida:*
```
<function __main__.<lambda>(x)>
```

Se usa la palabra reservada `lambda`, luego se definen los parámetros, y al final se agrega el cuerpo de la función, que en este caso sólo puede incluir una sola sentencia: la sentencia `return`. No hace falta escribir `return`, `lambda` sabe que tiene que regresar la única línea de código que tiene.

Ahora veamos cómo se usaría para revertir nuestra comparación anterior en un `filter`.

```python
numeros = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20]

list(filter(lambda x: not (x % 3 == 0), numeros))
```
*Salida:*
```
[1, 2, 4, 5, 7, 8, 10, 11, 13, 14, 16, 17, 19, 20]
```

Como puedes ver, esta sentencia nos regresa todos los números que no son divisibles entre 3. Revierte el funcionamiento de la función `numero_es_divisible_entre_3`.

Veamos un par de lambdas más:

```python
alabras = ["achicoria", "pasto", "sol", "loquillo", "moquillo", "sed", "pez", "jacaranda", "mil"]

list(filter(lambda x: len(x) > 5, palabras))
```
*Salida:*
```
['achicoria', 'loquillo', 'moquillo', 'jacaranda']
```

```python
numeros = [3, 5, -1, -7, -8, 4, -78, 5, -46, 56, 98, 9, -1, -2, -4]

list(filter(lambda x: x < 0, numeros))
```
*Salida:*
```
[-1, -7, -8, -78, -46, -1, -2, -4]
```

```python
list(filter(lambda x: not(x < 0), numeros))
```

*Salida:*
```
[3, 5, 4, 5, 56, 98, 9]
```

[`Anterior`](../Readme.md) | [`Siguiente`](../Readme.md)

</div>