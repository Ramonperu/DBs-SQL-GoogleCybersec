# Bases de datos y SQL

Bienvenidos a la introduccion de SQL y base de datos gracias al curso de Google de Ciberseguridad https://www.coursera.org/learn/linux-and-sql/home/week/1 



## Introducción

SQL (Structured Query Language) es un lenguaje estándar utilizado para gestionar y manipular bases de datos relacionales. Su propósito principal es realizar operaciones CRUD (***Crear, Leer, Actualizar, Borrar***) sobre los datos almacenados en una base de datos.

### Conceptos Básicos de SQL

**Tablas**: Son la estructura principal en una base de datos relacional. Una tabla está compuesta por filas y columnas, donde las columnas definen los datos y las filas contienen los registros.

**Consultas**: Las consultas en SQL se utilizan para solicitar datos de una base de datos. La consulta más común es la consulta `SELECT`, que se utiliza para extraer datos.

**Sentencias**: SQL se compone de varias sentencias, entre las más importantes están `SELECT`, `INSERT`, `UPDATE`, `DELETE`.

------

## SQL QUERYS O CONSULTAS 

Las consultas (queries) SQL (Structured Query Language) son comandos que se utilizan para interactuar con bases de datos relacionales. Las consultas SQL permiten realizar una amplia variedad de operaciones como seleccionar, insertar, actualizar y eliminar datos.

------

### Select

*La consulta `SELECT` se utiliza para recuperar datos de una o más tablas. Es la consulta más común y básica.*

***Ejemplo básico:***

```sql
SELECT nombre, edad FROM empleados;
```

*Selecciona las columnas `nombre` y `edad` de la tabla `empleados`.*

------

### Insert

*La consulta `INSERT` se utiliza para agregar nuevas filas a una tabla.*

***Ejemplo básico:***

```sql
INSERT INTO empleados (nombre, edad, puesto) VALUES ('Juan', 35, 'Ingeniero');
```

*Inserta una nueva fila en la tabla `empleados` con los valores especificados.*

------

### Update

*La consulta `UPDATE` se utiliza para modificar datos existentes en una tabla.*

***Ejemplo básico:***

```sql
UPDATE empleados SET edad = 36 WHERE nombre = 'Juan';
```

*Actualiza la edad del empleado llamado Juan a 36 años*

------

### Delete

*La consulta `DELETE` se utiliza para eliminar filas de una tabla.*

***Ejemplo básico:***

```sql
DELETE FROM empleados WHERE nombre = 'Juan';
```

*Elimina de la tabla `empleados` la fila correspondiente al empleado llamado Juan.*

------

### Create

*La consulta `CREATE TABLE` se utiliza para crear una nueva tabla en la base de datos.*

***Ejemplo básico:***

```sql
CREATE TABLE empleados (
    id INT PRIMARY KEY,
    nombre VARCHAR(50),
    edad INT,
    puesto VARCHAR(50)
);
```

*Crea una tabla llamada `empleados` con las columnas `id`, `nombre`, `edad` y `puesto`.*

------

## SQL FILTERS O FILTROS

Los filtros en SQL se utilizan para especificar criterios que determinan qué filas deben ser seleccionadas, actualizadas o eliminadas de una tabla. 

### FILTROS BASICOS CON CLAUSULA WHERE

------

#### Igualdad

***Ejemplo:***

```sql
SELECT * FROM empleados WHERE edad = 30;
```

*Selecciona todas las filas de la tabla `empleados` donde la columna `edad` es igual a 30.*

------

#### Desigualdad

***Ejemplo:***

```sql
SELECT * FROM empleados WHERE edad <> 30;
```

*Selecciona todas las filas donde la columna `edad` no es igual a 30. También se puede usar `!=` para desigualdad.*

------

#### Mayor/Menor Que

***Ejemplo:***

```sql
SELECT * FROM empleados WHERE edad > 30;
```

*Selecciona todas las filas donde la columna `edad` es mayor que 30.*

```sql
SELECT * FROM empleados WHERE edad < 30;
```

*Selecciona todas las filas donde la columna `edad` es menor que 30.*

------

#### Mayor o Igual/Menor o Igual Que

***Ejemplo:***

```sql
SELECT * FROM empleados WHERE edad >= 30;
```

*Selecciona todas las filas donde la columna `edad` es mayor o igual a 30.*

```sql
SELECT * FROM empleados WHERE edad <= 30;
```

*Selecciona todas las filas donde la columna `edad` es menor o igual a 30.*



### FILTROS AVANZADOS

------

####  BETWEEN

*El filtro `BETWEEN` se usa para seleccionar valores dentro de un rango.*

***Ejemplo:***

```sql
SELECT * FROM empleados WHERE edad BETWEEN 25 AND 35;
```

*Selecciona todas las filas donde la columna `edad` está entre 25 y 35, inclusive.*

------

#### IN

*El filtro `IN` se usa para especificar múltiples valores posibles para una columna.*

***Ejemplo:***

```sql
SELECT * FROM empleados WHERE puesto IN ('Ingeniero', 'Analista');
```

*Selecciona todas las filas donde la columna `puesto` es 'Ingeniero' o 'Analista'.*

------

#### LIKE

*El filtro `LIKE` se usa para buscar un patrón en una columna de texto.*

***Ejemplo:***

