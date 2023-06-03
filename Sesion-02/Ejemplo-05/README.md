[`Procesamiento de datos con Python`](../../Readme.md) > [`Sesión 02`](../Readme.md) > `Ejemplo 5`

# Ejemplo 5: Funciones

<div style="text-align: justify;">

## 1. Objetivos :dart:

- Entender la sintaxis de las funciones
- Aprender cómo pasarle parámetros a las funciones
- Entender cómo aprovechar los valores que regresa el `return`
- Entender el concepto de contexto y cómo las variables definidas dentro de la función sólo pueden ser accedidas dentro de la función

## 2. Requisitos :clipboard:

1. **PyCharm** instalado.

## 3. Desarrollo :rocket:

Queremos hacer funciones porque queremos evitar repetir código en nuestro programa. En vez de escribir 10 veces el mismo proceso en diferentes lugares de nuestro código, podemos escribir una función que contenga ese proceso y simplemente usarla en los 10 lugares donde suceda ese proceso.

### Sintaxis

Una función se ve así:

```python
def multiplicar_numero_por_pi(numero):
    resultado = numero * 3.14
    
    return resultado
```

Es muy importante notar lo siguiente:

- La declaración comienza con la palabra `def`.
- El nombre de la función sigue las mismas convenciones de nombramiento que las variables (snake_case).
- Los parámetros de la función van dentro del paréntesis.
- Hay unos dos puntos (:) después del paréntesis que indican el inicio del bloque de la función
- El bloque de la función (todos los procesos que se van a llevar a cabo cuando llamemos la función) deben de estar indentados. Lo que está indentado es parte de la función. En cuanto hay una línea que no esté indentada, eso indica que la definición de la función ha terminado.
- Las funciones tienen una sentencia `return` que regresa el resultado de nuestro proceso para que pueda ser utilizado en otras partes de nuestro programa.

### Parámetros

Los parámetros de una función son los nombres de los valores que le pasamos a la función cada vez que la llamamos. La función utiliza estos parámetros para realizar sus procesos. Estos parámetros son los ingredientes necesarios para que la función lleve a cabo su proceso. Sin parámetros, las funciones harían siempre lo mismo:

```python
def esta_funcion_hace_siempre_lo_mismo():
    
    resultado = 2 * 10
    
    return resultado

print(esta_funcion_hace_siempre_lo_mismo())
print(esta_funcion_hace_siempre_lo_mismo())
print(esta_funcion_hace_siempre_lo_mismo())
```

```
20
20
20
```

Vamos a modificar esta función para que el resultado sea distino dependiendo del valor que le pasemos:

```python
def esta_funcion_multiplica_el_argumento_por_10_y_lo_regresa(parametro):
    
    resultado = parametro * 10
    
    return resultado

print(esta_funcion_multiplica_el_argumento_por_10_y_lo_regresa(4))
print(esta_funcion_multiplica_el_argumento_por_10_y_lo_regresa(10))
print(esta_funcion_multiplica_el_argumento_por_10_y_lo_regresa(66))
```

```
40
100
660
```

Ahora nuestra función tiene mucha más utilidad, ya que es flexible. Tal vez habrás notado que en el nombre de la función usé la palabra argumento en vez de parámetro. Es un poco confuso pero los parámetros son los nombres que se definen para ser utilizados dentro de la función, mientras que los argumentos son los valores que le pasamos a la función cuando la llamamos.

Podemos definir más de un parámetro por función (en realidad el número es ilimitado), pero la mejor práctica es mantener el número de parámetros lo más pequeño posible. Entre menos parámetros usemos, mejor está pensada nuestra función.

Veamos una función con dos parámetros:

```python
def agregar_numero_a_lista_si_el_numero_es_par(lista, numero):
    
    if numero % 2 == 0:
        lista.append(numero)
        
    return lista

lista_de_ints = [2, 34, 26, 88, 4]

lista_de_ints = agregar_numero_a_lista_si_el_numero_es_par(lista_de_ints, 5)
lista_de_ints = agregar_numero_a_lista_si_el_numero_es_par(lista_de_ints, 66)

lista_de_ints
```

```
[2, 34, 26, 88, 4, 66]
```

Esta función recibe una lista y un número, checa si el número es par, y si es par agrega el número a la lista. Finalmente, regresa la lista (que puede estar modificada o no). Como puedes observar, podemos reasignar variables una y otra vez. Cada vez que obtenemos la lista modificada (o no) de la función `agregar_numero_a_lista_si_el_numero_es_par`, la reasignamos a `lista_de_ints` para tener la lisa actualizada.

### Return

Todas las funciones que hemos definido hasta ahora tienen al final una sentencia `return`. Dicha sentencia regresa el valor que escribimos a su derecha, que normalmente es el resultado del proceso que hemos realizado dentro de la función.

Si no hubiera `return`, los procesos que suceden dentro de nuestras funciones se quedarían ahí y no podríamos acceder a los resultados. Eso no sería muy útil que digamos, ¿no es así?

El valor que regresa nuestro `return` lo podemos guardar en otra variable para usarlo en el futuro o podemos imprimirlo directamente usando un `print` (aunque es recomendable mejor primero asignarlo a una variable y después imprimir la variable):

```python
def regresa_true_si_el_valor_esta_entre_50_y_60(valor):
    
    if valor > 50:
        if valor < 60:
            return True
    
    return False

resultado_1 = regresa_true_si_el_valor_esta_entre_50_y_60(58)
resultado_2 = regresa_true_si_el_valor_esta_entre_50_y_60(89)

if resultado_1 == True:
    print("El primer valor es mayor a 50 y menor a 60")

if resultado_2 == True:
    print("El segundo valor es mayor a 50 y menor a 60")
```

```
El primer valor es mayor a 50 y menor a 60
```

En esta función checamos primero si un valor es mayor a 50 (`valor > 50`). Si lo es, checamos ahora que sea menor a 60 (`valor < 60`). Si también lo es, quiere decir que el valor está entre 50 y 60 y la función regresa True. Si las condiciones no se cumplen, la función regresa False. Los resultado de llamar a las función con los valores 58 y 89 son guardados en variables, que después se utilizan en una nueva condición que determina si una cadena deberá imprimirse o no.

¿Puedes ver el potencial de esto?

### Contexto de una variable

Para terminar, es importante recordar algo que vimos en el Prework: Las variables definidas dentro de una función (ya sean parámetros o variables asignadas dentro de la función) **sólo pueden ser accedidas dentro de la función**. Una vez que la función termina, las variables desaparecen y no son accesibles desde ninguna parte de nuestro código.

Es por eso que este código lanza un error:

```python
def si_los_valores_son_iguales_regresa_exito(valor_1, valor_2):
    
    if valor_1 == valor_2:
        return "Éxito"
    else:
        return "Error"
    
resultado = si_los_valores_son_iguales_regresa_exito(4, 4)

print(valor_1)
```

También es por eso que el siguiente código lanza error:

```python
def suma_42_a_numero(numero):
    
    suma = numero + 42
    
    return suma

resultado = suma_42_a_numero(34)

print(suma)
```

El parámetro `valor_1` en la primera función y la variable `suma` de la segunda función sólo pueden ser usadas dentro de la función. Si intentamos usarlas fuera de la función, Python se encargará de recordarnos que eso no se puede hacer con un bonito error.

Pasemos ahora a lo emocionante. Vamos a definir unas cuantas funciones para dominar esta nueva herramienta tan útil.

[`Anterior`](../Readme.md) | [`Siguiente`](../Readme.md)

</div>