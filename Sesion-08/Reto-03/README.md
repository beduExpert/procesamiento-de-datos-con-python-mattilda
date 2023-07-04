## Reto 3: `merge` para completar información faltante

### 1. Objetivos:
    - Completar la tabla `users` usando la información contenida en las tablas `occupations` y `age_ranges`.
    
---
    
### 2. Desarrollo:

#### a) Complementado información usando el método `merge`

No es muy práctico tener las tablas `occupations` y `age_range` por sí solas, ya que la información que contienen está íntimamente relacionada con al información de la tabla `users`. Vamos entonces a unir las tres tablas en una sola tabla para tener esa información mucho más accesible. Tu Reto consiste en los siguientes pasos:

1. Lee tus archivos `users`, `occupations` y `age_range` (o como sea que les quisiste llamar) y conviértelos en `DataFrames`.
2. Utiliza el método `merge` para agregar la información contenida en la tabla `occupations` a la tabla `users`.
3. Utiliza el método `merge` para agregar la información contenida en la tabla `age_ranges` a la tabla `users`.
4. Si lo consideras necesario, renombra y reordena las columnas para que la información sea clara.
5. Guarda tu nuevo conjunto de datos en un nuevo archivo .csv.


```python
# Tu código va aquí
#
# ...
# ...
```

Compara tus resultados con tus compañeros y tu experta para asegurarse de que todos tengan un conjunto similar que contenga toda la información requerida.
