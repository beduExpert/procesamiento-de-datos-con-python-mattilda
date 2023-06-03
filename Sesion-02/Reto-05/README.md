[`Procesamiento de datos con Python`](../../Readme.md) > [`Sesión 02`](../Readme.md) > `Reto 5`

# Reto 5: Funciones

<div style="text-align: justify;">

## 1. Objetivos :dart:

- Practicar la declaración de funciones
- Practicar la definición de parámetros y su uso dentro de la función
- Practicar el uso de los valores retornados por una función
- Practicar el uso de funciones para evitar la repetición de código

## 2. Requisitos :clipboard:

1. **PyCharm** instalado.

## 3. Desarrollo :rocket:

### Función `numero_es_par`

Debajo tienes una función incompleta:

```python
def numero_es_par(numero):
    
    # Tu código va aquí
    # ...
    # ...
    
    return
```

Dicha función debería de tomar un parámetro `numero`, checar si el número es par, regresar `True` si el número es par y regresar False si el número no es par.

Completa la función para que el código de abajo (que realiza tests de la función) regrese todos los resultados esperados.

> **Pista:** Si no conoces el operador módulo (`%`), pídele al experto que explique su funcionamiento.

> **PD:** Si no entiendes la función `test_funcion` no te preocupes, por el momento sólo está ahí para probar tu código y que sepas si tu función funciona correctamente.

```python
def test_funcion(funcion_a_probar, num_de_errores, contador, parametros=[], resultado_esperado=None):
    resultado_test = funcion_a_probar(*parametros)
    print(f'Test {contador}: Resultado esperado es `{resultado_esperado}`, obtuvimos `{resultado_test}`')
    if resultado_test != resultado_esperado:
        num_de_errores += 1
        
    return num_de_errores
```

```python
print("== Tests numero_es_par==\n")

contador_de_tests = 0
errores = 0

contador_de_tests += 1
errores = test_funcion(numero_es_par, errores, contador_de_tests, parametros=[2], resultado_esperado=True)
contador_de_tests += 1
errores = test_funcion(numero_es_par, errores, contador_de_tests, parametros=[3], resultado_esperado=False)
contador_de_tests += 1
errores = test_funcion(numero_es_par, errores, contador_de_tests, parametros=[0], resultado_esperado=True)
contador_de_tests += 1
errores = test_funcion(numero_es_par, errores, contador_de_tests, parametros=[127], resultado_esperado=False)
contador_de_tests += 1
errores = test_funcion(numero_es_par, errores, contador_de_tests, parametros=[-88], resultado_esperado=True)
contador_de_tests += 1
errores = test_funcion(numero_es_par, errores, contador_de_tests, parametros=[-1349], resultado_esperado=False)

print(f'\nErrores encontrados: {errores}')
```

### Reutilización de código 

Debajo tenemos algo de código

```python
resultado_1 = 34 * 100 / 100
print(f'34 es el {resultado_1}% del número 100\n')

resultado_2 = 57 * 100 / 127
print(f'57 es el {resultado_2}% del número 127\n')

resultado_3 = 12 * 100 / 228
print(f'12 es el {resultado_3}% del número 228\n')

resultado_4 = 87 * 100 / 90
print(f'87 es el {resultado_4}% del número 90\n')

resultado_5 = 1 * 100 / 999
print(f'1 es el {resultado_5}% del número 999\n')

resultado_6 = 66 * 100 / 66
print(f'66 es el {resultado_6}% del número 66\n')
```

Este código funciona correctamente, pero como puedes ver, estamos escribiendo el mismo código una y otra vez. En la celda debajo, escribe una función que realice la operación matemática que estamos realizando arriba, para que podamos reusarla múltiples veces para obtener los resultados que queremos. Llena también los prints de manera que podamos leer el resultado en un formato comprensible.

> *Reto extra: Si quieres un reto extra, escribe también una función que genere las strings que vamos a pasar a los prints, para no tener que escribirlas desde 0 cada vez.*

