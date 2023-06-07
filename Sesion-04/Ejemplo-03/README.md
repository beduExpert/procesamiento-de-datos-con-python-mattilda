[`Procesamiento de datos con Python`](../../Readme.md) > [`Sesión 04`](../Readme.md) > `Ejemplo 3`

# Ejemplo 3: DataFrames

<div style="text-align: justify;">

## 1. Objetivos :dart:

- Aprender a crear DataFrames usando diccionarios de listas
- Aprender a indexar DataFrames para obtener subconjuntos de datos

## 2. Requisitos :clipboard:

1. **PyCharm** instalado.

## 3. Desarrollo :rocket:

Los DataFrames son entonces estructuras de datos bidimensionales. Tienen filas y columnas. Hay innumerables formas de crear DataFrames (si quieren ahondar en el tema, [aquí hay una fuente muy completa](https://www.geeksforgeeks.org/different-ways-to-create-pandas-dataframe/)). Vamos a aprender una de ellas: los diccionarios de listas.

Aquí tenemos un diccionario de listas:

```python
datos = {
    'columna_1': ['valor_fila_0', 'valor_fila_1', 'valor_fila_2', 'valor_fila_3', 'valor_fila_4'],
    'columna_2': ['valor_fila_0', 'valor_fila_1', 'valor_fila_2', 'valor_fila_3', 'valor_fila_4'],
    'columna_3': ['valor_fila_0', 'valor_fila_1', 'valor_fila_2', 'valor_fila_3', 'valor_fila_4'],
    'columna_4': ['valor_fila_0', 'valor_fila_1', 'valor_fila_2', 'valor_fila_3', 'valor_fila_4']
}
```

Vamos a convertirlo en un DataFrame:

```python
df = pd.DataFrame(datos)

df
```
```
      columna_1     columna_2     columna_3     columna_4
0  valor_fila_0  valor_fila_0  valor_fila_0  valor_fila_0
1  valor_fila_1  valor_fila_1  valor_fila_1  valor_fila_1
2  valor_fila_2  valor_fila_2  valor_fila_2  valor_fila_2
3  valor_fila_3  valor_fila_3  valor_fila_3  valor_fila_3
4  valor_fila_4  valor_fila_4  valor_fila_4  valor_fila_4
```

También podemos pasarle explícitamente un índice para cambiar el índice por defecto:

```python
df = pd.DataFrame(datos, index=['a', 'b', 'c', 'd', 'e'])

df
```
```
      columna_1     columna_2     columna_3     columna_4
a  valor_fila_0  valor_fila_0  valor_fila_0  valor_fila_0
b  valor_fila_1  valor_fila_1  valor_fila_1  valor_fila_1
c  valor_fila_2  valor_fila_2  valor_fila_2  valor_fila_2
d  valor_fila_3  valor_fila_3  valor_fila_3  valor_fila_3
e  valor_fila_4  valor_fila_4  valor_fila_4  valor_fila_4
```

Para observar columnas individualmente, usamos el operador de indexación y le pasamos el nombre de la columna:

```python
df['columna_1']
```
```
a    valor_fila_0
b    valor_fila_1
c    valor_fila_2
d    valor_fila_3
e    valor_fila_4
Name: columna_1, dtype: object
```

La columna que obtuvimos es una serie de Pandas con una propiedad `Name`.

También podemos ver más de una columna pasando una lista con los nombres de las columnas que queremos en el orden que las queremos:

```python
df[['columna_3', 'columna_1']]
```
```
      columna_3     columna_1
a  valor_fila_0  valor_fila_0
b  valor_fila_1  valor_fila_1
c  valor_fila_2  valor_fila_2
d  valor_fila_3  valor_fila_3
e  valor_fila_4  valor_fila_4
```

> **Importante:** Importante: Usamos las palabras observar o ver porque indexar columnas no regresa una copia de esas columnas, sino solamente una "vista" de esas columnas, como si estuviéramos viéndolas a través de una ventana. Eso quiere decir que los cambios que realicemos a las "vista" se verán reflejados en el DataFrame original.

Para indexar filas, podemos usar el operador `loc`.

Podemos pedir una sola fila:

```python
df.loc['a']
```
```
columna_1    valor_fila_0
columna_2    valor_fila_0
columna_3    valor_fila_0
columna_4    valor_fila_0
Name: a, dtype: object
```

O podemos pedir varias:

```python
df.loc[['c', 'a']]
```
```
      columna_1     columna_2     columna_3     columna_4
c  valor_fila_2  valor_fila_2  valor_fila_2  valor_fila_2
a  valor_fila_0  valor_fila_0  valor_fila_0  valor_fila_0
```

Podemos pedir rangos también:

```python
df.loc['b':]
```
```
      columna_1     columna_2     columna_3     columna_4
b  valor_fila_1  valor_fila_1  valor_fila_1  valor_fila_1
c  valor_fila_2  valor_fila_2  valor_fila_2  valor_fila_2
d  valor_fila_3  valor_fila_3  valor_fila_3  valor_fila_3
e  valor_fila_4  valor_fila_4  valor_fila_4  valor_fila_4
```

Podemos pasarle un segundo argumento a `loc` para seleccionar solamente algunas columnas de las filas que pedimos. En este caso estamos pidiendo la columna `'columna_2'` de la fila `'b'`, por lo que obtenemos un solo valor:

```python
df.loc['b', 'columna_2']
```
```
'valor_fila_1'
```

También podemos pedir múltiples filas y columnas:

```python
df.loc[['e', 'c'], ['columna_4', 'columna_2']]
```
```
      columna_4     columna_2
e  valor_fila_4  valor_fila_4
c  valor_fila_2  valor_fila_2
```

¡Vayamos a practicar esto en un Reto!

[`Anterior`](../Readme.md) | [`Siguiente`](../Readme.md)

</div>