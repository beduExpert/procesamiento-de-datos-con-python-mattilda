[`Procesamiento de datos con Python`](../../Readme.md) > [`Sesión 01`](../Readme.md) > `Ejemplo 1`

# Ejemplo 1: Listas 

<div style="text-align: justify;">

## 1. Objetivos :dart:

- Entender la sintaxis de las listas en **Python**
- Aprender a crear listas y accesarlas

## 2. Requisitos :clipboard:

1. **PyCharm** instalado.

## 3. Desarrollo :rocket:

1. Las listas son secuencias ordenadas de datos. El orden de los datos en la lista es el mismo orden que tienen los datos a la hora de ser asignados a la lista. Una lista se ve así:

    ```python
    lista_1 = [1, 4, 6, 2, 4]
    ```

    Cada elemento en la lista tiene un índice, que se usa para poder acceder a dicho elemento. Dado que las listas son ordenadas, los índices se van asignando secuencialmente desde el primer elemento hasta el último. El primer índice es siempre 0, y por lo tanto el último índice es siempre n - 1, donde n es el número total de elementos en la lista.

    Por lo tanto, para acceder al primer y al último elemento de la lista anterior, hacemos lo siguiente:

    ```python
    print(f'Primer elemento de la lista: {lista_1[0]}')
    print(f'Último elemento de la lista: {lista_1[4]}')
    ```

    ```
    Primer elemento de la lista: 1
    Último elemento de la lista: 4
    ```

    Si intentamos acceder a un índice que no existe, porque no hay suficientes elementos en la lista, Python nos da un error:

    ```python
    lista_1[10]
    ```

    Dado que es difícil saber cuántos elementos hay en una lista, a menos que nos pongamos a contar, hay algo que podemos hacer para acceder a los últimos elementos de una lista sin arriesgarnos a tener un error.

    Python nos permite acceder a los elementos empezando desde el último elemento hasta el primero (al revés, pues). Esto se hace usando números negativos. O sea que para acceder al último número puedo usar un -1, para acceder al penúltimo número puedo usar -2 y así consecutivamente:

    ```python
    print(lista_1[-1])
    print(lista_1[-2])
    ```

    ```
    4
    2
    ```

    Como podrás imaginar, no solamente podemos guardar datos crudos en una lista (1, 2, 3, 4, etc). Podemos guardar datos en variables y luego guardar esas variables en la lista. Las siguientes dos listas son equivalentes:

    ```python
    lista_con_valores_crudos = [1, 2, 3, 4, 5]

    uno = 1
    dos = 2
    tres = 3
    cuatro = 4
    cinco = 5

    lista_con_variables = [uno, dos, tres, cuatro, cinco]

    print(lista_con_valores_crudos)
    print(lista_con_variables)
    ```

    ```
    [1, 2, 3, 4, 5]
    [1, 2, 3, 4, 5]
    ```

2. Como vimos en el Prework, una lista puede contener cualquier tipo de dato de los que ya conocemos (incluso otras listas).

    ```python
    lista_de_ints = [1, 5, 8, 77, 45, 30]
    lista_de_floats = [2.4, 5.67, 8.7, 9.34]
    lista_de_strings = ["Juan", "Pepe", "Pedro", "Jose"]
    lista_de_booleanos = [True, False, False, True, False]
    lista_de_listas_de_ints = [[3, 4, 6], [7, 8, 9], [4, 6, 2]]
    ```

    A pesar de que Python nos permite guardar diversos tipos de datos en una sola lista, aprendimos que la mejor práctica es evitar esto y guardar un solo tipo de dato por lista

    ¡Vayamos a nuestro primer reto!
    

[`Anterior`](../Readme.md) | [`Siguiente`](../Readme.md)

</div>