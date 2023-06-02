[`Procesamiento de datos con Python`](../../Readme.md) > [`Sesión 02`](../Readme.md) > `Reto 2`

# Reto 2: Modificando listas

<div style="text-align: justify;">

## 1. Objetivos :dart:

- Practicar el uso de los métodos `append` `pop`.

## 2. Requisitos :clipboard:

1. **PyCharm** instalado.

## 3. Desarrollo :rocket:

### Modificar para eliminar diferencias

Debajo tienes dos listas definidas:

```python
lista_1 = [3.4, 0.7, 99.9, 5.41, 6.23, 7.9]

lista_2 = [3.4, 63.4, 0.7, 6.46, 99.9, 2.2, 5.41]
```

Ahora tienes una sentencia `if` que utiliza una comparación entre las dos listas.

```python
if lista_1 == lista_2:
    print("Tú y yo somos uno mismo")
```

Modifica la `lista_2` para lograr que ambas listas sean idénticas y el bello mensajes "Tú y yo somos uno mismo" se imprima. Puedes usar tanto `pop` como `append` pero **sólo puedes modificar la `lista_2`**.


### Corrigiendo fragmentos

Debajo hay un muy pequeño fragmento del capítulo 68 de la novela "Rayuela" de Julio Cortázar. Este fragmento ha sido modificado, como fácilmente podrás ver. Además, el fragmento termina con un oración inconclusa:

```python
fragmento_fragmentado = ['Apenas', 'él', 'le', 'amalaba', 'hidrolizado' 'el', 'noema,',
                         'a', 'ella', 'se', 'le', 'agolpaba', 'el', 'clémiso', 'súbito',
                         'y', 'caían', 'en', 'fermales', 'hidromurias,', 'en', 'salvajes', 'ambonios,',
                         'en', 'sustalos', 'distales', 'exasperantes.',
                         'Cada', 'vez', 'que', 'él', 'procuraba', 'relamar', 'las', 'incopelusas,']
```

Debajo hay código que toma la lista de arriba e imprime el fragmento en forma de texto. Tu reto es eliminar todas las modificaciones que han sido hechas al texto de Cortázar usando el método `pop`. Al terminar, puedes, si así lo deseas, agregar tu propio final a la oración inconclusa usando el método `append`.

El resultado será una colaboración tuya y de Cortázar:

```python
tu_nombre = ""  # Tu nombre va aquí

print(f'==Colaboración póstuma de Córtazar y {tu_nombre}==\n')
print(f'{" ".join(fragmento_fragmentado)}')
```


[`Anterior`](../Readme.md) | [`Siguiente`](../Readme.md)

</div>