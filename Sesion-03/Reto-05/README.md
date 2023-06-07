[`Procesamiento de datos con Python`](../../Readme.md) > [`Sesión 03`](../Readme.md) > `Reto 5`

# Reto 5: Lambda

<div style="text-align: justify;">

## 1. Objetivos :dart:

- Practicar la sintaxis y uso de las funciones `lambda` para poder aplicarlas a `filter`

## 2. Requisitos :clipboard:

1. **PyCharm** instalado.

## 3. Desarrollo :rocket:

### Conteo de votos

Eres el líder estudiantil de la H. Universidad Unida de Las Américas (sí, todos los países de América del Norte y América del Sur se han unido en un sólo país llamado Las Américas; ¡yei por la disolución de las fronteras!). Acabas de realizar una votación para decidir el Proyecto Comunitario que realizarán en conjunto todos los estudiantes de la universidad en el próximo año escolar. Las 2 opciones fueron:

1. Ética en Inteligencia Artificial (Código: AI)
1. Cambio Climático (Código: CC)

Los resultados de la votación fueron los siguientes:

```python
votos = ['AI', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'AI', 'CC', 'CC', 'CC', 'AI', 'AI', 'AI'
         , 'CC', 'AI', 'AI', 'CC', 'CC', 'CC', 'AI', 'CC', 'CC', 'AI', 'AI', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC',
         'CC', 'CC', 'CC', 'CC', 'AI', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'AI', 'AI', 'AI', 'CC', 'AI', 'CC', 'CC',
         'CC', 'AI', 'CC', 'AI', 'CC', 'AI', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'AI', 'CC', 'CC', 'CC', 'CC', 'AI',
         'CC', 'CC', 'CC', 'CC', 'CC', 'AI', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'AI', 'AI', 'CC', 'CC', 'CC', 'CC',
         'CC', 'CC', 'CC', 'CC', 'AI', 'CC', 'CC', 'CC', 'CC', 'AI', 'CC', 'AI', 'CC', 'AI', 'CC', 'CC', 'AI', 'AI', 'CC', 'CC',
         'CC', 'AI', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC',
         'CC', 'AI', 'CC', 'AI', 'CC', 'CC', 'CC', 'CC', 'AI', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 
         'AI', 'AI', 'AI', 'AI', 'CC', 'AI', 'CC', 'AI', 'AI', 'CC', 'CC', 'AI', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC',
         'AI', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'AI', 'CC', 'AI', 'CC', 'CC', 'AI', 'CC', 'AI', 'AI',
         'AI', 'CC', 'CC', 'AI', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'AI', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'AI', 'CC',
         'AI', 'AI', 'CC', 'CC', 'CC', 'AI', 'AI', 'AI', 'CC', 'AI', 'CC', 'CC', 'AI', 'CC', 'CC', 'AI', 'AI', 'CC', 'CC', 'CC',
         'CC', 'AI', 'AI', 'CC', 'CC', 'AI', 'AI', 'AI', 'CC', 'AI', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'AI',
         'AI', 'CC', 'CC', 'CC', 'CC', 'AI', 'CC', 'AI', 'AI', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'AI', 'CC', 'AI', 'CC',
         'CC', 'CC', 'CC', 'CC', 'AI', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'AI', 'CC', 'CC', 'CC', 'AI', 'CC',
         'AI', 'CC', 'CC', 'AI', 'AI', 'CC', 'CC', 'AI', 'CC', 'CC', 'CC', 'AI', 'CC', 'CC', 'AI', 'CC', 'AI', 'CC', 'AI', 'CC',
         'AI', 'AI', 'AI', 'CC', 'CC', 'CC', 'CC', 'CC', 'AI', 'CC', 'CC', 'CC', 'AI', 'CC', 'AI', 'CC', 'CC', 'CC', 'AI', 'AI',
         'CC', 'CC', 'CC', 'CC', 'CC', 'AI', 'CC', 'AI', 'AI', 'CC', 'CC', 'CC', 'AI', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC',
         'AI', 'AI', 'AI', 'AI', 'CC', 'CC', 'AI', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'AI', 'AI', 'CC', 'CC', 'CC', 'CC',
         'AI', 'AI', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'CC', 'AI', 'CC', 'CC', 'AI', 'CC', 'CC', 'CC', 'CC', 'AI',
         'CC', 'CC', 'AI', 'CC', 'AI', 'CC', 'CC', 'AI', 'CC', 'AI', 'CC', 'CC', 'CC', 'AI', 'CC', 'CC', 'AI', 'AI', 'CC', 'CC',
         'CC', 'CC', 'CC', 'AI', 'CC', 'CC', 'CC', 'AI', 'CC', 'AI', 'CC', 'CC', 'CC', 'CC', 'CC', 'AI', 'CC', 'CC', 'AI', 'CC',
         'AI', 'CC', 'CC', 'CC', 'AI', 'CC', 'AI']
```

¡Ha llegado el gran momento de contar los votos! Tu reto es el siguiente:

1. Crea una función llamada `voto_por_ai` que regrese `True` si el voto fue "AI".
1. Usa esa función para filtrar tus votos y asigna ese resultado a una variable llamada `votos_por_ai`.
1. Usando esa misma función, utiliza una función `lambda` y el operador `not` para filtrar de nuevo la lista `votos` y obtener una nueva lista llamada `votos_por_cc`.

```python
# Aquí va la función `voto_por_ai`
#
# ...
# ...

votos_por_ai = 

votos_por_cc = 

print(f'== Resultados de la votación para el Proyecto Comunitario 2025 ==\n')
print(f'{("Proyecto"):25}   Conteo')
print(f'---------------------------------------')
print(f'{("- Ética en AI"):25} | {len(votos_por_ai)}')
print(f'{("- Cambio Climático"):25} | {len(votos_por_cc)}')
print(f'---------------------------------------')
print(f'{("- Total"):25} | {len(votos_por_ai) + len(votos_por_cc)}')
```

Ahora sí, ¡listos para emprender el proyecto que cambiará el trayecto de la humanidad para bien!


[`Anterior`](../Readme.md) | [`Siguiente`](../Readme.md)

</div>