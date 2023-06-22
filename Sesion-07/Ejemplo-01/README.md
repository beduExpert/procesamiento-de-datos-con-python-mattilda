## Ejemplo 1: Casting

### 1. Objetivos:
    - Aprender a usar `astype`
    - Aprender a lidiar con errores usando `to_numeric`
    - Aprender a convertir `strings` e `ints` a `datetime`
 
---
    
### 2. Desarrollo:


```python
import pandas as pd
```


```python
df = pd.read_csv('../../Datasets/new_york_times_bestsellers-dirty.csv', index_col=0)

df.head()
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>amazon_product_url</th>
      <th>author</th>
      <th>description</th>
      <th>publisher</th>
      <th>title</th>
      <th>oid</th>
      <th>bestsellers_date.numberLong</th>
      <th>published_date.numberLong</th>
      <th>rank.numberInt</th>
      <th>rank_last_week.numberInt</th>
      <th>weeks_on_list.numberInt</th>
      <th>price.numberDouble</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>http://www.amazon.com/The-Host-Novel-Stephenie...</td>
      <td>Stephenie Meyer</td>
      <td>Descr: Aliens have taken control of the minds ...</td>
      <td>Little, Brown</td>
      <td>THE HOST</td>
      <td>5b4aa4ead3089013507db18c</td>
      <td>2008-05-24 00:00:00</td>
      <td>1212883200000</td>
      <td>2</td>
      <td>1</td>
      <td>3</td>
      <td>25.99</td>
    </tr>
    <tr>
      <th>1</th>
      <td>http://www.amazon.com/Love-Youre-With-Emily-Gi...</td>
      <td>Emily Giffin</td>
      <td>Descr: A woman's happy marriage is shaken when...</td>
      <td>St. Martin's</td>
      <td>LOVE THE ONE YOU'RE WITH</td>
      <td>5b4aa4ead3089013507db18d</td>
      <td>2008-05-24 00:00:00</td>
      <td>1212883200000</td>
      <td>3</td>
      <td>2</td>
      <td>2</td>
      <td>24.95</td>
    </tr>
    <tr>
      <th>2</th>
      <td>http://www.amazon.com/The-Front-Garano-Patrici...</td>
      <td>Patricia Cornwell</td>
      <td>Descr: A Massachusetts state investigator and ...</td>
      <td>Putnam</td>
      <td>THE FRONT</td>
      <td>5b4aa4ead3089013507db18e</td>
      <td>2008-05-24 00:00:00</td>
      <td>1212883200000</td>
      <td>4</td>
      <td>0</td>
      <td>1</td>
      <td>22.95</td>
    </tr>
    <tr>
      <th>3</th>
      <td>http://www.amazon.com/Snuff-Chuck-Palahniuk/dp...</td>
      <td>Chuck Palahniuk</td>
      <td>Descr: An aging porn queens aims to cap her ca...</td>
      <td>Doubleday</td>
      <td>SNUFF</td>
      <td>5b4aa4ead3089013507db18f</td>
      <td>2008-05-24 00:00:00</td>
      <td>1212883200000</td>
      <td>5</td>
      <td>0</td>
      <td>1</td>
      <td>24.95</td>
    </tr>
    <tr>
      <th>5</th>
      <td>http://www.amazon.com/Phantom-Prey-John-Sandfo...</td>
      <td>John Sandford</td>
      <td>Descr: The Minneapolis detective Lucas Davenpo...</td>
      <td>Putnam</td>
      <td>PHANTOM PREY</td>
      <td>5b4aa4ead3089013507db191</td>
      <td>2008-05-24 00:00:00</td>
      <td>1212883200000</td>
      <td>7</td>
      <td>4</td>
      <td>3</td>
      <td>26.95</td>
    </tr>
  </tbody>
</table>
</div>



Tenemos aquí un dataset donde no todos los tipos de datos han sido deducidos correctamente:


```python
df.dtypes
```




    amazon_product_url              object
    author                          object
    description                     object
    publisher                       object
    title                           object
    oid                             object
    bestsellers_date.numberLong     object
    published_date.numberLong        int64
    rank.numberInt                  object
    rank_last_week.numberInt         int64
    weeks_on_list.numberInt          int64
    price.numberDouble             float64
    dtype: object



Específicamente, tenemos dos columnas con fechas (`bestsellers_date.numberLong` y `published_date.numberLong`)  que tienen tipos `object` e `int64`. También tenemos una columna `rank.numberInt` que no tiene el tipo de dato adecuado.

Podemos usar el método `astype` para pasarle a nuestro `DataFrame` un `diccionario` de conversión. Por ejemplo, vamos a convertir nuestras dos columnas de fechas usando un `diccionario` de conversión. El tipo de dato que usamos para manejar fechas es el llamado `datetime`. Este tipo de dato nos permite manipular fechas y horarios muy eficientemente.


```python
diccionario_de_conversion = {
    'bestsellers_date.numberLong': 'datetime64[ns]',
    'published_date.numberLong': 'datetime64[ns]'
}
```


```python
temp = df.astype(diccionario_de_conversion)

