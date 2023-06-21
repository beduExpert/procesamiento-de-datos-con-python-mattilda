## Reto 5: Automatizando peticiones

### 1. Objetivos:
    - Automatizar la petición de datos a la API de la NASA por fechas.
 
---
    
### 2. Desarrollo:

### a) Automatizando peticiones

En el primer Reto realizaste una petición a la API de la NASA para pedir 5 datos de la hoja #100. Ahora, vamos a automatizar el proceso de realizar peticiones a la API para obtener una cantidad bastante mayor de datos.

Vamos a obtener ahora los datos por fechas, así que tendrás que ir a la página de la [api de la NASA](https://api.nasa.gov/), para revisar cómo es posible realizar peticiones por fecha. Queremos obtener los **dos primeros meses (Enero y Febrero) del año 1995**. Observa que la API sólo permite peticiones por fecha en rangos de 7 días.

Tu reto tiene los siguientes pasos:

1. Revisa la documentación de la API de la NASA para entender cómo realizar peticiones por fecha.
2. Realiza una primera petición de prueba para entender el formato de los datos que obtienes de regreso (cómo extraemos los datos que necesitamos y qué estructura tienen).
2. Escribe el código necesario para automatizar las peticiones a la API y obtener los meses de Enero y Febrero del año 1995.
3. Almacena los datos de cada petición y luego usa esos datos para crear `DataFrames`.
4. Concatena verticalmente tus `DataFrames` para obtener un `DataFrame` final que contenga todos los datos de tus peticiones. Cada fila tiene que corresponder a un objeto espacial.
5. Guarda tu `DataFrame` con el nombre de `near_earth_objects-january_february_1995-raw.csv`.

> **Nota**: En este momento no te preocupes por explorar o limpiar tu dataset. Eso lo haremos en la siguiente sesión. Lo que sí tienes que asegurarte es de normalizar tus datos antes de convertirlos en `DataFrame`.

¡Mucha suerte!


```python

```
