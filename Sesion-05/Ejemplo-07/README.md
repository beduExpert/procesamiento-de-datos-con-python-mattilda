## Ejemplo 7: Reindexando y renombrando columnas

### 1. Objetivos:
    - Limpiar un poco más nuestro dataset asignándole un índice y nombres de columnas apropiadas
 
---
    
### 2. Desarrollo:

Limpiemos nuestro dataset hasta que esté justo como lo dejamos en el Ejemplo pasado:


```python
import pandas as pd
```


```python
df = pd.read_csv('../../Datasets/melbourne_housing-raw.csv')
```


```python
df_2 = df.drop(columns=['BuildingArea', 'YearBuilt'])
```


```python
df_2['Regionname'] = df_2['Regionname'].fillna('Unknown')
```


```python
df_dropped = df_2.dropna(axis=0, how='any')
```


```python
df_dropped
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
      <th>Bedroom2</th>
      <th>Bathroom</th>
      <th>Car</th>
      <th>Landsize</th>
      <th>CouncilArea</th>
      <th>Lattitude</th>
      <th>Longtitude</th>
      <th>Regionname</th>
      <th>Propertycount</th>
    </tr>
  </thead>
  <tbody>
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
      <td>2.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>202.0</td>
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
      <td>2.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>156.0</td>
      <td>Yarra</td>
      <td>-37.80790</td>
      <td>144.99340</td>
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
      <td>3.0</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>134.0</td>
      <td>Yarra</td>
      <td>-37.80930</td>
      <td>144.99440</td>
      <td>Northern Metropolitan</td>
      <td>4019.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Abbotsford</td>
      <td>40 Federation La</td>
      <td>3</td>
      <td>h</td>
      <td>850000.0</td>
      <td>PI</td>
      <td>Biggin</td>
      <td>4/03/2017</td>
      <td>2.5</td>
      <td>3067.0</td>
      <td>3.0</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>94.0</td>
      <td>Yarra</td>
      <td>-37.79690</td>
      <td>144.99690</td>
      <td>Northern Metropolitan</td>
      <td>4019.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Abbotsford</td>
      <td>55a Park St</td>
      <td>4</td>
      <td>h</td>
      <td>1600000.0</td>
      <td>VB</td>
      <td>Nelson</td>
      <td>4/06/2016</td>
      <td>2.5</td>
      <td>3067.0</td>
      <td>3.0</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>120.0</td>
      <td>Yarra</td>
      <td>-37.80720</td>
      <td>144.99410</td>
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
    </tr>
    <tr>
      <th>19731</th>
      <td>Whittlesea</td>
      <td>30 Sherwin St</td>
      <td>3</td>
      <td>h</td>
      <td>601000.0</td>
      <td>S</td>
      <td>Ray</td>
      <td>29/07/2017</td>
      <td>35.5</td>
      <td>3757.0</td>
      <td>3.0</td>
      <td>2.0</td>
      <td>2.0</td>
      <td>1970.0</td>
      <td>Manningham</td>
      <td>-37.76311</td>
      <td>145.10494</td>
      <td>Northern Victoria</td>
      <td>2170.0</td>
    </tr>
    <tr>
      <th>19734</th>
      <td>Williamstown</td>
      <td>87 Pasco St</td>
      <td>3</td>
      <td>h</td>
      <td>1285000.0</td>
      <td>S</td>
      <td>Jas</td>
      <td>29/07/2017</td>
      <td>6.8</td>
      <td>3016.0</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>2010.0</td>
      <td>Whittlesea</td>
      <td>-37.68199</td>
      <td>145.01744</td>
      <td>Western Metropolitan</td>
      <td>6380.0</td>
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
      <td>3.0</td>
      <td>2.0</td>
      <td>2.0</td>
      <td>1999.0</td>
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
      <td>3.0</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>2011.0</td>
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
      <td>2.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>1980.0</td>
      <td>Hume</td>
      <td>-37.69815</td>
      <td>144.88019</td>
      <td>Western Metropolitan</td>
      <td>6543.0</td>
    </tr>
  </tbody>
</table>
<p>11646 rows × 19 columns</p>
</div>



Ahora, tenemos dos situaciones:

1. La primera es que nuestro índice no coincide con el número de filas que tenemos. En este caso, dado que nuestro índice es secuencial y numérico, y no tiene ningún significado además de eso, nos convendría que reflejara la cantidad de filas que tenemos en nuestro dataset.

Para lograr eso vamos a usar el método `reset_index`:


```python
df_dropped.reset_index()
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
      <th>index</th>
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
      <th>Bedroom2</th>
      <th>Bathroom</th>
      <th>Car</th>
      <th>Landsize</th>
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
      <td>1</td>
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
      <td>2.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>202.0</td>
      <td>Yarra</td>
      <td>-37.79960</td>
      <td>144.99840</td>
      <td>Northern Metropolitan</td>
      <td>4019.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
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
      <td>2.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>156.0</td>
      <td>Yarra</td>
      <td>-37.80790</td>
      <td>144.99340</td>
      <td>Northern Metropolitan</td>
      <td>4019.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4</td>
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
      <td>3.0</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>134.0</td>
      <td>Yarra</td>
      <td>-37.80930</td>
      <td>144.99440</td>
      <td>Northern Metropolitan</td>
      <td>4019.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>5</td>
      <td>Abbotsford</td>
      <td>40 Federation La</td>
      <td>3</td>
      <td>h</td>
      <td>850000.0</td>
      <td>PI</td>
      <td>Biggin</td>
      <td>4/03/2017</td>
      <td>2.5</td>
      <td>3067.0</td>
      <td>3.0</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>94.0</td>
      <td>Yarra</td>
      <td>-37.79690</td>
      <td>144.99690</td>
      <td>Northern Metropolitan</td>
      <td>4019.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>6</td>
      <td>Abbotsford</td>
      <td>55a Park St</td>
      <td>4</td>
      <td>h</td>
      <td>1600000.0</td>
      <td>VB</td>
      <td>Nelson</td>
      <td>4/06/2016</td>
      <td>2.5</td>
      <td>3067.0</td>
      <td>3.0</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>120.0</td>
      <td>Yarra</td>
      <td>-37.80720</td>
      <td>144.99410</td>
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
    </tr>
    <tr>
      <th>11641</th>
      <td>19731</td>
      <td>Whittlesea</td>
      <td>30 Sherwin St</td>
      <td>3</td>
      <td>h</td>
      <td>601000.0</td>
      <td>S</td>
      <td>Ray</td>
      <td>29/07/2017</td>
      <td>35.5</td>
      <td>3757.0</td>
      <td>3.0</td>
      <td>2.0</td>
      <td>2.0</td>
      <td>1970.0</td>
      <td>Manningham</td>
      <td>-37.76311</td>
      <td>145.10494</td>
      <td>Northern Victoria</td>
      <td>2170.0</td>
    </tr>
    <tr>
      <th>11642</th>
      <td>19734</td>
      <td>Williamstown</td>
      <td>87 Pasco St</td>
      <td>3</td>
      <td>h</td>
      <td>1285000.0</td>
      <td>S</td>
      <td>Jas</td>
      <td>29/07/2017</td>
      <td>6.8</td>
      <td>3016.0</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>2010.0</td>
      <td>Whittlesea</td>
      <td>-37.68199</td>
      <td>145.01744</td>
      <td>Western Metropolitan</td>
      <td>6380.0</td>
    </tr>
    <tr>
      <th>11643</th>
      <td>19737</td>
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
      <td>3.0</td>
      <td>2.0</td>
      <td>2.0</td>
      <td>1999.0</td>
      <td>Darebin</td>
      <td>-37.75948</td>
      <td>144.99615</td>
      <td>Western Metropolitan</td>
      <td>6543.0</td>
    </tr>
    <tr>
      <th>11644</th>
      <td>19738</td>
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
      <td>3.0</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>2011.0</td>
      <td>Hume</td>
      <td>-37.70322</td>
      <td>144.88236</td>
      <td>Western Metropolitan</td>
      <td>6543.0</td>
    </tr>
    <tr>
      <th>11645</th>
      <td>19739</td>
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
      <td>2.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>1980.0</td>
      <td>Hume</td>
      <td>-37.69815</td>
      <td>144.88019</td>
      <td>Western Metropolitan</td>
      <td>6543.0</td>
    </tr>
  </tbody>
