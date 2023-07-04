## Ejemplo 4: Agrupando datos con `groupby`

### 1. Objetivos:
    - Aprender a usar `grouby` para segmentar nuestros conjuntos de datos y aplicar funciones agregadoras a cada segmento.
 
---
    
### 2. Desarrollo:

#### a) Segmentando datos con `groupby`

En nuestro Reto pasado construimos un nuevo conjunto de datos agregando la información de las tablas `occupations` y `age_ranges` a la tabla `users`. Vamos a leer este dataset primero:


```python
import pandas as pd
```


```python
users = pd.read_csv('../../Datasets/MovieLens/users-full.csv', index_col=0)

users
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>gender</th>
      <th>age_id</th>
      <th>age_range</th>
      <th>occupation_id</th>
      <th>occupation</th>
      <th>cp</th>
    </tr>
    <tr>
      <th>user_id</th>
      <th></th>
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
      <td>Under 18</td>
      <td>10</td>
      <td>K-12 student</td>
      <td>48067</td>
    </tr>
    <tr>
      <th>2</th>
      <td>M</td>
      <td>56</td>
      <td>56+</td>
      <td>16</td>
      <td>self-employed</td>
      <td>70072</td>
    </tr>
    <tr>
      <th>3</th>
      <td>M</td>
      <td>25</td>
      <td>25-34</td>
      <td>15</td>
      <td>scientist</td>
      <td>55117</td>
    </tr>
    <tr>
      <th>4</th>
      <td>M</td>
      <td>45</td>
      <td>45-49</td>
      <td>7</td>
      <td>executive/managerial</td>
      <td>02460</td>
    </tr>
    <tr>
      <th>5</th>
      <td>M</td>
      <td>25</td>
      <td>25-34</td>
      <td>20</td>
      <td>writer</td>
      <td>55455</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
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
      <td>25-34</td>
      <td>15</td>
      <td>scientist</td>
      <td>32603</td>
    </tr>
    <tr>
      <th>6037</th>
      <td>F</td>
      <td>45</td>
      <td>45-49</td>
      <td>1</td>
      <td>academic/educator</td>
      <td>76006</td>
    </tr>
    <tr>
      <th>6038</th>
      <td>F</td>
      <td>56</td>
      <td>56+</td>
      <td>1</td>
      <td>academic/educator</td>
      <td>14706</td>
    </tr>
    <tr>
      <th>6039</th>
      <td>F</td>
      <td>45</td>
      <td>45-49</td>
      <td>0</td>
      <td>other or not specified</td>
      <td>01060</td>
    </tr>
    <tr>
      <th>6040</th>
      <td>M</td>
      <td>25</td>
      <td>25-34</td>
      <td>6</td>
      <td>doctor/health care</td>
      <td>11106</td>
    </tr>
  </tbody>
</table>
<p>6040 rows × 6 columns</p>
</div>



Vamos a ver qué pasa si agrupamos nuestro conjunto usando la columna `gender`:


```python
users.groupby('gender')
```




    <pandas.core.groupby.generic.DataFrameGroupBy object at 0x1168447c0>



Para ver algún resultado más legible tenemos que aplicar funciones agregadoras a nuestro objeto `groupby`:


```python
users.groupby('gender').size()
```




    gender
    F    1709
    M    4331
    dtype: int64



`size` nos hace un conteo de cuántas muestras hay en cada grupo y regresa el total. Ahora podemos ver entonces que hay 1709 mujeres y 4331 hombres en nuestro dataset.

También podemos pedir columnas específicas de nuestros grupos y aplicar agregaciones a cada columna:


```python
users.groupby('gender')['occupation'].value_counts()
```




    gender  occupation            
    F       college/grad student      234
            other or not specified    232
            academic/educator         209
            executive/managerial      139
            doctor/health care        102
            clerical/admin            100
            artist                     91
            homemaker                  89
            sales/marketing            79
            writer                     78
            K-12 student               66
            technician/engineer        52
            self-employed              51
            programmer                 50
            retired                    34
            customer service           31
            scientist                  28
            lawyer                     22
            unemployed                 15
            tradesman/craftsman         4
            farmer                      3
    M       executive/managerial      540
            college/grad student      525
            other or not specified    479
            technician/engineer       450
            programmer                338
            academic/educator         319
            sales/marketing           223
            writer                    203
            self-employed             190
            artist                    176
            doctor/health care        134
            K-12 student              129
            scientist                 116
            retired                   108
            lawyer                    107
            customer service           81
            clerical/admin             73
            tradesman/craftsman        66
            unemployed                 57
            farmer                     14
            homemaker                   3
    Name: occupation, dtype: int64



Podemos usar dos o más columnas para agrupar también. Lo que sucede es que el dataset se agrupa usando la primer columna, y luego, dentro de cada grupo se hace una segunda agrupación usando la segunda columna:


```python
users.groupby(['gender', 'age_range'])['occupation'].value_counts()
```




    gender  age_range  occupation            
    F       18-24      college/grad student      163
                       other or not specified     32
                       academic/educator          18
                       sales/marketing            15
                       writer                     14
                                                ... 
    M       Under 18   executive/managerial        1
                       farmer                      1
                       lawyer                      1
                       programmer                  1
                       retired                     1
    Name: occupation, Length: 241, dtype: int64



Aquí hemos segmentado nuestro dataset en dos niveles. En el primer nivel, podemos obtener datasets independientes para cada género:


```python
users_ga_counts = users.groupby(['gender', 'age_range'])['occupation'].value_counts()
```


```python
users_ga_counts.loc['F']
```




    age_range  occupation            
    18-24      college/grad student      163
               other or not specified     32
               academic/educator          18
               sales/marketing            15
               writer                     14
                                        ... 
    Under 18   other or not specified      9
               artist                      2
               unemployed                  2
               academic/educator           1
               executive/managerial        1
    Name: occupation, Length: 110, dtype: int64



En un segundo nivel, podemos obtener datasets por cada rango de edades en cada género:


```python
users_ga_counts.loc[('F', '18-24')]
```




    occupation
    college/grad student      163
    other or not specified     32
    academic/educator          18
    sales/marketing            15
    writer                     14
    artist                      9
    clerical/admin              9
    technician/engineer         6
    unemployed                  6
    customer service            5
    homemaker                   5
    K-12 student                3
    doctor/health care          3
    executive/managerial        3
    programmer                  3
    self-employed               2
    lawyer                      1
    scientist                   1
    Name: occupation, dtype: int64



¡Genial!

Ahora, no todas las funciones están disponibles "out-of-the-box" para ser aplicadas a objetos `groupby`. Hay algunas funciones que no podemos utilizar directamente y que para poder aplicarlas necesitamos usar el método `agg`. `agg` recibe una función o una lista de funciones y se las aplica a las columnas solicitadas de cada grupo.

Por ejemplo, podemos encontrar la "moda" (la categoría que más veces aparece en una columna específica) de esta manera:


```python
users.groupby('gender')['occupation'].agg(pd.Series.mode)
```




    gender
    F    college/grad student
    M    executive/managerial
    Name: occupation, dtype: object



Podemos aplicar la función a dos columnas al mismo tiempo:


```python
users.groupby('gender')[['age_range', 'occupation']].agg(pd.Series.mode)
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>age_range</th>
      <th>occupation</th>
    </tr>
    <tr>
      <th>gender</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>F</th>
      <td>25-34</td>
      <td>college/grad student</td>
    </tr>
    <tr>
      <th>M</th>
      <td>25-34</td>
      <td>executive/managerial</td>
    </tr>
  </tbody>
</table>
</div>



Y también podemos aplicar varias funciones al mismo tiempo pasándole a `agg` una lista de funciones. En este caso vamos a usar algunos análisis estadísticos a la columna `age_id`. En realidad estos análisis no van a ser precisos porque esta columna contiene ids que representan rangos de edades, no edades como tal. Pero considéralo un simple ejemplo para ver cómo funcionan las herramientas:


```python
users.groupby('gender')['age_id'].agg(['mean', 'median', 'std'])
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>mean</th>
      <th>median</th>
      <th>std</th>
    </tr>
    <tr>
      <th>gender</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>F</th>
      <td>30.859567</td>
      <td>25</td>
      <td>13.242564</td>
    </tr>
    <tr>
      <th>M</th>
      <td>30.552297</td>
      <td>25</td>
      <td>12.757110</td>
    </tr>
  </tbody>
</table>
</div>



Vamos ahora a practicar nuestras nuevas herramientas en unos cuantos Retos.


```python

```
