## Ejemplo 6: Automatizando peticiones

### 1. Objetivos:
    - Usar todo lo que aprendimos para automatizar peticiones al API
    - Guardar nuestros resultados en un archivo tipo .csv
 
---
    
### 2. Desarrollo:

Veamos cómo usar todo lo que aprendimos para automatizar el proceso de realizar múltiples peticiones a la API, reunirlas en un `DataFrame` y guardarlo en un .csv:


```python
import pandas as pd
import requests
import time
```


```python
endpoint = 'https://api.nasa.gov/neo/rest/v1/neo/browse/'
payload = {'api_key': 'tu_api_key_va_aqui'}
```


```python
dict_datos = {}

for i in range(0, 10):
    
    try:
        time.sleep(5)
        r = requests.get(endpoint, params=payload, timeout=5)

        if r.status_code == 200:
            json = r.json()

            data = json['near_earth_objects']
            dict_datos[i] = data

            new_link = json['links']['next']
            endpoint = new_link
    except:
        continue
```


```python
for key in dict_datos:
    normalized = pd.json_normalize(dict_datos[key])
    df = pd.DataFrame.from_dict(normalized)
    dict_datos[key] = df
```


```python
lista_de_dataframes = []

for key in dict_datos:
    lista_de_dataframes.append(dict_datos[key])
```


```python
df_completo = pd.concat(lista_de_dataframes, axis=0).reset_index(drop=True)
```