```sql
SELECT * FROM empleados WHERE nombre LIKE 'J%';
```

*Este filtro selecciona todas las filas donde la columna `nombre` empieza con la letra 'J'.*

```sql
SELECT * FROM empleados WHERE nombre LIKE '%a%';
```

*Este filtro selecciona todas las filas donde la columna `nombre` contiene la letra 'a'.*

------

#### IS NULL / IS NOT NULL

*Estos filtros se usan para buscar valores nulos o no nulos.*

***Ejemplo:***

```sql
SELECT * FROM empleados WHERE salario IS NULL;
```

*Selecciona todas las filas donde la columna `salario` es nula.*

```sql
SELECT * FROM empleados WHERE salario IS NOT NULL;
```

*Selecciona todas las filas donde la columna `salario` no es nula.*



### COMBINACION DE FILTROS

------

#### AND

*El operador `AND` se usa para combinar múltiples condiciones y requiere que todas las condiciones sean verdaderas.*

***Ejemplo:***

```sql
SELECT * FROM empleados WHERE edad > 25 AND puesto = 'Ingeniero';
```

*Selecciona todas las filas donde la columna `edad` es mayor que 25 y la columna `puesto` es 'Ingeniero'.*

------

#### OR

*El operador `OR` se usa para combinar múltiples condiciones y requiere que al menos una de las condiciones sea verdadera.*

***Ejemplo:***

```sql
SELECT * FROM empleados WHERE edad > 25 OR puesto = 'Ingeniero';
```

*Selecciona todas las filas donde la columna `edad` es mayor que 25 o la columna `puesto` es 'Ingeniero'.*

------

#### NOT

*El operador `NOT` se usa para negar una condición.*

***Ejemplo:***

```sql
SELECT * FROM empleados WHERE NOT edad > 25;
```

*Selecciona todas las filas donde la columna `edad` no es mayor que 25.*

------



## JOIN TABLE O TABLAS DE UNION

Las operaciones de `JOIN` en SQL permiten combinar filas de dos o más tablas basadas en una columna relacionada entre ellas.

------

### Inner join

*`INNER JOIN` devuelve las filas que tienen coincidencias en ambas tablas.*

***Ejemplo:***

```sql
SELECT empleados.nombre, departamentos.nombre AS departamento
FROM empleados
INNER JOIN departamentos ON empleados.departamento_id = departamentos.id;
```

*Selecciona los nombres de los empleados y los nombres de sus departamentos correspondientes. Solo se incluyen las filas donde `departamento_id` de `empleados` coincide con `id` de `departamentos`.*

------

### Left join (Left outer join)

*`LEFT JOIN` devuelve todas las filas de la tabla de la izquierda y las filas coincidentes de la tabla de la derecha. Si no hay coincidencia, las filas de la derecha tendrán valores NULL.*

***Ejemplo:***

```sql
SELECT empleados.nombre, departamentos.nombre AS departamento
FROM empleados
LEFT JOIN departamentos ON empleados.departamento_id = departamentos.id;
```

*Selecciona todos los nombres de los empleados y los nombres de sus departamentos correspondientes. Si un empleado no está asignado a un departamento, el nombre del departamento será NULL.*

------

### Right join (Right outer join)

*`RIGHT JOIN` devuelve todas las filas de la tabla de la derecha y las filas coincidentes de la tabla de la izquierda. Si no hay coincidencia, las filas de la izquierda tendrán valores NULL.*

***Ejemplo:***

```sql
SELECT empleados.nombre, departamentos.nombre AS departamento
FROM empleados
RIGHT JOIN departamentos ON empleados.departamento_id = departamentos.id;
```

*Selecciona todos los nombres de los departamentos y los nombres de los empleados asignados. Si un departamento no tiene empleados asignados, el nombre del empleado será NULL.*

------

### Full join (Full outer join)

*`FULL JOIN` devuelve todas las filas cuando hay una coincidencia en una de las tablas. Devuelve NULLs cuando no hay coincidencias en una de las tablas.*

***Ejemplo:***

```sql
SELECT empleados.nombre, departamentos.nombre AS departamento
FROM empleados
FULL JOIN departamentos ON empleados.departamento_id = departamentos.id;
```

*Selecciona todos los nombres de los empleados y los nombres de los departamentos. Incluye filas donde no hay coincidencia en ambas tablas, resultando en valores NULL donde no haya coincidencias.*

------

### Cross join

*`CROSS JOIN` devuelve el producto cartesiano de las dos tablas. Es decir, cada fila de la primera tabla se combina con todas las filas de la segunda tabla.*

***Ejemplo:***

```sql
SELECT empleados.nombre, departamentos.nombre AS departamento
FROM empleados
CROSS JOIN departamentos;
```

*Selecciona todas las combinaciones posibles de empleados y departamentos, lo que resulta en un gran número de filas.*

------

### Self join

*Un `SELF JOIN` es una combinación de una tabla consigo misma. Se utiliza cuando necesitas comparar filas dentro de la misma tabla.*

***Ejemplo:***

```sql
SELECT a.nombre AS empleado1, b.nombre AS empleado2
FROM empleados a, empleados b
WHERE a.jefe_id = b.id;
```

*Selecciona los nombres de empleados y sus jefes correspondientes comparando la tabla `empleados` consigo misma.*
