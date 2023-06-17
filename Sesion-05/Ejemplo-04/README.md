## Ejemplo 4: Identificación y conteo de NaNs

### 1. Objetivos:
    - Aprender a identificar NaNs
    - Aprender a realizar conteo de NaNs por fila y por columna
 
---
    
### 2. Desarrollo:

Los `NaNs` se ven así:


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



Para contarlos podemos usar una función vectorizada llamada `isna`, que nos regresa esto:


```python
df.isna()
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
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>Cegatron</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>Pikame Mucho</th>
      <td>True</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>Lazarillo de Tormes</th>
      <td>True</td>
      <td>True</td>
      <td>True</td>
    </tr>
    <tr>
      <th>Stevie Wonder</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>Needle</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>El AyMeDuele</th>
      <td>False</td>
      <td>False</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>



`isna` regresa `True` cuando encuentra un `NaN` y `False` cuando el valor es válido.

Después, podemos contar cuántos `NaNs` existen usando la agregación `sum`, que suma `1` por cada `True` y `0` por cada `False`:


```python
df.isna().sum(axis=0)
```




    precio                2
    cantidad_en_stock     1
    productos_vendidos    2
    dtype: int64



Con `axis=0` nos regresa el conteo por columnas. Con `axis=1` nos regresa el conteo por filas:


```python
df.isna().sum(axis=1)
```




    Pokemaster             0
    Cegatron               0
    Pikame Mucho           1
    Lazarillo de Tormes    3
    Stevie Wonder          0
    Needle                 0
    El AyMeDuele           1
    dtype: int64



Practiquemos rápidamente esto antes de aprender a deshacernos de estos `NaNs`.


```python

```
