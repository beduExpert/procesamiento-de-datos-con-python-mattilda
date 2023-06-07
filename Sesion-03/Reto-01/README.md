[`Procesamiento de datos con Python`](../../Readme.md) > [`Sesión 03`](../Readme.md) > `Reto 1`

# Reto 1: Map

<div style="text-align: justify;">

## 1. Objetivos :dart:

- Practicar el uso de `map` para transformar los datos en una `lista`

## 2. Requisitos :clipboard:

1. **PyCharm** instalado.

## 3. Desarrollo :rocket:

### Proporción a porcentajes

Tenemos una lista que contiene proporciones:

```python
proporciones = [0.45, 0.2, 0.78, 0.4, 0.77, 0.9, 0.4, 0.5, 0.67, 0.24, 0.73]
```

Queremos convertir esta lista en una lista `porcentajes`, donde las proporciones hayan sido convertidas a porcentajes. Termina la función `proporcion_a_porcentajes` y después utiliza `map` para convertir proporciones y asignar la lista transformada a porcentajes:

```python
def proporcion_a_porcentajes(proporcion):
    
    ## Tu código va aquí
    # ...
    # ...
    
    return

porcentajes =  

def imprimir_proporciones_en_equivalencia_a_porcentajes(proporciones, porcentajes):
    
    print(f'==Proporciones y su equivalencia en porcentajes de 1==\n')
    
    for i in range(len(proporciones)):
        print(f'- {proporciones[i]} es el {int(porcentajes[i])}% de 1.')
        

def imprimir_analisis_estadistico(datos):
    
    def mediana(datos):
        datos_sorted = sorted(datos)
        len_datos = len(datos)
        
        if len_datos % 2 == 0:
            mediana = (datos_sorted[int(len_datos / 2) - 1] + datos_sorted[int(len_datos / 2)]) / 2
        else:
            import math
            mediana = datos_sorted[int(math.floor(len_datos / 2))]
            
        return mediana
    
    print(f'==Análisis estadístico de los datos recibidos==\n')
    print(f'Valor mínimo: {min(datos)}')
    print(f'Valor máximo: {max(datos)}')
    print(f'Rango de valores: {max(datos) - min(datos)}')
    print(f'Promedio: {sum(datos) / len(datos)}')
    print(f'Mediana: {mediana(datos)}')  

imprimir_proporciones_en_equivalencia_a_porcentajes(proporciones, porcentajes)    
```

### Strings a números

Tenemos una lista con strings que representan valores númericos:

```python
numeros_como_strings = ["3", "7", "45", "89", "12", "9", "5", "89", "78", "87", "44", "45", "26", "84", "98", "46", "99", "84"]
```

Para poder realizar algunos cálculos estádisticos, necesitamos que estas cademas sean convertidas a ints. Escribe la función `string_a_int` y asigna el resultado de su aplicación a `numeros_como_strings` a la variable `numeros_como_ints`:

```python
def string_a_int(string):
    
    ## Tu código va aquí
    # ...
    # ...
    
    return

numeros_como_ints =    

imprimir_analisis_estadistico(numeros_como_ints)
```

[`Anterior`](../Readme.md) | [`Siguiente`](../Readme.md)

</div>