</table>
<p>11646 rows × 20 columns</p>
</div>



Nuestro índice ya está correcto, pero ahora tenemos un columna llamada `index` que contiene el índice original. Como no queremos guardar esos datos, agregamos la opción `drop=True` para eliminar el índice anterior:


```python
df_dropped.reset_index(drop=True)
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
      <th>Bedroom2</th>
      <th>Bathroom</th>
      <th>Car</th>
      <th>Landsize</th>
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
      <td>85 Turner St</td>
      <td>2</td>
      <td>h</td>
      <td>1480000.0</td>
      <td>S</td>
      <td>Biggin</td>
      <td>3/12/2016</td>
      <td>2.5</td>
      <td>3067.0</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>202.0</td>
      <td>Yarra</td>
      <td>-37.79960</td>
      <td>144.99840</td>
      <td>Northern Metropolitan</td>
      <td>4019.0</td>
    </tr>
    <tr>
      <th>1</th>
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
      <td>2.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>156.0</td>
      <td>Yarra</td>
      <td>-37.80790</td>
      <td>144.99340</td>
      <td>Northern Metropolitan</td>
      <td>4019.0</td>
    </tr>
    <tr>
      <th>2</th>
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
      <td>3.0</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>134.0</td>
      <td>Yarra</td>
      <td>-37.80930</td>
      <td>144.99440</td>
      <td>Northern Metropolitan</td>
      <td>4019.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Abbotsford</td>
      <td>40 Federation La</td>
      <td>3</td>
      <td>h</td>
      <td>850000.0</td>
      <td>PI</td>
      <td>Biggin</td>
      <td>4/03/2017</td>
      <td>2.5</td>
      <td>3067.0</td>
      <td>3.0</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>94.0</td>
      <td>Yarra</td>
      <td>-37.79690</td>
      <td>144.99690</td>
      <td>Northern Metropolitan</td>
      <td>4019.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Abbotsford</td>
      <td>55a Park St</td>
      <td>4</td>
      <td>h</td>
      <td>1600000.0</td>
      <td>VB</td>
      <td>Nelson</td>
      <td>4/06/2016</td>
      <td>2.5</td>
      <td>3067.0</td>
      <td>3.0</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>120.0</td>
      <td>Yarra</td>
      <td>-37.80720</td>
      <td>144.99410</td>
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
    </tr>
    <tr>
      <th>11641</th>
      <td>Whittlesea</td>
      <td>30 Sherwin St</td>
      <td>3</td>
      <td>h</td>
      <td>601000.0</td>
      <td>S</td>
      <td>Ray</td>
      <td>29/07/2017</td>
      <td>35.5</td>
      <td>3757.0</td>
      <td>3.0</td>
      <td>2.0</td>
      <td>2.0</td>
      <td>1970.0</td>
      <td>Manningham</td>
      <td>-37.76311</td>
      <td>145.10494</td>
      <td>Northern Victoria</td>
      <td>2170.0</td>
    </tr>
    <tr>
      <th>11642</th>
      <td>Williamstown</td>
      <td>87 Pasco St</td>
      <td>3</td>
      <td>h</td>
      <td>1285000.0</td>
      <td>S</td>
      <td>Jas</td>
      <td>29/07/2017</td>
      <td>6.8</td>
      <td>3016.0</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>2010.0</td>
      <td>Whittlesea</td>
      <td>-37.68199</td>
      <td>145.01744</td>
      <td>Western Metropolitan</td>
      <td>6380.0</td>
    </tr>
    <tr>
      <th>11643</th>
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
      <td>3.0</td>
      <td>2.0</td>
      <td>2.0</td>
      <td>1999.0</td>
      <td>Darebin</td>
      <td>-37.75948</td>
      <td>144.99615</td>
      <td>Western Metropolitan</td>
      <td>6543.0</td>
    </tr>
    <tr>
      <th>11644</th>
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
      <td>3.0</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>2011.0</td>
      <td>Hume</td>
      <td>-37.70322</td>
      <td>144.88236</td>
      <td>Western Metropolitan</td>
      <td>6543.0</td>
    </tr>
    <tr>
      <th>11645</th>
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
      <td>2.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>1980.0</td>
      <td>Hume</td>
      <td>-37.69815</td>
      <td>144.88019</td>
      <td>Western Metropolitan</td>
      <td>6543.0</td>
    </tr>
  </tbody>
</table>
<p>11646 rows × 19 columns</p>
</div>



Guardemos nuestros cambios:


```python
df_dropped = df_dropped.reset_index(drop=True)
```

Ahora tenemos un problema con los nombres de las columnas: Tienen inconsistencias en la manera cómo están nombradas y algunas incluso tienen errores ortográficos. Vamos a cambiarles los nombres para tener consistencia:


```python
column_name_mapping = {
    'Suburb': 'suburb',
    'Address': 'address',
    'Rooms': 'rooms',
    'Type': 'type',
    'Price': 'price',
    'Method': 'method',
    'SellerG': 'seller_g',
    'Date': 'date',
    'Distance': 'distance',
    'Postcode': 'post_code',
    'Bedroom2': 'bedrooms',
    'Bathroom': 'bathroom',
    'Car': 'car',
    'Landsize': 'land_size',
    'CouncilArea': 'council_area',
    'Lattitude': 'latitude',
    'Longtitude': 'longitude',
    'Regionname': 'region_name',
    'Propertycount': 'property_count'
}
```


```python
df_renamed = df_dropped.rename(columns=column_name_mapping)

