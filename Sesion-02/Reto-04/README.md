[`Procesamiento de datos con Python`](../../Readme.md) > [`Sesión 02`](../Readme.md) > `Reto 4`

# Reto 4: Modificando diccionarios

<div style="text-align: justify;">

## 1. Objetivos :dart:

- Entender cómo crear diccionarios y cómo acceder a ellos

## 2. Requisitos :clipboard:

1. **PyCharm** instalado.

## 3. Desarrollo :rocket:

### Modificar para eliminar diferencias

Debajo tienes un diccionario que contiene algo de información sobre una persona:

```python
registro = {
    "id": "23f-58j-kju7-54re",
    "nombre": "Alberto",
    "apellido_materno": "Gutierrez",
    "apellido_paterno": "Sosa",
    "profesion": "Contador",
    "ultimo_nivel_de_estudios": "Maestría",
    "lugar_de_estudios": "UAM",
    "numero_de_cuenta": "25367890",
    "nip_de_cajero": "142"
}
```

Ahora, tenemos una serie de impresiones que muestran esta información en forma de tabla:

```python
print(f'Registro con id: {registro["id"]}\n')
print(f'---------------------------------------\n')
print(f'{("Nombre"):25} | {registro["nombre"]:25}')
print(f'{("Apellido Materno"):25} | {registro["apellido_materno"]:25}')
print(f'{("Apellido Paterno"):25} | {registro["apellido_paterno"]:25}')
print(f'{("Profesión"):25} | {registro["profesion"]:25}')
print(f'{("Último nivel de estudios"):25} | {registro["ultimo_nivel_de_estudios"]:25}')
print(f'{("Lugar de estudios"):25} | {registro["lugar_de_estudios"]:25}')
print(f'{("Fecha de nacimiento"):25} | {registro["fecha_de_nacimiento"]:25}')
print(f'{("Lugar de nacimiento"):25} | {registro["lugar_de_nacimiento"]:25}')
```

La actividad tienen 3 partes:

1. Usando la técnica para modificar valores en un diccionario, cambia la información del diccionario para que sea la tuya.
1. Usando la técnica para agregar datos al diccionario agrega las llaves que estén siendo accesadas en el print pero que no han sido agregadas al diccionario.
1. Usando la técnica para eliminar datos del diccionario, elimina los datos sensibles que no quieras que estén incluidos en el diccionario.

Recuerda sólo utilizar métodos y operadores para realizar el ejercicio. **No reescribas el diccionario directamente**.

[`Anterior`](../Readme.md) | [`Siguiente`](../Readme.md)

</div>