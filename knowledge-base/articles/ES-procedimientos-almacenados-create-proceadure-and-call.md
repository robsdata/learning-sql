
# **DISPARADORES Y PROCEDIMIENTOS**
---

* Identificar diferentes modalidades que posee el SQL para mejorar el acceso a la información almacenada en la base de datos.

* Conocer otras formas de tratamiento de datos por medio de objetos almacenados en la base de datos.


## **FUNCIONES**
* Funciones de fila única
* Funciones de agrupación

La diferencia fundamental es que mientras las primeras realizan la acción sobre una única fila cada vez, las de agrupación obtienen un resultado a partir de un conjunto de elementos. Se trata de seleccionar un conjunto de elementos, filtrarlos por las condiciones que creamos oportunas y obtener un resultado a partir de él.

## **FUNCIONES DE FILA UNICA**
Estas funciones operan solo en una única fila y retorna un valor por cada una. Hay diferentes tipos de funciones de fila única:

* Carácter
* Numérica
* Fecha
* Conversión
* General

Las funciones de fila única son usadas para **manipular elementos de datos**. Ellas **aceptan uno o más argumentos y retorna un valor por cada fila** que es retornada por la consulta. Un argumento puede ser alguno de los siguientes:

* Constantes.
* Valores variables.
* Nombres de columnas.
* Expresiones.

Algunas características de funciones de fila única son:

* Actúan por cada fila retornada por la consulta.
* Retornan un valor por cada fila.
* Posibilitan el retorno de un valor de dato de un tipo diferente de que es originalmente referenciado.
* Posibilidad de esperar uno o más argumentos.
* Pueden ser usadas en las cláusulas SELECT, WHERE y ORDER BY; pueden ser anidadas.

En el caso de las funciones de fila única, cada sistema gestor de base de datos proporciona sus propias funciones. Por ello, se recomienda buscar en la documentación técnica de cada gestor de base de datos, las funciones existentes para el tratamiento de cadenas, fechas, etc.

Cuando trabajas con MySQL y deseas obtener resultados de una consulta que devuelvan una sola fila, generalmente utilizas funciones que extraen esa fila. Estas funciones dependen del lenguaje de programación que estés utilizando para interactuar con MySQL. A continuación, te mostraré ejemplos de cómo obtener una fila única en diferentes lenguajes de programación:

Python (usando pymysql):
``` python

import pymysql

conexion = pymysql.connect(host="hostname", user="usuario", password="contraseña", database="nombre_base_de_datos")

consulta = "SELECT columna1, columna2 FROM tabla WHERE condicion = valor"
with conexion.cursor() as cursor:
    cursor.execute(consulta)
    fila = cursor.fetchone()

    if fila:
        columna1, columna2 = fila
        # Realiza operaciones con los datos
    else:
        print("No se encontraron resultados.")

conexion.close()
```

**Explicación paso a paso:**

**Importar el módulo pymysql**: En la primera línea, importamos el módulo pymysql, que proporciona funcionalidad para conectarse y trabajar con bases de datos MySQL desde Python.

**Establecer la conexión**: Utilizamos la función connect de pymysql para establecer una conexión a la base de datos MySQL. Debes proporcionar la información de la base de datos, como:

* Nombre del host
* Nombre de usuario
* Nontraseña 
* Nombre de la base de datos a la que deseas conectarte. 

Asegúrate de reemplazar "hostname", "usuario", "contraseña" y "nombre_base_de_datos" con los valores correctos.

**Definir la consulta SQL**: Creamos una cadena llamada consulta que contiene la consulta SQL que deseamos ejecutar. En este caso, estamos seleccionando las columnas columna1 y columna2 de la tabla tabla donde se cumple una cierta condición.

**Ejecutar la consulta**: Usamos un bloque with para crear un cursor de base de datos llamado cursor. Luego, ejecutamos la consulta SQL utilizando el método execute del cursor.

**Obtener la fila de resultados**: Utilizamos el método fetchone del cursor para obtener la primera fila de resultados de la consulta. Si la consulta devuelve resultados, la fila se almacena en la variable fila.

**Procesar los resultados:** Verificamos si se obtuvo una fila (if fila:) y, si es así, desempaquetamos los valores de las columnas en las variables columna1 y columna2. Puedes realizar operaciones con estos datos en este punto.

**Cerrar la conexión:** Finalmente, cerramos la conexión a la base de datos utilizando el método close en la variable conexion.