df_renamed
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
      <th>suburb</th>
      <th>address</th>
      <th>rooms</th>
      <th>type</th>
      <th>price</th>
      <th>method</th>
      <th>seller_g</th>
      <th>date</th>
      <th>distance</th>
      <th>post_code</th>
      <th>bedrooms</th>
      <th>bathroom</th>
      <th>car</th>
      <th>land_size</th>
      <th>council_area</th>
      <th>latitude</th>
      <th>longitude</th>
      <th>region_name</th>
      <th>property_count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
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
      <td>2.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>202.0</td>
      <td>Yarra</td>
      <td>-37.79960</td>
      <td>144.99840</td>
      <td>Northern Metropolitan</td>
      <td>4019.0</td>
    </tr>
    <tr>
      <th>1</th>
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
      <td>2.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>156.0</td>
      <td>Yarra</td>
      <td>-37.80790</td>
      <td>144.99340</td>
      <td>Northern Metropolitan</td>
      <td>4019.0</td>
    </tr>
    <tr>
      <th>2</th>
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
      <td>3.0</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>134.0</td>
      <td>Yarra</td>
      <td>-37.80930</td>
      <td>144.99440</td>
      <td>Northern Metropolitan</td>
      <td>4019.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Abbotsford</td>
      <td>40 Federation La</td>
      <td>3</td>
      <td>h</td>
      <td>850000.0</td>
      <td>PI</td>
      <td>Biggin</td>
      <td>4/03/2017</td>
      <td>2.5</td>
      <td>3067.0</td>
      <td>3.0</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>94.0</td>
      <td>Yarra</td>
      <td>-37.79690</td>
      <td>144.99690</td>
      <td>Northern Metropolitan</td>
      <td>4019.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Abbotsford</td>
      <td>55a Park St</td>
      <td>4</td>
      <td>h</td>
      <td>1600000.0</td>
      <td>VB</td>
      <td>Nelson</td>
      <td>4/06/2016</td>
      <td>2.5</td>
      <td>3067.0</td>
      <td>3.0</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>120.0</td>
      <td>Yarra</td>
      <td>-37.80720</td>
      <td>144.99410</td>
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
    </tr>
    <tr>
      <th>11641</th>
      <td>Whittlesea</td>
      <td>30 Sherwin St</td>
      <td>3</td>
      <td>h</td>
      <td>601000.0</td>
      <td>S</td>
      <td>Ray</td>
      <td>29/07/2017</td>
      <td>35.5</td>
      <td>3757.0</td>
      <td>3.0</td>
      <td>2.0</td>
      <td>2.0</td>
      <td>1970.0</td>
      <td>Manningham</td>
      <td>-37.76311</td>
      <td>145.10494</td>
      <td>Northern Victoria</td>
      <td>2170.0</td>
    </tr>
    <tr>
      <th>11642</th>
      <td>Williamstown</td>
      <td>87 Pasco St</td>
      <td>3</td>
      <td>h</td>
      <td>1285000.0</td>
      <td>S</td>
      <td>Jas</td>
      <td>29/07/2017</td>
      <td>6.8</td>
      <td>3016.0</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>2010.0</td>
      <td>Whittlesea</td>
      <td>-37.68199</td>
      <td>145.01744</td>
      <td>Western Metropolitan</td>
      <td>6380.0</td>
    </tr>
    <tr>
      <th>11643</th>
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
      <td>3.0</td>
      <td>2.0</td>
      <td>2.0</td>
      <td>1999.0</td>
      <td>Darebin</td>
      <td>-37.75948</td>
      <td>144.99615</td>
      <td>Western Metropolitan</td>
      <td>6543.0</td>
    </tr>
    <tr>
      <th>11644</th>
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
      <td>3.0</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>2011.0</td>
      <td>Hume</td>
      <td>-37.70322</td>
      <td>144.88236</td>
      <td>Western Metropolitan</td>
      <td>6543.0</td>
    </tr>
    <tr>
      <th>11645</th>
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
      <td>2.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>1980.0</td>
      <td>Hume</td>
      <td>-37.69815</td>
      <td>144.88019</td>
      <td>Western Metropolitan</td>
      <td>6543.0</td>
    </tr>
  </tbody>
</table>
<p>11646 rows × 19 columns</p>
</div>



¡Listo! Nuestro dataset va agarrando forma.


```python

```
