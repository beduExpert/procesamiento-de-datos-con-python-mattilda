## Reto 3: Evitando errores con try except

### 1. Objetivos:
    - Usar una estructura try except para evitar que una función lance un error
 
---
    
### 2. Desarrollo:

### a) Evitando errores al hacer conversión de tipos de dato

La conversión de tipos de dato (data casting) es una de las labores más importantes de un procesador de datos. A veces tenemos datos que deberían de tener un tipo de dato pero que tienen otro. Vamos a imaginar que tenemos un sistema donde recibimos input de un usuario. Este input son números que están representados como strings, como por ejemplo:

- "1.5"
- "4"
- "100.23"
- "134.99"

Nosotros queremos guardar esos datos como `float`, no como `string` y por lo tanto vamos a crear una función que convierta una `lista` de `strings` en una `lista` de `float`. El problema es que a veces, el usuario envía inputs que no son números representados como `strings`, sino otro tipo de caracteres, como:

- "a"
- "fgwe"
- "4r5t"
- "#!"

Esos caracteres no los podemos convertir en `float` y por lo tanto vamos a sustituirlos por un `NaN` de `numpy` (`np.nan`). Tu reto es el siguiente:

1. Completa la función debajo que recibe una `lista` de `strings` y regresa una `lista` de `floats`.
2. Usa un `for loop` para iterar por la `lista` de `strings` y convertir uno por uno los valores a `float` (puedes leer cómo hacer eso [aquí](http://lineadecodigo.com/python/iterar-una-lista-en-python/) y [aquí](https://es.stackoverflow.com/questions/49194/c%C3%B3mo-convertir-un-tipo-string-a-float-o-int))
3. Los resultados exitosos de la conversión guárdalos en una la `lista` `lista_de_floats` que es lo que regresa la función.
4. Agrega una estructura `try except` para evitar errores cuando la conversión no sea posible y para agregar un `np.nan` a `lista_de_floats` en caso de que la conversión haya fallado.


```python
def lista_de_strings_a_lista_de_floats(lista_de_strings):
    
    lista_de_floats = []
    
    ## Tú código va aquí
    ## ...
    ## ...
        
    return lista_de_floats
```


```python

def test_lista_de_strings_a_lista_de_floats(lista_de_strings_a_lista_de_floats):
    
    import numpy as np
    
    errores = 0
    
    lista_1_original = ['1', '2', '3', '4', '5']
    lista_1_esperada = [1.0, 2.0, 3.0, 4.0, 5.0]
    lista_1_obtenida = lista_de_strings_a_lista_de_floats(lista_1_original)
    if lista_1_obtenida != lista_1_esperada:
        print(f'Error!\n')
        print(f'- Lista original: {lista_1_original}')
        print(f'- Lista esperada: {lista_1_esperada}')
        print(f'- Lista recibida: {lista_1_obtenida}')
        print('\n')
        errores += 1
        
    lista_2_original = []
    lista_2_esperada = []
    lista_2_obtenida = lista_de_strings_a_lista_de_floats(lista_2_original)
    if lista_2_obtenida != lista_2_esperada:
        print(f'Error!\n')
        print(f'- Lista original: {lista_2_original}')
        print(f'- Lista esperada: {lista_2_esperada}')
        print(f'- Lista recibida: {lista_2_obtenida}')
        print('\n')
        errores += 1
        
    lista_3_original = ['1.2', '33', '55.5', 'f', '78']
    lista_3_esperada = [1.2, 33.0, 55.5, np.nan, 78.0]
    lista_3_obtenida = lista_de_strings_a_lista_de_floats(lista_3_original)
    if lista_3_obtenida != lista_3_esperada:
        print(f'Error!\n')
        print(f'- Lista original: {lista_3_original}')
        print(f'- Lista esperada: {lista_3_esperada}')
        print(f'- Lista recibida: {lista_3_obtenida}')
        print('\n')
        errores += 1
        
    lista_4_original = ['f', 'g', 't', 'e', 'r']
    lista_4_esperada = [np.nan, np.nan, np.nan, np.nan, np.nan]
    lista_4_obtenida = lista_de_strings_a_lista_de_floats(lista_4_original)
    if lista_4_obtenida != lista_4_esperada:
        print(f'Error!\n')
        print(f'- Lista original: {lista_4_original}')
        print(f'- Lista esperada: {lista_4_esperada}')
        print(f'- Lista recibida: {lista_4_obtenida}')
        print('\n')
        errores += 1
        
    lista_5_original = ['f', '4.4', 't', '6.6', 'r', '9.9']
    lista_5_esperada = [np.nan, 4.4, np.nan, 6.6, np.nan, 9.9]
    lista_5_obtenida = lista_de_strings_a_lista_de_floats(lista_5_original)
    if lista_5_obtenida != lista_5_esperada:
        print(f'Error!\n')
        print(f'- Lista original: {lista_5_original}')
        print(f'- Lista esperada: {lista_5_esperada}')
        print(f'- Lista recibida: {lista_5_obtenida}')
        print('\n')
        errores += 1
        
    if errores > 0:
        return
    
    print(f'Todo funciona correctamente!')

test_lista_de_strings_a_lista_de_floats(lista_de_strings_a_lista_de_floats)
```


```python

```
