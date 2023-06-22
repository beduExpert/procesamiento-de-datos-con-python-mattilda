## Reto 4: Apply

### 1. Objetivos:
    - Practicar el uso del método `apply` para obtener columnas nuevas a partir de columnas existentes
    
---
    
### 2. Desarrollo:

#### a) Obteniendo columnas nuevas a partir de existentes

Vamos a trabajar con el dataset que guardaste de tu Reto anterior. Esta vez tu Reto es el siguiente:

1. Crea una función que reciba un valor (en este caso el diámetro en metros de un objeto espacial) y regrese la proporción de ese valor en comparación con el diámetro de la Tierra. El diámetro de la Tierra es de 12,742 km. Así que el diámetro de un objeto que mida 10000 metros corresponde a un valor de 0.00078 en proporción al diámetro de la Tierra.
2. Usa la columna 'estimated_diameter.meters.estimated_diameter_max', aplícale la función usando `apply` y crea una nueva columna llamada `proportion_of_max_diameter_to_earth`.
3. Asigna el resultado a la variable `df_reto_4`.
4. Guarda tu conjunto de datos en un archivo .csv.


```python
df_reto_4 =
```

Pídele a tu experta la función de verificación `revisar_aplicacion` (encontrada en el archivo `helpers.py` de la carpeta donde se encuentra este Reto), pégala debajo y corre la celda para verificar tu resultado:


```python
def revisar_aplicacion(df_reto_4):
    
    assert 'proportion_of_max_diameter_to_earth' in df_reto_4, 'No existe una columna llamada "proportion_of_max_diameter_to_earth" en el DataFrame'
    assert df_reto_4['proportion_of_max_diameter_to_earth'].equals(df_reto_4['estimated_diameter.meters.estimated_diameter_max'] / 12742000), 'La transformacion no fue realizada adecuadamente'
    
    print(f'La transformación y creación de una nueva columna fue realizada exitosamente!')
    
revisar_aplicacion(df_reto_4)
```