Este código se encarga de conectar a la base de datos, ejecutar la consulta SQL y procesar los resultados de una manera segura y eficiente. Asegúrate de reemplazar los valores de conexión y la consulta SQL con los correspondientes a tu base de datos y necesidades específicas.

Aquí tienes una lista de algunas funciones comunes de MySQL que puedes utilizar para obtener resultados de una sola fila en una consulta:

**SELECT**: La declaración SELECT te permite recuperar columnas específicas de una tabla o una expresión calculada. Puedes usar la cláusula WHERE para filtrar resultados y LIMIT para limitar el número de filas devueltas.

``` sql
SELECT columna1, columna2 FROM tabla WHERE condicion = valor LIMIT 1;

```

**COUNT**(): La función COUNT() cuenta el número de filas que cumplen con una condición específica.

``` sql
SELECT COUNT(*) FROM tabla WHERE condicion = valor;

```

**SUM**(): La función SUM() calcula la suma de los valores de una columna numérica.
``` sql
SELECT SUM(columna) FROM tabla WHERE condicion = valor;

```

**AVG**(): La función AVG() calcula el promedio de los valores de una columna numérica.
``` sql
SELECT AVG(columna) FROM tabla WHERE condicion = valor;

```

**MAX**(): La función MAX() devuelve el valor máximo de una columna.
``` sql
SELECT MAX(columna) FROM tabla WHERE condicion = valor;

```

**MIN**(): La función MIN() devuelve el valor mínimo de una columna.
``` sql
SELECT MIN(columna) FROM tabla WHERE condicion = valor;

```

**CONCAT**(): La función CONCAT() se utiliza para concatenar valores de columna o cadenas de texto.
``` sql
SELECT CONCAT(columna1, ' ', columna2) FROM tabla WHERE condicion = valor;

```

**DATE_FORMAT**(): La función DATE_FORMAT() se usa para formatear fechas según un patrón específico.
``` sql
SELECT DATE_FORMAT(fecha, '%Y-%m-%d') FROM tabla WHERE condicion = valor;

```


**NOW**(): La función NOW() devuelve la fecha y hora actuales.
``` sql
SELECT NOW() AS fecha_actual;

```

**IFNULL**() o **COALESCE**(): Estas funciones se utilizan para manejar valores nulos en las consultas y devolver un valor predeterminado si una columna es nula.
``` sql
SELECT IFNULL(columna, 'Valor predeterminado') FROM tabla WHERE condicion = valor;

```
Estas son solo algunas de las funciones de fila única que puedes utilizar en MySQL para realizar consultas y obtener resultados específicos. Puedes combinar estas funciones según tus necesidades para realizar cálculos y formatear datos de acuerdo a tus requerimientos.

## FUNCIONES ALMACENADAS
Las funciones almacenadas, también conocidas como procedimientos almacenados, son bloques de código SQL que se almacenan en la base de datos y se pueden invocar y reutilizar en múltiples consultas. Estas funciones permiten encapsular lógica de negocio, mejorar la seguridad y reutilizar código en aplicaciones y sistemas de bases de datos. A continuación, se describen los conceptos clave y se proporciona un ejemplo de función almacenada en MySQL:

**Conceptos clave de las funciones almacenadas:**

* **Procedimiento Almacenado**: Es un conjunto de sentencias SQL que se almacenan en la base de datos y se pueden invocar mediante un nombre.

* **Función Almacenada**: Es similar a un procedimiento almacenado, pero devuelve un valor y se puede utilizar en expresiones SQL.

* **Parámetros**: Las funciones almacenadas pueden recibir parámetros de entrada que se utilizan en el cuerpo de la función.

* **Variables Locales**: Puedes declarar y utilizar variables locales dentro de una función almacenada.

* **Sentencias de Control**: Las funciones almacenadas admiten sentencias de control de flujo como IF, CASE, WHILE, etc.

* **Reutilización de Código**: Las funciones almacenadas permiten reutilizar código de manera eficiente en múltiples lugares dentro de una base de datos.

**Ejemplo de una función almacenada en MySQL:**
Supongamos que tenemos una base de datos que almacena información de empleados y queremos crear una función almacenada para calcular el salario anual de un empleado en función de su salario mensual y el número de meses trabajados en el año. Aquí está un ejemplo de cómo podría ser la función almacenada en MySQL:

