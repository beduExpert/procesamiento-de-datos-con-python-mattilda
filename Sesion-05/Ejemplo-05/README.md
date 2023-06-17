## Ejemplo 5: Limpiando nans

### 1. Objetivos:
    - Aprender a limpiar NaNs por filas
    - Aprender a limpiar NaNs por columnas
    - Aprender a llenar NaNs con otros valores útiles
 
---
    
### 2. Desarrollo:

### 1) Limpiando NaNs por filas

Tenemos el siguiente dataset


```python
import pandas as pd
import numpy as np
```


```python
datos = {
    'precio': [34, 54, np.nan, np.nan, 56, 12, 34],
    'cantidad_en_stock': [3, 6, 14, np.nan, 5, 2, 10],
    'productos_vendidos': [3, 45, 23, np.nan, 24, 6, np.nan]
}

df = pd.DataFrame(datos, index=["Pokemaster", "Cegatron", "Pikame Mucho", "Lazarillo de Tormes", "Stevie Wonder", "Needle", "El AyMeDuele"])
```


```python
df
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>precio</th>
      <th>cantidad_en_stock</th>
      <th>productos_vendidos</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Pokemaster</th>
      <td>34.0</td>
      <td>3.0</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>Cegatron</th>
      <td>54.0</td>
      <td>6.0</td>
      <td>45.0</td>
    </tr>
    <tr>
      <th>Pikame Mucho</th>
      <td>NaN</td>
      <td>14.0</td>
      <td>23.0</td>
    </tr>
    <tr>
      <th>Lazarillo de Tormes</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Stevie Wonder</th>
      <td>56.0</td>
      <td>5.0</td>
      <td>24.0</td>
    </tr>
    <tr>
      <th>Needle</th>
      <td>12.0</td>
      <td>2.0</td>
      <td>6.0</td>
    </tr>
    <tr>
      <th>El AyMeDuele</th>
      <td>34.0</td>
      <td>10.0</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



Para limpiar las filas que tengan mínimo 1 valor `NaN`, se utiliza `dropna(axis=0, how='any')`:


```python
df.dropna(axis=0, how='any')
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>precio</th>
      <th>cantidad_en_stock</th>
      <th>productos_vendidos</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Pokemaster</th>
      <td>34.0</td>
      <td>3.0</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>Cegatron</th>
      <td>54.0</td>
      <td>6.0</td>
      <td>45.0</td>
    </tr>
    <tr>
      <th>Stevie Wonder</th>
      <td>56.0</td>
      <td>5.0</td>
      <td>24.0</td>
    </tr>
    <tr>
      <th>Needle</th>
      <td>12.0</td>
      <td>2.0</td>
      <td>6.0</td>
    </tr>
  </tbody>
</table>
</div>



Con el `axis=0` le estamos diciendo que queremos eliminar por filas. Con `how='any'` le decimos que queremos eliminar cualquier fila que tenga mínimo un `NaN`.

Si quisiéramos eliminar sólo las filas donde **todos** los valores sean `NaN`, podemos usar `axis='all'`:


```python
df.dropna(axis=0, how='all')
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>precio</th>
      <th>cantidad_en_stock</th>
      <th>productos_vendidos</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Pokemaster</th>
      <td>34.0</td>
      <td>3.0</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>Cegatron</th>
      <td>54.0</td>
      <td>6.0</td>
      <td>45.0</td>
    </tr>
    <tr>
      <th>Pikame Mucho</th>
      <td>NaN</td>
      <td>14.0</td>
      <td>23.0</td>
    </tr>
    <tr>
      <th>Stevie Wonder</th>
      <td>56.0</td>
      <td>5.0</td>
      <td>24.0</td>
    </tr>
    <tr>
      <th>Needle</th>
      <td>12.0</td>
      <td>2.0</td>
      <td>6.0</td>
    </tr>
    <tr>
      <th>El AyMeDuele</th>
      <td>34.0</td>
      <td>10.0</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



Estos resultados no se aplican directamente al `DataFrame` original. Si queremos que persistan tenemos que asignarlos a otra variable:


```python
df_dropped = df.dropna(axis=0, how='all')
```

### Limpiando NaNs por columnas

Vamos a agregar una columna:


```python
df['descuento'] = np.nan
```


```python
df
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>precio</th>
      <th>cantidad_en_stock</th>
      <th>productos_vendidos</th>
      <th>descuento</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Pokemaster</th>
      <td>34.0</td>
      <td>3.0</td>
      <td>3.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Cegatron</th>
      <td>54.0</td>
      <td>6.0</td>
      <td>45.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Pikame Mucho</th>
      <td>NaN</td>
      <td>14.0</td>
      <td>23.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Lazarillo de Tormes</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Stevie Wonder</th>
      <td>56.0</td>
      <td>5.0</td>
      <td>24.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Needle</th>
      <td>12.0</td>
      <td>2.0</td>
      <td>6.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>El AyMeDuele</th>
      <td>34.0</td>
      <td>10.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



Al igual que por filas, eliminar `NaNs` por columna también se puede hacer usando ´any´ y ´all´. La única diferencia es que ahora hay que usar `axis=1` para que se haga la eliminación por columnas:


