## Ejemplo 2: For Loops

### 1. Objetivos:
    - Aprender a usar `for loops` para luego poder automatizar procesos
 
---
    
### 2. Desarrollo:

Los `for loops` nos ayudan a automatizar procesos. Básicamente definimos primero sobre qué queremos iterar (o ciclar), después definimos una variable (o variables) que van a recibir cada valor de la iteración, y luego tenemos el bloque del `for loop`, que es donde realizamos los procesos a automatizar. Mira cómo se ven en acción:


```python
for i in range(0, 10):
    print(i)
```

    0
    1
    2
    3
    4
    5
    6
    7
    8
    9



```python
lista_de_numeros = []

for i in range(0, 50):
    lista_de_numeros.append(i)
    
print(lista_de_numeros)
```

    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49]



```python
numero = 150

for _ in range(0, 20):
    
    # este proceso es independiente del loop, por eso no usamos la variable del loop
    # en este caso el loop solo sirve para realizar una tarea repetidas veces
    
    numero = numero + 1

print(numero)
```

    170



```python
dict_1 = {
    'a': 1,
    'b': 2,
    'c': 3,
    'd': 4,
    'e': 5
}

for key in dict_1:
    print(dict_1[key])
```

    1
    2
    3
    4
    5

