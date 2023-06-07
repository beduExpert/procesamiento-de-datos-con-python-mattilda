[`Procesamiento de datos con Python`](../../Readme.md) > [`Sesión 03`](../Readme.md) > `Ejemplo 5`

# Ejemplo 5: Not

<div style="text-align: justify;">

## 1. Objetivos :dart:

- Aprender a extender las capacidades de los operadores de comparación usando `not`.

## 2. Requisitos :clipboard:

1. **PyCharm** instalado.

## 3. Desarrollo :rocket:

`not` es muy sencillo, así que simplemente vamos a ver cómo funciona usando una de nuestras funciones anteriores. `not` recibe un sólo booleano, así que por el momento sólo podremos usar una función al mismo tiempo:

```python
def numero_es_divisible_entre_3(numero):
    return numero % 3 == 0

not(numero_es_divisible_entre_3(9))
```
*Salida:*
```
False
```
```python
not(numero_es_divisible_entre_3(10))
```
*Salida:*
```
True
```
¿Ves? `not` simplemente regresa `True` cuando la comparación es `False` y viceversa.

Obviamente esto sólo es útil si podemos aplicarlo a un `filter`. Pero para hacer eso tendremos primero que aprender sobre funciones `lambda`.

[`Anterior`](../Readme.md) | [`Siguiente`](../Readme.md)

</div>