``` sql
DELIMITER //

CREATE FUNCTION CalcularSalarioAnual(salarioMensual DECIMAL(10, 2), mesesTrabajados INT)
RETURNS DECIMAL(10, 2)
BEGIN
    DECLARE salarioAnual DECIMAL(10, 2);
    
    IF mesesTrabajados < 12 THEN
        SET salarioAnual = salarioMensual * mesesTrabajados;
    ELSE
        SET salarioAnual = salarioMensual * 12;
    END IF;

    RETURN salarioAnual;
END //

DELIMITER ;

```
En este ejemplo:

* Hemos creado una función llamada CalcularSalarioAnual.
* La función toma dos parámetros de entrada: salarioMensual y mesesTrabajados.
* Declaramos una variable local llamada salarioAnual para almacenar el resultado.
* Utilizamos una sentencia IF para calcular el salario anual en función de los meses trabajados y el salario mensual.
* Finalmente, la función devuelve el salario anual calculado.

Una vez creada esta función almacenada, puedes invocarla en consultas SQL como si fuera una columna o valor calculado:

```sql
SELECT nombre, CalcularSalarioAnual(salarioMensual, 9) AS salario_anual
FROM empleados
WHERE departamento = 'Ventas';

```

Esta es una forma básica de cómo se crea y utiliza una función almacenada en MySQL. Las funciones almacenadas pueden volverse mucho más complejas según las necesidades de tu aplicación y pueden proporcionar un alto grado de modularidad y reutilización de código en tu base de datos.

**Sintaxis para la creacion de una funcion almacenada**

```sql
CREATE OR REPLACE FUNCTION nombre_de_funcion (prametro1, prametro2, prametrox)
RETURNS tipo
/* CHAR/INT/FLOAT/DECIMAL/etc. */
BEGIN
........
RETURN valor
END

```

El uso de OR REPLACE permite sobrescribir una función existente. Si se omite, y la función existe, se producirá, un error.

La sintaxis de los parámetros es la misma que en los procedimientos almacenados, exceptuando que solo pueden ser de entrada.

La orden RETURN dentro de una función devuelve el valor que la función debe devolver, el cual se convierte al tipo especificado en la cabecera de la función. Puede haber más de una instrucción RETURN, pero solo se ejecutará la primera que se encuentre dentro de la lógica del programa.

Ejemplo de creación de una función almacenada:

```sql
DELIMETER //
CREATE FUNCTION holaMundo()
RETURNS VARCHAR(20)
BEGIN
RETIRN 'Hola Mundo';
END
//
DELIMETER;


```

## USO DE FUNCIONES AVANZADAS

### SUB CONSULTA

Las subconsultas, también conocidas como consultas anidadas o consultas subordinadas, son consultas SQL que se incluyen dentro de una consulta principal. Se utilizan para realizar una operación de consulta más compleja al incorporar los resultados de una consulta interna en la consulta externa. Las subconsultas pueden aparecer en diversas partes de una consulta, como la cláusula SELECT, la cláusula FROM, la cláusula WHERE o la cláusula HAVING.

Aquí tienes ejemplos de cómo se utilizan las subconsultas en consultas SQL:

**Subconsulta en la cláusula WHERE:** Una subconsulta en la cláusula WHERE se utiliza para filtrar resultados en función de los resultados de otra consulta. Por ejemplo, puedes usar una subconsulta para seleccionar todos los empleados cuyos salarios sean mayores que el salario promedio de la empresa.

```sql
SELECT nombre, salario
FROM empleados
WHERE salario > (SELECT AVG(salario) FROM empleados);

```


**Subconsulta en la cláusula SELECT:** Una subconsulta en la cláusula SELECT se utiliza para obtener un valor calculado basado en los resultados de otra consulta. Por ejemplo, puedes usar una subconsulta para mostrar el salario máximo de la empresa junto con cada empleado.

```sql
SELECT nombre, salario, (SELECT MAX(salario) FROM empleados) AS salario_maximo
FROM empleados;

```


**Subconsulta en la cláusula FROM:** Puedes utilizar una subconsulta en la cláusula FROM para crear una tabla virtual que luego se utiliza en la consulta principal. Esto puede ser útil cuando deseas realizar operaciones más complejas antes de consultar los datos.

```sql
SELECT departamento, AVG(salario) AS salario_promedio
FROM (SELECT departamento, salario FROM empleados WHERE salario > 50000) AS empleados_filtrados
GROUP BY departamento;

```


