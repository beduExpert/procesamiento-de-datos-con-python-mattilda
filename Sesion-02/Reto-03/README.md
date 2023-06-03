[`Procesamiento de datos con Python`](../../Readme.md) > [`Sesión 02`](../Readme.md) > `Reto 3`

# Reto 3: Creando y accesando diccionarios

<div style="text-align: justify;">

## 1. Objetivos :dart:

- Entender cómo crear diccionarios y cómo acceder a ellos

## 2. Requisitos :clipboard:

1. **PyCharm** instalado.

## 3. Desarrollo :rocket:

### Modificar para eliminar diferencias

Debajo hemos definido un diccionario. Este diccionario se encuentra incompleto, aunque no lo parezca:

```python
ventas_mensuales = {
    "fecha_de_corte": "01/05/2020",
    "unidad": "Aragón",
    # Tu código va aquí
    #...
}
```

Debajo tenemos algunos procedimientos que han sido realizados utilizando este diccionario. Como puedes ver, algunos de los accesos que se están haciendo van a fallar porque el diccionario ventas_mensuales no está completo:

```python
ventas_totales_de_insumos = ventas_mensuales["ventas_pasteleria"] + ventas_mensuales["ventas_panaderia"]
ganancias_totales = ventas_mensuales["ganancias_pasteleria"] + ventas_mensuales["ganancias_panaderia"]
ganancias_netas = ganancias_totales - ventas_mensuales["gastos_mensuales_totales"]

print(f'==Resumen de ventas mensuales de la unidad {ventas_mensuales["unidad"]}==/n')
print(f'Fecha de corte: {ventas_mensuales["fecha_de_corte"]}/n')
print(f'  - Ventas totales de insumos: {ventas_totales_de_insumos}')
print(f'  - Ganancias totales: {ganancias_totales}')
print(f'  - Ganancias netas: {ganancias_netas}')
print(f'\n')
print(f'(Información recabada por: {ventas_mensuales["analista"]})')
```

Completa el diccionario `ventas_mensuales` para que el código que imprime el resumen de las ventas funcione correctamente.


[`Anterior`](../Readme.md) | [`Siguiente`](../Readme.md)

</div>