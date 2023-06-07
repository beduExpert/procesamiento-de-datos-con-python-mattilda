[`Procesamiento de datos con Python`](../../Readme.md) > [`Sesión 03`](../Readme.md) > `Reto 3`

# Reto 3: And

<div style="text-align: justify;">

## 1. Objetivos :dart:

- Practicar el operador `and` y usarlo para realizar filtros más complejos

## 2. Requisitos :clipboard:

1. **PyCharm** instalado.

## 3. Desarrollo :rocket:

### Filtrando valores atípicos en ambos extremos

Regresemos a nuestro ejemplo de EyePoker Inc. Esta vez tenemos un nuevo conjunto de datos con más empleados (la industria de picadores de ojos va en aumento vertiginoso). Además incluye los sueldos de algunos internos. Estos sueldos son muy bajos (simbólicos, podríamos llamarlos), como puedes ver:

```python
sueldos = [26, 32, 26, 1.5, 30, 30, 1, 2, 32, 28, 30, 28, 30, 28, 27, 30, 110, 1.5, 2, 34, 30, 28, 26, 28, 2, 30, 28, 85, 25, 1.5,
           1.5, 30, 34, 34, 30, 30, 120, 28, 2, 2, 1.5, 28, 120, 1, 1.5, 125, 2, 1.5, 28, 29, 30, 34, 33, 28, 2, 1, 1.5, 26, 28,
          26, 26, 30, 30, 28, 2, 2, 1.5, 2, 1.5, 28, 27, 130, 1.5, 2, 26, 26, 28, 30, 30, 30, 28, 28, 1, 1, 135, 1, 1, 1.5, 2,
          2, 2, 1.5, 2]
```

En realidad a nosotros sólo nos interesa analizar los sueldos de los empleados que tiene la empresa a largo plazo. Como tenemos bastantes internos, es muy probable que la inclusión de estos sueldos vaya a distorsionar nuestro cálculo del sueldo típico en la empresa:

```python
print(f'El sueldo "típico" en EyePoker Inc. es de {sum(sueldos) / len(sueldos)}')
```

Para evitar esta distorsión y calcular solamente el sueldo típico de los empleados que están contratados a largo plazo, vamos a filtrar nuestra lista.

Lo que tienes que hacer es lo siguiente:

1. Define una función que regrese `True` cuando el argumento sea mayor que 20.
1. Define una función que regrese `True` cuando el argumento sea menor que 40.
1. Define una tercera función que una las dos primeras funciones usando un operador `and`.
1. Filtrar la lista y asignarla a `sueldos_filtrados`.

```python
# Aquí va tu primera función
#
# ...
# ...

# Aquí va tu segunda función
#
# ...
# ...

# Aquí va tu tercera función
#
# ...
# ..

sueldos_filtrados =

print(f'El sueldo "típico" en EyePoker Inc. es de {sum(sueldos_filtrados) / len(sueldos_filtrados)}')
```

[`Anterior`](../Readme.md) | [`Siguiente`](../Readme.md)

</div>