## Reto 3: Map

### 1. Objetivos:
    - Practicar el uso del método `map` para mapear un dato a otro dato que le corresponde.
    
---
    
### 2. Desarrollo:

#### a) Booleanos a numéricos

Vamos a trabajar sobre el dataset que guardaste en el Reto anterior. Esta vez tu Reto es muy sencillo:

1. La columna `is_potentially_hazardous_asteroid` tiene valores `booleanos`. Crea un diccionario de mapeo donde hagas un correspondencia de cada valor `booleano` con su equivalente numérico y transforma esa columna.
2. Usa una función para mapear la columna `relative_velocity.kilometers_per_hour` a una nueva columna llamada `relative_velocity.kilometers_per_minute`, que contenga la velocidad del objeto en kilómetros por minuto.
3. Guarda tu `DataFrame` resultante en la variable `df_reto_3`.
4. Guarda tu resultado en un archivo .csv.


```python
df_reto_3 =
```


```python
def revisar_resultados(df_reto_3):
    
    import pandas as np
    import pandas.api.types as pdtypes
    
    assert pdtypes.is_int64_dtype(df_reto_3['is_potentially_hazardous_asteroid']), 'La columna "is_potentially_hazardous_asteroid" no ha sido transformada a tipo numerico'
    assert len(df_reto_3['is_potentially_hazardous_asteroid'].unique()) == 2, 'Hubo un error con la correspondencia de valores booleanos a numéricos. Hay más de dos valores posibles en la columna resultante'
    assert df_reto_3['relative_velocity.kilometers_per_minute'].equals(df_reto_3['relative_velocity.kilometers_per_hour'] / 60), 'La conversión de kilometros por hora a kilómetros por minuto no fue realizada correctamente'
    
    print(f'Todos los procesos fueron realizados exitosamente!')

revisar_resultados(df_reto_3)
```
