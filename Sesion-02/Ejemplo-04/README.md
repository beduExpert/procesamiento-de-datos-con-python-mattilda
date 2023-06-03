[`Procesamiento de datos con Python`](../../Readme.md) > [`Sesión 02`](../Readme.md) > `Ejemplo 4`

# Ejemplo 4: Modificando diccionarios

<div style="text-align: justify;">

## 1. Objetivos :dart:

- Practicar los 3 métodos básicos de modificación de diccionarios: agregar datos, modificar datos y borrar llaves.

## 2. Requisitos :clipboard:

1. **PyCharm** instalado.

## 3. Desarrollo :rocket:

Tenemos 3 maneras básicas de modificar nuestros diccionarios:

### Agregar datos

Para agregar un dato a un diccionario ya existente, basta con "llamar" la llave que queremos agregar y asignarle un valor:

```python
from pprint import pprint

info_de_contacto = {
    "nombre": "Isabel",
    "tel": 5546352431,
    "dir": {
        "colonia": "Del Valle Centro",
        "calle": "Pilares",
        "num": 69,
        "cp": "03100"
    }
}

pprint(info_de_contacto)
```

```
{'dir': {'calle': 'Pilares',
         'colonia': 'Del Valle Centro',
         'cp': '03100',
         'num': 69},
 'nombre': 'Isabel',
 'tel': 5546352431}
```

```python
info_de_contacto["email"] = "isabel.arriaga@gmail.com"

pprint(info_de_contacto)
```

```
{'dir': {'calle': 'Pilares',
         'colonia': 'Del Valle Centro',
         'cp': '03100',
         'num': 69},
 'email': 'isabel.arriaga@gmail.com',
 'nombre': 'Isabel',
 'tel': 5546352431}
```

### Modificar pares llave-valor existentes

Para modificar un par llave-valor ya existente, basta con reasignar a una llave de nuestro diccionario el nuevo valor que queremos agregar. Por ejemplo, imaginemos que esta persona cambió de dirección:

```python
info_de_contacto["dir"] = {
        "colonia": "Escandón",
        "calle": "Progreso",
        "num": 189,
        "cp": "11800"
    }

pprint(info_de_contacto)
```

```
{'dir': {'calle': 'Progreso', 'colonia': 'Escandón', 'cp': '11800', 'num': 189},
 'email': 'isabel.arriaga@gmail.com',
 'nombre': 'Isabel',
 'tel': 5546352431}
```

Podemos incluso modificar estructuras de datos dentro de nuestro diccionario. Por ejemplo, ¿qué tal si hubo un error al agregar la nueva dirección y ahora tenemos que cambiar solamente el número de residencia:

```python
info_de_contacto["dir"]["num"] = 289

pprint(info_de_contacto)
```

```
{'dir': {'calle': 'Progreso', 'colonia': 'Escandón', 'cp': '11800', 'num': 289},
 'email': 'isabel.arriaga@gmail.com',
 'nombre': 'Isabel',
 'tel': 5546352431}
```

### Eliminando datos

Para eliminar datos, se puede usar el método `pop`. Como bien recordarás, el nombre de este método es idéntico al método para eliminar elementos de una lista. La diferencia es que el método `pop` de las listas recibe índices como argumentos, el método pop de diccionarios recibe llaves como argumentos:

```
info_de_contacto.pop("tel")

pprint(info_de_contacto)
```

```
{'dir': {'calle': 'Progreso', 'colonia': 'Escandón', 'cp': '11800', 'num': 289},
 'email': 'isabel.arriaga@gmail.com',
 'nombre': 'Isabel'}
```

Vayamos ahora a nuestro cuarto Reto para practicar estas herramientas a profundidad.

[`Anterior`](../Readme.md) | [`Siguiente`](../Readme.md)

</div>