## Ejemplo 5: Filtros

### 1. Objetivos:
    - Aprender cómo funcionan los filtros
    - Aplicar varios filtros para verlos en acción
 
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



Digamos que queremos todas los records donde el nombre del autor empiece con 'R'. Primero, usamos `operadores de comparación` (o en este caso, el método `str.startswith`) para obtener nuestro filtro:


```python
df['author'].str.startswith('R')
```




    0       False
    1       False
    2       False
    3       False
    5       False
            ...  
    3027    False
    3028    False
    3029    False
    3030    False
    3031    False
    Name: author, Length: 2266, dtype: bool



Lo que obtenemos de regreso es una `Serie` con la misma longitud que la `Serie` original. Se aplicó el método o la comparación a cada elemento de la `Serie` original. Estos métodos o comparaciones regresan `True` o `False` dependiendo de cada valor. La `Serie` resultante acumula los `Trues` y `Falses` que obtengamos de la comparación o de la aplicación del método.

Después, al pasar este filtro al `operador de indexación` del `DataFrame`, todas las filas a las que les corresponda un `True` se mantienen, mientras que las filas a las que les corresponde un `False` se dejan fuera del subconjunto resultante:


```python
df[df['author'].str.startswith('R')].head()
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
      <th>79</th>
      <td>http://www.amazon.com/Chasing-Darkness-Elvis-N...</td>
      <td>Robert Crais</td>
      <td>Descr: he Los Angeles private eye Elvis Cole r...</td>
      <td>Simon &amp; Schuster</td>
      <td>CHASING DARKNESS</td>
      <td>5b4aa4ead3089013507db209</td>
      <td>2008-07-05 00:00:00</td>
      <td>1216512000000</td>
      <td>7</td>
      <td>0</td>
      <td>1</td>
      <td>25.95</td>
    </tr>
    <tr>
      <th>94</th>
      <td>http://www.amazon.com/Chasing-Darkness-Elvis-N...</td>
      <td>Robert Crais</td>
      <td>Descr: Is the Los Angeles private eye Elvis Co...</td>
      <td>Simon &amp; Schuster</td>
      <td>CHASING DARKNESS</td>
      <td>5b4aa4ead3089013507db221</td>
      <td>2008-07-12 00:00:00</td>
      <td>1217116800000</td>
      <td>11</td>
      <td>7</td>
      <td>2</td>
      <td>25.95</td>
    </tr>
    <tr>
      <th>110</th>
      <td>http://www.amazon.com/Killer-View-Fleming-Ridl...</td>
      <td>Ridley Pearson</td>
      <td>Descr: A sheriff in Sun Valley, Idaho, investi...</td>
      <td>Putnam</td>
      <td>KILLER VIEW</td>
      <td>5b4aa4ead3089013507db239</td>
      <td>2008-07-19 00:00:00</td>
      <td>1217721600000</td>
      <td>15</td>
      <td>0</td>
      <td>1</td>
      <td>24.95</td>
    </tr>
    <tr>
      <th>143</th>
      <td>http://www.amazon.com/Foreign-Body-Robin-Cook/...</td>
      <td>Robin Cook</td>
      <td>Descr: A medical student investigates a rising...</td>
      <td>Putnam</td>
      <td>FOREIGN BODY</td>
      <td>5b4aa4ead3089013507db26f</td>
      <td>2008-08-09 00:00:00</td>
      <td>1219536000000</td>
      <td>9</td>
      <td>0</td>
      <td>1</td>
      <td>25.95</td>
    </tr>
    <tr>
      <th>158</th>
      <td>http://www.amazon.com/Foreign-Body-Robin-Cook/...</td>
      <td>Robin Cook</td>
      <td>Descr: A medical student investigates a rising...</td>
      <td>Putnam</td>
      <td>FOREIGN BODY</td>
      <td>5b4aa4ead3089013507db287</td>
      <td>2008-08-16 00:00:00</td>
      <td>1220140800000</td>
      <td>No Rank</td>
      <td>9</td>
      <td>2</td>
      <td>25.95</td>
    </tr>
  </tbody>
</table>
</div>



Podemos también guardar nuestros filtros en variables y después utilizarlos:


```python
filtro_precio_mayor_a_20 = df['price.numberDouble'] > 20
```


```python
df[filtro_precio_mayor_a_20].head()
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



Podemos incluso aplicar dos o más filtros utilizando `operadores lógicos`. En este caso, nuestro operador `and` se representa con un `&` y el operador `or` se representa con `|`:


```python
filtro_rank_numero_uno = df['rank.numberInt'] == '1'
```


```python
df[filtro_precio_mayor_a_20 & filtro_rank_numero_uno].head()
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
      <th>51</th>
      <td>http://www.amazon.com/Fearless-Fourteen-Janet-...</td>
      <td>Janet Evanovich</td>
      <td>Descr: Stephanie Plum and her boyfriend Joe Mo...</td>
      <td>St. Martin’s</td>
      <td>FEARLESS FOURTEEN</td>
      <td>5b4aa4ead3089013507db1db</td>
      <td>2008-06-21 00:00:00</td>
      <td>1215302400000</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>27.95</td>
    </tr>
    <tr>
      <th>63</th>
      <td>http://www.amazon.com/Fearless-Fourteen-Janet-...</td>
      <td>Janet Evanovich</td>
      <td>Descr: Stephanie Plum and her boyfriend Joe Mo...</td>
      <td>St. Martin’s</td>
      <td>FEARLESS FOURTEEN</td>
      <td>5b4aa4ead3089013507db1ef</td>
      <td>2008-06-28 00:00:00</td>
      <td>1215907200000</td>
      <td>1</td>
      <td>1</td>
      <td>2</td>
      <td>27.95</td>
    </tr>
    <tr>
      <th>85</th>
      <td>http://www.amazon.com/Tribute-Nora-Roberts/dp/...</td>
      <td>Nora Roberts</td>
      <td>Descr: A former child star returns to Virginia...</td>
      <td>Putnam</td>
      <td>TRIBUTE</td>
      <td>5b4aa4ead3089013507db217</td>
      <td>2008-07-12 00:00:00</td>
      <td>1217116800000</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>26.95</td>
    </tr>
    <tr>
      <th>98</th>
      <td>http://www.amazon.com/Tribute-Nora-Roberts/dp/...</td>
      <td>Nora Roberts</td>
      <td>Descr: A former child star returns to Virginia...</td>
      <td>Putnam</td>
      <td>TRIBUTE</td>
      <td>5b4aa4ead3089013507db22b</td>
      <td>2008-07-19 00:00:00</td>
      <td>1217721600000</td>
      <td>1</td>
      <td>1</td>
      <td>2</td>
      <td>26.95</td>
    </tr>
    <tr>
      <th>111</th>
      <td>http://www.amazon.com/Secret-Servant-Gabriel-A...</td>
      <td>Daniel Silva</td>
      <td>Descr: Gabriel Allon, an art restorer and an o...</td>
      <td>Putnam</td>
      <td>THE SECRET SERVANT</td>
      <td>5b4aa4ead3089013507db23f</td>
      <td>2008-07-26 00:00:00</td>
      <td>1218326400000</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>26.95</td>
    </tr>
  </tbody>
</table>
</div>


