[`Procesamiento de datos con Python`](../../Readme.md) > [`Sesión 02`](../Readme.md) > `Ejemplo 2`

# Ejemplo 2: Modificando listas

<div style="text-align: justify;">

## 1. Objetivos :dart:

- Conocer los 2 métodos básicos que tenemos para modificar listas

## 2. Requisitos :clipboard:

1. **PyCharm** instalado.

## 3. Desarrollo :rocket:

### Append

`append` agrega un elemento al final de la lista:

```python
lista_1 = [1, 2, 3, 4, 5, 6]

lista_1.append(7)

lista_1
```

```
[1, 2, 3, 4, 5, 6, 7]
```

### Pop

`pop` remueve el último elemento de la lista si lo llamamos sin argumentos. Si le pasamos un índice, remueve el elemento que se encuentre almacenado en ese índice:

```python
lista_2 = [1, 2, 3, 4, 5, 6]

lista_2.pop()

lista_2
```

```
[1, 2, 3, 4, 5]
```

```python
lista_2.pop(1)

lista_2
```

```
[1, 3, 4, 5]
```

¡Practiquemos ahora con un segundo reto!

[`Anterior`](../Readme.md) | [`Siguiente`](../Readme.md)

</div>