[`Procesamiento de datos con Python`](../../Readme.md) > [`Sesión 04`](../Readme.md) > `Reto 4`

# Reto 4: Manipulación de columnas

<div style="text-align: justify;">

## 1. Objetivos :dart:

- Practicar asignar, reasignar y eliminar columnas de DataFrames

## 2. Requisitos :clipboard:

1. **PyCharm** instalado.

## 3. Desarrollo :rocket:

### Transformación de DataFrames

Eres de nuevo el Data Wrangler Inc. Tienes el mismo conjunto de datos que en el Reto pasado:

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

Esta vez el Analista de Datos te hace 3 nuevos pedidos que incluyen la creación de una nueva columna, la asignación de nuevos datos a una columna y la eliminación de un par de columnas. Crea un DataFrame usando `datos_productos` e `indice`, realiza sus pedidos y envíalos para su verificación:

```python
df_productos = 

# Agrega por favor una nueva columna a `df_productos_mas_columna_nueva` con el nombre de columna "nivel de dolor"
columna_nueva = [4, 7, 6, 8, 9, 7, 3]
df_productos_mas_columna_nueva = df_productos.copy()

# Cambia por favor el `DataFrame` `df_productos_descuento` cambiando la columna `precio` por la información contenida en `precios_descuento`
precios_descuento = [8000, 4000, 2000, 500, 14000, 10000, 15000]
df_productos_descuento = df_productos.copy()

# Elimina por favor las columnas "precio" y "peso" de `df_productos` y asigna el resultado a `df_productos_sin_precio_ni_peso`
df_productos_sin_precio_ni_peso =

def verificar_modificaciones(datos_productos, indice, df_productos, columna_nueva, df_productos_mas_columna_nueva, 
                             precios_descuento, df_productos_descuento, df_productos_sin_precio_ni_peso):
    
    import pandas as pd
    
    df_productos_esperado = pd.DataFrame(datos_productos, index=indice)
    if not df_productos_esperado.equals(df_productos):
        print(f'df_productos ha sido creado incorrectamente ... Favor de revisar')
        return
    
    print(f'== Verificación de Modificaciones ==\n')
    columna_nueva_serie = pd.Series(columna_nueva, index=indice)
    df_productos_mas_columna_nueva_2 = df_productos.copy()
    df_productos_mas_columna_nueva_2['nivel de dolor'] = columna_nueva_serie
    verificar_modificacion(df_productos_mas_columna_nueva_2, df_productos_mas_columna_nueva, 'Agrega por favor columna `columna_nueva` a `df_productos_mas_columna_nueva` con el nombre de columna "nivel de dolor"')
    
    precios_descuento_serie = pd.Series(precios_descuento, index=indice)
    df_productos_descuento_2 = df_productos.copy()
    df_productos_descuento_2['precio'] = precios_descuento_serie
    verificar_modificacion(df_productos_descuento_2, df_productos_descuento, 'Cambia por favor el `DataFrame` `df_productos_descuento` cambiando la columna `precio` por la información contenida en `precios_descuento`')
    
    df_productos_sin_precio_ni_peso_2 = df_productos.drop(columns=['precio', 'peso'])
    verificar_modificacion(df_productos_sin_precio_ni_peso_2, df_productos_sin_precio_ni_peso, 'Elimina por favor las columnas "precio" y "peso"')
    
def verificar_modificacion(esperada, recibida, descripcion):
    es_correcta = "Correcto" if esperada.equals(recibida) else "Incorrecto"
    respuesta = "Muchas gracias!" if es_correcta == "Correcto" else "Favor de revisar"
    print(f"\n- Descripción de pedido: {descripcion}")
    print(f"El pedido es {es_correcta} ... {respuesta}")

verificar_modificaciones(datos_productos, indice, df_productos, columna_nueva, df_productos_mas_columna_nueva, 
                             precios_descuento, df_productos_descuento, df_productos_sin_precio_ni_peso)
```

[`Anterior`](../Readme.md) | [`Siguiente`](../Readme.md)

</div>