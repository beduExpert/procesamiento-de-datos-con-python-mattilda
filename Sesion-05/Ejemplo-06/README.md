## Ejemplo 6: Limpiando NaNs en un dataset real

### 1. Objetivos:
    - Aplicar lo aprendido hasta ahora en un dataset real
 
---
    
### 2. Desarrollo:


```python
import pandas as pd
```

Para leer un archivo .csv en `pandas`, usamos `read_csv` y le indicamos que el separador (el signo que delimita las columnas en el archivo .csv) es una coma:


```python
df = pd.read_csv('../../Datasets/melbourne_housing-raw.csv', sep=',')

df
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
      <th>Suburb</th>
      <th>Address</th>
      <th>Rooms</th>
      <th>Type</th>
      <th>Price</th>
      <th>Method</th>
      <th>SellerG</th>
      <th>Date</th>
      <th>Distance</th>
      <th>Postcode</th>
      <th>...</th>
      <th>Bathroom</th>
      <th>Car</th>
      <th>Landsize</th>
      <th>BuildingArea</th>
      <th>YearBuilt</th>
      <th>CouncilArea</th>
      <th>Lattitude</th>
      <th>Longtitude</th>
      <th>Regionname</th>
      <th>Propertycount</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Abbotsford</td>
      <td>68 Studley St</td>
      <td>2</td>
      <td>h</td>
      <td>NaN</td>
      <td>SS</td>
      <td>Jellis</td>
      <td>3/09/2016</td>
      <td>2.5</td>
      <td>3067.0</td>
      <td>...</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>126.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Yarra</td>
      <td>-37.80140</td>
      <td>144.99580</td>
      <td>Northern Metropolitan</td>
      <td>4019.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Abbotsford</td>
      <td>85 Turner St</td>
      <td>2</td>
      <td>h</td>
      <td>1480000.0</td>
      <td>S</td>
      <td>Biggin</td>
      <td>3/12/2016</td>
      <td>2.5</td>
      <td>3067.0</td>
      <td>...</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>202.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Yarra</td>
      <td>-37.79960</td>
      <td>144.99840</td>
      <td>Northern Metropolitan</td>
      <td>4019.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Abbotsford</td>
      <td>25 Bloomburg St</td>
      <td>2</td>
      <td>h</td>
      <td>1035000.0</td>
      <td>S</td>
      <td>Biggin</td>
      <td>4/02/2016</td>
      <td>2.5</td>
      <td>3067.0</td>
      <td>...</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>156.0</td>
      <td>79.0</td>
      <td>1900.00</td>
      <td>Yarra</td>
      <td>-37.80790</td>
      <td>144.99340</td>
      <td>Northern Metropolitan</td>
      <td>4019.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Abbotsford</td>
      <td>18/659 Victoria St</td>
      <td>3</td>
      <td>u</td>
      <td>NaN</td>
      <td>VB</td>
      <td>Rounds</td>
      <td>4/02/2016</td>
      <td>2.5</td>
      <td>3067.0</td>
      <td>...</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Yarra</td>
      <td>-37.81140</td>
      <td>145.01160</td>
      <td>Northern Metropolitan</td>
      <td>4019.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Abbotsford</td>
      <td>5 Charles St</td>
      <td>3</td>
      <td>h</td>
      <td>1465000.0</td>
      <td>SP</td>
      <td>Biggin</td>
      <td>4/03/2017</td>
      <td>2.5</td>
      <td>3067.0</td>
      <td>...</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>134.0</td>
      <td>150.0</td>
      <td>1900.00</td>
      <td>Yarra</td>
      <td>-37.80930</td>
      <td>144.99440</td>
      <td>Northern Metropolitan</td>
      <td>4019.0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>19735</th>
      <td>Windsor</td>
      <td>201/152 Peel St</td>
      <td>2</td>
      <td>u</td>
      <td>560000.0</td>
      <td>PI</td>
      <td>hockingstuart</td>
      <td>29/07/2017</td>
      <td>4.6</td>
      <td>3181.0</td>
      <td>...</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>585.0</td>
      <td>NaN</td>
      <td>Whittlesea</td>
      <td>-37.67681</td>
      <td>145.00323</td>
      <td>Southern Metropolitan</td>
      <td>4380.0</td>
    </tr>
    <tr>
      <th>19736</th>
      <td>Wollert</td>
      <td>60 Saltlake Bvd</td>
      <td>3</td>
      <td>h</td>
      <td>525300.0</td>
      <td>S</td>
      <td>Stockdale</td>
      <td>29/07/2017</td>
      <td>25.5</td>
      <td>3750.0</td>
      <td>...</td>
      <td>2.0</td>
      <td>2.0</td>
      <td>NaN</td>
      <td>333.0</td>
      <td>NaN</td>
      <td>Darebin</td>
      <td>-37.75884</td>
      <td>145.00264</td>
      <td>Northern Metropolitan</td>
      <td>2940.0</td>
    </tr>
    <tr>
      <th>19737</th>
      <td>Yarraville</td>
      <td>2 Adeney St</td>
      <td>2</td>
      <td>h</td>
      <td>750000.0</td>
      <td>SP</td>
      <td>hockingstuart</td>
      <td>29/07/2017</td>
      <td>6.3</td>
      <td>3013.0</td>
      <td>...</td>
      <td>2.0</td>
      <td>2.0</td>
      <td>1999.0</td>
      <td>199.0</td>
      <td>140.00</td>
      <td>Darebin</td>
      <td>-37.75948</td>
      <td>144.99615</td>
      <td>Western Metropolitan</td>
      <td>6543.0</td>
    </tr>
    <tr>
      <th>19738</th>
      <td>Yarraville</td>
      <td>54 Pentland Pde</td>
      <td>6</td>
      <td>h</td>
      <td>2450000.0</td>
      <td>VB</td>
      <td>Village</td>
      <td>29/07/2017</td>
      <td>6.3</td>
      <td>3013.0</td>
      <td>...</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>2011.0</td>
      <td>238.0</td>
      <td>118.00</td>
      <td>Hume</td>
      <td>-37.70322</td>
      <td>144.88236</td>
      <td>Western Metropolitan</td>
      <td>6543.0</td>
    </tr>
    <tr>
      <th>19739</th>
      <td>Yarraville</td>
      <td>10/127 Somerville Rd</td>
      <td>3</td>
      <td>t</td>
      <td>645000.0</td>
      <td>SP</td>
      <td>Jas</td>
      <td>29/07/2017</td>
      <td>6.3</td>
      <td>3013.0</td>
      <td>...</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>1980.0</td>
      <td>0.0</td>
      <td>66.32</td>
      <td>Hume</td>
      <td>-37.69815</td>
      <td>144.88019</td>
      <td>Western Metropolitan</td>
      <td>6543.0</td>
    </tr>
  </tbody>
</table>
<p>19740 rows × 21 columns</p>
</div>




```python
df.shape
```




    (19740, 21)




```python
df.head(5)
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
      <th>Suburb</th>
      <th>Address</th>
      <th>Rooms</th>
      <th>Type</th>
      <th>Price</th>
      <th>Method</th>
      <th>SellerG</th>
      <th>Date</th>
      <th>Distance</th>
      <th>Postcode</th>
      <th>...</th>
      <th>Bathroom</th>
      <th>Car</th>
      <th>Landsize</th>
      <th>BuildingArea</th>
      <th>YearBuilt</th>
      <th>CouncilArea</th>
      <th>Lattitude</th>
      <th>Longtitude</th>
      <th>Regionname</th>
      <th>Propertycount</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Abbotsford</td>
      <td>68 Studley St</td>
      <td>2</td>
      <td>h</td>
      <td>NaN</td>
      <td>SS</td>
      <td>Jellis</td>
      <td>3/09/2016</td>
      <td>2.5</td>
      <td>3067.0</td>
      <td>...</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>126.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Yarra</td>
      <td>-37.8014</td>
      <td>144.9958</td>
      <td>Northern Metropolitan</td>
      <td>4019.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Abbotsford</td>
      <td>85 Turner St</td>
      <td>2</td>
      <td>h</td>
      <td>1480000.0</td>
      <td>S</td>
      <td>Biggin</td>
      <td>3/12/2016</td>
      <td>2.5</td>
      <td>3067.0</td>
      <td>...</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>202.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Yarra</td>
      <td>-37.7996</td>
      <td>144.9984</td>
      <td>Northern Metropolitan</td>
      <td>4019.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Abbotsford</td>
      <td>25 Bloomburg St</td>
      <td>2</td>
      <td>h</td>
      <td>1035000.0</td>
      <td>S</td>
      <td>Biggin</td>
      <td>4/02/2016</td>
      <td>2.5</td>
      <td>3067.0</td>
      <td>...</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>156.0</td>
      <td>79.0</td>
      <td>1900.0</td>
      <td>Yarra</td>
      <td>-37.8079</td>
      <td>144.9934</td>
      <td>Northern Metropolitan</td>
      <td>4019.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Abbotsford</td>
      <td>18/659 Victoria St</td>
      <td>3</td>
      <td>u</td>
      <td>NaN</td>
      <td>VB</td>
      <td>Rounds</td>
      <td>4/02/2016</td>
      <td>2.5</td>
      <td>3067.0</td>
      <td>...</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Yarra</td>
      <td>-37.8114</td>
      <td>145.0116</td>
      <td>Northern Metropolitan</td>
      <td>4019.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Abbotsford</td>
      <td>5 Charles St</td>
      <td>3</td>
      <td>h</td>
      <td>1465000.0</td>
      <td>SP</td>
      <td>Biggin</td>
      <td>4/03/2017</td>
      <td>2.5</td>
      <td>3067.0</td>
      <td>...</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>134.0</td>
      <td>150.0</td>
      <td>1900.0</td>
      <td>Yarra</td>
      <td>-37.8093</td>
      <td>144.9944</td>
      <td>Northern Metropolitan</td>
      <td>4019.0</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 21 columns</p>