```python
df.dropna(axis=1, how='any')
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Pokemaster</th>
    </tr>
    <tr>
      <th>Cegatron</th>
    </tr>
    <tr>
      <th>Pikame Mucho</th>
    </tr>
    <tr>
      <th>Lazarillo de Tormes</th>
    </tr>
    <tr>
      <th>Stevie Wonder</th>
    </tr>
    <tr>
      <th>Needle</th>
    </tr>
    <tr>
      <th>El AyMeDuele</th>
    </tr>
  </tbody>
</table>
</div>




```python
df_dropped = df.dropna(axis=1, how='all')
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>precio</th>
      <th>cantidad_en_stock</th>
      <th>productos_vendidos</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Pokemaster</th>
      <td>34.0</td>
      <td>3.0</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>Cegatron</th>
      <td>54.0</td>
      <td>6.0</td>
      <td>45.0</td>
    </tr>
    <tr>
      <th>Pikame Mucho</th>
      <td>NaN</td>
      <td>14.0</td>
      <td>23.0</td>
    </tr>
    <tr>
      <th>Lazarillo de Tormes</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Stevie Wonder</th>
      <td>56.0</td>
      <td>5.0</td>
      <td>24.0</td>
    </tr>
    <tr>
      <th>Needle</th>
      <td>12.0</td>
      <td>2.0</td>
      <td>6.0</td>
    </tr>
    <tr>
      <th>El AyMeDuele</th>
      <td>34.0</td>
      <td>10.0</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



### Llenando NaNs con valores

Otra cosa que podemos hacer es llenar los valores `NaN` con algún otro valor.

Por ejemplo, digamos que tenemos este dataset:


```python
df
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>precio</th>
      <th>cantidad_en_stock</th>
      <th>productos_vendidos</th>
      <th>descuento</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Pokemaster</th>
      <td>34.0</td>
      <td>3.0</td>
      <td>3.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Cegatron</th>
      <td>54.0</td>
      <td>6.0</td>
      <td>45.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Pikame Mucho</th>
      <td>NaN</td>
      <td>14.0</td>
      <td>23.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Lazarillo de Tormes</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Stevie Wonder</th>
      <td>56.0</td>
      <td>5.0</td>
      <td>24.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Needle</th>
      <td>12.0</td>
      <td>2.0</td>
      <td>6.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>El AyMeDuele</th>
      <td>34.0</td>
      <td>10.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



Lo primero que hay que hacer es eliminar filas y columnas donde **todos** los valores sean `NaN`, puesto que no nos sirven de nada:


```python
df_no_nans = df.dropna(axis=0, how='all')
df_no_nans = df_no_nans.dropna(axis=1, how='all')

df_no_nans
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>precio</th>
      <th>cantidad_en_stock</th>
      <th>productos_vendidos</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Pokemaster</th>
      <td>34.0</td>
      <td>3.0</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>Cegatron</th>
      <td>54.0</td>
      <td>6.0</td>
      <td>45.0</td>
    </tr>
    <tr>
      <th>Pikame Mucho</th>
      <td>NaN</td>
      <td>14.0</td>
      <td>23.0</td>
    </tr>
    <tr>
      <th>Stevie Wonder</th>
      <td>56.0</td>
      <td>5.0</td>
      <td>24.0</td>
    </tr>
    <tr>
      <th>Needle</th>
      <td>12.0</td>
      <td>2.0</td>
      <td>6.0</td>
    </tr>
    <tr>
      <th>El AyMeDuele</th>
      <td>34.0</td>
      <td>10.0</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



Ahora, digamos que podemos asumir que si hay un valor `NaN` en "productos_vendidos" es porque no ha sido vendido aún. En ese caso podemos rellenar ese `NaN` usando `fillna`:


```python
df_no_nans['productos_vendidos'] = df_no_nans['productos_vendidos'].fillna(0)

df_no_nans
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>precio</th>
      <th>cantidad_en_stock</th>
      <th>productos_vendidos</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Pokemaster</th>
      <td>34.0</td>
      <td>3.0</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>Cegatron</th>
      <td>54.0</td>
      <td>6.0</td>
      <td>45.0</td>
    </tr>
    <tr>
      <th>Pikame Mucho</th>
      <td>NaN</td>
      <td>14.0</td>
      <td>23.0</td>
    </tr>
    <tr>
      <th>Stevie Wonder</th>
      <td>56.0</td>
      <td>5.0</td>
      <td>24.0</td>
    </tr>
    <tr>
      <th>Needle</th>
      <td>12.0</td>
      <td>2.0</td>
      <td>6.0</td>
    </tr>
    <tr>
      <th>El AyMeDuele</th>
      <td>34.0</td>
      <td>10.0</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
</div>



Para finalizar, "precio" sí es una variable muy importante, así que nos deshacemos de las filas que aún tengan `NaNs`:


```python
df_no_nans.dropna(axis=0)
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>precio</th>
      <th>cantidad_en_stock</th>
      <th>productos_vendidos</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Pokemaster</th>
      <td>34.0</td>
      <td>3.0</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>Cegatron</th>
      <td>54.0</td>
      <td>6.0</td>
      <td>45.0</td>
    </tr>
    <tr>
      <th>Stevie Wonder</th>
      <td>56.0</td>
      <td>5.0</td>
      <td>24.0</td>
    </tr>
    <tr>
      <th>Needle</th>
      <td>12.0</td>
      <td>2.0</td>
      <td>6.0</td>
    </tr>
    <tr>
      <th>El AyMeDuele</th>
      <td>34.0</td>
      <td>10.0</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
</div>




```python

```