**Subconsulta en la cláusula HAVING:** Las subconsultas también se pueden utilizar en la cláusula HAVING para filtrar los resultados después de haberse agrupado utilizando GROUP BY.

```sql
SELECT departamento, AVG(salario) AS salario_promedio
FROM empleados
GROUP BY departamento
HAVING AVG(salario) > (SELECT AVG(salario) FROM empleados);

```


**Subconsulta correlacionada:** Una subconsulta correlacionada es una subconsulta que referencia una columna de la consulta principal en su condición. Se ejecuta para cada fila de la consulta principal y puede utilizar valores de esa fila en la subconsulta. Por ejemplo, puedes usar una subconsulta correlacionada para encontrar empleados con salarios superiores al salario promedio de su departamento.

```sql
SELECT nombre, salario, departamento
FROM empleados e
WHERE salario > (SELECT AVG(salario) FROM empleados WHERE departamento = e.departamento);

```

### REFERENCIAS EXTERNAS


En SQL, una subconsulta es una consulta que se incluye dentro del cuerpo de otra consulta, conocida como la "consulta principal". La subconsulta generalmente se utiliza para proporcionar datos o realizar cálculos específicos que ayudan a la consulta principal a tomar decisiones más informadas o a obtener resultados más precisos.

Ahora, cuando hablamos de "referencias externas" en una subconsulta, nos referimos al hecho de que la subconsulta puede necesitar acceder a datos de la consulta principal para funcionar correctamente. Es decir, dentro de la subconsulta, puedes hacer referencia a valores de columnas que pertenecen a la tabla o tablas mencionadas en la consulta principal. Estos valores de columna se denominan "referencias externas" porque **provienen de una fuente externa a la subconsulta, que es la consulta principal.**

Por ejemplo, supongamos que tienes una consulta principal que selecciona información de empleados y una subconsulta que se utiliza para calcular algún valor basado en datos de empleados, como el salario promedio de los empleados en el mismo departamento. Dentro de la subconsulta, es posible que necesites hacer referencia a la columna del "departamento" de la fila actual de la consulta principal. Esta referencia al valor del "departamento" es una "referencia externa" porque proviene de la consulta principal.

Cuando ejecutas una consulta que contiene una subconsulta con referencias externas, la subconsulta se ejecuta una vez por cada fila en la consulta principal. Esto significa que la subconsulta se adapta a los valores específicos de la fila actual de la consulta principal en cada iteración, permitiendo que se realicen cálculos o se obtengan datos basados en las referencias externas.

En resumen, las referencias externas en subconsultas permiten que las subconsultas accedan a valores de columnas de la consulta principal, lo que puede ser esencial para realizar cálculos o tomar decisiones en el contexto de la consulta principal.

Aquí tienes un ejemplo práctico de una consulta SQL que utiliza una subconsulta con referencias externas. Supongamos que tenemos dos tablas: una tabla llamada empleados que contiene información sobre los empleados y otra tabla llamada departamentos que almacena información sobre los departamentos a los que pertenecen los empleados. Queremos encontrar el salario promedio de los empleados en cada departamento y mostrar los departamentos con salarios promedio superiores al salario promedio general de la empresa:

#### EJEMPLO 1

```sql
-- Crear la tabla de empleados
CREATE TABLE empleados (
    id INT PRIMARY KEY,
    nombre VARCHAR(50),
    salario DECIMAL(10, 2),
    departamento_id INT
);

-- Insertar datos de ejemplo en la tabla de empleados
INSERT INTO empleados (id, nombre, salario, departamento_id)
VALUES
    (1, 'Juan', 50000.00, 1),
    (2, 'Ana', 60000.00, 1),
    (3, 'Carlos', 55000.00, 2),
    (4, 'María', 62000.00, 2),
    (5, 'Pedro', 48000.00, 3);

-- Crear la tabla de departamentos
CREATE TABLE departamentos (
    id INT PRIMARY KEY,
    nombre VARCHAR(50)
);

-- Insertar datos de ejemplo en la tabla de departamentos
INSERT INTO departamentos (id, nombre)
VALUES
    (1, 'Ventas'),
    (2, 'Desarrollo'),
    (3, 'Marketing');

```

Ahora, podemos escribir una consulta SQL que utilice una subconsulta con referencias externas para calcular el salario promedio de cada departamento y luego compararlo con el salario promedio general de la empresa:


