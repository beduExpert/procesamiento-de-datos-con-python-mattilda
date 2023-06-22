## Reto 1: Casting

### 1. Objetivos:
    - Aplicar diversas técnicas de casting a un dataset nuevo
 
---
    
### 2. Desarrollo:

#### a) Transformando tipos de datos

Vamos a trabajar con una versión un poco modificada del dataset que creaste en la sesión pasada. Si bien recuerdas, al final de la sesión pasada automatizamos un programa de Python para obtener un `DataFrame` con todos los objetos que orbitaron cerca de la Tierra en Enero y Febrero de 1995. Para construir este dataset, usamos el API gratuito que ofrece la [NASA](https://api.nasa.gov/).

Me tomé la libertad de modificar un poco dicho dataset para que pudiera ser utilizado más efectivamente para los fines de esta sesión. Encontrarás la versión modificada en la ruta '../../Datasets/near_earth_objects-jan_feb_1995-dirty.csv'. Todos los Retos de esta sesión los harás con ese conjunto de datos.

Te recomiendo que al finalizar cada reto guardes la nueva versión modificada de tu dataset bajo un nombre que indique el reto realizado (por ejemplo, 'near_earth_objects-jan_feb_1995-reto_1.csv'), para que puedas ir trabajando incrementalmente a través de los retos y no tengas que repetir procesos. Puedes guardar conjuntos de datos en formato `csv` usando el método `DataFrame.to_csv('ruta')`.

Tu primer Reto consistirá en seguir los siguientes pasos:

1. Lee el dataset y crea un `DataFrame` con él.
2. Realiza una pequeña exploración para familiarizarte con él.
3. Convierte la columna `relative_velocity.kilometers_per_hour` de `object` a `float64`.
4. Convierte la columna `close_approach_date` a tipo de dato `datetime64[ms]` usando el método `astype` y un diccionario de conversión.
5. Convierte la columna `epoch_date_close_approach` a tipo de dato `datetime64[ms]` usando el método `to_datetime`.
6. Asigna el `DataFrame` resultante a la variable `df_reto_1`.
7. Guarda tu resultado en un archivo .csv.


```python
df_reto_1 =
```

Pídele a tu experta la función de verificación `checar_conversiones` (encontrada en el archivo `helpers.py` de la carpeta donde se encuentra este Reto), pégala debajo y corre la celda para verificar tu resultado:


```python
def checar_conversiones(df_reto_1):
    
    import pandas as pd
    import pandas.api.types as ptypes
    
    assert ptypes.is_float_dtype(df_reto_1['relative_velocity.kilometers_per_hour']), 'Cuidado... La columna `relative_velocity.kilometers_per_hour` no es de tipo `float64`'
    assert ptypes.is_datetime64_any_dtype(df_reto_1['close_approach_date']), 'Cuidado... La columna `close_approach_date` no es de tipo `datetime64[ns]`'
    assert ptypes.is_datetime64_any_dtype(df_reto_1['epoch_date_close_approach']), 'Cuidado... La columna `epoch_date_close_approach` no es de tipo `datetime64[ns]'
    
    print(f'¡Éxito! ¡Todas tus conversiones fueron realizadas adecuadamente!')
    
checar_conversiones(df_reto_1)
```

```python

```
