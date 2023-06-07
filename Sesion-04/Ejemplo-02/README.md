[`Procesamiento de datos con Python`](../../Readme.md) > [`Sesión 04`](../Readme.md) > `Ejemplo 2`

# Ejemplo 2: Indexación de series

<div style="text-align: justify;">

## 1. Objetivos :dart:

- Aprender métodos avanzados de indexación de series

## 2. Requisitos :clipboard:

1. **PyCharm** instalado.

## 3. Desarrollo :rocket:

> **Nota:** Algunas de las siguientes técnicas también son posibles en listas

Las series nos permiten muchas más maneras de acceder a sus datos que vuelven a su sistema de indexación sumamente flexible. Veamos algunas de ellas:

```python
serie = pd.Series(['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i'])

serie
```
```
0    a
1    b
2    c
3    d
4    e
5    f
6    g
7    h
8    i
dtype: object
```

Podemos pedir más de un elemento al mismo tiempo pasando una lista de índices:

```python
serie.loc[[0, 1, 2]]
```
```
5    f
8    i
2    c
4    e
dtype: object
```

Podemos pedir "desde el principio hasta el índice x" o "desde el índice x hasta el final" de esta manera:

```python
serie.loc[:4]
```
```
6    g
7    h
8    i
dtype: object
```

Podemos pedir incluso rangos:

```python
serie.loc[3:8]
```
```
3    d
4    e
5    f
6    g
7    h
8    i
dtype: object
```

También podemos usar rangos cuando nuestro índice no es numérico:

```python
serie_2 = pd.Series([1, 2, 3, 4, 5, 6, 7, 8], index=['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h'])

serie_2
```
```
a    1
b    2
c    3
d    4
e    5
f    6
g    7
h    8
dtype: int64
```

```python
serie_2.loc['c':'f']
```
```
c    3
d    4
e    5
f    6
dtype: int64
```

Vamos a practicar esto para que quede más claro.

[`Anterior`](../Readme.md) | [`Siguiente`](../Readme.md)

</div>