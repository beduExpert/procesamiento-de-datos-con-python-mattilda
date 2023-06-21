## Reto 2: Automatizando con `for loops`

### 1. Objetivos:
    - Automatizar un proceso sencillo usando `for loops`
 
---
    
### 2. Desarrollo:

### a) Potencias de 2

Las potencias de 2 son sumamente importantes en el mundo computacional. Dado que las computadoras trabajan con lenguaje binario, gran parte del funcionamiento interno de las computadoras funciona con potencias de 2. He aquí una pequeña muestra de las primeras potencias de 2:

- 2<sup>0</sup> = 1
- 2<sup>1</sup> = 2
- 2<sup>2</sup> = 4
- 2<sup>3</sup> = 8
- 2<sup>4</sup> = 16
- 2<sup>5</sup> = 32
- 2<sup>6</sup> = 64
- 2<sup>7</sup> = 128
- 2<sup>8</sup> = 256

Tu reto es completar la función `potencia_de_dos`. Esta función recibe el exponente (el número pequeño al lado del 2) y regresa el resultado de 2 elevado a esa potencia. El detalle es que no puedes usar ningún operador o función que compute exponentes (como `**` o `np.power`), sino que tienes que realizar el cálculo utilizando 1 `bloque if` y 1 `for loop`. Completa el código debajo.

> **Nota**: Tu función sólo debe computar exponentes positivos


```python
def potencia_de_dos(exponente):
    
    resultado = 2
    
    ## Tu código va aquí
        
    return resultado
```


```python

def revisar_potencia_de_dos(potencia_de_dos):
    
    import numpy as np
    
    if potencia_de_dos(0) != np.power(2, 0):
        print(f'Error!')
        print(f'Computando 2^0 ... Resultado esperado: {np.power(2, 0)} - Resultado obtenido {potencia_de_dos(0)}')
        return
    
    if potencia_de_dos(2) != np.power(2, 2):
        print(f'Error!')
        print(f'Computando 2^2 ... Resultado esperado: {np.power(2, 2)} - Resultado obtenido {potencia_de_dos(2)}')
        return
    
    if potencia_de_dos(8) != np.power(2, 8):
        print(f'Error!')
        print(f'Computando 2^8 ... Resultado esperado: {np.power(2, 8)} - Resultado obtenido {potencia_de_dos(8)}')
        return
    
    if potencia_de_dos(16) != np.power(2, 16):
        print(f'Error!')
        print(f'Computando 2^16 ... Resultado esperado: {np.power(2, 16)} - Resultado obtenido {potencia_de_dos(16)}')
        return
    
    if potencia_de_dos(56) != np.power(2, 56):
        print(f'Error!')
        print(f'Computando 2^256 ... Resultado esperado: {np.power(2, 256)} - Resultado obtenido {potencia_de_dos(256)}')
        return
        
    print(f'La funcion es correcta!')

revisar_potencia_de_dos(potencia_de_dos)
```


```python

```
