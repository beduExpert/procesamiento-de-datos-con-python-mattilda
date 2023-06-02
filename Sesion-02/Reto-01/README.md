[`Procesamiento de datos con Python`](../../Readme.md) > [`Sesión 01`](../Readme.md) > `Reto 1`

# Reto 1: Creando listas y accediendo a ellas

<div style="text-align: justify;">

## 1. Objetivos :dart:

- Practicar crear listas con valores crudos y variables
- Practicar acceder a listas usando índices

## 2. Requisitos :clipboard:

1. **PyCharm** instalado.

## 3. Desarrollo :rocket:

### Definiendo una lista

1. Debajo de esta celda hay un nombre de una variable que aún no ha sido asignada:

    ```python
    mi_informacion = 
    ```

    Ahora tenemos un `print` que imprime una cadena formateada para mostrar cierta información acerca de ti (Las triples comillas ''' nos sirven para generar cadenas de varias líneas):

    ```python
    print(f'''
    ¡Hola! Mi nombre es {mi_informacion[0]}. Todos me dicen {mi_informacion[1]}.
    Mi comida favorita es {mi_informacion[2]}. Y la comida que más detesto es {mi_informacion[3]}.
    Mi trabajo ideal sería {mi_informacion[4]}.
    ¡Gracias, chau!
    ''')
    ```

    Para que esta cadena funcione, asigna una lista a la variable `mi_informacion` con toda la información necesaria para imprimir tu micro-bio debajo de la celda.

### Una lista construida con variables

1. Debajo de esta celda vemos los nombres de varias variables y una lista que las contiene.

    ```python    
    info_0 = 
    info_1 = 
    info_2 = 
    info_3 = 
    info_4 = 

    info_faltante[info_0, info_1, info_2, info_3, info_4]
    ```

    Ahora, tenemos un `print` que imprime una pequeña historia utilizando la lista `info_faltante` que contiene a las demás variables:

    ```python
    print(f'''
    Algún día los {info_faltante[0]} lograrán su objetivo. Su objetivo de {info_faltante[1]}.
    Ese día, los humanos {info_faltante[2]} y tendrán que {info_faltante[3]}.
    Por esa razón yo todos los días {info_faltante[4]}.
    ''')
    ```

    Tu reto será asignar las variables `info_x` con la información que desees para crear una historia a tu gusto. Cada variable puede contener una string que tenga varias palabras (frases, pues). Si te dan ganas, ¡comparte la historia con tus compañeros!

### Practicando con el operador de indexación

1. Debajo de esta celda hay una lista con números dentro:

    ```python
    respuestas = [0.58, 9, 2, 3, 37, 5, 75, 4]
    ```

    Ahora, tenemos un `print` con una cadena interpolada. Como puedes ver todas las interpolaciones están vacías:

    ```python
    print(f'''
    1. Los humanos tenemos {} ojos en la cara.
    2. Un humano adulto tiene {} dientes dentro de su boca.
    3. Un feto tarda {} meses en gestarse antes de nacer.
    4. La expectativa de vida en México es de alrededor de {} años.
    5. Las horas de sueño al día recomendadas para adultos jóvenes son entre {} y {}.
    6. El récord actual de velocidad en 100 metros (09/05/2020) fue establecido por Usain Bolt y es de {}
    ''')
    ```

    Tu reto es llenar las interpolaciones en la string con elementos de la lista de arriba. Usa los índices de los elementos para acceder a las respuestas correctas y llenar la lista con información coherente. No todas las respuestas están en la lista. Para obtener algunas respuestas tendrás que acceder a elementos de la lista y realizar operaciones numéricas conn ellos (usando `+` o `-`).

    > *Reto extra: Si quieres un poco más de dificultad, accede a todos los elementos usando solamente números negativos como índices*.



[`Anterior`](../Readme.md) | [`Siguiente`](../Readme.md)

</div>