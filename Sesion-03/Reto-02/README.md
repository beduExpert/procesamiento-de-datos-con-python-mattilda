[`Procesamiento de datos con Python`](../../Readme.md) > [`Sesión 03`](../Readme.md) > `Reto 2`

# Reto 2: Filter

<div style="text-align: justify;">

## 1. Objetivos :dart:

- Practicar el uso de `filter` para filtrar los datos en una `lista`

## 2. Requisitos :clipboard:

1. **PyCharm** instalado.

## 3. Desarrollo :rocket:

### Limpiando datos nulos

Debajo tenemos una lista que incluye datos acerca de las edades de las personas que han asistido a un curso de Cocina Medieval (ya sabes: puerco al horno, manzanas asadas, aguardiente, sangre fresca de tus enemigos). Algunas de las personas que atendieron no quisieron dar su edad. Es por eso que algunos de los elementos son `None`:

```python
edades = [12, 16, 19, None, 21, 25, 24, None, None, 16, 17, 25, 23, 28, None, 23, 35, 59, 67, None, 34, 21, 23, 15, 14, None, 18, 24, 23, 17]
```

Queremos realizar una pequeña visualización (un histograma, que ya aprenderás a hacer más tarde) con nuestros datos. Pero no nos interesan los datos que vienen como `None`. Escribe una función llamada `valor_no_es_none` que reciba un valor, cheque si el valor es `None`, regrese `False` si el valor es `None` o regrese `True` si el valor no es `None`. Después úsala para filtrar tus datos:

```python
## Tu función va aquí
##
## ...
## ...

def crear_histograma_con(datos):
    import seaborn as sns
    import numpy as np
    
    sns.distplot(datos, kde=False, bins=len(np.unique(datos)))

edades_filtradas =

crear_histograma_con(edades_filtradas)
```

### Filtrando datos atípicos

Aquí tenemos una lista que contiene datos acerca de los sueldos (cada número representa "miles de pesos") de los empleados de EyePoker Inc. (la empresa donde se producen los mejores picadores de ojos en todo el Hemisferio Occidental):

```python
sueldos = [26, 32, 26, 30, 30, 32, 28, 30, 28, 110, 34, 30, 28, 26, 28, 30, 28, 85, 25, 30, 34, 34, 30, 30, 120, 28, 28, 120, 125]
```

En general todos los sueldos se encuentran en un rango bastante restringido, pero tenemos algunos datos sobre sueldos "anormalmente" grandes. Los sueldos tan grandes son los de los ejecutivos, que claramente no tienen ninguna noción de "justicia" (eso pasa cuando tus picadores de ojos son los mejores de todo el Hemisferio Occidental). Nosotros queremos usar el promedio para tener una idea de cuál es el sueldo típico en esta empresa. Nuestros valores atípicos (los sueldos anormalmente grandes) van a arruinar nuestro cálculo.

Mira cuál es el sueldo típico si no filtramos nuestros valores anormalmente grandes:

```python
print(f'El sueldo "típico" en EyePoker Inc. es de {sum(sueldos) / len(sueldos)}')
```

Para corregir esto haz una función llamada `numero_es_menor_que_40` que descarte los números mayores de 40, y úsala para filtrar la lista `sueldos`, para tener un cálculo más apropiado del sueldo típico en esta empresa.

```python
## Tu función va aquí
##
## ...
## ...

sueldos_filtrados =

print(f'El sueldo "típico" en EyePoker Inc. es de {sum(sueldos_filtrados) / len(sueldos_filtrados)}')
```

[`Anterior`](../Readme.md) | [`Siguiente`](../Readme.md)

</div>