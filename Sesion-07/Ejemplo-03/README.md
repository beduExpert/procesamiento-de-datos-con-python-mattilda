## Ejemplo 3: `map`

### 1. Objetivos:
    - Usar `map` para convertir datos usando un `diccionario` o una `función``
 
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



Digamos que queremos transformar los datos de nuestra columna 'rank.numberInt' para que el 'rankink' esté dado por letras, no por números.

Sabemos que hay un valor 'No Rank' en esa columna, así que nuestro diccionario de conversión podría verse así:


```python
int_a_letra = {
    '1': 'a',
    '2': 'b',
    '3': 'c',
    '4': 'd',
    '5': 'e',
    '6': 'f',
    '7': 'g',
    '8': 'h',
    '9': 'i',
    '10': 'j',
    '11': 'k',
    '12': 'l',
    '13': 'm',
    '14': 'n',
    '15': 'o',
    '16': 'p',
    'No Rank': 'z'
}
```

Lo aplicamos usando `map`:


```python
df['rank.numberInt'].map(int_a_letra).head(20)
```




    0     b
    1     c
    2     d
    3     e
    5     g
    6     h
    7     i
    8     j
    9     l
    10    m
    11    n
    13    z
    14    d
    16    f
    17    g
    18    h
    19    i
    20    j
    21    k
    22    l
    Name: rank.numberInt, dtype: object



También podemos usar una función para `map`. Por ejemplo esta función que realiza una correspondencia entre el precio de un libro y su representación en `string`:


```python
def double_to_money(value):
    
    return f'${value} USD'
```


```python
df['price.numberDouble'].map(double_to_money)
```




    0       $25.99 USD
    1       $24.95 USD
    2       $22.95 USD
    3       $24.95 USD
    5       $26.95 USD
               ...    
    3027    $26.95 USD
    3028    $27.95 USD
    3029    $27.95 USD
    3030    $26.95 USD
    3031    $28.99 USD
    Name: price.numberDouble, Length: 2266, dtype: object



Lo único que tienes que pensar al usar `map` es: "¿Este dato tiene una correspondencia con otro dato que pueda representar con un diccionario o una función?". Y listo.


```python

```
