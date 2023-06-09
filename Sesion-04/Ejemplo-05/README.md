[`Procesamiento de datos con Python`](../../Readme.md) > [`Sesión 04`](../Readme.md) > `Ejemplo 5`

# Ejemplo 5: Lectura de JSON

<div style="text-align: justify;">

## 1. Objetivos :dart:

- Aprender a leer archivos JSON y crear DataFrames con ellos


## 2. Requisitos :clipboard:

1. **PyCharm** instalado.

## 3. Desarrollo :rocket:

Primero tenemos que importar la biblioteca `json` que nos ayuda a lidiar con formato JSON en Python:

```python
import json
```

Después leemos el archivo JSON usando `open`:

```python
f = open('../../Datasets/zomato_reviews-clean.json', 'r')
```

La ruta (o path) puede ser absoluto o relativo (en el Prework hay un link donde se explica esto con más claridad). El 'r' significa que queremos leer el archivo (read).

Después convertimos nuestro archivo JSON en un diccionario de Python:

```python
json_data = json.load(f)
```

Después cerramos nuestro archivo:

```python
f.close()
```

Y finalmente pasamos el diccionario a `pandas.DataFrame.from_dict` para crear un DataFrame:

```
df = pd.DataFrame.from_dict(json_data)
```

¡Listo! Ahora vamos a ver qué podemos hacer con este DataFrame.

[`Anterior`](../Readme.md) | [`Siguiente`](../Readme.md)

</div>