```sql
SELECT 
    d.nombre AS departamento,
    AVG(e.salario) AS salario_promedio_departamento
FROM 
    departamentos d
JOIN 
    empleados e ON d.id = e.departamento_id
GROUP BY 
    d.id, d.nombre
HAVING 
    AVG(e.salario) > (SELECT AVG(salario) FROM empleados);

```

**Esta consulta hace lo siguiente:**

* Selecciona el nombre del departamento (d.nombre) y el salario promedio de los empleados en ese departamento (AVG(e.salario)).
* Utiliza una subconsulta en la cláusula HAVING para calcular el salario promedio general de la empresa (SELECT AVG(salario) FROM empleados) y compara este valor con el salario promedio del departamento.
* Solo muestra los departamentos donde el salario promedio del departamento (AVG(e.salario)) sea mayor que el salario promedio general de la empresa.

El resultado de esta consulta mostrará los departamentos cuyo salario promedio es superior al salario promedio general de la empresa.


#### EJEMPLO 2
Vamos a crear un ejemplo que utiliza referencias externas en una subconsulta en SQL. Supongamos que tienes dos tablas: una tabla llamada clientes que almacena información sobre los clientes y otra tabla llamada órdenes que contiene detalles sobre las órdenes realizadas por esos clientes. Queremos encontrar el cliente que ha realizado la mayor cantidad de órdenes.


```sql
-- Crear la tabla de clientes
CREATE TABLE clientes (
    id INT PRIMARY KEY,
    nombre VARCHAR(50),
    email VARCHAR(100)
);

-- Insertar datos de ejemplo en la tabla de clientes
INSERT INTO clientes (id, nombre, email)
VALUES
    (1, 'Juan Pérez', 'juan@example.com'),
    (2, 'Ana Gómez', 'ana@example.com'),
    (3, 'Carlos López', 'carlos@example.com');

-- Crear la tabla de órdenes
CREATE TABLE ordenes (
    id INT PRIMARY KEY,
    cliente_id INT,
    fecha DATE
);

-- Insertar datos de ejemplo en la tabla de órdenes
INSERT INTO ordenes (id, cliente_id, fecha)
VALUES
    (1, 1, '2023-09-01'),
    (2, 1, '2023-09-05'),
    (3, 2, '2023-08-25'),
    (4, 3, '2023-09-10'),
    (5, 2, '2023-09-02');

```

Ahora, podemos escribir una consulta SQL que utiliza una subconsulta con referencias externas para encontrar el cliente con la mayor cantidad de órdenes:


```sql
SELECT nombre, COUNT(*) AS total_ordenes
FROM clientes
WHERE id = (
    SELECT cliente_id
    FROM ordenes
    GROUP BY cliente_id
    ORDER BY COUNT(*) DESC
    LIMIT 1
);

```

**Esta consulta hace lo siguiente:**
1. En la subconsulta interna, calcula la cantidad de órdenes por cliente utilizando COUNT(*) y agrupa los resultados por cliente_id. Luego, los ordena en orden descendente (DESC) para que el cliente con la mayor cantidad de órdenes esté en la parte superior y utiliza LIMIT 1 para obtener solo la fila principal de ese cliente.

2. En la consulta principal, utiliza la referencia externa cliente_id de la subconsulta para encontrar el nombre del cliente correspondiente en la tabla de clientes.

El resultado de esta consulta mostrará el nombre del cliente que ha realizado la mayor cantidad de órdenes y el total de órdenes que ha realizado. En este caso, el resultado sería:

```sql
+-------------+---------------+
| nombre      | total_ordenes |
+-------------+---------------+
| Juan Pérez  | 2             |
+-------------+---------------+

```

Esto indica que "Juan Pérez" es el cliente que ha realizado la mayor cantidad de órdenes, un total de 2 órdenes.

### ANIDAR SUB CONSULTAS

Anidar subconsultas en SQL se refiere a incorporar subconsultas dentro de otras subconsultas o dentro de la consulta principal. Esta técnica se utiliza para realizar consultas más complejas y obtener resultados más específicos al combinar varias capas de consultas anidadas. Las subconsultas anidadas se ejecutan de adentro hacia afuera, es decir, la subconsulta más interna se ejecuta primero y su resultado se utiliza en la subconsulta que la envuelve, y así sucesivamente.

A continuación, te proporciono un ejemplo y una explicación de cómo anidar subconsultas en SQL:

