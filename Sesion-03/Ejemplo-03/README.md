[`Procesamiento de datos con Python`](../../Readme.md) > [`Sesión 03`](../Readme.md) > `Ejemplo 3`

# Ejemplo 3: And

<div style="text-align: justify;">

## 1. Objetivos :dart:

- Aprender a extender las capacidades de los operadores de comparación usando `and`.
- Usar `and` para llamar `filter` con múltiples filtros.

## 2. Requisitos :clipboard:

1. **PyCharm** instalado.

## 3. Desarrollo :rocket:

Muchas veces una sola sentencia de comparación no va ser suficiente para filtrar los datos como queremos. En ese caso, and puede ayudarnos a unir dos sentencias. `and` regresa `True` cuando ambas sentencias regresan `True`.

Digamos que tenemos dos funciones que realizan una comparación y regresan `True` cuando la comparación se cumple:

```python
def numero_es_divisible_entre_3(numero):
    return numero % 3 == 0

def numero_es_menor_que_10(numero):
    return numero < 10
```

Vamos a realizar algunas comparaciones usando ambas funciones para evaluar el mismo número:

```python
numero_es_divisible_entre_3(9) and numero_es_menor_que_10(9)
```
*Salida:*
```
True
```

```python
numero_es_divisible_entre_3(12) and numero_es_menor_que_10(12)
```
*Salida:*
```
False
```

```python
numero_es_divisible_entre_3(8) and numero_es_menor_que_10(8)
```
*Salida:*
```
False
```

```python
numero_es_divisible_entre_3(16) and numero_es_menor_que_10(16)
```
*Salida:*
```
False
```

Como puedes ver, `and` sólo regresa True cuando ambas comparaciones regresan `True`.

Veamos ahora cómo aplicarlo a un `filter`. Tenemos una lista que queremos filtrar:

```python
numeros = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20]
```

En esta ocasión vamos a construir una función que reúna ambas funciones que tenemos, porque `filter` sólo recibe una función (más adelante veremos otras opciones):

```python
def numero_es_divisible_entre_3_y_menor_que_10(numero):    
    return numero_es_divisible_entre_3(numero) and numero_es_menor_que_10(numero)
```

Ahora la aplicamos:

```python
list(filter(numero_es_divisible_entre_3_y_menor_que_10, numeros))
```
*Salida:*
```
[3, 6, 9]
```

¡Genial! ¿No es así? Vayamos ahora a practicar esta herramienta.

[`Anterior`](../Readme.md) | [`Siguiente`](../Readme.md)

</div>