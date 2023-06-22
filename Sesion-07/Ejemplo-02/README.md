## Ejemplo 2: Manipulación de Strings

### 1. Objetivos:
    - Aprender a usar `replace`, `strip`, `title`, `upper`, `lower` y `split` para transformar datos tipo `string``
 
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



Empecemos con la columna `description` que tiene un 'Descr:' al inicio de cada texto. Si queremos remover ese texto podemos usar el método `replace` de la propiedad `str` de esa `Serie`:


```python
df['description'].str.replace('Descr:', '')
```




    0        Aliens have taken control of the minds and bo...
    1        A woman's happy marriage is shaken when she e...
    2        A Massachusetts state investigator and his te...
    3        An aging porn queens aims to cap her career b...
    5        The Minneapolis detective Lucas Davenport inv...
                                  ...                        
    3027     The New York lawyer Stone Barrington discover...
    3028     Jake Fisher discovers that neither the woman ...
    3029     Six friends meet in the 1970s at a summer art...
    3030     Bernie Gunther, the Berlin cop, is sent to Sm...
    3031     A New Hampshire baker finds herself in the mi...
    Name: description, Length: 2266, dtype: object



Para que el cambio persista, tenemos que reasignarlo:


```python
df['description'] = df['description'].str.replace('Descr:', '')
```


```python
df.loc[0, 'description']
```




    ' Aliens have taken control of the minds and bodies of most humans, but one woman won’t surrender.     '



Como puedes ver, tenemos también espacios vacíos al principio y final de nuestras `strings`. Vamos a removerlos usando `strip`:


```python
df['description'].str.strip()
```




    0       Aliens have taken control of the minds and bod...
    1       A woman's happy marriage is shaken when she en...
    2       A Massachusetts state investigator and his tea...
    3       An aging porn queens aims to cap her career by...
    5       The Minneapolis detective Lucas Davenport inve...
                                  ...                        
    3027    The New York lawyer Stone Barrington discovers...
    3028    Jake Fisher discovers that neither the woman h...
    3029    Six friends meet in the 1970s at a summer arts...
    3030    Bernie Gunther, the Berlin cop, is sent to Smo...
    3031    A New Hampshire baker finds herself in the mid...
    Name: description, Length: 2266, dtype: object




```python
df['description'] = df['description'].str.strip()
```


```python
df.loc[0, 'description']
```




    'Aliens have taken control of the minds and bodies of most humans, but one woman won’t surrender.'



Perfecto.

Ahora veamos la columna 'title', cuyos textos están en mayúsculas. Esto no es muy agradable, así que podemos usar algunos métodos para modificar el patrón de mayúsculas y minúsculas:


```python
df['title'].str.lower()
```




    0                       the host
    1       love the one you're with
    2                      the front
    3                          snuff
    5                   phantom prey
                      ...           
    3027     unintended consequences
    3028                   six years
    3029            the interestings
    3030        a man without breath
    3031             the storyteller
    Name: title, Length: 2266, dtype: object




```python
df['title'].str.title()
```




    0                       The Host
    1       Love The One You'Re With
    2                      The Front
    3                          Snuff
    5                   Phantom Prey
                      ...           
    3027     Unintended Consequences
    3028                   Six Years
    3029            The Interestings
    3030        A Man Without Breath
    3031             The Storyteller
    Name: title, Length: 2266, dtype: object



Este último es más adecuado, vamos a guardarlo:


```python
df['title'] = df['title'].str.title()
```

Ahora, digamos que queremos separar nuestra columna `author` en dos columnas `author_first_name` y `author_last_name`. Eso lo podemos hacer con el método `split`:


```python
df['author'].str.split(' ')
```




    0         [Stephenie, Meyer]
    1            [Emily, Giffin]
    2       [Patricia, Cornwell]
    3         [Chuck, Palahniuk]
    5           [John, Sandford]
                    ...         
    3027         [Stuart, Woods]
    3028         [Harlan, Coben]
    3029         [Meg, Wolitzer]
    3030          [Philip, Kerr]
    3031         [Jodi, Picoult]
    Name: author, Length: 2266, dtype: object



Podemos convertirlo en dos columnas así:


```python
df['author'].str.split(' ', expand=True)
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
      <th>1</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Stephenie</td>
      <td>Meyer</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Emily</td>
      <td>Giffin</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Patricia</td>
      <td>Cornwell</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Chuck</td>
      <td>Palahniuk</td>
    </tr>
    <tr>
      <th>5</th>
      <td>John</td>
      <td>Sandford</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>3027</th>
      <td>Stuart</td>
      <td>Woods</td>
    </tr>
    <tr>
      <th>3028</th>
      <td>Harlan</td>
      <td>Coben</td>
    </tr>
    <tr>
      <th>3029</th>
      <td>Meg</td>
      <td>Wolitzer</td>
    </tr>
    <tr>
      <th>3030</th>
      <td>Philip</td>
      <td>Kerr</td>
    </tr>
    <tr>
      <th>3031</th>
      <td>Jodi</td>
      <td>Picoult</td>
    </tr>
  </tbody>
