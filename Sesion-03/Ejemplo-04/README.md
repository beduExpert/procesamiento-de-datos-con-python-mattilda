[`Procesamiento de datos con Python`](../../Readme.md) > [`Sesión 03`](../Readme.md) > `Ejemplo 4`

# Ejemplo 4: Or

<div style="text-align: justify;">

## 1. Objetivos :dart:

- Aprender a extender las capacidades de los operadores de comparación usando `or`.
- Usar `or` para llamar `filter` con múltiples filtros.

## 2. Requisitos :clipboard:

1. **PyCharm** instalado.

## 3. Desarrollo :rocket:

Vamos a usar las mismas funciones que definimos en nuestro ejemplo pasado:

```python
def numero_es_divisible_entre_3(numero):
    return numero % 3 == 0

def numero_es_menor_que_10(numero):
    return numero < 10
```

Pero ahora veamos qué sucede cuando usamos or para unir dos comparaciones:

```python
numero_es_divisible_entre_3(9) or numero_es_menor_que_10(9)
```
*Salida:*
```
True
```

```python
numero_es_divisible_entre_3(12) or numero_es_menor_que_10(12)
```
*Salida:*
```
True
```

```python
numero_es_divisible_entre_3(8) or numero_es_menor_que_10(8)
```
*Salida:*
```
True
```

```python
numero_es_divisible_entre_3(16) or numero_es_menor_que_10(16)
```
*Salida:*
```
False
```

Como ves, `or` regresa `True` cuando una de las dos comparaciones regresa `True` o cuando ambas regresan `True`. En cambio, sólo regresa `False` cuando ambas comparaciones regresan `False`.

Veamos ahora qué sucede si lo aplicamos a la misma lista de la vez pasada:

```python
numeros = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20]
```

```python
def numero_es_divisible_entre_3_y_menor_que_10(numero):    
    return numero_es_divisible_entre_3(numero) or numero_es_menor_que_10(numero)
```

```python
list(filter(numero_es_divisible_entre_3_y_menor_que_10, numeros))
```
*Salida:*
```
[1, 2, 3, 4, 5, 6, 7, 8, 9, 12, 15, 18]
```

¡Interesante! Quedará mucho más claro después de realizar algunos Retos.


[`Anterior`](../Readme.md) | [`Siguiente`](../Readme.md)

</div>