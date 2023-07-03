## Reto 2: Convertir tablas en MySQL a `DataFrames` de `pandas`

### 1. Objetivos:
    - Solicitar todos los datos de las tablas que están almacenadas en nuestra base de datos, convertirlos a `DataFrames` y guardarlos.
    
---
    
### 2. Desarrollo:

#### a) Tablas a `DataFrames`

Ya que tenemos nuestra conexión funcionando adecuadamente, vamos a utilizarla para realizar consultas a las base de datos y construir una base de datos local. Tu Reto consiste en los siguientes pasos:

1. Vuelve a establecer la conexión a la base de datos
2. Usando el comando `SELECT * FROM nombre_de_tabla`, realiza consultas a cada una de las 5 tablas que existen en la base de datos.
3. Crea un `DataFrame` por cada tabla que obtuviste. Para asignarle los nombres de las columnas correctamente, revisa el archivo [Readme.md](../../Datasets/MovieLens/Readme.md) donde está contenida toda esa información.
4. Asegúrate de que el índice sea adecuado en cada `DataFrame`. En los casos en los que haya datos redundantes, convierte una de las columnas en índice.
5. Si lo deseas ordena las columnas de la manera en la que mejor te parezca.
6. Guarda tus `DataFrames` en formato .csv para utilizarlos en los siguientes Retos.

> **NOTA IMPORTANTE**: La tabla movies es un poco complicada porque contiene muchos signos distintos. Tanto en la columna de nombre de película como la de género, encontramos signos como `,`, `:`, `.`, `|`. Esto hace un poco complicado el almacenamiento y lectura de este archivo. Si elijes guardar este archivo como un .csv separado por comas (`,`), a la hora de leerlo de regreso, `pandas` puede confundirse y pensar que el título de una película que contiene comas constituye dos columnas. Por esta razón, te recomiendo que la tabla `movies` la guardes agregando un separador poco convencional como `sep='$'`. De esta manera será muchísimo más fácil leer tu archivo de regreso usando ese separador.


```python
# Tu código va a aquí
#
# ...
# ...
```

Compara con tus compañeros y revisa con la experta para que todos estén seguros de que tienen sus `DataFrames` estructurados de la manera correcta y que sus archivos .csv fueron creados exitosamente. Vamos a utilizar estos archivos en los Retos siguientes, así que es muy importante que tus datos estén estructurados adecuadamente.


```python

```