</table>
<p>2266 rows × 2 columns</p>
</div>




```python
df[['author_first_name', 'author_last_name']] = df['author'].str.split(' ', expand=True)
```


```python
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
      <th>author_first_name</th>
      <th>author_last_name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>http://www.amazon.com/The-Host-Novel-Stephenie...</td>
      <td>Stephenie Meyer</td>
      <td>Aliens have taken control of the minds and bod...</td>
      <td>Little, Brown</td>
      <td>The Host</td>
      <td>5b4aa4ead3089013507db18c</td>
      <td>2008-05-24 00:00:00</td>
      <td>1212883200000</td>
      <td>2</td>
      <td>1</td>
      <td>3</td>
      <td>25.99</td>
      <td>Stephenie</td>
      <td>Meyer</td>
    </tr>
    <tr>
      <th>1</th>
      <td>http://www.amazon.com/Love-Youre-With-Emily-Gi...</td>
      <td>Emily Giffin</td>
      <td>A woman's happy marriage is shaken when she en...</td>
      <td>St. Martin's</td>
      <td>Love The One You'Re With</td>
      <td>5b4aa4ead3089013507db18d</td>
      <td>2008-05-24 00:00:00</td>
      <td>1212883200000</td>
      <td>3</td>
      <td>2</td>
      <td>2</td>
      <td>24.95</td>
      <td>Emily</td>
      <td>Giffin</td>
    </tr>
    <tr>
      <th>2</th>
      <td>http://www.amazon.com/The-Front-Garano-Patrici...</td>
      <td>Patricia Cornwell</td>
      <td>A Massachusetts state investigator and his tea...</td>
      <td>Putnam</td>
      <td>The Front</td>
      <td>5b4aa4ead3089013507db18e</td>
      <td>2008-05-24 00:00:00</td>
      <td>1212883200000</td>
      <td>4</td>
      <td>0</td>
      <td>1</td>
      <td>22.95</td>
      <td>Patricia</td>
      <td>Cornwell</td>
    </tr>
    <tr>
      <th>3</th>
      <td>http://www.amazon.com/Snuff-Chuck-Palahniuk/dp...</td>
      <td>Chuck Palahniuk</td>
      <td>An aging porn queens aims to cap her career by...</td>
      <td>Doubleday</td>
      <td>Snuff</td>
      <td>5b4aa4ead3089013507db18f</td>
      <td>2008-05-24 00:00:00</td>
      <td>1212883200000</td>
      <td>5</td>
      <td>0</td>
      <td>1</td>
      <td>24.95</td>
      <td>Chuck</td>
      <td>Palahniuk</td>
    </tr>
    <tr>
      <th>5</th>
      <td>http://www.amazon.com/Phantom-Prey-John-Sandfo...</td>
      <td>John Sandford</td>
      <td>The Minneapolis detective Lucas Davenport inve...</td>
      <td>Putnam</td>
      <td>Phantom Prey</td>
      <td>5b4aa4ead3089013507db191</td>
      <td>2008-05-24 00:00:00</td>
      <td>1212883200000</td>
      <td>7</td>
      <td>4</td>
      <td>3</td>
      <td>26.95</td>
      <td>John</td>
      <td>Sandford</td>
    </tr>
  </tbody>
</table>
</div>



¡Éxito!


```python

```
