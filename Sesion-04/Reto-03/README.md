[`Procesamiento de datos con Python`](../../Readme.md) > [`Sesión 04`](../Readme.md) > `Reto 3`

# Reto 3: DataFrames

<div style="text-align: justify;">

## 1. Objetivos :dart:

- Aprender a crear DataFrames e indexar por columna y por fila

## 2. Requisitos :clipboard:

1. **PyCharm** instalado.

## 3. Desarrollo :rocket:

### Creación e indexación de DataFrames

Eres el Data Wrangler (procesador de datos) de EyePoker Inc. Tienes el siguiente diccionario con datos que se refieren a diferentes productos que vende la empresa. Este es tu conjunto de datos y el índice que le corresponde:

```python
datos_productos = {
    "nombre": ["Pokemaster", "Cegatron", "Pikame Mucho", "Lazarillo de Tormes", "Stevie Wonder", "Needle", "El AyMeDuele"],
    "precio": [10000, 5500, 3500, 750, 15500, 12250, 23000],
    "peso": [1.2, 1.5, 2.3, 5.5, 3.4, 2.4, 8.8],
    "capacidad de destrucción retinal": [3, 7, 6, 8, 9, 2, 10],
    "disponible": [True, False, True, True, False, False, True]
}

indice = [1, 2, 3, 4, 5, 6, 7]
```

El Analista de Datos de la empresa quiere realizar algunas visualizaciones con este conjunto de datos, pero no es muy buen procesador de datos, así que te pide a ti ayuda para crear los subconjuntos de datos que necesita para sus visualizaciones.

Te ha dado las descripciones de los subconjuntos que necesita, en el orden en el que los quiere.

Tu primer paso es convertir tu diccionario a DataFrame usando `datos_productos` e `indice`:

```python
df_productos =
```

Ahora, indexa tu DataFrame para obtener los subconjuntos requeridos. Los productos en existencia tienen un orden específico en la base de datos. El orden correcto es el que está definido en `datos_productos`. Eso significa que el "Pokemaster" tiene el índice 1 y es el primer producto; y el "El AyMeDuele" tiene el ìndice 7 y es el último producto.

Realiza las indexaciones debajo. Recuerda ordenar tus DataFrames en el orden en el que los menciona el Analista:

```python
# Quiero un DataFrame que contenga los productos "Pikame Mucho" y "Stevie Wonder"
pm_sw =

# Quiero un DataFrame que contenga desde el producto #4 hasta el último
p4_final =

# Quiero un DataFrame que contenga los productos "El AyMeDuele", "Lazarillo de Tormes" y "Needle"
amd_lt_n =

# Quiero un DataFrame que contenga desde el primer producto hasta el producto #5
primer_p5 =

# Quiero un DataFrame que contenga los productos "Pikame Mucho" y "Lazarillo de Tormes", pero sólo con las columnas "nombre", "precio" y "peso"
pm_lt_pp =

# Quiero un DataFrame que contenga todos los productos pero con sólo las columnas 'nombre', 'precio' y 'capacidad de destrucción retinal'
t_pcdr =

# Quiero un DataFrame que contenga desde el producto #3 hasta el #6, pero sólo las columnas 'nombre', 'precio' y 'disponible'
p3_p6_pd =

def verificar_indexaciones(datos_productos, indice, df_productos, pm_sw, p4_final, amd_lt_n, primer_p5, pm_lt_pp, t_pcdr, p3_p6_pd):
    
    import pandas as pd
    
    df_productos_esperado = pd.DataFrame(datos_productos, index=indice)
    if not df_productos_esperado.equals(df_productos):
        print(f'df_productos ha sido creado incorrectamente ... Favor de revisar')
        return
    
    print(f'== Verificación de Indexaciones ==\n')
    verificar_indexacion(df_productos.loc[[3, 5]], pm_sw, 'DataFrame que contenga los productos "Pikame Mucho" y "Stevie Wonder"')
    verificar_indexacion(df_productos.loc[4:], p4_final, 'DataFrame que contenga desde el producto #4 hasta el último')
    verificar_indexacion(df_productos.loc[[7, 4, 6]], amd_lt_n, 'DataFrame que contenga los productos "El AyMeDuele", "Lazarillo de Tormes" y "Needle"')
    verificar_indexacion(df_productos.loc[:5], primer_p5, 'DataFrame que contenga desde el primer producto hasta el producto #5')
    verificar_indexacion(df_productos.loc[[3, 4], ['nombre', 'precio', 'peso']], pm_lt_pp, 'DataFrame que contenga los productos "Pikame Mucho" y "Lazarillo de Tormes", pero sólo con las columnas "nombre", "precio" y "peso"')
    verificar_indexacion(df_productos[['nombre', 'precio', 'capacidad de destrucción retinal']], t_pcdr, "DataFrame que contenga todos los productos pero con sólo las columnas 'nombre', 'precio' y 'capacidad de destrucción retinal'")
    verificar_indexacion(df_productos.loc[3:6, ['nombre', 'precio', 'disponible']], p3_p6_pd, "DataFrame que contenga desde el producto #3 hasta el #6, pero sólo las columnas 'nombre', 'precio' y 'disponible'")
    
def verificar_indexacion(esperada, recibida, descripcion):
    es_correcta = "Correcto" if esperada.equals(recibida) else "Incorrecto"
    respuesta = "Muchas gracias!" if es_correcta == "Correcto" else "Favor de revisar"
    print(f"\n- Descripción de pedido: {descripcion}")
    print(f"El pedido es {es_correcta} ... {respuesta}")

verificar_indexaciones(datos_productos, indice, df_productos, pm_sw, p4_final, amd_lt_n, primer_p5, pm_lt_pp, t_pcdr, p3_p6_pd)  
```

[`Anterior`](../Readme.md) | [`Siguiente`](../Readme.md)

</div>