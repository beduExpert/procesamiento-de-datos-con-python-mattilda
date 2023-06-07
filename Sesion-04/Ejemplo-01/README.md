[`Procesamiento de datos con Python`](../../Readme.md) > [`Sesión 03`](../Readme.md) > `Ejemplo 1`

# Ejemplo 1: Series

<div style="text-align: justify;">

## 1. Objetivos :dart:

- Entender qué son las series
- Aprender a crear series de pandas
- Aprender los métodos básicos de indexación de las series

## 2. Requisitos :clipboard:

1. **PyCharm** instalado.

## 3. Desarrollo :rocket:

Antes de cualquier cosa, importaremos los paquetes necesarios para este ejemplo, en este caso `pandas`.

```python
import pandas as pd
```

Las series son secuencias ordenadas unidimensionales que pueden contener diferentes tipos de valores. En esto se parecen a las listas. De hecho podemos crear series usando listas.

```python
serie_1 = pd.Series([3, 7, 9, 8])
```

Una gran diferencia que tienen con las listas es que cada elemento en una serie tiene un índice asociado que no necesariamente es una secuencia de enteros como en las listas. En este aspecto, nuestras series se parecen a los diccionarios:

```python
serie_1
```
*Salida:*
```
0    3
1    7
2    9
3    8
dtype: int64
```

La columna de la izquierda es nuestro índice, la columna de la derecha son los datos almacenados en la serie. El texto en la parte inferior es el tipo de dato que tenemos en nuestra serie.

Los tipos de datos más comunes que podemos encontrar son:

1. `int64`: Equivalente a `int`
1. `float64`: Equivalente a `float`
1. `bool`: Equivalente a `bool` (duh)
1. `object`: Equivalente a `str`, o indica que hay una mezcla de tipos de datos numéricos y no-numéricos en la serie

> *Importante: Tener series que contengan diversos tipos de datos es una muy mala práctica. Lo recomendable es siempre tener homogeneidad de tipos de datos en cada serie que tengamos. De todas maneras, se encontrarán por ahí algunos conjuntos de datos que contienen series con tipos de datos diversos. Es por eso que cuando nos topemos con un tipo de dato `obj` tenemos que ser cuidadosos y no asumir automáticamente que el tipo de dato incluido son strings.*

Podemos crear series con un índice generado por nosotrxs:

```
serie_2 = pd.Series([4, 7, 9, 8], index=[10, 11, 12, 13])

serie_2
```
*Salida:*
```
10    4
11    7
12    9
13    8
dtype: int64
```

Incluso podemos usar strings en el índice:

```python
serie_3 = pd.Series([5, 8, 7, 2], index=['a', 'b', 'c', 'd'])

serie_3
```
*Salida:*
```
a    5
b    8
c    7
d    2
dtype: int64
```

Debido a su similitud, podemos incluso crear series usando diccionarios:

```python
datos = {
    "Juan": 45,
    "Pepe": 56,
    "Alfonsina": 12,
    "Jenny": 49,
    "Marco P.": 12
}

serie_4 = pd.Series(datos)

serie_4
```
*Salida:*
```
Juan         45
Pepe         56
Alfonsina    12
Jenny        49
Marco P.     12
dtype: int64
```

Al igual que en las listas, podemos acceder a nuestros datos usando el operador de indexación. La diferencia es que en una serie tenemos que incluir el operador `loc` para indicarle a la serie que estamos accesándola usando los nombres de los índices:

```python
serie_1.loc[2]
```
```
3
```

```python
serie_2.loc[12]
```
```
9
```

```python
serie_3.loc['c']
```
```
7
```

```python
serie_4.loc['Marco P.']
```
```
12
```

¡Vayamos a nuestro primer Reto!

[`Anterior`](../Readme.md) | [`Siguiente`](../Readme.md)

</div>