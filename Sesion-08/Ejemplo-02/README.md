## Ejemplo 2: Consultas a la base de datos y construcción de `DataFrames`

### 1. Objetivos:
    - Realizar consultas a la base de datos y construir un `DataFrame` para cada tabla.
 
---
    
### 2. Desarrollo:

#### a) Tablas a `DataFrames`

Ya que tenemos nuestra conexión, basta con usar el comando `SELECT * FROM nombre_de_tabla` para pedir todos los datos que hay en cada tabla:


```python
import mysql.connector
import pandas as pd
```


```python
cnx = mysql.connector.connect(
    host="localhost",
    port=3306,
    user="movienerd",
    password='sonerdy',
    database='movielens'
)
```


```python
cursor = cnx.cursor()
```


```python
cursor.execute("SELECT * FROM users")
```


```python
result = cursor.fetchall()
```

Si recuerdas el último ejemplo, `fetchall` nos regresa una `lista` de `tuplas`. Cada `tupla` representa una fila de nuestro conjunto de datos:


```python
result[0]
```




    (1, 'F', 1, 10, '48067')



Afortunadamente `pandas` puede recibir justamente `listas` de `tuplas` como ingredientes para construir `DataFrames`. Sólo hace falta indicarle el nombre de las columnas. Los nombres de las columnas están especificados en el [archivo Readme.md](../../Datasets/MovieLens/Readme.md) que venía incluido con el dataset:


```python
df = pd.DataFrame(result, columns=['user_id', 'gender', 'age', 'occupation', 'cp'])
```


```python
df.head()
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user_id</th>
      <th>gender</th>
      <th>age</th>
      <th>occupation</th>
      <th>cp</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>F</td>
      <td>1</td>
      <td>10</td>
      <td>48067</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>M</td>
      <td>56</td>
      <td>16</td>
      <td>70072</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>M</td>
      <td>25</td>
      <td>15</td>
      <td>55117</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>M</td>
      <td>45</td>
      <td>7</td>
      <td>02460</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>M</td>
      <td>25</td>
      <td>20</td>
      <td>55455</td>
    </tr>
  </tbody>
</table>
</div>



Creo que sería una buena idea convertir la columna `user_id` en índice para no tener información redundante:


```python
df = df.set_index('user_id', drop=True)

df.head()
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



¡Listo! Vamos a guardar nuestros `DataFrames` en archivos .csv para que no haga falta volver a extraerlos de la base de datos. Ya podemos decirle adiós a nuestro fiel MySQL. ¡Chao, bellisimo!


```python

```
