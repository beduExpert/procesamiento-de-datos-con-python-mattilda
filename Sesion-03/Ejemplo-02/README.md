[`Procesamiento de datos con Python`](../../Readme.md) > [`Sesión 03`](../Readme.md) > `Ejemplo 2`

# Ejemplo 2: Filter

<div style="text-align: justify;">

## 1. Objetivos :dart:

- Entender cómo funciona la función `filter` y verla aplicada en ejemplos para después poder reproducir su uso

## 2. Requisitos :clipboard:

1. **PyCharm** instalado.

## 3. Desarrollo :rocket:

`filter` nos permite filtrar nuestras listas para dejar fuera elementos que no queremos. Tal vez te parezca un poco extraño esto. ¿Por qué queremos filtrar datos? Una de las tareas más importantes de procesamiento es la de limpiar nuestros conjuntos de datos para que tengan solamente aquellos que necesitamos para nuestro análisis. Una de las técnicas de limpieza más comunes es la de filtrar nuestro conjunto de datos. Vamos a aprender a hacer esto usando `filter`.

Como ya vimos, `filter` recibe una función y una lista, y regresa una nueva lista con los elementos que fueron filtrados. La función debe de regresar `True` o `False`. Cada que la función regresa `True`, el elemento al que le fue aplicado la función se agrega a la nueva lista. Cada que la función regresa `False` (o `None`), el elemento al que le fue aplicado la función es descartado.

Veamos esto en acción:

```python
numeros = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

def numero_es_par(numero):
    return numero % 2 == 0

print(list(filter(numero_es_par, numeros)))
```
*Salida:*
```
[2, 4, 6, 8, 10]
```

Como nuestra función regresa `True` si el valor es par, nuestra lista resultante sólo tiene valores pares.

Veamos otro ejemplo:

```python
def numero_es_mayor_a_5(numero):
    return numero > 5
    
print(list(filter(numero_es_mayor_a_5, numeros)))
```
*Salida:*
```
[6, 7, 8, 9, 10]
```

Algunos ejemplos más:

```python
def palabra_tiene_mas_de_5_caracteres(palabra):
    return len(palabra) > 5
    
palabras = ["achicoria", "pasto", "sol", "loquillo", "moquillo", "sed", "pez", "jacaranda", "mil"]

print(list(filter(palabra_tiene_mas_de_5_caracteres, palabras)))
```
*Salida:*
```
['achicoria', 'loquillo', 'moquillo', 'jacaranda']
```

```python
def numero_es_negativo(numero):
    return numero < 0
    
numeros = [3, 5, -1, -7, -8, 4, -78, 5, -46, 56, 98, 9, -1, -2, -4]

print(list(filter(numero_es_negativo, numeros)))
```
*Salida:*
```
[-1, -7, -8, -78, -46, -1, -2, -4]
```

```python
def numero_es_divisible_entre_9(numero):
    return numero % 9 == 0
    
numeros = [3, 7, 9, 34, 72, 90, 87, 34, 99, 56, 12, 18]

print(list(filter(numero_es_divisible_entre_9, numeros)))
```
*Salida:*
```
[9, 72, 90, 99, 18]
```

¡Ahora es tu turno de poner `filter` en práctica!

[`Anterior`](../Readme.md) | [`Siguiente`](../Readme.md)

</div>