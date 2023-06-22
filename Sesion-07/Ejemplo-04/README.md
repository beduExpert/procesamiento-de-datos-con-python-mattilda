## Ejemplo 4: `apply`

### 1. Objetivos:
    - Usar `apply` para aplicar funciones a `Series` y `DataFrames`
 
---
    
### 2. Desarrollo:


```python
import pandas as pd
import numpy as np
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



Podemos aplicar funciones a nuestras `Series` con el método `apply`:


```python
def years_since_bestseller(value):
    
    as_datetime = pd.to_datetime(value, unit='ms')
    today = pd.to_datetime('today')
    difference_in_days = (today - as_datetime).days
    in_years = difference_in_days / 365
    
    return in_years
```


```python
df['published_date.numberLong'].apply(years_since_bestseller)
```




    0       11.975342
    1       11.975342
    2       11.975342
    3       11.975342
    5       11.975342
              ...    
    3027     7.065753
    3028     7.065753
    3029     7.065753
    3030     7.065753
    3031     7.065753
    Name: published_date.numberLong, Length: 2266, dtype: float64



O esta otra:


```python
def weeks_on_list_percentage_of_maximum(value, max_weeks_on_list):
    
    percentage = value * 100 / max_weeks_on_list
    as_string = f'{percentage:.2f}%'
    
    return as_string
```


```python
df['weeks_on_list.numberInt'].apply(weeks_on_list_percentage_of_maximum, args=(df['weeks_on_list.numberInt'].max(),))
```




    0       2.78%
    1       1.85%
    2       0.93%
    3       0.93%
    5       2.78%
            ...  
    3027    1.85%
    3028    4.63%
    3029    1.85%
    3030    0.93%
    3031    7.41%
    Name: weeks_on_list.numberInt, Length: 2266, dtype: object



Veremos cómo usar `apply` en `DataFrames` en un módulo posterior, ya que este dataset no se presta mucho para eso.


```python

```
