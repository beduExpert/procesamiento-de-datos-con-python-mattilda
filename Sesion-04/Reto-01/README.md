[`Procesamiento de datos con Python`](../../Readme.md) > [`Sesión 04`](../Readme.md) > `Reto 1`

# Reto 1: Series

<div style="text-align: justify;">

## 1. Objetivos :dart:

- Practicar la creación de `Series` y la indexación básica de éstas

## 2. Requisitos :clipboard:

1. **PyCharm** instalado.

## 3. Desarrollo :rocket:

### Creación de series

A continuación tenemos unas variables que contienen los nombres de los ejecutivos más importantes de nuestra ya conocida EyePoker Inc. Debajo de eso hay una variable que no ha sido asignada aún:

```python
ejecutivo_1 = 'Marco P.'
ejecutivo_2 = 'Jenny'
ejecutivo_3 = 'Britney Baby'
ejecutivo_4 = 'Pepe Guardabosques'
ejecutivo_5 = 'Lombardo El Destructor'

sueldos =
```

Tu tarea es crear una serie de Pandas y asignarla a la variable `sueldos`. La información que hay dentro de esta variable son (oh, sorpresa) los sueldos de dichos ejecutivos.

Los valores de la serie serán los sueldos, mientras que el índice de la serie serán los nombres de los ejecutivos.

Crea una serie y asígnala a `sueldos` de manera que el código que tenemos debajo funcione correctamente:

```python
print('== Sueldos de los principales ejecutivos de EyePoker Inc. ==\n')

print(f'{("Ejecutivo"):25} | {("Sueldo")}')
print('----------------------------------------')
print(f'{ejecutivo_1:25} | ${(sueldos.loc[ejecutivo_1])} MXN')
print(f'{ejecutivo_2:25} | ${(sueldos.loc[ejecutivo_2])} MXN')
print(f'{ejecutivo_3:25} | ${(sueldos.loc[ejecutivo_3])} MXN')
print(f'{ejecutivo_4:25} | ${(sueldos.loc[ejecutivo_4])} MXN')
print(f'{ejecutivo_5:25} | ${(sueldos.loc[ejecutivo_5])} MXN')
```

[`Anterior`](../Readme.md) | [`Siguiente`](../Readme.md)

</div>