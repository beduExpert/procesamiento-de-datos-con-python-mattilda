[`Procesamiento de datos con Python`](../../Readme.md) > [`Sesión 04`](../Readme.md) > `Ejemplo 6`

# Ejemplo 6: Análisis exploratorio de datos

<div style="text-align: justify;">

## 1. Objetivos :dart:

- Aprender las herramientas básicas para darle un primer vistazo a los datos que tenemos en nuestros `DataFrames`

## 2. Requisitos :clipboard:

1. **PyCharm** instalado.

## 3. Desarrollo :rocket:

```python
import pandas as pd
import json
```

Ok, tenemos aquí nuestro conjunto de datos del Ejemplo pasado:

```python
f = open('../../Datasets/zomato_reviews-clean.json', 'r')
json_data = json.load(f)
f.close()

df = pd.DataFrame.from_dict(json_data)
df
```

Podemos saber la forma de nuestro DataFrame accediendo a la propiedad `shape`. El primer valor es el número de filas, mientras que el segundo es el número de columnas:

```python
df.shape
```
```
(1180,8)
```

Podemos ver un número determinado de filas comenzando desde el principio con `head`:

```python
df.head(5)
```

Podemos ver también las filas del final con `tail`:

```python
df.tail(5)
```

Podemos ver los `dtypes` de todas nuestras columnas accediendo a esa propiedad:

```python
df.dtypes
```
```
has_online_delivery         int64
price_range                 int64
currency                   object
name                       object
cuisines                   object
location.address           object
location.city              object
user_rating.rating_text    object
dtype: object
```

También podemos usar la función `info` del DataFrame para ver más información sobre las columnas. Por ejemplo, el número de valores no nulos que hay en cada una.

```python
df.info()
```
```
<class 'pandas.core.frame.DataFrame'>
Index: 1180 entries, 0 to 1179
Data columns (total 8 columns):
 #   Column                   Non-Null Count  Dtype 
---  ------                   --------------  ----- 
 0   has_online_delivery      1180 non-null   int64 
 1   price_range              1180 non-null   int64 
 2   currency                 1180 non-null   object
 3   name                     1180 non-null   object
 4   cuisines                 1180 non-null   object
 5   location.address         1180 non-null   object
 6   location.city            1180 non-null   object
 7   user_rating.rating_text  1180 non-null   object
dtypes: int64(2), object(6)
memory usage: 83.0+ KB
```

En caso de que tengamos tantas columnas que no podamos verlas todas en el preview de arriba, podemos acceder a una lista de columnas usando las propiedad `columns`:

```python
df.columns
```
```
Index(['has_online_delivery', 'price_range', 'currency', 'name', 'cuisines',
       'location.address', 'location.city', 'user_rating.rating_text'],
      dtype='object')
```

Vamos a un Reto para que puedas practicar leer un conjunto de datos y hacer una exploración básica.

[`Anterior`](../Readme.md) | [`Siguiente`](../Readme.md)

</div>