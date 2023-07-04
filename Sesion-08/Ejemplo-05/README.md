# Ejemplo 5: Lectura de archivos `.xls`

## Objetivos

- Mostrar la lectura de archivos .xls de forma simple.

## Desarrollo

Los archivos de Excel son una de las formas más comunes (tristemente) de almacenar datos. Afortunadamente el método de Pandas `read_excel()` nos permite leer fácilmente este tipo de archivos.

Por ejemplo, se tiene el siguiente archivo [equipos.xlsx](../../Datasets/equipos.xlsx) (Nota: `xlsx` es el formato de las hojas de cálculo de Microsoft).

El siguiente código muestra cómo usar el método `read_excel` para importar este archivo de Excel a un DataFrame de Pandas. Para ejecutar estos códigos debes instalar previamente `openpyxl`.


```python
!pip install openpyxl
```

```python
import pandas as pd
df = pd.read_excel('../../Datasets/equipos.xlsx')
df
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>equipo</th>
      <th>puntos</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>A</td>
      <td>26</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>B</td>
      <td>19</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>C</td>
      <td>24</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>D</td>
      <td>22</td>
    </tr>
  </tbody>
</table>
</div>



Como hemos visto en otras sesiones, a veces quisiéramos que una de las columnas de nuestro archivo funcione como índice, para ello podemos simplemente añadimos la opción `index_col` indicando la columna que queremos que funcione como índice.


```python
df = pd.read_excel('../../Datasets/equipos.xlsx', index_col='id')
df
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>equipo</th>
      <th>puntos</th>
    </tr>
    <tr>
      <th>id</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>A</td>
      <td>26</td>
    </tr>
    <tr>
      <th>2</th>
      <td>B</td>
      <td>19</td>
    </tr>
    <tr>
      <th>3</th>
      <td>C</td>
      <td>24</td>
    </tr>
    <tr>
      <th>4</th>
      <td>D</td>
      <td>22</td>
    </tr>
  </tbody>
</table>
</div>



El archivo `equipos` tiene dos hojas, si queremos acceder a la segunda, basta con usar la opción `sheet_name`).


```python
df = pd.read_excel('../../Datasets/equipos.xlsx', sheet_name='Hoja 2', index_col='id')
df
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>equipo</th>
      <th>puntos</th>
    </tr>
    <tr>
      <th>id</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>5</th>
      <td>E</td>
      <td>1</td>
    </tr>
    <tr>
      <th>6</th>
      <td>F</td>
      <td>7</td>
    </tr>
    <tr>
      <th>7</th>
      <td>G</td>
      <td>2</td>
    </tr>
    <tr>
      <th>8</th>
      <td>H</td>
      <td>9</td>
    </tr>
  </tbody>
</table>
</div>


