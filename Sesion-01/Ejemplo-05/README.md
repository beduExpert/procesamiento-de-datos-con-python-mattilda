[`Procesamiento de datos con Python`](../../Readme.md) > [`Sesión 01`](../Readme.md) > `Ejemplo 5`

# Ejemplo 5: Interpolación de cadenas

<div style="text-align: justify;">

## 1. Objetivos :dart:

- Aprender a imprimir cadenas
- Aprender a interpolar variables dentro de cadenas

## 2. Requisitos :clipboard:

1. **PyCharm** instalado.

## 3. Desarrollo :rocket:

1. Podemos hacer anotaciones en las salidas de nuestro código de la siguiente manera:

    ```python
    var_1 = 15.3
    var_2 = 23.4

    print("Suma de var_1 y var_2")
    print(var_1 + var_2)
    ```

    ```bash
    Suma de var_1 y var_2
    38.7
    ```

2. Pero a veces resulta necesario o deseable interpolar el valor de una variable dentro de dicha cadena. Para eso usamos las llamadas *f-strings*. El formado de una f-string es el siguiente:

    ```python
    f "Esto es texto {esto_es_una_variable} esto es más texto"
    ```

    Escribiendo una `f` antes de las comillas le indicamos a **Python** que lo que pongas dentro de las llaves (`{}`) será código de **Python**. En este caso, una variable asignada previamente.

    Ahora podemos hacer lo siguiente:

    ```python
    var_3 = 43
    var_4 = 24.3

    suma = var_3 + var_4

    print(f'La suma de var_3 y var_4 es: {suma}')
    ```

    ```bash
    La suma de var_3 y var_4 es: 67.3
    ```

3. O incluso algo como esto: 

    ```python
    print(f'La suma de {var_3} y {var_4} es: {var_3 + var_4}')
    ```

    ```bash
    La suma de 43 y 24.3 es: 67.3
    ``` 
    
    Vas a ver muchas anotaciones como éstas a través del código de este módulo. Ahora ya sabes qué significan y cómo crearlas.

[`Anterior`](../Readme.md) | [`Siguiente`](../Reto-02/README.md)

</div>