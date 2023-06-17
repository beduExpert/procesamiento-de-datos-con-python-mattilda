[`Procesamiento de datos con Python`](../../Readme.md) > [`Sesión 05`](../Readme.md) > `Ejemplo 2`

# Ejemplo 2: Agregaciones

<div style="text-align: justify;">

## 1. Objetivos :dart:

- Aprender cómo usar agregaciones para resumir o reducir un arreglo

## 2. Requisitos :clipboard:

1. **PyCharm** instalado.

## 3. Desarrollo :rocket:

Las agregaciones entonces aplican una función a todo el arreglo entero y regresan un único valor que es la agregación o reducción del arreglo.

Pandas ya tiene incluidas bastantes de éstas. Así que podemos llamarlas con tan sólo usar un método de nuestra Serie:

```python
serie = pd.Series([1, 2, 3, 4, 5])
```

`sum` suma todos los elementos de nuestro arreglo:

```python
serie.sum()
```
```
15
```

`min` y `max` nos dan el valor mínimo y máximo, respectivamente, de nuestro arreglo:

```python
serie.min()
```
```
1
```

```python
serie.max()
```
```
5
```

`count` nos da el conteo total del número de elementos en nuestro arreglo:

```python
serie.count()
```
```
5
```

[`Anterior`](../Readme.md) | [`Siguiente`](../Readme.md)

</div>