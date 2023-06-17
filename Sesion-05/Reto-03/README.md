## Reto 3: Agregaciones con `DataFrames`

### 1. Objetivos:
    - Aplicar agregaciones a `DataFrames` completos para obtener un análisis estadístico
 
---
    
### 2. Desarrollo:

#### a) Análisis estadístico con agregaciones

Eres el Analista de Datos de EyePoker Inc. Te han pedido que realices ciertas agregaciones con un conjunto de datos para poder realizar un análisis estadístico básico de los datos que hay dentro.

El conjunto de datos es el siguiente:


```python
## Realiza aquí los imports que necesites
```


```python
datos = {
    'producto': ["Pokemaster", "Cegatron", "Pikame Mucho", "Lazarillo de Tormes", "Stevie Wonder", "Needle", "El AyMeDuele", "El Desretinador", "Sacamel Ojocles", "Desojado", "Maribel Buenas Noches", "Cíclope", "El Cuatro Ojos"],
    'precio': [12000, 5500, 2350, 4800, 8900, 6640, 1280, 1040, 23100, 16700, 15000, 13400, 19600],
    'cantidad_en_stock': [34, 54, 36, 78, 56, 12, 34, 4, 0, 18, 45, 23, 5],
    'cantidad_vendidos': [120, 34, 59, 9, 15, 51, 103, 72, 39, 23, 10, 62, 59]
}

df = pd.DataFrame(datos)
```


```python
df
```

Tu tarea es muy simple. Usando métodos de agregación, asigna las variables de la siguiente celda con los resultados de agregar nuestro `DataFrame` **por columna** usando cada una de las medidas estadísticas. Algunas de los métodos ya los conoces. Los que no, [puedes encontrarlos en este link](https://www.interactivechaos.com/manual/tutorial-de-pandas/dataframes-metodos-de-agregacion-y-estadistica). Lo que queremos obtener es una `Serie` con los nombres de las columnas como índice y las agregaciones por columna como valores. Una de las columnas que tenemos en el `DataFrame` no se presta para realizar análisis numéricos, elimínala antes de realizar tu análisis y asigna el resultado a la variable `df_droppped`.

**Sólo** utiliza funciones de agregación para tu análisis. En este caso no requieres hacer ninguna operación aritmética.


```python
df_dropped =

# El valor mínimo de cada columna
mins =

# El valor máximo de cada columna
maxs =

# El promedio por columna
means =

# La mediana por columna (El valor que se encuentra a la mitad de la secuencia ordenada de valores)
medians =

# La desviación estándar por columna
stds =
```


```python
def resumen_estadistico(df, df_dropped, mins, maxs, means, medians, stds):
    
    import pandas as pd
    
    error = False
    
    df_dropped_2 = df.drop(columns=['producto'])
    if not df_dropped_2.equals(df_dropped):
        print(f'La columna no-numérica no fue eliminada correctamente... Por favor inténtalo de nuevo')
        error = True
        
    if not df_dropped.min(axis=0).equals(mins):
        print(f'El valor mínimo no fue computado adecuadamente... Por favor inténtalo de nuevo')
        error = True
        
    if not df_dropped.max(axis=0).equals(maxs):
        print(f'El valor máximo no fue computado adecuadamente... Por favor inténtalo de nuevo')
        error = True
        
    if not df_dropped.mean(axis=0).equals(means):
        print(f'El promedio no fue computado adecuadamente... Por favor inténtalo de nuevo')
        error = True
    
    if not df_dropped.median(axis=0).equals(medians):
        print(f'La mediana no fue computada adecuadamente... Por favor inténtalo de nuevo')
        error = True
        
    if not df_dropped.std(axis=0).equals(stds):
        print(f'La desviación estándar no fue computada adecuadamente... Por favor inténtalo de nuevo')
        error = True
    
    if not error:
        rango = maxs - mins
        mins.name = 'Min'
        maxs.name = 'Max'
        rango.name = 'Rango'
        means.name = 'Promedio'
        medians.name = 'Mediana'
        stds.name = 'Std'
        
        resumen = pd.concat([mins, maxs, rango, means, medians, stds], axis=1)
        print(resumen)

resumen_estadistico(df, df_dropped, mins, maxs, means, medians, stds)
```


```python

```