```python
resultado_1 = 
print(f'')

resultado_2 = 
print(f'')

resultado_3 = 
print(f'')

resultado_4 = 
print(f'')

resultado_5 = 
print(f'')

resultado_6 = 
print(f'')
```

### Función `acceso_autorizado`

Debajo tenemos un conjunto de datos que tiene información de varios usuarios de una plataforma web. Este diccionario relaciona `usernames` con un rol y (a veces) con un nip de acceso:

```python
usuarios = {
    "manolito_garcia": {
        "rol": "admin"
    },
    "sebas_macaco_23": {
        "rol": "editor",
        "nip_de_acceso": 3594
    },
    "la_susanita_maestra": {
        "rol": "admin"
    },
    "pepe_le_pu_88": {
        "rol": "lector"
    },
    "jonny_bravo_estuvo_aqui": {
        "rol": "editor",
        "nip_de_acceso": 9730
    },
    "alfonso_torres_69": {
        "rol": "editor",
        "nip_de_acceso": 2849
    },
    "jocosita_99": {
        "rol": "lector"
    }
}
```

Nuestra plataforma tiene 3 roles:

1. Admin: estos pueden editar información sin necesitar un nip de acceso.
1. Editor: pueden editar información sólo si escriben correctamenta su nip de acceso.
1. Lector: no pueden editar, sólo ver la información, no necesitan nip de acceso.

En la celda debajo, crea una función llamada `nivel_de_acceso_para_username` que reciba 3 parámetros:

1. `base_de_datos`: que será siempre nuestro diccionario usuarios.
1. `username`: El username del usuario que está solicitando acceso.
1. `nip_de_acceso`: El nip de acceso, que puede ser None en el caso de que el usuario no tenga uno (o que haya olvidado escribirlo a la hora de pedir acceso.

Con estos 3 parámetros, nuestra función tiene que regresar uno de los códigos de acceso siguientes:

0: Acceso denegado (esto sucede si el rol es editor y el nip_de_acceso es incorrecto).
1: Modo edición autorizada (esto sucede si el rol es admin o si el rol es editor y el nip_de_acesso es correcto).
2: Modo lectura autorizada (esto sucede si el rol es lector).

Después, corre los tests para asegurarte de que tu función es correcta.

> Tip: Recuerda que puedes "anidar" sentencias if dentro de otras sentencias if.

> Reto extra: Agrega un chequeo que regrese 0 si el username que recibió tu función no existe en la base de datos.

```python
print("== Tests nivel_de_acceso_para_username==\n")

contador_de_tests = 0
errores = 0

contador_de_tests += 1
errores = test_funcion(nivel_de_acceso_para_username, errores, contador_de_tests,
                       parametros=[usuarios, "manolito_garcia", None], resultado_esperado=1)
contador_de_tests += 1
errores = test_funcion(nivel_de_acceso_para_username, errores, contador_de_tests,
                       parametros=[usuarios, "sebas_macaco_23", 3594], resultado_esperado=1)
contador_de_tests += 1
errores = test_funcion(nivel_de_acceso_para_username, errores, contador_de_tests,
                       parametros=[usuarios, "jonny_bravo_estuvo_aqui", 9999], resultado_esperado=0)
contador_de_tests += 1
errores = test_funcion(nivel_de_acceso_para_username, errores, contador_de_tests,
                       parametros=[usuarios, "pepe_le_pu_88", None], resultado_esperado=2)
contador_de_tests += 1
errores = test_funcion(nivel_de_acceso_para_username, errores, contador_de_tests, 
                       parametros=[usuarios, "alfonso_torres_69", None], resultado_esperado=0)

# Corre el siguiente código sólo si decidiste realizar el reto extra
#
# contador_de_tests += 1
# errores = test_funcion(nivel_de_acceso_para_username, errores, contador_de_tests,
#                        parametros=[usuarios, "los_yeah_yeahs_97", 1345], resultado_esperado=0)

print(f'\nErrores encontrados: {errores}')
```


[`Anterior`](../Readme.md) | [`Siguiente`](../Readme.md)

</div>