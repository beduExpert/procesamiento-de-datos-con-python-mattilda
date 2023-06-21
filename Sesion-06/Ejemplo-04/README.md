## Ejemplo 4: Concat con Series

### 1. Objetivos:
    - Usar pd.concat para concatenar `Series`
 
---
    
### 2. Desarrollo:

Muchas veces vamos a tener `Series` o `DataFrames` que queremos unir en una sola estructura. Para eso podemos usar `pd.concat`. Concatenando `Series`, podemos hacer lo siguiente:


```python
import pandas as pd
```


```python
serie_1 = pd.Series([1, 2, 3], index=['a', 'b', 'c'])
serie_2 = pd.Series([4, 5, 6], index=['d', 'f', 'e'])
```


```python
pd.concat([serie_1, serie_2], axis=0)
```




    a    1
    b    2
    c    3
    d    4
    f    5
    e    6
    dtype: int64



También podemos concatenar horizontalmente:


```python
pd.concat([serie_1, serie_2], axis=1)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
      <th>1</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>1.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>b</th>
      <td>2.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>c</th>
      <td>3.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>d</th>
      <td>NaN</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>f</th>
      <td>NaN</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>e</th>
      <td>NaN</td>
      <td>6.0</td>
    </tr>
  </tbody>
</table>
</div>



Podemos nombrar nuestras columnas para saber cuál era cuál:



```python
pd.concat([serie_1, serie_2], axis=1, keys=['serie_1', 'serie_2'])
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>serie_1</th>
      <th>serie_2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>1.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>b</th>
      <td>2.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>c</th>
      <td>3.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>d</th>
      <td>NaN</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>f</th>
      <td>NaN</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>e</th>
      <td>NaN</td>
      <td>6.0</td>
    </tr>
  </tbody>
</table>
</div>



Esto pasa si concatenamos horizontalmente usando el mismo índice:


```python
serie_3 = pd.Series([7, 8, 9], index=['a', 'b', 'c'])

pd.concat([serie_1, serie_3], axis=1, keys=['serie_1', 'serie_3'])
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>serie_1</th>
      <th>serie_3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>1</td>
      <td>7</td>
    </tr>
    <tr>
      <th>b</th>
      <td>2</td>
      <td>8</td>
    </tr>
    <tr>
      <th>c</th>
      <td>3</td>
      <td>9</td>
    </tr>
  </tbody>
</table>
</div>



Si concatenamos verticalmente dos `Series` que comparten el índice, tenemos el problema de no poder diferenciar los índices:


```python
pd.concat([serie_1, serie_3], axis=0)
```




    a    1
    b    2
    c    3
    a    7
    b    8
    c    9
    dtype: int64



A veces queremos esto, pero cuando no, podemos agregar un segundo nivel de índice para hacer la diferencia:


```python
pd.concat([serie_1, serie_3], axis=0, keys=['serie_1', 'serie_3'])
```




    serie_1  a    1
             b    2
             c    3
    serie_3  a    7
             b    8
             c    9
    dtype: int64



Esto se llama un `Multiíndice`. Podemos acceder a un `multiíndice` en un solo nivel o en ambos:


```python
series_concat = pd.concat([serie_1, serie_3], axis=0, keys=['serie_1', 'serie_3'])
```


```python
series_concat.loc['serie_1']
```




    a    1
    b    2
    c    3
    dtype: int64




```python
series_concat.loc[('serie_1', 'b')]
```




    2




```python

```
