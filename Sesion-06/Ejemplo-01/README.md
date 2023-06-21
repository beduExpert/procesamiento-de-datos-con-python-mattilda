## Ejemplo 1: Usando la biblioteca Request

### 1. Objetivos:
    - Aprender a usar la biblioteca Request para hacer peticiones HTTP
 
---
    
### 2. Desarrollo:


```python
import requests
import pandas as pd
```

Vamos a hacer peticiones a una api de la NASA que ofrece datos sobre objetos que orbitan cerca de la Tierra. Pueden ver la documentación [aquí](https://api.nasa.gov/). Ahí podemos ver los endpoints y la manera en la que se usa la Api Key. Ve a la página y consigue tu propia Api Key para que puedas realizar los ejercicios.

Ahora, para empezar, necesitamos nuestro endpoint y nuestro diccionario de parámetros.


```python
endpoint = 'https://api.nasa.gov/neo/rest/v1/neo/browse/'
payload = {'api_key': 'tu_api_key_va_aqui'}
```

Ambos se los pasamos al método `GET` de requests para realizar la petición a ese endpoint y enviar los parámetros como información extra que el API necesita para validar nuestra petición:


```python
r = requests.get(endpoint, params=payload)
```

Ahora, podemos leer lo siguiente de nuestro objeto de respuesta:


```python
r.status_code
```




    200



r.json()

¡Esa es una respuesta muy larga! Vamos a diseccionarla:


```python
json = r.json()
```


```python
json.keys()
```




    dict_keys(['links', 'page', 'near_earth_objects'])




```python
json['links']
```




    {'next': 'http://www.neowsapp.com/rest/v1/neo/browse?page=1&size=20&api_key=KidBlDQkkXeu9dFpdV5GSVDrTH2H640zggDaZJ1a',
     'self': 'http://www.neowsapp.com/rest/v1/neo/browse?page=0&size=20&api_key=KidBlDQkkXeu9dFpdV5GSVDrTH2H640zggDaZJ1a'}




```python
json['page']
```




    {'size': 20, 'total_elements': 23798, 'total_pages': 1190, 'number': 0}




```python
data = json['near_earth_objects']
```


```python
data[0]
```




    {'links': {'self': 'http://www.neowsapp.com/rest/v1/neo/2021277?api_key=KidBlDQkkXeu9dFpdV5GSVDrTH2H640zggDaZJ1a'},
     'id': '2021277',
     'neo_reference_id': '2021277',
     'name': '21277 (1996 TO5)',
     'designation': '21277',
     'nasa_jpl_url': 'http://ssd.jpl.nasa.gov/sbdb.cgi?sstr=2021277',
     'absolute_magnitude_h': 16.1,
     'estimated_diameter': {'kilometers': {'estimated_diameter_min': 1.6016033798,
       'estimated_diameter_max': 3.5812940302},
      'meters': {'estimated_diameter_min': 1601.6033797856,
       'estimated_diameter_max': 3581.2940301941},
      'miles': {'estimated_diameter_min': 0.9951898937,
       'estimated_diameter_max': 2.2253122528},
      'feet': {'estimated_diameter_min': 5254.6044325359,
       'estimated_diameter_max': 11749.652706022}},
     'is_potentially_hazardous_asteroid': False,
     'close_approach_data': [{'close_approach_date': '1945-06-07',
       'close_approach_date_full': '1945-Jun-07 22:35',
       'epoch_date_close_approach': -775272300000,
       'relative_velocity': {'kilometers_per_second': '15.5094751879',
        'kilometers_per_hour': '55834.1106763388',
        'miles_per_hour': '34693.1450477507'},
       'miss_distance': {'astronomical': '0.0334232973',
        'lunar': '13.0016626497',
        'kilometers': '5000054.084456751',
        'miles': '3106889.5396991238'},
       'orbiting_body': 'Mars'}],
     'orbital_data': {'orbit_id': '164',
      'orbit_determination_date': '2020-04-29 06:55:15',
      'first_observation_date': '1990-02-04',
      'last_observation_date': '2020-04-28',
      'data_arc_in_days': 11041,
      'observations_used': 656,
      'orbit_uncertainty': '0',
      'minimum_orbit_intersection': '.313031',
      'jupiter_tisserand_invariant': '3.267',
      'epoch_osculation': '2459000.5',
      'eccentricity': '.5205881322259853',
      'semi_major_axis': '2.37660147442171',
      'inclination': '20.95226489770891',
      'ascending_node_longitude': '167.3841292218327',
      'orbital_period': '1338.23680580907',
      'perihelion_distance': '1.139370951806989',
      'perihelion_argument': '250.1729646080978',
      'aphelion_distance': '3.613831997036431',
      'perihelion_time': '2458492.539296262276',
      'mean_anomaly': '136.646856932786',
      'mean_motion': '.2690106851323308',
      'equinox': 'J2000',
      'orbit_class': {'orbit_class_type': 'AMO',
       'orbit_class_range': '1.017 AU < q (perihelion) < 1.3 AU',
       'orbit_class_description': 'Near-Earth asteroid orbits similar to that of 1221 Amor'}},
     'is_sentry_object': False}



`links` y `page` son metadata que vamos a utilizar luego para automatizar el proceso de peticiones. `data` es una lista de diccionarios que contiene los datos que queremos utilizar. Vamos a convertirlos en un `DataFrame`:


```python
normalized = pd.json_normalize(data)

df = pd.DataFrame.from_dict(normalized)

df.head()
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>neo_reference_id</th>
      <th>name</th>
      <th>designation</th>
      <th>nasa_jpl_url</th>
      <th>absolute_magnitude_h</th>
      <th>is_potentially_hazardous_asteroid</th>
      <th>close_approach_data</th>
      <th>is_sentry_object</th>
      <th>links.self</th>
      <th>...</th>
      <th>orbital_data.perihelion_argument</th>
      <th>orbital_data.aphelion_distance</th>
      <th>orbital_data.perihelion_time</th>
      <th>orbital_data.mean_anomaly</th>
      <th>orbital_data.mean_motion</th>
      <th>orbital_data.equinox</th>
      <th>orbital_data.orbit_class.orbit_class_type</th>
      <th>orbital_data.orbit_class.orbit_class_range</th>
      <th>orbital_data.orbit_class.orbit_class_description</th>
      <th>name_limited</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2021277</td>
      <td>2021277</td>
      <td>21277 (1996 TO5)</td>
      <td>21277</td>
      <td>http://ssd.jpl.nasa.gov/sbdb.cgi?sstr=2021277</td>
      <td>16.1</td>
      <td>False</td>
      <td>[{'close_approach_date': '1945-06-07', 'close_...</td>
      <td>False</td>
      <td>http://www.neowsapp.com/rest/v1/neo/2021277?ap...</td>
      <td>...</td>
      <td>250.1729646080978</td>
      <td>3.613831997036431</td>
      <td>2458492.539296262276</td>
      <td>136.646856932786</td>
      <td>.2690106851323308</td>
      <td>J2000</td>
      <td>AMO</td>
      <td>1.017 AU &lt; q (perihelion) &lt; 1.3 AU</td>
      <td>Near-Earth asteroid orbits similar to that of ...</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2162038</td>
      <td>2162038</td>
      <td>162038 (1996 DH)</td>
      <td>162038</td>
      <td>http://ssd.jpl.nasa.gov/sbdb.cgi?sstr=2162038</td>
      <td>16.6</td>
      <td>False</td>
      <td>[]</td>
      <td>False</td>
      <td>http://www.neowsapp.com/rest/v1/neo/2162038?ap...</td>
      <td>...</td>
      <td>351.5495073253862</td>
      <td>2.025868476312066</td>
      <td>2459176.565253751041</td>
      <td>273.1861379061811</td>
      <td>.493077766590875</td>
      <td>J2000</td>
      <td>AMO</td>
      <td>1.017 AU &lt; q (perihelion) &lt; 1.3 AU</td>
      <td>Near-Earth asteroid orbits similar to that of ...</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2189058</td>
      <td>2189058</td>
      <td>189058 (2000 UT16)</td>
      <td>189058</td>
      <td>http://ssd.jpl.nasa.gov/sbdb.cgi?sstr=2189058</td>
      <td>16.5</td>
      <td>False</td>
      <td>[]</td>
      <td>False</td>
      <td>http://www.neowsapp.com/rest/v1/neo/2189058?ap...</td>
      <td>...</td>
      <td>91.24858681610077</td>
      <td>3.884205451986184</td>
      <td>2459278.734090121480</td>
      <td>293.4095292372738</td>
      <td>.2393325373380815</td>
      <td>J2000</td>
      <td>AMO</td>
      <td>1.017 AU &lt; q (perihelion) &lt; 1.3 AU</td>
      <td>Near-Earth asteroid orbits similar to that of ...</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2276274</td>
      <td>2276274</td>
      <td>276274 (2002 SS41)</td>
      <td>276274</td>
      <td>http://ssd.jpl.nasa.gov/sbdb.cgi?sstr=2276274</td>
      <td>17.2</td>
      <td>False</td>
      <td>[]</td>
      <td>False</td>
      <td>http://www.neowsapp.com/rest/v1/neo/2276274?ap...</td>
      <td>...</td>
      <td>101.7860072730271</td>
      <td>2.910206355077709</td>
      <td>2459093.016756074428</td>
      <td>330.1368350661496</td>
      <td>.322786554576405</td>
      <td>J2000</td>
      <td>AMO</td>
      <td>1.017 AU &lt; q (perihelion) &lt; 1.3 AU</td>
      <td>Near-Earth asteroid orbits similar to that of ...</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2322913</td>
      <td>2322913</td>
      <td>322913 (2002 CM1)</td>
      <td>322913</td>
      <td>http://ssd.jpl.nasa.gov/sbdb.cgi?sstr=2322913</td>
      <td>16.7</td>
      <td>False</td>
      <td>[]</td>
      <td>False</td>
      <td>http://www.neowsapp.com/rest/v1/neo/2322913?ap...</td>
      <td>...</td>
      <td>84.19797366483287</td>
      <td>3.361558630853122</td>
      <td>2458482.209254870466</td>
      <td>146.5048635106909</td>
      <td>.2826692640905165</td>
      <td>J2000</td>
      <td>AMO</td>
      <td>1.017 AU &lt; q (perihelion) &lt; 1.3 AU</td>
      <td>Near-Earth asteroid orbits similar to that of ...</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 44 columns</p>
</div>



¡Listo! Ahora tenemos un `DataFrame` con los datos de nuestra primera petición. En esta sesión vamos a aprender a automatizar este proceso. Pero antes, practiquemos un poco el uso de la biblioteca `requests`.


```python

```