Supongamos que tenemos tres tablas: empleados, departamentos y salarios. Queremos encontrar el nombre de los empleados que trabajan en el departamento con el nombre "Ventas" y que tienen el salario más alto entre todos los empleados de ese departamento.

Primero, necesitamos encontrar el salario máximo en el departamento "Ventas" y luego identificar al empleado que tiene ese salario máximo.


```sql
SELECT nombre
FROM empleados
WHERE departamento_id = (
    SELECT id
    FROM departamentos
    WHERE nombre = 'Ventas'
) AND salario = (
    SELECT MAX(salario)
    FROM salarios
    WHERE empleado_id IN (
        SELECT id
        FROM empleados
        WHERE departamento_id = (
            SELECT id
            FROM departamentos
            WHERE nombre = 'Ventas'
        )
    )
);

```

**Explicación de la consulta anidada:**
1. La subconsulta interna más profunda se encuentra en la parte inferior y busca el id del departamento "Ventas" en la tabla departamentos. Esta subconsulta se ejecuta primero y devuelve el id del departamento.

2. La siguiente subconsulta anidada utiliza el id del departamento "Ventas" obtenido en la subconsulta anterior para encontrar el salario máximo en la tabla salarios para empleados que trabajan en ese departamento. Esta subconsulta devuelve el salario máximo en el departamento "Ventas".

3. La subconsulta principal se encuentra en la parte superior y busca el nombre de los empleados que trabajan en el departamento "Ventas" (identificado por su departamento_id) y que tienen el salario máximo (identificado por el salario máximo obtenido en la subconsulta anterior).

El resultado de esta consulta será el nombre de los empleados que cumplen con ambas condiciones: trabajan en el departamento "Ventas" y tienen el salario máximo en ese departamento. Las subconsultas anidadas permiten realizar consultas más avanzadas y específicas al dividir el problema en pasos más pequeños y combinar los resultados de manera lógica.


#### UPDATE

Las subconsultas también se pueden utilizar con la declaración UPDATE en SQL para realizar actualizaciones condicionales basadas en datos de otras tablas o subconsultas. Esto permite modificar registros en una tabla en función de valores calculados o seleccionados de otras tablas o subconsultas. Aquí hay un ejemplo de cómo usar subconsultas con UPDATE:

Supongamos que tienes dos tablas: empleados y salarios, y deseas actualizar el salario de todos los empleados en un departamento específico al salario máximo dentro de ese departamento. Aquí está cómo puedes hacerlo utilizando subconsultas:

```sql
UPDATE empleados AS e
JOIN salarios AS s ON e.id = s.empleado_id
SET s.salario = (
    SELECT MAX(salario)
    FROM salarios
    WHERE empleado_id IN (
        SELECT id
        FROM empleados
        WHERE departamento_id = (
            SELECT id
            FROM departamentos
            WHERE nombre = 'Ventas'
        )
    )
)
WHERE e.departamento_id = (
    SELECT id
    FROM departamentos
    WHERE nombre = 'Ventas'
);

```

**En este ejemplo:**
1. Utilizamos un UPDATE con una cláusula JOIN para unir la tabla empleados con la tabla salarios utilizando la clave primaria id del empleado.

2. La cláusula SET se utiliza para establecer el salario (s.salario) en el resultado de la subconsulta que busca el salario máximo en el departamento de "Ventas". La subconsulta anidada encuentra el id del departamento "Ventas" y luego encuentra el salario máximo dentro de ese departamento.

3. La cláusula WHERE se utiliza para limitar la actualización solo a los empleados que pertenecen al departamento de "Ventas". Esto se logra mediante una subconsulta que encuentra el id del departamento "Ventas".

Como resultado, esta consulta UPDATE actualizará el salario de todos los empleados en el departamento de "Ventas" al salario máximo encontrado en ese departamento.

Ten en cuenta que este es solo un ejemplo y las subconsultas con UPDATE pueden ser mucho más complejas según tus necesidades. Siempre es importante tener en cuenta la seguridad y hacer una copia de seguridad de tus datos antes de realizar actualizaciones masivas en una base de datos.

#### EXISTS

La función EXISTS en SQL se utiliza para verificar la existencia de registros en una subconsulta. Devuelve un valor booleano (TRUE o FALSE) que indica si la subconsulta devuelve algún resultado. En otras palabras, EXISTS se utiliza para verificar si hay al menos un registro que cumple con una condición específica dentro de la subconsulta.

La sintaxis básica de EXISTS es la siguiente:

