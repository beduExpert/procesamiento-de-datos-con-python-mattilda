[`Procesamiento de datos con Python`](../../Readme.md) > [`Sesión 03`](../Readme.md) > `Ejemplo 1`

# Ejemplo 1: Map

<div style="text-align: justify;">

## 1. Objetivos :dart:

- Entender cómo funciona la función `map` y verla aplicada en ejemplos para después poder reproducir su uso.

## 2. Requisitos :clipboard:

1. **PyCharm** instalado.

## 3. Desarrollo :rocket:

Muchas veces vamos a querer aplicar funciones a cada uno de los elementos en una lista. Esto es un procedimiento muy común en la ciencia de datos. Aplicar funciones elemento por elemento a una lista es bastante tedioso sin utilizar la función `map`. Por suerte, `map` hace todo muy fácil e intuitivo.

Para poder usar `map` primero necesitamos una lista:

```python
numeros = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

Listo.

Ahora tenemos que pensar qué proceso queremos aplicar a cada uno de los elementos de la lista. Digamos que queremos multiplicarlos por 10. Hay que escribir una función entonces que reciba un parámetro (que va a ser cada uno de nuestros números) y lo regrese multiplicado por 10:

```python
def multiplicar_por_10(numero):
    return numero * 10
```

El siguente paso es aplicar nuestra función a la lista usando `map`:

```python
list(map(multiplicar_por_10, numeros))
```

*Salida:*
```
[10, 20, 30, 40, 50, 60, 70, 80, 90, 100]
```

¿Por qué estamos agregando esa función `list`? Como viste en el Prework, `list` nos ayuda a convertir el resultado de map en una lista común y corriente. Podríamos guardar el resultado de este procedimiento en otra variable:

```python
numeros_por_10 = list(map(multiplicar_por_10, numeros))
print(numeros_por_10)
```
*Salida:*
```
[10, 20, 30, 40, 50, 60, 70, 80, 90, 100]
```

¡Tan fácil como eso!

Podemos aplicar una infinidad de funciones a nuestra lista usando `map`. Veamos algunos otros ejemplos:

```python
def convertir_en_string_mas_unidad(numero):
    return f'{numero} seg'

print(list(map(convertir_en_string_mas_unidad, numeros)))
```
*Salida:*
```
['1 seg',
 '2 seg',
 '3 seg',
 '4 seg',
 '5 seg',
 '6 seg',
 '7 seg',
 '8 seg',
 '9 seg',
 '10 seg']
```

```python
def convertir_a_numeros_negativos(numero):
    return numero * -1

print(list(map(convertir_a_numeros_negativos, numeros)))
```
*Salida:*
```
[-1, -2, -3, -4, -5, -6, -7, -8, -9, -10]
```

```python
def convertir_en_0_si_menor_a_5(numero):
    if numero < 5:
        return 0
    else:
        return numero
        
print(list(map(convertir_en_0_si_menor_a_5, numeros)))
```
*Salida:*
```
[0, 0, 0, 0, 5, 6, 7, 8, 9, 10]
```

```python
def convertir_en_true_si_mayor_a_6(numero):
    if numero > 6:
        return True
    else:
        return False
print(list(map(convertir_en_true_si_mayor_a_6, numeros)))
```
*Salida:*
```
[False, False, False, False, False, False, True, True, True, True]
```

Ahora es tu turno de practicar. ¡Vayamos al primer Reto!

[`Anterior`](../Readme.md) | [`Siguiente`](../Readme.md)

</div>