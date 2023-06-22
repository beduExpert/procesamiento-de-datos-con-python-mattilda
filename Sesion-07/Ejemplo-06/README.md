## Ejemplo 6: Sort

### 1. Objetivos:
    - Aprender a usar `sort_values` para reordenar nuestros datos
 
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



Por ejemplo, queremos ordenar nuestras entradas empezando por el libro de mayor precio hasta el libro de menor precio. Esto es un ordenamiento usando la columna 'price.numberDouble' de manera descendente. Esto se haría de la siguiente manera:


```python
df.sort_values('price.numberDouble', ascending=False)
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
      <th>2264</th>
      <td>http://www.amazon.com/1Q84-Haruki-Murakami-ebo...</td>
      <td>Haruki Murakami</td>
      <td>Descr: In 1980s Tokyo, a woman who punishes pe...</td>
      <td>Knopf</td>
      <td>1Q84</td>
      <td>5b4aa4ead3089013507dbff5</td>
      <td>2011-12-03 00:00:00</td>
      <td>1324166400000</td>
      <td>11</td>
      <td>12</td>
      <td>6</td>
      <td>30.50</td>
    </tr>
    <tr>
      <th>2255</th>
      <td>http://www.amazon.com/1Q84-Haruki-Murakami-ebo...</td>
      <td>Haruki Murakami</td>
      <td>Descr: In 1980s Tokyo, a woman who punishes pe...</td>
      <td>Knopf</td>
      <td>1Q84</td>
      <td>5b4aa4ead3089013507dbfe2</td>
      <td>2011-11-26 00:00:00</td>
      <td>1323561600000</td>
      <td>12</td>
      <td>10</td>
      <td>5</td>
      <td>30.50</td>
    </tr>
    <tr>
      <th>2276</th>
      <td>http://www.amazon.com/1Q84-Haruki-Murakami-ebo...</td>
      <td>Haruki Murakami</td>
      <td>Descr: In 1980s Tokyo, a woman who punishes pe...</td>
      <td>Knopf</td>
      <td>1Q84</td>
      <td>5b4aa4ead3089013507dc00b</td>
      <td>2011-12-10 00:00:00</td>
      <td>1324771200000</td>
      <td>13</td>
      <td>11</td>
      <td>7</td>
      <td>30.50</td>
    </tr>
    <tr>
      <th>2287</th>
      <td>http://www.amazon.com/1Q84-Haruki-Murakami-ebo...</td>
      <td>Haruki Murakami</td>
      <td>Descr: In 1980s Tokyo, a woman who punishes pe...</td>
      <td>Knopf</td>
      <td>1Q84</td>
      <td>5b4aa4ead3089013507dc01e</td>
      <td>2011-12-17 00:00:00</td>
      <td>1325376000000</td>
      <td>12</td>
      <td>13</td>
      <td>8</td>
      <td>30.50</td>
    </tr>
    <tr>
      <th>2232</th>
      <td>http://www.amazon.com/1Q84-Haruki-Murakami-ebo...</td>
      <td>Haruki Murakami</td>
      <td>Descr: In 1980s Tokyo, a woman who punishes pe...</td>
      <td>Knopf</td>
      <td>1Q84</td>
      <td>5b4aa4ead3089013507dbfb4</td>
      <td>2011-11-12 00:00:00</td>
      <td>1322352000000</td>
      <td>6</td>
      <td>6</td>
      <td>3</td>
      <td>30.50</td>
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
    </tr>
    <tr>
      <th>2205</th>
      <td>http://www.amazon.com/1225-Christmas-Tree-Lane...</td>
      <td>Debbie Macomber</td>
      <td>Descr: Puppies and an ex-husband loom large in...</td>
      <td>Mira</td>
      <td>1225 CHRISTMAS TREE LANE</td>
      <td>5b4aa4ead3089013507dbf81</td>
      <td>2011-10-22 00:00:00</td>
      <td>1320537600000</td>
      <td>15</td>
      <td>10</td>
      <td>4</td>
      <td>16.95</td>
    </tr>
    <tr>
      <th>237</th>
      <td>http://www.amazon.com/Cedar-Cove-Christmas-Deb...</td>
      <td>Debbie Macomber</td>
      <td>Descr: A pregnant woman shows up in Cedar Cove...</td>
      <td>Mira</td>
      <td>A CEDAR COVE CHRISTMAS</td>
      <td>5b4aa4ead3089013507db30d</td>
      <td>2008-10-04 00:00:00</td>
      <td>1224374400000</td>
      <td>7</td>
      <td>0</td>
      <td>1</td>
      <td>16.95</td>
    </tr>
    <tr>
      <th>1343</th>
      <td>http://www.amazon.com/Blockade-Billy-Stephen-K...</td>
      <td>Stephen King</td>
      <td>Descr: A tale about the dark side of baseball,...</td>
      <td>Scribner</td>
      <td>BLOCKADE BILLY</td>
      <td>5b4aa4ead3089013507db9f6</td>
      <td>2010-06-13 00:00:00</td>
      <td>1277596800000</td>
      <td>16</td>
      <td>13</td>
      <td>3</td>
      <td>14.99</td>
    </tr>
    <tr>
      <th>1310</th>
      <td>http://www.amazon.com/Blockade-Billy-Stephen-K...</td>
      <td>Stephen King</td>
      <td>Descr: A tale about the dark side of baseball,...</td>
      <td>Simon &amp; Schuster</td>
      <td>BLOCKADE BILLY</td>
      <td>5b4aa4ead3089013507db9c7</td>
      <td>2010-05-30 00:00:00</td>
      <td>1276387200000</td>
      <td>9</td>
      <td>0</td>
      <td>1</td>
      <td>14.99</td>
    </tr>
    <tr>
      <th>1328</th>
      <td>http://www.amazon.com/Blockade-Billy-Stephen-K...</td>
      <td>Stephen King</td>
      <td>Descr: A tale about the dark side of baseball,...</td>
      <td>Scribner</td>
      <td>BLOCKADE BILLY</td>
      <td>5b4aa4ead3089013507db9df</td>
      <td>2010-06-06 00:00:00</td>
      <td>1276992000000</td>
      <td>13</td>
      <td>9</td>
      <td>2</td>
      <td>14.99</td>
    </tr>
  </tbody>
</table>
<p>2266 rows × 12 columns</p>
</div>



Si convertimos 'published_date.numberLong' a `datetime`, podemos también ordenar desde la publicación más antigua hasta la publicación más reciente:


```python
df['published_date.numberLong'] = pd.to_datetime(df['published_date.numberLong'], unit='ms')
```


```python
df.sort_values('published_date.numberLong', ascending=True)
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
      <td>2008-06-08</td>
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
      <td>2008-06-08</td>
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
      <td>2008-06-08</td>
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
      <td>2008-06-08</td>
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
      <td>2008-06-08</td>
      <td>7</td>
      <td>4</td>
      <td>3</td>
      <td>26.95</td>
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
    </tr>
    <tr>
      <th>3026</th>
      <td>http://www.amazon.com/Dont-Go-Lisa-Scottoline-...</td>
      <td>Lisa Scottoline</td>
      <td>Descr: An Army doctor returns from Afghanistan...</td>
      <td>St. Martin's</td>
      <td>DON'T GO</td>
      <td>5b4aa4ead3089013507dc591</td>
      <td>2013-04-20 00:00:00</td>
      <td>2013-05-05</td>
      <td>7</td>
      <td>2</td>
      <td>2</td>
      <td>27.99</td>
    </tr>
    <tr>
      <th>3027</th>
      <td>http://www.amazon.com/Unintended-Consequences-...</td>
      <td>Stuart Woods</td>
      <td>Descr: The New York lawyer Stone Barrington di...</td>
      <td>Putnam</td>
      <td>UNINTENDED CONSEQUENCES</td>
      <td>5b4aa4ead3089013507dc592</td>
      <td>2013-04-20 00:00:00</td>
      <td>2013-05-05</td>
      <td>8</td>
      <td>4</td>
      <td>2</td>
      <td>26.95</td>
    </tr>
    <tr>
      <th>3028</th>
      <td>http://www.amazon.com/Six-Years-Harlan-Coben/d...</td>
      <td>Harlan Coben</td>
      <td>Descr: Jake Fisher discovers that neither the ...</td>
      <td>Dutton</td>
      <td>SIX YEARS</td>
      <td>5b4aa4ead3089013507dc593</td>
      <td>2013-04-20 00:00:00</td>
      <td>2013-05-05</td>
      <td>9</td>
      <td>8</td>
      <td>5</td>
      <td>27.95</td>
    </tr>
    <tr>
      <th>3029</th>
      <td>http://www.amazon.com/The-Interestings-Novel-M...</td>
      <td>Meg Wolitzer</td>
      <td>Descr: Six friends meet in the 1970s at a summ...</td>
      <td>Riverhead</td>
      <td>THE INTERESTINGS</td>
      <td>5b4aa4ead3089013507dc595</td>
      <td>2013-04-20 00:00:00</td>
      <td>2013-05-05</td>
      <td>11</td>
      <td>11</td>
      <td>2</td>
      <td>27.95</td>
    </tr>
    <tr>
      <th>3031</th>
      <td>http://www.amazon.com/The-Storyteller-Jodi-Pic...</td>
      <td>Jodi Picoult</td>
      <td>Descr: A New Hampshire baker finds herself in ...</td>
      <td>Emily Bestler/Atria</td>
      <td>THE STORYTELLER</td>
      <td>5b4aa4ead3089013507dc598</td>
      <td>2013-04-20 00:00:00</td>
      <td>2013-05-05</td>
      <td>14</td>
      <td>10</td>
      <td>8</td>
      <td>28.99</td>
    </tr>
  </tbody>
