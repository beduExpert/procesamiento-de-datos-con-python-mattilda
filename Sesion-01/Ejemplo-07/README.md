[`Procesamiento de datos con Python`](../../Readme.md) > [`Sesión 01`](../Readme.md) > `Ejemplo 7`

# Ejemplo 7: Estructuras de control de flujo

<div style="text-align: justify;">

## 1. Objetivos :dart:

- Conocer las estructuras de control, cómo funcionan y para qué sirven

## 2. Requisitos :clipboard:

1. **PyCharm** instalado.

## 3. Desarrollo :rocket:

1. Queremos darle a nuestro programa la capacidad de tomar decisiones. Esto puede hacerse usando una sentencia if. Una sentencia if usa una comparación para obtener un booleano. Si el booleano es `True`, el bloque de la sentencia se corre. Si el booleano es `False` nos saltamos a lo que sigue después del bloque.

    ```python
    var_1 = 4
    var_2 = 5

    if var_1 < var_2:
        print("El bloque se ha ejecutado")
    ```

    ```bash
    El bloque se ha ejecutado
    ```

    ```python
    if var_1 > var_2:
        print("El bloque se ha ejecutado")
    
    print("Yo estoy afuera del bloque, y de todas maneras me van a llamar")
    ```

    ```bash
    Yo estoy afuera del bloque, y de todas maneras me van a llamar
    ```

2. Hay veces que queremos tener una acción por defecto, que queremos que suceda en caso de que la comparación sea falsa. Para eso podemos usar una sentencia `else`. Piénsalo como preguntarse a uno mismo: "Si meto mi mano a la bolsa y resulta que encuentro un billete de $50, me compro unos nachos; si no hay nada, veré la película llorando de tristeza".

    Implementamos la acción por defecto así:

    ```python
    if var_1 > var_2:
        print("La condición se ha cumplido")
    else:
        print("La condición no se ha cumplido, y por lo tanto yo me imprimo")
    ```

    ```bash
    La condición no se ha cumplido, y por lo tanto yo me imprimo
    ```

3. Si queremos que haya más de dos opciones, podemos agregar opciones usando la sentencia `elif`:

    
    ```python
    if var_1 > var_2:
        print("La primera condición se ha cumplido")
    elif var_1 < var_2:
        print("La segunda condición se ha cumplido")
    else:
        print("Las primeras dos comparaciones fueron Falsas")
    ```

    ```bash
    La segunda condición se ha cumplido
    ```

    ¿Puedes pensar bajo condiciones se correría la sentencia `else`?

    ¡Vayamos al último reto de la sesión!


[`Anterior`](../Readme.md) | [`Siguiente`](../Reto-02/README.md)

</div>