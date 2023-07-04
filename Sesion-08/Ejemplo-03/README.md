## Ejemplo 3: Uniendo `DataFrames` con `merge`

### 1. Objetivos:
    - Tomar una base de datos segmentada y unirla usando el método `merge`
 
---
    
### 2. Desarrollo:

#### a) Conformando un solo `DataFrame` a partir de la información de dos

Ya tenemos todos nuestros conjuntos de datos guardados cada uno en un archivo .csv. Cada uno contiene información que los demás no contienen, así que necesitamos una manera de unirlos para poder *complementar* con un conjunto la información que le hace falta a otro.

Vamos a leer 2 de nuestros datasets:


```python
import pandas as pd
```


```python
users = pd.read_csv('../../Datasets/MovieLens/users-raw.csv', index_col=0, names=['gender', 'age', 'occupation', 'cp'])
```


```python
users.index.name = 'user_id'
```


```python
occupations = pd.read_csv('../../Datasets/MovieLens/occupations-raw.csv', index_col=0, names=['description'])
```


```python
occupations.index.name = 'occupation_id'
```


```python
users.head()
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>gender</th>
      <th>age</th>
      <th>occupation</th>
      <th>cp</th>
    </tr>
    <tr>
      <th>user_id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>F</td>
      <td>1</td>
      <td>10</td>
      <td>48067</td>
    </tr>
    <tr>
      <th>2</th>
      <td>M</td>
      <td>56</td>
      <td>16</td>
      <td>70072</td>
    </tr>
    <tr>
      <th>3</th>
      <td>M</td>
      <td>25</td>
      <td>15</td>
      <td>55117</td>
    </tr>
    <tr>
      <th>4</th>
      <td>M</td>
      <td>45</td>
      <td>7</td>
      <td>02460</td>
    </tr>
    <tr>
      <th>5</th>
      <td>M</td>
      <td>25</td>
      <td>20</td>
      <td>55455</td>
    </tr>
  </tbody>
</table>
</div>



`users` contiene una columna llamada `occupation` que tiene códigos que corresponden a un índice de la tabla `occupations`. Cada código está mapeado a una descripción textual de la ocupación.

Para "jalar" la información textual de las ocupaciones a la tabla `users` hacemos lo siguiente:


```python
users_full = pd.merge(users, occupations, left_on='occupation', right_index=True).sort_index()
```


```python
users_full
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>gender</th>
      <th>age</th>
      <th>occupation</th>
      <th>cp</th>
      <th>description</th>
    </tr>
    <tr>
      <th>user_id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>F</td>
      <td>1</td>
      <td>10</td>
      <td>48067</td>
      <td>K-12 student</td>
    </tr>
    <tr>
      <th>2</th>
      <td>M</td>
      <td>56</td>
      <td>16</td>
      <td>70072</td>
      <td>self-employed</td>
    </tr>
    <tr>
      <th>3</th>
      <td>M</td>
      <td>25</td>
      <td>15</td>
      <td>55117</td>
      <td>scientist</td>
    </tr>
    <tr>
      <th>4</th>
      <td>M</td>
      <td>45</td>
      <td>7</td>
      <td>02460</td>
      <td>executive/managerial</td>
    </tr>
    <tr>
      <th>5</th>
      <td>M</td>
      <td>25</td>
      <td>20</td>
      <td>55455</td>
      <td>writer</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>6036</th>
      <td>F</td>
      <td>25</td>
      <td>15</td>
      <td>32603</td>
      <td>scientist</td>
    </tr>
    <tr>
      <th>6037</th>
      <td>F</td>
      <td>45</td>
      <td>1</td>
      <td>76006</td>
      <td>academic/educator</td>
    </tr>
    <tr>
      <th>6038</th>
      <td>F</td>
      <td>56</td>
      <td>1</td>
      <td>14706</td>
      <td>academic/educator</td>
    </tr>
    <tr>
      <th>6039</th>
      <td>F</td>
      <td>45</td>
      <td>0</td>
      <td>01060</td>
      <td>other or not specified</td>
    </tr>
    <tr>
      <th>6040</th>
      <td>M</td>
      <td>25</td>
      <td>6</td>
      <td>11106</td>
      <td>doctor/health care</td>
    </tr>
  </tbody>
</table>
<p>6040 rows × 5 columns</p>
</div>



Ahora podríamos cambiar los nombres de nuestras columnas para que sean más descriptivas:


```python
users_full = users_full.rename(columns={'occupation': 'occupation_id', 'description': 'occupation'})
```


```python
users_full
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>gender</th>
      <th>age</th>
      <th>occupation_id</th>
      <th>cp</th>
      <th>occupation</th>
    </tr>
    <tr>
      <th>user_id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>F</td>
      <td>1</td>
      <td>10</td>
      <td>48067</td>
      <td>K-12 student</td>
    </tr>
    <tr>
      <th>2</th>
      <td>M</td>
      <td>56</td>
      <td>16</td>
      <td>70072</td>
      <td>self-employed</td>
    </tr>
    <tr>
      <th>3</th>
      <td>M</td>
      <td>25</td>
      <td>15</td>
      <td>55117</td>
      <td>scientist</td>
    </tr>
    <tr>
      <th>4</th>
      <td>M</td>
      <td>45</td>
      <td>7</td>
      <td>02460</td>
      <td>executive/managerial</td>
    </tr>
    <tr>
      <th>5</th>
      <td>M</td>
      <td>25</td>
      <td>20</td>
      <td>55455</td>
      <td>writer</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>6036</th>
      <td>F</td>
      <td>25</td>
      <td>15</td>
      <td>32603</td>
      <td>scientist</td>
    </tr>
    <tr>
      <th>6037</th>
      <td>F</td>
      <td>45</td>
      <td>1</td>
      <td>76006</td>
      <td>academic/educator</td>
    </tr>
    <tr>
      <th>6038</th>
      <td>F</td>
      <td>56</td>
      <td>1</td>
      <td>14706</td>
      <td>academic/educator</td>
    </tr>
    <tr>
      <th>6039</th>
      <td>F</td>
      <td>45</td>
      <td>0</td>
      <td>01060</td>
      <td>other or not specified</td>
    </tr>
    <tr>
      <th>6040</th>
      <td>M</td>
      <td>25</td>
      <td>6</td>
      <td>11106</td>
      <td>doctor/health care</td>
    </tr>
  </tbody>
</table>
<p>6040 rows × 5 columns</p>
</div>



Listo. Ahora tenemos un `DataFrame` que incluye la información de ambos conjuntos de datos. Esto incrementa muchísimo nuestras posibilidades de análisis y visualización.
