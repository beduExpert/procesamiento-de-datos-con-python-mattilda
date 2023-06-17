## Reto 4: Identificando y limpiando NaNs

### 1. Objetivos:
    - Practicar la identificación de NaNs
    - Practicar eliminar NaNs de un `DataFrame` usando diferentes técnicas
 
---
    
### 2. Desarrollo:

#### a) Limpiando un Dataset de NaNs

Eres el Data Wrangler de EyePoker Inc. Te han dado el siguiente dataset para que apliques algunas técnicas de procesamiento de datos:


```python
import pandas as pd
import numpy as np

pd.options.mode.chained_assignment = None 
```


```python
datos = {
    'precio': [12000, 5500, np.nan, 4800, 8900, np.nan, 1280, 1040, 23100, np.nan, 15000, 13400, np.nan],
    'cantidad_en_stock': [34, 54, np.nan, 78, 56, np.nan, 34, 4, 0, 18, 45, 23, 5],
    'cantidad_vendidos': [120, 34, np.nan, 9, 15, np.nan, 103, np.nan, np.nan, 23, 10, 62, 59],
    'descuentos': [np.nan] * 13
}

df = pd.DataFrame(datos, index=["Pokemaster", "Cegatron", "Pikame Mucho", "Lazarillo de Tormes", "Stevie Wonder", "Needle", "El AyMeDuele", "El Desretinador", "Sacamel Ojocles", "Desojado", "Maribel Buenas Noches", "Cíclope", "El Cuatro Ojos"])
```


```python
df
```

Para poder realizar los análisis y visualizaciones posteriores, te han pedido que elimines los `NaNs` del dataset. Realiza los siguientes pasos para limpiar tu dataset:

1. Has un conteo de cuántos `NaNs` hay en cada fila y en cada columna
2. Elimina las filas y columnas donde **todos** los valores sean `NaN`.
3. Dado que la columna `cantidad_vendidos` no es tan importante, cambia los `NaNs` que haya en esa columna por `0`.
4. Dado que la columna `precio` es muy importante, elimina las filas restantes que tengan algún `NaN` en dicha columna.

Realiza todas tus transformaciones usando el `DataFrame` `df_copy`.


```python
df_copy = df.copy()

## Realiza aquí tus transformaciones
##
## ...
## ...
```


```python
def revisar_limpieza(df, df_copy):
    df_2 = df.copy()
    df_2 = df_2.dropna(axis=0, how='all')
    df_2 = df_2.dropna(axis=1, how='all')
    df_2['cantidad_vendidos'] = df_2['cantidad_vendidos'].fillna(0)
    df_2 = df_2.dropna(axis=0)
    
    if not df_2.equals(df_copy):
        print(f'La transformación no fue realizada adecuadamente... Por favor revisa tu procedimiento.\n')
        print(f'DataFrame esperado:\n')
        print(df_2)
        
        print(f'\nDataframe obtenido:\n')
        print(df_copy)
    else:
        print(f'La transformación fue realizada exitosamente... Muchas gracias!')

revisar_limpieza(df, df_copy)
```


```python

```