```sql
SELECT columnas
FROM tabla
WHERE EXISTS (subconsulta);

```

**Aquí está cómo funciona EXISTS:**
La consulta principal selecciona las columnas de una tabla específica.

* La cláusula WHERE se utiliza para especificar una condición. La condición se evalúa como verdadera si la subconsulta dentro de EXISTS devuelve al menos un resultado.

* La subconsulta es una consulta anidada que se ejecuta dentro de EXISTS. Si la subconsulta devuelve algún resultado, la condición se considera verdadera y se seleccionan los registros en la consulta principal.

Veamos un ejemplo práctico. Supongamos que tienes dos tablas: empleados y departamentos, y deseas encontrar todos los empleados que trabajan en el departamento de "Ventas". Puedes hacerlo utilizando EXISTS de la siguiente manera:

```sql
SELECT nombre
FROM empleados
WHERE EXISTS (
    SELECT 1
    FROM departamentos
    WHERE nombre = 'Ventas' AND empleados.departamento_id = departamentos.id
);

```

En este ejemplo:

* La consulta principal selecciona el nombre de los empleados de la tabla empleados.

* La subconsulta dentro de EXISTS verifica si existe algún registro en la tabla departamentos donde el nombre sea "Ventas" y el departamento_id en la tabla empleados coincida con el id en la tabla departamentos.

* Si la subconsulta devuelve al menos un resultado (es decir, si existe al menos un departamento llamado "Ventas" al que algún empleado pertenece), entonces se seleccionará el nombre del empleado en la consulta principal.

> **EXISTS** es útil cuando deseas filtrar registros en función de la existencia de registros relacionados en otra tabla o en una subconsulta.

#### BETWEEN
Para expresar una condición que quiere encontrar un valor entre unos límites concretos, podemos utilizar BETWEEN:


```sql
SELECT nombre_columnas_a_seleccionar
FROM tabla_a_consultar
WHERE columna BETWEEN límite1 AND limite2;    
```

Un ejemplo en el que se pide “Los códigos de los empleados que ganan entre 20.000 y 50.000 euros anuales” sería:

```sql
SELECT codigo_empl
FROM empleados
WHERE sueldo BETWEEN 2.0E+4 and 5.0E+4;

```

#### IN
Para comprobar si un valor coincide con los elementos de una lista utilizaremos IN, y para ver si no coincide, NOT IN:


```sql
SELECT nombre_columnas_a_seleccionar
FROM tabla_a_consultar
WHERE columna [NOT] IN (valor1, ..., valorN);

```

“Queremos saber el nombre de todos los departamentos que se encuentran en las ciudades de Lleida o Tarragona”:

```sql
SELECT nombre_dep, ciudad_dep
FROM departamentos
WHERE ciudad_dep IN ('Lleida', 'Tarragona');

```

#### LIKE
Para comprobar si una columna de tipo carácter cumple alguna propiedad determinada, podemos usar LIKE:

```sql
SELECT nombre_columnas_a_seleccionar FROM tabla_a_consultar WHERE columna LIKE característica;

```

Los patrones del SQL92 para expresar características son los siguientes:

* Pondremos un carácter “_” para cada carácter individual que queramos considerar.
* Pondremos un carácter “%” para expresar una secuencia de caracteres, que puede no estar formada por ninguno.

A continuación, presentamos un ejemplo en el que buscaremos los nombres de los empleados que empiezan por J, y otro ejemplo en el que obtendremos los proyectos que comienzan por S y tienen cinco letras:

**Nombres de empleados que empiezan por la letra J:**
```sql
SELECT codigo_empl, nombre_empl
FROM empleados
WHERE nombre_empl LIKE 'J%';    

```

**Proyectos que empiezan por S y tienen cinco letras:**
```sql
SELECT codigo_proyec
FROM proyectos
WHERE nombre_proyec LIKE 'S_ _ _ _';

```

#### IS NULL
Para comprobar si un valor es nulo utilizaremos IS NULL, y para averiguar si no lo es, IS NOT NULL. El formato es:

```sql
SELECT nombre_columnas_a_seleccionar
FROM tabla_a_consultar
WHERE columna IS [NOT] NULL;

```

Un ejemplo de uso de este predicado sería “Queremos saber el código y el nombre de todos los empleados que no están asignados a ningún proyecto”:

```sql
SELECT codigo_empl, nombre_empl
FROM empleados
WHERE num_proyec IS NULL;

```