temp.head()
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>amazon_product_url</th>
      <th>author</th>
      <th>description</th>
      <th>publisher</th>
      <th>title</th>
      <th>oid</th>
      <th>bestsellers_date.numberLong</th>
      <th>published_date.numberLong</th>
      <th>rank.numberInt</th>
      <th>rank_last_week.numberInt</th>
      <th>weeks_on_list.numberInt</th>
      <th>price.numberDouble</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>http://www.amazon.com/The-Host-Novel-Stephenie...</td>
      <td>Stephenie Meyer</td>
      <td>Descr: Aliens have taken control of the minds ...</td>
      <td>Little, Brown</td>
      <td>THE HOST</td>
      <td>5b4aa4ead3089013507db18c</td>
      <td>2008-05-24</td>
      <td>1970-01-01 00:20:12.883200</td>
      <td>2</td>
      <td>1</td>
      <td>3</td>
      <td>25.99</td>
    </tr>
    <tr>
      <th>1</th>
      <td>http://www.amazon.com/Love-Youre-With-Emily-Gi...</td>
      <td>Emily Giffin</td>
      <td>Descr: A woman's happy marriage is shaken when...</td>
      <td>St. Martin's</td>
      <td>LOVE THE ONE YOU'RE WITH</td>
      <td>5b4aa4ead3089013507db18d</td>
      <td>2008-05-24</td>
      <td>1970-01-01 00:20:12.883200</td>
      <td>3</td>
      <td>2</td>
      <td>2</td>
      <td>24.95</td>
    </tr>
    <tr>
      <th>2</th>
      <td>http://www.amazon.com/The-Front-Garano-Patrici...</td>
      <td>Patricia Cornwell</td>
      <td>Descr: A Massachusetts state investigator and ...</td>
      <td>Putnam</td>
      <td>THE FRONT</td>
      <td>5b4aa4ead3089013507db18e</td>
      <td>2008-05-24</td>
      <td>1970-01-01 00:20:12.883200</td>
      <td>4</td>
      <td>0</td>
      <td>1</td>
      <td>22.95</td>
    </tr>
    <tr>
      <th>3</th>
      <td>http://www.amazon.com/Snuff-Chuck-Palahniuk/dp...</td>
      <td>Chuck Palahniuk</td>
      <td>Descr: An aging porn queens aims to cap her ca...</td>
      <td>Doubleday</td>
      <td>SNUFF</td>
      <td>5b4aa4ead3089013507db18f</td>
      <td>2008-05-24</td>
      <td>1970-01-01 00:20:12.883200</td>
      <td>5</td>
      <td>0</td>
      <td>1</td>
      <td>24.95</td>
    </tr>
    <tr>
      <th>5</th>
      <td>http://www.amazon.com/Phantom-Prey-John-Sandfo...</td>
      <td>John Sandford</td>
      <td>Descr: The Minneapolis detective Lucas Davenpo...</td>
      <td>Putnam</td>
      <td>PHANTOM PREY</td>
      <td>5b4aa4ead3089013507db191</td>
      <td>2008-05-24</td>
      <td>1970-01-01 00:20:12.883200</td>
      <td>7</td>
      <td>4</td>
      <td>3</td>
      <td>26.95</td>
    </tr>
  </tbody>
</table>
</div>




```python
temp.dtypes
```




    amazon_product_url                     object
    author                                 object
    description                            object
    publisher                              object
    title                                  object
    oid                                    object
    bestsellers_date.numberLong    datetime64[ns]
    published_date.numberLong      datetime64[ns]
    rank.numberInt                         object
    rank_last_week.numberInt                int64
    weeks_on_list.numberInt                 int64
    price.numberDouble                    float64
    dtype: object



Como puedes ver, nuestras columnas han sido transformadas. Pero parece que hay un problema, puesto que hay muchísima diferencia de años entre la columna `bestsellers_date` y la columna `published_date`. Esto se debe a que `published_date` está en formato 'milisegundos desde La Época (la medianoche UTC del 1 de enero de 1970)' y `pandas` asume por default que estamos lidiando con nanosegundos.

