[`Procesamiento de datos con Python`](../../Readme.md) > [`Sesión 04`](../Readme.md) > `Reto 2`

# Reto 2: Indexación de series

<div style="text-align: justify;">

## 1. Objetivos :dart:

- Practicar técnicas avanzadas de indexación de series

## 2. Requisitos :clipboard:

1. **PyCharm** instalado.

## 3. Desarrollo :rocket:

### Indexación de series

Tenemos una serie que contiene los gastos mensuales totales (en MXN) de distintas divisiones de EyePoker Inc. Tú eres el Contador Oficial y tienes que obtener subconjuntos de datos que sirvan para agregar los gastos totales de diferentes combinaciones de divisiones.

Los datos son los siguientes:

```python
import pandas as pd

gastos_mensuales = {
    'A': 15000,
    'B': 200000,
    'C': 3250000,
    'D': 120000,
    'E': 135000,
    'F': 55000,
    'G': 100000,
    'H': 25000
}

gastos_serie = pd.Series(gastos_mensuales)
gastos_serie

```

El índice es el nombre de la división y los valores son los gastos mensuales en MXN.

Indexando la serie `gastos_serie` extrae las combinaciones de divisiones que se indican debajo para poder hacer los cálculos necesarios.

```python
# Los gastos de la división 'D' y 'G'
gastos_D_G =

# Los gastos de la división 'A' y 'E'
gastos_A_E =

# Los gastos de la división 'B', 'F' y 'H'
gastos_B_F_H =

# Los gastos desde la primera división hasta la división 'E'
gastos_principio_a_E =

# Los gastos desde la división 'D' hasta la 'G'
gastos_D_a_G =

# Los gastos desde la división 'C' hasta el la última división
gastos_C_a_final =

def revisar_indexaciones(gastos_serie, gastos_D_G, gastos_A_E, gastos_B_F_H,
                         gastos_principio_a_E, gastos_D_a_G, gastos_C_a_final):
    
    print(f'== Revisión de Indexaciones ==\n')
    print(f"{'Indexación':30} | {'Resultado':15} | {'Suma esperada ':15} | {'Suma recibida ':15}")
    print("-"*85)
    revisar_indexacion(gastos_serie.loc[['D', 'G']], gastos_D_G, 'División D y G')
    revisar_indexacion(gastos_serie.loc[['A', 'E']], gastos_A_E, 'División A y E')
    revisar_indexacion(gastos_serie.loc[['B', 'F', 'H']], gastos_B_F_H, 'División B, F y H')
    revisar_indexacion(gastos_serie.loc[:'E'], gastos_principio_a_E, 'Desde primera División a E')
    revisar_indexacion(gastos_serie.loc['D':'G'], gastos_D_a_G, 'División D y G')
    revisar_indexacion(gastos_serie.loc['C':], gastos_C_a_final, 'División C a última División')

def formatear_precio(precio):
    return f"${precio} MXN"
    
def revisar_indexacion(esperada, recibida, nombre):
    es_correcta = 'Correcta' if esperada.equals(recibida) else 'Incorrecta'
    suma_esperada = formatear_precio(sum(esperada))
    suma_recibida = formatear_precio(sum(recibida))
    print(f"{nombre:30} | {es_correcta:15} | {suma_esperada:15} | {suma_recibida:15}")

revisar_indexaciones(gastos_serie, gastos_D_G, gastos_A_E, gastos_B_F_H,
                         gastos_principio_a_E, gastos_D_a_G, gastos_C_a_final)
```

[`Anterior`](../Readme.md) | [`Siguiente`](../Readme.md)

</div>