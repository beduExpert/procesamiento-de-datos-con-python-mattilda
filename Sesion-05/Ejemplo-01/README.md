[`Procesamiento de datos con Python`](../../Readme.md) > [`Sesión 05`](../Readme.md) > `Ejemplo 1`

# Ejemplo 1: Funciones vectorizadas con series

<div style="text-align: justify;">

## 1. Objetivos :dart:

- Aprender cómo usar Funciones vectorizadas aplicadas a series de Pandas

## 2. Requisitos :clipboard:

1. **PyCharm** instalado.

## 3. Desarrollo :rocket:

Tenemos la siguiente Serie:

```python
serie_1 = pd.Series([1, 2, 3, 4, 5, 6, 7, 8, 9, 10])
```

Recuerdas cómo utilizamos `map` para aplicar una función elemento por elemento a un arreglo. Podemos utilizar funciones vectorizadas para hacer esto mismo con Series y DataFrames de pandas. Esto resulta sumamente eficiente pues pandas está construido para funcionar de esta manera. Primero que nada, veamos cómo es posible aplicar operaciones aritméticas a Series de pandas y son aplicadas elemento por elemento. Por ejemplo:

```python
serie_1 + 10
```
```
0    11
1    12
2    13
3    14
4    15
5    16
6    17
7    18
8    19
9    20
dtype: int64
```

```python
serie_1 * 10
```
```
0     10
1     20
2     30
3     40
4     50
5     60
6     70
7     80
8     90
9    100
dtype: int64
```

```python
(serie_1 + 10) * 100
```
```
0    1100
1    1200
2    1300
3    1400
4    1500
5    1600
6    1700
7    1800
8    1900
9    2000
dtype: int64
```

```python
serie_1 * 60 / 100
```
```
0    0.6
1    1.2
2    1.8
3    2.4
4    3.0
5    3.6
6    4.2
7    4.8
8    5.4
9    6.0
dtype: float64
```

Podemos también aplicar funciones de manera vectorizada a una Serie de pandas. Esto quiere decir que, sin necesidad de utilizar `map` la función se aplica automáticamente a cada elemento. Vamos a utilizar una biblioteca llamada `numpy` para probar algunas de estas funciones vectorizadas.

```python
import numpy as np
np.power(serie_1, 2)
```
```
0      1
1      4
2      9
3     16
4     25
5     36
6     49
7     64
8     81
9    100
dtype: int64
```

```python
np.sqrt(serie_1)
```
```
0    1.000000
1    1.414214
2    1.732051
3    2.000000
4    2.236068
5    2.449490
6    2.645751
7    2.828427
8    3.000000
9    3.162278
dtype: float64
```

¿Ves qué fácil resulta?

[`Anterior`](../Readme.md) | [`Siguiente`](../Readme.md)

</div>