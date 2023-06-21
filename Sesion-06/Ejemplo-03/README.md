## Ejemplo 3: Excepciones y try except

### 1. Objetivos:
    - Aprender a usar try except para evitar que las excepciones detengan nuestros programas
 
---
    
### 2. Desarrollo:

Durante el proceso de un programa pueden suceder diferentes tipos de errores, que llamamos `Excepciones`. Una `Excepción` puede suceder en alguno de estos casos, por ejemplo:


```python
lista_1 = [1, 2, 3, 4, 5]

lista_1[10]
```


    ---------------------------------------------------------------------------

    IndexError                                Traceback (most recent call last)

    <ipython-input-1-f0bb0e1b4da7> in <module>
          1 lista_1 = [1, 2, 3, 4, 5]
          2 
    ----> 3 lista_1[10]
    

    IndexError: list index out of range



```python
dict_1 = {
    'a': 1,
    'b': 2,
    'c': 3,
    'd': 4
}

dict_1['z']
```


    ---------------------------------------------------------------------------

    KeyError                                  Traceback (most recent call last)

    <ipython-input-2-25cc6ca79f61> in <module>
          6 }
          7 
    ----> 8 dict_1['z']
    

    KeyError: 'z'



```python
int("Holi")
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    <ipython-input-3-639408661f5f> in <module>
    ----> 1 int("Holi")
    

    ValueError: invalid literal for int() with base 10: 'Holi'


Cuando automatizamos programas, tenemos que evitar que Excepciones ocurran, pues detendrían nuestro programa y arruinarían nuestra automatización. Podemos usar estructuras try except para evitar que esto suceda:


```python
lista_2 = [1, 2, 3, 4, 5]

try:
    print(lista_2[10])
except:
    print("Ese numero esta fuera de rango")
    print("Mejor leamos este número")
    print(lista_2[2])
```

    Ese numero esta fuera de rango
    Mejor leamos este número
    3



```python
dict_2 = {
    'a': 1,
    'b': 2,
    'c': 3,
    'd': 4
}

try:
    print(dict_2['z'])
except:
    print("Esa llave no existe")
    print("Mejor leamos esta llave")
    print(dict_2['b'])
```

    Esa llave no existe
    Mejor leamos esta llave
    2



```python
try:
    print(int("Holi"))
except:
    print("Ese no es un número")
    print("Mejor vamos a imprimirlo convirtiéndolo en una lista")
    print(list("Holi"))
```

    Ese no es un número
    Mejor vamos a imprimirlo convirtiéndolo en una lista
    ['H', 'o', 'l', 'i']



```python

```
