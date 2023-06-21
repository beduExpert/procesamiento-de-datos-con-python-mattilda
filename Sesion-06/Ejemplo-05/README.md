## Ejemplo 5: Concat con DataFrames

### 1. Objetivos:
    - Usar pd.concat para concatenar `DataFrames`
 
---
    
### 2. Desarrollo:

Exactamente los mismos principios aplican a la concatenación de `DataFrames`:


```python
import pandas as pd
```


```python
data_1 = {
    'column_1': [1, 2, 3],
    'column_2': [4, 5, 6]
}

df_1 = pd.DataFrame(data_1, index=['a', 'b', 'c'])

df_1
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>column_1</th>
      <th>column_2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>1</td>
      <td>4</td>
    </tr>
    <tr>
      <th>b</th>
      <td>2</td>
      <td>5</td>
    </tr>
    <tr>
      <th>c</th>
      <td>3</td>
      <td>6</td>
    </tr>
  </tbody>
</table>
</div>




```python
data_2 = {
    'column_1': [7, 8, 9],
    'column_2': [10, 11, 12]
}

df_2 = pd.DataFrame(data_1, index=['d', 'e', 'f'])

df_2
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>column_1</th>
      <th>column_2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>d</th>
      <td>7</td>
      <td>10</td>
    </tr>
    <tr>
      <th>e</th>
      <td>8</td>
      <td>11</td>
    </tr>
    <tr>
      <th>f</th>
      <td>9</td>
      <td>12</td>
    </tr>
  </tbody>
</table>
</div>



Podemos unirlos verticalmente:


```python
pd.concat([df_1, df_2], axis=0)
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>column_1</th>
      <th>column_2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>1</td>
      <td>4</td>
    </tr>
    <tr>
      <th>b</th>
      <td>2</td>
      <td>5</td>
    </tr>
    <tr>
      <th>c</th>
      <td>3</td>
      <td>6</td>
    </tr>
    <tr>
      <th>d</th>
      <td>7</td>
      <td>10</td>
    </tr>
    <tr>
      <th>e</th>
      <td>8</td>
      <td>11</td>
    </tr>
    <tr>
      <th>f</th>
      <td>9</td>
      <td>12</td>
    </tr>
  </tbody>
</table>
</div>



Horizontalmente:


```python
pd.concat([df_1, df_2], axis=1)
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>column_1</th>
      <th>column_2</th>
      <th>column_1</th>
      <th>column_2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>1.0</td>
      <td>4.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>b</th>
      <td>2.0</td>
      <td>5.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>c</th>
      <td>3.0</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>d</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>7.0</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>e</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>8.0</td>
      <td>11.0</td>
    </tr>
    <tr>
      <th>f</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>9.0</td>
      <td>12.0</td>
    </tr>
  </tbody>
</table>
</div>



Si tienen el mismo índice, evitamos los `NaNs`:


```python
data_3 = {
    'column_3': [7, 8, 9],
    'column_4': [10, 11, 12]
}

df_3 = pd.DataFrame(data_3, index=['a', 'b', 'c'])

df_3
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>column_3</th>
      <th>column_4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>7</td>
      <td>10</td>
    </tr>
    <tr>
      <th>b</th>
      <td>8</td>
      <td>11</td>
    </tr>
    <tr>
      <th>c</th>
      <td>9</td>
      <td>12</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.concat([df_1, df_3], axis=1)
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>column_1</th>
      <th>column_2</th>
      <th>column_3</th>
      <th>column_4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>1</td>
      <td>4</td>
      <td>7</td>
      <td>10</td>
    </tr>
    <tr>
      <th>b</th>
      <td>2</td>
      <td>5</td>
      <td>8</td>
      <td>11</td>
    </tr>
    <tr>
      <th>c</th>
      <td>3</td>
      <td>6</td>
      <td>9</td>
      <td>12</td>
    </tr>
  </tbody>
</table>
</div>



Si concatenamos verticalmente con el mismo índice, no podemos diferenciarlos:


```python
data_4 = {
    'column_1': [7, 8, 9],
    'column_2': [10, 11, 12]
}

df_4 = pd.DataFrame(data_4, index=['a', 'b', 'c'])

df_4
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>column_1</th>
      <th>column_2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>7</td>
      <td>10</td>
    </tr>
    <tr>
      <th>b</th>
      <td>8</td>
      <td>11</td>
    </tr>
    <tr>
      <th>c</th>
      <td>9</td>
      <td>12</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.concat([df_1, df_4], axis=0)
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>column_1</th>
      <th>column_2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>1</td>
      <td>4</td>
    </tr>
    <tr>
      <th>b</th>
      <td>2</td>
      <td>5</td>
    </tr>
    <tr>
      <th>c</th>
      <td>3</td>
      <td>6</td>
    </tr>
    <tr>
      <th>a</th>
      <td>7</td>
      <td>10</td>
    </tr>
    <tr>
      <th>b</th>
      <td>8</td>
      <td>11</td>
    </tr>
    <tr>
      <th>c</th>
      <td>9</td>
      <td>12</td>
    </tr>
  </tbody>
</table>
</div>



Podemos agregar `multiíndices`:


```python
df_concat = pd.concat([df_1, df_4], axis=0, keys=['df_1', 'df_4'])

df_concat
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>column_1</th>
      <th>column_2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="3" valign="top">df_1</th>
      <th>a</th>
      <td>1</td>
      <td>4</td>
    </tr>
    <tr>
      <th>b</th>
      <td>2</td>
      <td>5</td>
    </tr>
    <tr>
      <th>c</th>
      <td>3</td>
      <td>6</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">df_4</th>
      <th>a</th>
      <td>7</td>
      <td>10</td>
    </tr>
    <tr>
      <th>b</th>
      <td>8</td>
      <td>11</td>
    </tr>
    <tr>
      <th>c</th>
      <td>9</td>
      <td>12</td>
    </tr>
  </tbody>
</table>
</div>



Y podemos accesarlos de igual manera:


```python
df_concat.loc['df_1']
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>column_1</th>
      <th>column_2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>1</td>
      <td>4</td>
    </tr>
    <tr>
      <th>b</th>
      <td>2</td>
      <td>5</td>
    </tr>
    <tr>
      <th>c</th>
      <td>3</td>
      <td>6</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_concat.loc[('df_1', 'b')]
```




    column_1    2
    column_2    5
    Name: (df_1, b), dtype: int64



También podemos unir más de dos `DataFrames` agregándolos todos a la lista:


```python
pd.concat([df_1, df_2, df_3, df_4], axis=1)
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>column_1</th>
      <th>column_2</th>
      <th>column_1</th>
      <th>column_2</th>
      <th>column_3</th>
      <th>column_4</th>
      <th>column_1</th>
      <th>column_2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>1.0</td>
      <td>4.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>7.0</td>
      <td>10.0</td>
      <td>7.0</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>b</th>
      <td>2.0</td>
      <td>5.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>8.0</td>
      <td>11.0</td>
      <td>8.0</td>
      <td>11.0</td>
    </tr>
    <tr>
      <th>c</th>
      <td>3.0</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>9.0</td>
      <td>12.0</td>
      <td>9.0</td>
      <td>12.0</td>
    </tr>
    <tr>
      <th>d</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>7.0</td>
      <td>10.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>e</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>8.0</td>
      <td>11.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>f</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>9.0</td>
      <td>12.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python

```
