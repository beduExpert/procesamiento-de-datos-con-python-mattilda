## Reto 6: Sort

### 1. Objetivos:
    - Practicar el uso de `sort_values` para obtener datos específicos
    
---
    
### 2. Desarrollo:

#### a) Reordenamiento para hallazgo de valores

Vamos a trabajar sobre el dataset que guardaste en la sesión anterior. Tu Reto consiste en lo siguiente:

1. Usa `sort_values` y `loc` para obtener el valor de la velocidad en kilómetros por segundo más lenta de todos los objetos que tenemos en el dataset y asígnalo a `velocidad_en_kilometros_por_segundo_de_objeto_mas_lento`.
2. Usa `sort_values` y `loc` para obtener el valor del diámetro más grande medido que existe en nuestro dataset y asígnalo a `medida_de_diametro_mas_grande`


```python
velocidad_en_kilometros_por_segundo_de_objeto_mas_lento =
medida_de_diametro_mas_grande = 
```


```python
def corroborar_hallazgos(velocidad_en_kilometros_por_segundo_de_objeto_mas_lento, medida_de_diametro_mas_grande):
    
    assert velocidad_en_kilometros_por_segundo_de_objeto_mas_lento == 0.681436673, 'Esa no es la velocidad en kilómetros por segundo del objeto más lento'
    assert medida_de_diametro_mas_grande == 6516.883821679, 'Ese no es el diámetro más grande medido en nuestro dataset'
    
    print('Tus hallazgos son correctos. ¡Bien hecho!')

corroborar_hallazgos(velocidad_en_kilometros_por_segundo_de_objeto_mas_lento, medida_de_diametro_mas_grande)
```
