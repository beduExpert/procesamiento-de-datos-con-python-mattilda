
# Sesión 01: Fundamentos de Python

<img src="https://raw.githubusercontent.com/beduExpert/Introduccion-a-Bases-de-Datos-Diciembre-2020/master/imagenes/pizarron.png" align="right" height="100" width="100" hspace="10">
<div style="text-align: justify;">

## 1. Objetivos

1. Asignar variables, operadores matemáticos y tipos de datos.
2. Realizar interpolación de Strings.
3. Realizar comparaciones y estructuras de control de flujo.

## 2. Contenido

---

### <ins><strong>Conociendo PyCharm</strong></ins>

<img src="https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Ftse4.mm.bing.net%2Fth%3Fid%3DOIP.pIi0CfGswG8JLy2f1w6dLQHaHa%26pid%3DApi&f=1&ipt=dc5ce13197d65c5c3ec3211fc9308c8ea281976d6ed92b5900e115ebe8b2619e&ipo=images" align="right" width="15%" hspace=10px>

Ya hemos hablado sobre **PyCharm** en el Prework. En este ejemplo vamos a realizar un pequeño repaso para que te quede muy claro cómo aprovechar al máximo esta herramienta.

> 🌟 *Es importante que hayas instalado previamente esta herramienta. Las instrucciones de instalación las pruedes encontrar por completo en el Prework.*


- [**`Ejemplo 1`**](Ejemplo-01/README.md)

---

### <ins><strong>Variables en Python</strong></ins>

<img src="https://i.imgur.com/6cg2E9Q.png" align="right" width="50%" hspace=10px>

En **Python** usamos <u>variables</u> para asignarles valores que podemos usar después a lo largo de todo nuestro programa.

La sintaxis, para definir variables es la siguiente:

```python
nombre_de_variable = valor
```

`valor` puede llenarse con muchos posibles valores. Ya iremos aprendiendo poco a poco cuáles son estos.


- [**`Ejemplo 2`**](Ejemplo-02/README.md)
- [**`Reto 1`**](Reto-01/README.md)

---

### <ins>Operaciones numéricas</ins>

<img src="https://www.creativefabrica.com/wp-content/uploads/2021/01/07/arithmetic-operator-vector-icon-Graphics-7631157-1.jpg" align="right" width="30%" hspace=10px>


Hemos estado asignando números a variables. En **Python** podemos realizar operaciones matemáticas de una forma muy sencilla. Simplemente tenemos que usar los <u>operadores aritméticos</u> que ya conocemos para hacer operaciones entre las variables que hayamos definido previamente. Los operadores aritméticos en **Python** son los siguientes:

- Suma: `+`
- Resta: `-`
- Multiplicación: `*`
- División: `/`
- Exponente: `**`

¡Practiquemos con ellos!

- [**`Ejemplo 3`**](Ejemplo-03/README.md)
- [**`Reto 2`**](Reto-02/README.md)

---

### <ins>Tipos de datos en Python</ins>

<img src="https://thermomix.com.au/cdn/shop/products/thermomix-themix-shop-spice-jar-labels-food-storage-28905824485553_2048x2048.jpg?v=1628180747" align="right" width="25%" hspace=10px>

Python tiene diferentes tipos de datos para representar diferentes cosas. Por el momento vamos a aprender los 4 básicos y esenciales:

- `int` => números enteros
- `float` => números decimales
- `string` => secuencias de caracteres (texto)
- `boolean` => booleanos (True o False)

Por el momento no importa si no entiendes para qué sirven las cadenas (strings) y los booleanos. Eso lo veremos más adelante.

- [**`Ejemplo 4`**](Ejemplo-04/README.md)

---

### <ins>Interpolación de Strings</ins>

<img src="https://favtutor.com/resources/images/uploads/mceu_73837422811670390560897.jpg" align="right" width="40%" hspace=10px>

Más adelante veremos que las cadenas pueden contener información muy relevante dentro de nuestros conjuntos de datos (como nombres de personas, descripciones de procesos, categorías, etc). Por lo pronto, vamos a utilizar nuestras cadenas para imprimir anotaciones en nuestras salidas. Queremos obtener resultados que se vean más o menos así:

`Suma de variable_1 y variable_2: 10`

Vamos a ver cómo hacer eso.

- [**`Ejemplo 5`**](Ejemplo-05/README.md)
- [**`Reto 3`**](Reto-03/README.md)

---

### <ins>Booleanos y operadores de comparación</ins>

<img src="https://universitylifecafe.k-state.edu/images/bookshelfarticles/truefalseexams.jpg" align="right" width="40%" hspace=10px>

Ya practicamos con enteros, flotantes y cadenas. Sólo nos falta entender para qué usar los booleanos. Nuestros programas necesitan una manera de tomar decisiones. Nosotros en la vida real solemos tomar decisiones haciendo comparaciones entre las opciones y tomando la decisión que más nos convenga tomando en cuenta el contexto. El primer paso para lograr esto son los operadores de comparación. Sirven para comparar valores. Regresan un booleano `True` cuando la comparación es cierta y un booleano `False` cuando la comparación es falsa.

Python tiene los siguientes <u>operadores de comparación</u>:

```python
Mayor que: >
Mayor o igual que: >=
Menor que: <
Menor o igual que: <=
Igual que: ==
No igual (distinto) que: !=
```

Veamos cómo funcionan.

- [**`Ejemplo 6`**](Ejemplo-06/README.md)
- [**`Reto 4`**](Reto-04/README.md)

---

### <ins>Estructuras de control de flujo</ins>

<img src="https://www.programiz.com/sites/tutorial2program/files/python-if.png" align="right" width="50%" hspace=10px>

Para finalizar, vamos a juntar todo lo que hemos aprendido el día de hoy y vamos a darle a nuestro programa la capacidad de tomar decisiones. Los programas tienen datos de entrada (inputs) y datos de salida (outputs). Varían sus salidas dependiendo de las entradas que reciban. Para poder tomar decisiones, utilizan las llamadas estructuras de control de flujo. Que se ven así:

```python
if var_1 > var_2:
    print("OK")
else:
    print("ERROR")
```

Vamos a ver cómo funcionan.

- [**`Ejemplo 7`**](Ejemplo-07/estructuras_de_control_de_flujo.ipynb)
- [**`Reto 5`**](Reto-05/estructuras_de_control_de_flujo.ipynb)

---

### 3. Postwork

[**`Postwork Sesión 1`**](Postwork/Readme.md)
