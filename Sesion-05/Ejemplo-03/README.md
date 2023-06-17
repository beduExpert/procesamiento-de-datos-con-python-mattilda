[`Procesamiento de datos con Python`](../../Readme.md) > [`Sesión 05`](../Readme.md) > `Ejemplo 3`

# Ejemplo 3: Funciones vectorizadas y agregaciones con DataFrames

<div style="text-align: justify;">

## 1. Objetivos :dart:

- Aprender cómo usar Funciones vectorizadas y agregaciones aplicadas a `DataFrames` completos

## 2. Requisitos :clipboard:

1. **PyCharm** instalado.

## 3. Desarrollo :rocket:

Tenemos el siguiente dataset:

```python
datos = {
    'precio': [34, 54, 223, 78, 56, 12, 34],
    'cantidad_en_stock': [3, 6, 10, 2, 5, 45, 2],
    'productos_vendidos': [3, 45, 23, 76, 24, 6, 2]
}

df = pd.DataFrame(datos, index=["Pokemaster", "Cegatron", "Pikame Mucho", "Lazarillo de Tormes", "Stevie Wonder", "Needle", "El AyMeDuele"])

df
```
```
                     precio  cantidad_en_stock  productos_vendidos
Pokemaster               34                  3                   3
Cegatron                 54                  6                  45
Pikame Mucho            223                 10                  23
Lazarillo de Tormes      78                  2                  76
Stevie Wonder            56                  5                  24
Needle                   12                 45                   6
El AyMeDuele             34                  2                   2
```

Si aplicamos operaciones aritméticas a nuestro DataFrame la operación se aplicará elemento por elemento a nuestro DataFrame completo:

```python
df * 100
```
```
                     precio  cantidad_en_stock  productos_vendidos
Pokemaster             3400                300                 300
Cegatron               5400                600                4500
Pikame Mucho          22300               1000                2300
Lazarillo de Tormes    7800                200                7600
Stevie Wonder          5600                500                2400
Needle                 1200               4500                 600
El AyMeDuele           3400                200                 200
```

```python
(df + 100) / 2
```
```
                     precio  cantidad_en_stock  productos_vendidos
Pokemaster             67.0               51.5                51.5
Cegatron               77.0               53.0                72.5
Pikame Mucho          161.5               55.0                61.5
Lazarillo de Tormes    89.0               51.0                88.0
Stevie Wonder          78.0               52.5                62.0
Needle                 56.0               72.5                53.0
El AyMeDuele           67.0               51.0                51.0
```

También podemos aplicar funciones vectorizadas con el mismo resultado:

```python
import numpy as np
```

```python
np.power(df,2)
```
```
                     precio  cantidad_en_stock  productos_vendidos
Pokemaster             1156                  9                   9
Cegatron               2916                 36                2025
Pikame Mucho          49729                100                 529
Lazarillo de Tormes    6084                  4                5776
Stevie Wonder          3136                 25                 576
Needle                  144               2025                  36
El AyMeDuele           1156                  4                   4
```

```python
np.sqrt(df)
```
```
                        precio  cantidad_en_stock  productos_vendidos
Pokemaster            5.830952           1.732051            1.732051
Cegatron              7.348469           2.449490            6.708204
Pikame Mucho         14.933185           3.162278            4.795832
Lazarillo de Tormes   8.831761           1.414214            8.717798
Stevie Wonder         7.483315           2.236068            4.898979
Needle                3.464102           6.708204            2.449490
El AyMeDuele          5.830952           1.414214            1.414214
```

```python
np.sin(df) + 100
```
```
                         precio  cantidad_en_stock  productos_vendidos
Pokemaster           100.529083         100.141120          100.141120
Cegatron              99.441211          99.720585          100.850904
Pikame Mucho         100.053053          99.455979           99.153780
Lazarillo de Tormes  100.513978         100.909297          100.566108
Stevie Wonder         99.478449          99.041076           99.094422
Needle                99.463427         100.850904           99.720585
El AyMeDuele         100.529083         100.909297          100.909297
```

Si usamos agregaciones, las agregaciones se hacen de manera automática por columna:

```python
df.sum()
```
```
precio                491
cantidad_en_stock      73
productos_vendidos    179
dtype: int64
```

Aunque podemos cambiar ese comportamiento usando `axis=1` para hacerlo por fila:

```python
df.sum(axis=1)
```
```
Pokemaster              40
Cegatron               105
Pikame Mucho           256
Lazarillo de Tormes    156
Stevie Wonder           85
Needle                  63
El AyMeDuele            38
dtype: int64
```

Todas las demás agregaciones funcionan también. El default (o `axis=0`) es hacerlo por columna, pero todas pueden funcionar por fila usando `axis=1`:

```python
df.min()
```
```
precio                12
cantidad_en_stock      2
productos_vendidos     2
dtype: int64
```

```python
df.min(axis=1)
```
```
Pokemaster              3
Cegatron                6
Pikame Mucho           10
Lazarillo de Tormes     2
Stevie Wonder           5
Needle                  6
El AyMeDuele            2
dtype: int64
```

```python
df.max()
```
```
precio                223
cantidad_en_stock      45
productos_vendidos     76
dtype: int64
```

```python
df.max(axis=1)
```
```
Pokemaster              34
Cegatron                54
Pikame Mucho           223
Lazarillo de Tormes     78
Stevie Wonder           56
Needle                  45
El AyMeDuele            34
dtype: int64
```


[`Anterior`](../Readme.md) | [`Siguiente`](../Readme.md)

</div>