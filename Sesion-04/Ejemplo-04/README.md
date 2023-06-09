[`Procesamiento de datos con Python`](../../Readme.md) > [`Sesión 04`](../Readme.md) > `Ejemplo 4`

# Ejemplo 4: Manipulación de columnas

<div style="text-align: justify;">

## 1. Objetivos :dart:

- Aprender a crear nuevas columnas en un DataFrame
- Aprender a reasignar columnas
- Aprender a eliminar columnas


## 2. Requisitos :clipboard:

1. **PyCharm** instalado.

## 3. Desarrollo :rocket:

Tenemos aquí un DataFrame:

```python
datos = {
    "Nombre": ["Pepinillo Hernández", "Lúpulo de Dios", "Juan Juon", "Jimmy el Patatas", "Lorenzo Retaguardias"],
    "Cereal favorito": ["Korn Floks", "Verdurinis", "Zumbaritas", "Diabetukis, Papá", "Fibra Máxima 3000"],
    "Hora del desayuno": ["11:00", "07:30", "07:00", "08:30", "09:30"]
}

df = pd.DataFrame(datos)
df
```
```
                 Nombre    Cereal favorito Hora del desayuno
0   Pepinillo Hernández         Korn Floks             11:00
1        Lúpulo de Dios         Verdurinis             07:30
2             Juan Juon         Zumbaritas             07:00
3      Jimmy el Patatas   Diabetukis, Papá             08:30
4  Lorenzo Retaguardias  Fibra Máxima 3000             09:30
```

Podemos agregar nuevas columnas a nuestros DataFrames con una sintaxis muy parecida a la de los diccionarios:

```python
df["Fruta con la que acompaña el cereal"] = pd.Series(['Pera', 'Manzana', 'Plátano', 'Guayaba', 'Pizza'])
df
```
```
                 Nombre  ... Fruta con la que acompaña el cereal
0   Pepinillo Hernández  ...                                Pera
1        Lúpulo de Dios  ...                             Manzana
2             Juan Juon  ...                             Plátano
3      Jimmy el Patatas  ...                             Guayaba
4  Lorenzo Retaguardias  ...                               Pizza
[5 rows x 4 columns]
```

Podemos usar la misma sintaxis para asignar una nueva Serie a una columna existente:

```python
df["Hora del desayuno"] = pd.Series(["10:30", "06:30", "06:00", "07:00", "08:00"])

df
```
```
                 Nombre  ... Fruta con la que acompaña el cereal
0   Pepinillo Hernández  ...                                Pera
1        Lúpulo de Dios  ...                             Manzana
2             Juan Juon  ...                             Plátano
3      Jimmy el Patatas  ...                             Guayaba
4  Lorenzo Retaguardias  ...                               Pizza
```

También podemos eliminar una columna usando el siguiente método:

```python
df.drop(columns=['Fruta con la que acompaña el cereal'])
```
```
                 Nombre    Cereal favorito Hora del desayuno
0   Pepinillo Hernández         Korn Floks             10:30
1        Lúpulo de Dios         Verdurinis             06:30
2             Juan Juon         Zumbaritas             06:00
3      Jimmy el Patatas   Diabetukis, Papá             07:00
4  Lorenzo Retaguardias  Fibra Máxima 3000             08:00
```

Recuerda que estos métodos sólo regresan "vistas". Para que el cambio permanezca, tenemos que asignar el resultado de la operación a la variable `df` o a alguna otra variable:

```python
df_dropped = df.drop(columns=['Fruta con la que acompaña el cereal'])

df
```
```
                 Nombre  ... Fruta con la que acompaña el cereal
0   Pepinillo Hernández  ...                                Pera
1        Lúpulo de Dios  ...                             Manzana
2             Juan Juon  ...                             Plátano
3      Jimmy el Patatas  ...                             Guayaba
4  Lorenzo Retaguardias  ...                               Pizza
[5 rows x 4 columns]
```

```python
df_dropped
```
```
                 Nombre    Cereal favorito Hora del desayuno
0   Pepinillo Hernández         Korn Floks             10:30
1        Lúpulo de Dios         Verdurinis             06:30
2             Juan Juon         Zumbaritas             06:00
3      Jimmy el Patatas   Diabetukis, Papá             07:00
4  Lorenzo Retaguardias  Fibra Máxima 3000             08:00
```

[`Anterior`](../Readme.md) | [`Siguiente`](../Readme.md)

</div>