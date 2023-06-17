[`Procesamiento de datos con Python`](../../Readme.md) > [`Sesión 05`](../Readme.md) > `Reto 1`

# Reto 1: Funciones vectorizadas

<div style="text-align: justify;">

## 1. Objetivos :dart:

- Practicar el uso de funciones vectorizadas

## 2. Requisitos :clipboard:

1. **PyCharm** instalado.

## 3. Desarrollo :rocket:

### Porcentaje del total

Eres profesor en la H. Universidad de las Américas Unidas. Has realizado el examen final de la primera generación de estudiantes de la escuela. El conteo máximo de aciertos en el examen era de 68 (es decir, 68 aciertos equivale al 100% de las preguntas respondidas correctamente). La siguiente Serie reúne los aciertos obtenidos por los 25 alumnos de la generación:

```python
aciertos = pd.Series([50, 55, 45, 65, 66, 46, 48, 53, 55, 56, 59, 68, 67, 60, 45, 56, 66, 64, 59, 55, 34, 45, 49, 48, 55])
```

Tus calificaciones las das siempre en "porcentaje de aciertos". Tu reto es convertir la Serie aciertos en la Serie porcentajes, que contiene cada valor de aciertos como un porcentaje del número de aciertos totales (68).

**SÓLO**  puedes usar funciones vectorizadas de numpy para realizar tus cálculos. [Aquí puedes encontrar las funciones que necesitas](https://interactivechaos.com/es/manual/tutorial-de-numpy/funciones-universales-matematicas).

```python
## Realiza aquí tus cálculos
##
## ...
## ...

porcentajes =

def obtener_calificaciones(aciertos, porcentajes):
    
    import numpy as np
    
    porcentajes_correcto = np.divide(np.multiply(aciertos, 100), 68)
    if not porcentajes_correcto.equals(porcentajes):
        print(f'Hay algún error en tus cálculos...')
        print(f'¡Por favor intenta de nuevo!')
        return
        
    print(f'== Calificaciones finales ==\n')
    print(f'{("Id del Alumno"):15} | {("Porcentaje de Aciertos"):15}')
    print(f'----------------------------------------')
    for i in range(0, len(porcentajes)):
        print(f'{i:<15} | {np.round(porcentajes[i], 2):<}%')

obtener_calificaciones(aciertos, porcentajes)
```

[`Anterior`](../Readme.md) | [`Siguiente`](../Readme.md)

</div>