#### NY/SOME y ALL
Para ver si una columna cumple que todas sus filas (ALL) o algunas de sus filas (ANY/SOME) satisfagan una condición, podemos hacer:
```sql
SELECT nombre_columnas_a seleccionar
FROM   tabla_a_consultar
WHERE  columna operador_comparación {ALL|ANY|SOME} subconsulta;

```

Veamos un ejemplo de aplicación de ALL para encontrar los códigos y los nombres de los proyectos en los que los sueldos de todos los empleados asignados son menores que el precio del proyecto:

```sql
SELECT codigo_proyec, nombre_proyec
FROM proyectos
WHERE precio > ALL (SELECT sueldo
    FROM empleados
    WHERE codigo_proyec = num_proyec);    

```

Fijémonos en la condición de WHERE de la sub consulta, que nos asegura que los sueldos que observamos son los de los empleados asignados al proyecto de la consulta.

A continuación, presentamos un ejemplo de ANY/SOME para buscar los códigos y los nombres de los proyectos que tiene algún empleado que gana un sueldo más elevado que el precio del proyecto en el que trabaja:

```sql
SELECT codigo_proyec, nombre_proyec
FROM proyectos
WHERE precio < ANY (SELECT sueldo
   FROM empleados
   WHERE codigo_proyec = num_proyec);    

```


#### Predicado IN y Subquery

* **Predicado IN**: En SQL, el predicado IN se utiliza para comparar un valor con un conjunto de valores o resultados. Por ejemplo, puedes usar IN para verificar si un valor se encuentra en una lista de valores o en el resultado de una subconsulta.

* **Subquery**: Una subconsulta es una consulta SQL que se utiliza dentro de otra consulta. Puede ser una consulta independiente o parte de una expresión condicional. En el contexto del predicado IN, una subconsulta puede proporcionar los valores con los que se comparará un valor en la consulta principal.

* **Relación entre IN y Subquery**: El contenido colocado en el predicado IN generalmente consiste en una lista de valores o una subconsulta. La subconsulta se ejecuta y devuelve un conjunto de resultados que se utilizan para la comparación con el valor en la consulta principal. El predicado IN devuelve TRUE si el valor coincide con al menos uno de los valores o resultados en la lista o subconsulta.

* **Sustituir IN con Subquery**: La afirmación "El contenido colocado en el predicado IN podría ser sustituido por un subquery" es falsa. Esto se debe a que, en realidad, el contenido dentro de IN a menudo incluye subconsultas como una forma de proporcionar dinámicamente los valores con los que se realizará la comparación.


#### Función INSTR

Función INSTR: INSTR es una función de fila única en SQL que se utiliza para encontrar la posición de una subcadena dentro de una cadena de caracteres más grande. La sintaxis general de la función INSTR es la siguiente:

```sql
INSTR(cadena, subcadena[, posición[, aparición]])

```

**Explicación de los parámetros:**

cadena: La cadena de caracteres en la que deseas buscar la subcadena.
subcadena: La subcadena que deseas encontrar en la cadena principal.
posición (opcional): Especifica la posición inicial de la búsqueda en la cadena principal (por defecto, comienza desde el principio).
aparición (opcional): Indica cuál aparición de la subcadena deseas encontrar si hay varias ocurrencias (por defecto, es 1).
Uso de INSTR: INSTR es útil cuando necesitas buscar y trabajar con datos dentro de cadenas de caracteres, como encontrar la posición de un carácter o una subcadena específica en un texto más largo. La función devuelve la posición donde se encuentra la subcadena o cero si no se encuentra.

#### LIKE:

En SQL, el predicado LIKE se utiliza para buscar patrones dentro de cadenas de caracteres. Puedes usar caracteres comodín, como % (que representa cero o más caracteres) o _ (que representa un carácter), para buscar cadenas de caracteres que cumplan ciertos patrones.

**Ejemplo de uso**: Por ejemplo, si deseas encontrar todos los nombres que comienzan con "Ana", puedes usar el predicado LIKE de la siguiente manera:

```sql
SELECT nombre FROM empleados WHERE nombre LIKE 'Ana%';

```

Esto recuperará todos los nombres que comienzan con "Ana".

LIKE es versátil y útil para realizar búsquedas y filtrar datos basados en patrones de texto en una base de datos. Puede ser utilizado en combinación con otros operadores y funciones para realizar consultas más avanzadas en datos de texto.