</table>
<p>2266 rows × 12 columns</p>
</div>



Por ejemplo, podríamos primero filtrar para sólo tener los libros de la editorial que tiene más libros como 'best sellers' y después ordenarlos del que pasó más días en la lista de 'best sellers' al que pasó menos días en la lista:


```python
df['publisher'].value_counts()
```




    Putnam                                     267
    Grand Central                              227
    Knopf                                      216
    Little, Brown                              211
    Doubleday                                  153
                                              ... 
    Daw                                          1
    Harper Voyager/HarperCollins Publishers      1
    Morrow/HarperCollins Publishers              1
    Viking,                                      1
    Twelve                                       1
    Name: publisher, Length: 69, dtype: int64




```python
df_putnam = df[df['publisher'] == 'Putnam']
```


```python
df_putnam.sort_values('weeks_on_list.numberInt', ascending=False)
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
      <th>470</th>
      <td>http://www.amazon.com/Scarpetta-Kay-Patricia-C...</td>
      <td>Patricia Cornwell</td>
      <td>Descr: The forensic pathologist Kay Scarpetta ...</td>
      <td>Putnam</td>
      <td>SCARPETTA</td>
      <td>5b4aa4ead3089013507db491</td>
      <td>2009-02-14 00:00:00</td>
      <td>2009-03-01</td>
      <td>15</td>
      <td>14</td>
      <td>11</td>
      <td>27.95</td>
    </tr>
    <tr>
      <th>455</th>
      <td>http://www.amazon.com/Scarpetta-Kay-Patricia-C...</td>
      <td>Patricia Cornwell</td>
      <td>Descr: The forensic pathologist Kay Scarpetta ...</td>
      <td>Putnam</td>
      <td>SCARPETTA</td>
      <td>5b4aa4ead3089013507db47c</td>
      <td>2009-02-07 00:00:00</td>
      <td>2009-02-22</td>
      <td>14</td>
      <td>12</td>
      <td>10</td>
      <td>27.95</td>
    </tr>
    <tr>
      <th>438</th>
      <td>http://www.amazon.com/Scarpetta-Kay-Patricia-C...</td>
      <td>Patricia Cornwell</td>
      <td>Descr: The forensic pathologist Kay Scarpetta ...</td>
      <td>Putnam</td>
      <td>SCARPETTA</td>
      <td>5b4aa4ead3089013507db466</td>
      <td>2009-01-31 00:00:00</td>
      <td>2009-02-15</td>
      <td>12</td>
      <td>6</td>
      <td>9</td>
      <td>27.95</td>
    </tr>
    <tr>
      <th>421</th>
      <td>http://www.amazon.com/Scarpetta-Kay-Patricia-C...</td>
      <td>Patricia Cornwell</td>
      <td>Descr: The forensic pathologist Kay Scarpetta ...</td>
      <td>Putnam</td>
      <td>SCARPETTA</td>
      <td>5b4aa4ead3089013507db44c</td>
      <td>2009-01-24 00:00:00</td>
      <td>2009-02-08</td>
      <td>6</td>
      <td>6</td>
      <td>8</td>
      <td>27.95</td>
    </tr>
    <tr>
      <th>1072</th>
      <td>http://www.amazon.com/U-Undertow-Kinsey-Millho...</td>
      <td>Sue Grafton</td>
      <td>Descr: Kinsey Millhone investigates the case o...</td>
      <td>Putnam</td>
      <td>U IS FOR UNDERTOW</td>
      <td>5b4aa4ead3089013507db84e</td>
      <td>2010-01-17 00:00:00</td>
      <td>2010-01-31</td>
      <td>12</td>
      <td>11</td>
      <td>7</td>
      <td>27.95</td>
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
    </tr>
    <tr>
      <th>925</th>
      <td>http://www.amazon.com/The-Scarpetta-Factor-Nov...</td>
      <td>Patricia Cornwell</td>
      <td>Descr: Apparent threats on Kay Scarpetta’s  li...</td>
      <td>Putnam</td>
      <td>THE SCARPETTA FACTOR</td>
      <td>5b4aa4ead3089013507db754</td>
      <td>2009-10-24 00:00:00</td>
      <td>2009-11-08</td>
      <td>2</td>
      <td>0</td>
      <td>1</td>
      <td>27.95</td>
    </tr>
    <tr>
      <th>2150</th>
      <td>http://www.amazon.com/Son-Stone-Barrington-Nov...</td>
      <td>Stuart Woods</td>
      <td>Descr: The New York lawyer Stone Barrington ge...</td>
      <td>Putnam</td>
      <td>SON OF STONE</td>
      <td>5b4aa4ead3089013507dbf27</td>
      <td>2011-09-24 00:00:00</td>
      <td>2011-10-09</td>
      <td>5</td>
      <td>0</td>
      <td>1</td>
      <td>26.95</td>
    </tr>
    <tr>
      <th>2137</th>
      <td>http://www.amazon.com/Killing-Blues-Jesse-Ston...</td>
      <td>Michael Brandman</td>
      <td>Descr: Jesse Stone, the chief of police in Par...</td>
      <td>Putnam</td>
      <td>ROBERT B. PARKER’S KILLING THE BLUES</td>
      <td>5b4aa4ead3089013507dbf13</td>
      <td>2011-09-17 00:00:00</td>
      <td>2011-10-02</td>
      <td>5</td>
      <td>0</td>
      <td>1</td>
      <td>25.95</td>
    </tr>
    <tr>
      <th>993</th>
      <td>http://www.amazon.com/U-Undertow-Kinsey-Millho...</td>
      <td>Sue Grafton</td>
      <td>Descr: Kinsey Millhone investigates the case o...</td>
      <td>Putnam</td>
      <td>U IS FOR UNDERTOW</td>
      <td>5b4aa4ead3089013507db7cb</td>
      <td>2009-12-05 00:00:00</td>
      <td>2009-12-20</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>27.95</td>
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
      <td>2008-06-08</td>
      <td>4</td>
      <td>0</td>
      <td>1</td>
      <td>22.95</td>
    </tr>
  </tbody>
</table>
<p>267 rows × 12 columns</p>
</div>