```python
df_completo
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
      <th>orbital_data.aphelion_distance</th>
      <th>orbital_data.perihelion_time</th>
      <th>orbital_data.mean_anomaly</th>
      <th>orbital_data.mean_motion</th>
      <th>orbital_data.equinox</th>
      <th>orbital_data.orbit_class.orbit_class_type</th>
      <th>orbital_data.orbit_class.orbit_class_description</th>
      <th>orbital_data.orbit_class.orbit_class_range</th>
      <th>name_limited</th>
      <th>orbital_data.orbit_class</th>
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
      <td>3.613831997036431</td>
      <td>2458492.539296262276</td>
      <td>136.646856932786</td>
      <td>.2690106851323308</td>
      <td>J2000</td>
      <td>AMO</td>
      <td>Near-Earth asteroid orbits similar to that of ...</td>
      <td>1.017 AU &lt; q (perihelion) &lt; 1.3 AU</td>
      <td>NaN</td>
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
      <td>2.025868476312066</td>
      <td>2459176.565253751041</td>
      <td>273.1861379061811</td>
      <td>.493077766590875</td>
      <td>J2000</td>
      <td>AMO</td>
      <td>Near-Earth asteroid orbits similar to that of ...</td>
      <td>1.017 AU &lt; q (perihelion) &lt; 1.3 AU</td>
      <td>NaN</td>
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
      <td>3.884205451986184</td>
      <td>2459278.734090121480</td>
      <td>293.4095292372738</td>
      <td>.2393325373380815</td>
      <td>J2000</td>
      <td>AMO</td>
      <td>Near-Earth asteroid orbits similar to that of ...</td>
      <td>1.017 AU &lt; q (perihelion) &lt; 1.3 AU</td>
      <td>NaN</td>
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
      <td>2.910206355077709</td>
      <td>2459093.016756074428</td>
      <td>330.1368350661496</td>
      <td>.322786554576405</td>
      <td>J2000</td>
      <td>AMO</td>
      <td>Near-Earth asteroid orbits similar to that of ...</td>
      <td>1.017 AU &lt; q (perihelion) &lt; 1.3 AU</td>
      <td>NaN</td>
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
      <td>3.361558630853122</td>
      <td>2458482.209254870466</td>
      <td>146.5048635106909</td>
      <td>.2826692640905165</td>
      <td>J2000</td>
      <td>AMO</td>
      <td>Near-Earth asteroid orbits similar to that of ...</td>
      <td>1.017 AU &lt; q (perihelion) &lt; 1.3 AU</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <th>195</th>
      <td>3879534</td>
      <td>3879534</td>
      <td>(2019 UO4)</td>
      <td>2019 UO4</td>
      <td>http://ssd.jpl.nasa.gov/sbdb.cgi?sstr=3879534</td>
      <td>24.7</td>
      <td>False</td>
      <td>[{'close_approach_date': '2019-10-16', 'close_...</td>
      <td>False</td>
      <td>http://www.neowsapp.com/rest/v1/neo/3879534?ap...</td>
      <td>...</td>
      <td>2.356145063887216</td>
      <td>2458734.942685330012</td>
      <td>20.2230372412315</td>
      <td>.4538657096149674</td>
      <td>J2000</td>
      <td>APO</td>
      <td>Near-Earth asteroid orbits which cross the Ear...</td>
      <td>a (semi-major axis) &gt; 1.0 AU; q (perihelion) &lt;...</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>196</th>
      <td>3892768</td>
      <td>3892768</td>
      <td>(2019 VT4)</td>
      <td>2019 VT4</td>
      <td>http://ssd.jpl.nasa.gov/sbdb.cgi?sstr=3892768</td>
      <td>24.4</td>
      <td>False</td>
      <td>[{'close_approach_date': '2019-11-21', 'close_...</td>
      <td>False</td>
      <td>http://www.neowsapp.com/rest/v1/neo/3892768?ap...</td>
      <td>...</td>
      <td>1.695958399821732</td>
      <td>2458817.861061683347</td>
      <td>344.1161203782057</td>
      <td>.6025508309412494</td>
      <td>J2000</td>
      <td>AMO</td>
      <td>Near-Earth asteroid orbits similar to that of ...</td>
      <td>1.017 AU &lt; q (perihelion) &lt; 1.3 AU</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>197</th>
      <td>3593352</td>
      <td>3593352</td>
      <td>(2010 GE69)</td>
      <td>2010 GE69</td>
      <td>http://ssd.jpl.nasa.gov/sbdb.cgi?sstr=3593352</td>
      <td>NaN</td>
      <td>False</td>
      <td>[]</td>
      <td>False</td>
      <td>http://www.neowsapp.com/rest/v1/neo/3593352?ap...</td>
      <td>...</td>
      <td>2.252320635427747</td>
      <td>2454865.269039801145</td>
      <td>182.0553238983248</td>
      <td>.4192591974900937</td>
      <td>J2000</td>
      <td>AMO</td>
      <td>Near-Earth asteroid orbits similar to that of ...</td>
      <td>1.017 AU &lt; q (perihelion) &lt; 1.3 AU</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>198</th>
      <td>3943343</td>
      <td>3943343</td>
      <td>(2019 YS1)</td>
      <td>2019 YS1</td>
      <td>http://ssd.jpl.nasa.gov/sbdb.cgi?sstr=3943343</td>
      <td>25.7</td>
      <td>False</td>
      <td>[{'close_approach_date': '2019-12-14', 'close_...</td>
      <td>False</td>
      <td>http://www.neowsapp.com/rest/v1/neo/3943343?ap...</td>
      <td>...</td>
      <td>2.873109473373824</td>
      <td>2458816.635743913359</td>
      <td>8.354869418916564</td>
      <td>.3654118195342511</td>
      <td>J2000</td>
      <td>APO</td>
      <td>Near-Earth asteroid orbits which cross the Ear...</td>
      <td>a (semi-major axis) &gt; 1.0 AU; q (perihelion) &lt;...</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>199</th>
      <td>3943345</td>
      <td>3943345</td>
      <td>(2019 YU1)</td>
      <td>2019 YU1</td>
      <td>http://ssd.jpl.nasa.gov/sbdb.cgi?sstr=3943345</td>
      <td>24.3</td>
      <td>False</td>
      <td>[{'close_approach_date': '2019-12-20', 'close_...</td>
      <td>False</td>
      <td>http://www.neowsapp.com/rest/v1/neo/3943345?ap...</td>
      <td>...</td>
      <td>1.413689789640154</td>
      <td>2458767.240822438503</td>
      <td>58.45753614966404</td>
      <td>.8203509800434466</td>
      <td>J2000</td>
      <td>APO</td>
      <td>Near-Earth asteroid orbits which cross the Ear...</td>
      <td>a (semi-major axis) &gt; 1.0 AU; q (perihelion) &lt;...</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>200 rows × 45 columns</p>
</div>




```python
df_completo.to_csv('../../Datasets/near_earth_objects-raw.csv')
```

¡Listo! Ya tenemos nuestro dataset para procesar en la siguiente sesión. En este último reto vas a implementar tú mismo este proceso, con la única diferencia de que vas a pedir de la página 10 a la 110. ¡Mucha suerte!