</div>




```python
df.isna().sum()
```




    Suburb               0
    Address              0
    Rooms                0
    Type                 0
    Price             4344
    Method               0
    SellerG              0
    Date                 0
    Distance             8
    Postcode             8
    Bedroom2          4413
    Bathroom          4413
    Car               4413
    Landsize          4796
    BuildingArea     11123
    YearBuilt        10389
    CouncilArea       4444
    Lattitude         4292
    Longtitude        4292
    Regionname           8
    Propertycount        8
    dtype: int64



Hay demasiados `NaNs` en las columnas 'BuildingArea' y 'YearBuilt', así que vamos a deshacernos de esas columnas:


```python
df_2 = df.drop(columns=['BuildingArea', 'YearBuilt'])

df_2.isna().sum()
```




    Suburb              0
    Address             0
    Rooms               0
    Type                0
    Price            4344
    Method              0
    SellerG             0
    Date                0
    Distance            8
    Postcode            8
    Bedroom2         4413
    Bathroom         4413
    Car              4413
    Landsize         4796
    CouncilArea      4444
    Lattitude        4292
    Longtitude       4292
    Regionname          8
    Propertycount       8
    dtype: int64



Llenemos los `NaNs` en Regionname con la palabra `Unknown`:


```python
df_2['Regionname'] = df_2['Regionname'].fillna('Unknown')

df_2.isna().sum()
```




    Suburb              0
    Address             0
    Rooms               0
    Type                0
    Price            4344
    Method              0
    SellerG             0
    Date                0
    Distance            8
    Postcode            8
    Bedroom2         4413
    Bathroom         4413
    Car              4413
    Landsize         4796
    CouncilArea      4444
    Lattitude        4292
    Longtitude       4292
    Regionname          0
    Propertycount       8
    dtype: int64



Ahora eliminemos las filas que contengan al menos un `NaN`:


```python
df_dropped = df_2.dropna(axis=0, how='any')

df_dropped.isna().sum()
```




    Suburb           0
    Address          0
    Rooms            0
    Type             0
    Price            0
    Method           0
    SellerG          0
    Date             0
    Distance         0
    Postcode         0
    Bedroom2         0
    Bathroom         0
    Car              0
    Landsize         0
    CouncilArea      0
    Lattitude        0
    Longtitude       0
    Regionname       0
    Propertycount    0
    dtype: int64



Éste es el número de columnas con el que nos quedamos:


```python
df_dropped.shape
```




    (11646, 19)



Guardemos el resultado:


```python
df_dropped.to_csv('../../Datasets/melbourne_housing-no_nans.csv')
```

Seguiremos trabajando este dataset en el último ejemplo.


```python

```
