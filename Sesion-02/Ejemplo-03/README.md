[`Procesamiento de datos con Python`](../../Readme.md) > [`Sesión 02`](../Readme.md) > `Ejemplo 3`

# Ejemplo 3: Creando y accesando diccionarios

<div style="text-align: justify;">

## 1. Objetivos :dart:

- Aprender a crear diccionarios con pares llaves-valor
- Aprender a acceder a los valores guardados en el diccionario

## 2. Requisitos :clipboard:

1. **PyCharm** instalado.

## 3. Desarrollo :rocket:

Los diccionarios se definen usando llaves ({}):

```python
diccionario_1 = {}
```

¡`diccionario_1` ya es un diccionario! Sólo que está vacío. Para incluir datos dentro de un diccionario, tenemos que agregar pares llave-valor dentro de las llaves ({}). Cada par llave-valor se separa con una coma (,):

```python
diccionario_2 = {
    "llave_1": "valor_1",
    "llave_2": "valor_2",
    "llave_3": "valor_3",
    "llave_4": "valor_4"
}
```

Nuestras llaves pueden ser tanto cadenas como enteros (pueden ser otras cosas, pero estos son los más comunes):

```python
diccionario_3 = {
    1: "Uno",
    2: "Dos",
    3: "Tres",
    4: "Cuatro"
}
```

Nuestros valores pueden ser cualquier tipo de dato que conozcas hasta este momento (e incluso otras cosas que aprenderás después):

```python
diccionario_4 = {
    "int": 123,
    "float": 23.56,
    "string": "Hola",
    "booleano": True,
    "lista": [1, 2, 3, 4],
    "diccionario": {
        1: "uno",
        2: "dos"
    }
}
```

Acceder a un diccionario es tan fácil como escribir el nombre del diccionario, agregar corchetes ([]) y pasarle el nombre de la llave que quieres acceder. Por obvias razones, un diccionario no puede tener más de una llave con el mismo nombre. Si tenemos otras estructuras de datos dentro de nuestro diccionario, podemos acceder a los elementos dentro de ellas después de haber accedido primero a toda la estructura de datos:

```python
print(diccionario_4["float"])
print(diccionario_4["booleano"])
print(diccionario_4["lista"][3])
print(diccionario_4["diccionario"][1])
```

```
23.56
True
4
uno
```

¡Practiquemos ahora un poco más en nuestro tercer Reto de la sesión!

[`Anterior`](../Readme.md) | [`Siguiente`](../Readme.md)

</div>