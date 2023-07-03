## Ejemplo 1: Conectándose a una base de datos remota

### 1. Objetivos:
    - Usar `mysql-connector-python` para conectarse a una base de datos remota.
 
---
    
### 2. Desarrollo:

#### a) Realizar una conexión y el `cursor`

Para conectarnos necesitamos primero importar la biblioteca:


```python
import mysql.connector
```

Después necesitamos saber la siguiente información acerca de la instancia de MySQL a la que queremos conectarnos:

1. Host
2. Puerto
3. Usuario
4. Contraseña
5. Base de datos a la que queremos conectarnos (recuerda que MySQL **no** es una base de datos, es un Sistema de Gestión de Bases de Datos; es decir, es software que nos ayuda a organizar bases de datos para que sean de fácil acceso)

Todos esos datos los usamos para crear una conexión:


```python
# Llenar esta información con los datos que te compartan los ingenieros de Bedu

cnx = mysql.connector.connect(
    host="",
    port=3306,
    user="",
    password='',
    database='movielens'
)
```

Ahora, para poder realizar lecturas a nuestra base de datos, tenemos que crear un objeto llamado `cursor`:


```python
cursor = cnx.cursor()
```

Éste objeto lo podemos usar para realizar cualquier consulta en lenguaje SQL. Por ejemplo, veamos qué tablas existen en nuestra base de datos:


```python
cursor.execute("SHOW TABLES")
```

Después de ejecutar el comando, tenemos que extraer la información de esta manera:


```python
result = cursor.fetchall()
```


```python
result
```

Listo. Sabemos que tenemos 5 tablas en nuestra base de datos.

Por último, es importante cerrar nuestro `cursor` para no utilizar memoria extra en nuestra computadora:


```python
cursor.close()
```