Para evitar este problema vamos a usar el método `pd.to_datetime` para convertir `published_date`:


```python
pd.to_datetime(df['published_date.numberLong'], unit='ms')
```




    0      2008-06-08
    1      2008-06-08
    2      2008-06-08
    3      2008-06-08
    5      2008-06-08
              ...    
    3027   2013-05-05
    3028   2013-05-05
    3029   2013-05-05
    3030   2013-05-05
    3031   2013-05-05
    Name: published_date.numberLong, Length: 2266, dtype: datetime64[ns]



`to_datetime` nos permite especificar las unidades para que la conversión se realice con éxito.

Vamos ahora qué pasa si queremos convertir `rank.numberInt` usando `astype`:


```python
df['rank.numberInt'].astype(int)
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    <ipython-input-19-179e35ea2d8a> in <module>
    ----> 1 df['rank.numberInt'].astype(int)
    

    ~/.conda/envs/data_science/lib/python3.8/site-packages/pandas/core/generic.py in astype(self, dtype, copy, errors)
       5696         else:
       5697             # else, only a single dtype is given
    -> 5698             new_data = self._data.astype(dtype=dtype, copy=copy, errors=errors)
       5699             return self._constructor(new_data).__finalize__(self)
       5700 


    ~/.conda/envs/data_science/lib/python3.8/site-packages/pandas/core/internals/managers.py in astype(self, dtype, copy, errors)
        580 
        581     def astype(self, dtype, copy: bool = False, errors: str = "raise"):
    --> 582         return self.apply("astype", dtype=dtype, copy=copy, errors=errors)
        583 
        584     def convert(self, **kwargs):


    ~/.conda/envs/data_science/lib/python3.8/site-packages/pandas/core/internals/managers.py in apply(self, f, filter, **kwargs)
        440                 applied = b.apply(f, **kwargs)
        441             else:
    --> 442                 applied = getattr(b, f)(**kwargs)
        443             result_blocks = _extend_blocks(applied, result_blocks)
        444 


    ~/.conda/envs/data_science/lib/python3.8/site-packages/pandas/core/internals/blocks.py in astype(self, dtype, copy, errors)
        623             vals1d = values.ravel()
        624             try:
    --> 625                 values = astype_nansafe(vals1d, dtype, copy=True)
        626             except (ValueError, TypeError):
        627                 # e.g. astype_nansafe can fail on object-dtype of strings


    ~/.conda/envs/data_science/lib/python3.8/site-packages/pandas/core/dtypes/cast.py in astype_nansafe(arr, dtype, copy, skipna)
        872         # work around NumPy brokenness, #1987
        873         if np.issubdtype(dtype.type, np.integer):
    --> 874             return lib.astype_intsafe(arr.ravel(), dtype).reshape(arr.shape)
        875 
        876         # if we have a datetime/timedelta array of objects


    pandas/_libs/lib.pyx in pandas._libs.lib.astype_intsafe()


    ValueError: invalid literal for int() with base 10: 'No Rank'


No podemos hacerlo porque hay unos valores tipo `string` que no pueden ser convertidos a `int`. Para esto usamos el método `to_numeric`, que nos permite indicar que cuando un error sea encontrado, debe de ser sustituido por un `NaN`:


```python
pd.to_numeric(df['rank.numberInt'], errors='coerce')
```




    0        2.0
    1        3.0
    2        4.0
    3        5.0
    5        7.0
            ... 
    3027     8.0
    3028     9.0
    3029    11.0
    3030    13.0
    3031    14.0
    Name: rank.numberInt, Length: 2266, dtype: float64



Vamos a reasignar el resultado al `DataFrame` original:


```python
df['rank.numberInt'] = pd.to_numeric(df['rank.numberInt'], errors='coerce')
```

Ahora, para convertirlo a tipo `int` podemos eliminar los `NaNs` y luego usar `astype`:


```python
df = df.dropna(axis=0).copy()
```


```python
df['rank.numberInt'] = df['rank.numberInt'].astype(int)
```


```python
df.dtypes
```




    amazon_product_url              object
    author                          object
    description                     object
    publisher                       object
    title                           object
    oid                             object
    bestsellers_date.numberLong     object
    published_date.numberLong        int64
    rank.numberInt                   int64
    rank_last_week.numberInt         int64
    weeks_on_list.numberInt          int64
    price.numberDouble             float64
    dtype: object



¡Listo!


```python

```
