
# OPTIMIZACION DE CONSULTAS
---
 	
* Comprender la importancia de optimizar instrucciones de acceso a base de datos.
* Identificar componentes que permiten mejorar el acceso a la información.

## CONSULTAS COMBINADAS

Las consultas combinadas pueden ser de tres tipos:

* Combinación interna.
* Combinación externa.
* Uniones.

Las consultas combinadas utilizando la cláusula JOIN en SQL son una forma poderosa de combinar datos de múltiples tablas relacionadas en una sola consulta. La cláusula JOIN se utiliza para especificar cómo se deben combinar las filas de una tabla con las filas de otra tabla basándose en una columna común. A continuación, te explicaré las consultas combinadas JOIN y proporcionaré ejemplos:

Supongamos que tienes dos tablas: empleados y departamentos, y deseas obtener una lista de empleados junto con el nombre de su departamento. Ambas tablas tienen una columna departamento_id que se utiliza para relacionar a cada empleado con su departamento correspondiente.

Aquí está una consulta SQL que utiliza INNER JOIN para combinar las tablas y obtener la información deseada:

```sql
SELECT empleados.nombre, departamentos.nombre AS nombre_departamento
FROM empleados
INNER JOIN departamentos ON empleados.departamento_id = departamentos.id;

```

En esta consulta:

* empleados y departamentos son los nombres de las tablas que estamos combinando.
* empleados.departamento_id y departamentos.id son las columnas que se utilizan para realizar la unión. Estas columnas deben ser iguales o tener una relación de clave foránea.
* AS nombre_departamento se utiliza para darle un alias al nombre del departamento en el resultado de la consulta, para que sea más legible.

La consulta anterior devuelve una lista de empleados junto con el nombre de su departamento. La cláusula INNER JOIN asegura que solo se incluyan las filas que tienen coincidencias en ambas tablas. Si un empleado no tiene un departamento correspondiente, no aparecerá en el resultado.

Además del INNER JOIN, hay otros tipos de JOIN disponibles:

* **LEFT JOIN**: Devuelve todas las filas de la tabla izquierda (primer tabla mencionada) y las filas coincidentes de la tabla derecha (segunda tabla mencionada). Si no hay coincidencias en la tabla derecha, se rellenan con valores NULL.
* **RIGHT JOIN**: Similar al LEFT JOIN, pero devuelve todas las filas de la tabla derecha y las filas coincidentes de la tabla izquierda. Las filas no coincidentes en la tabla izquierda se rellenan con valores NULL.
FULL OUTER JOIN: Devuelve todas las filas de ambas tablas, rellenando con NULL en caso de que no haya coincidencias en una u otra tabla.
* **SELF JOIN**: Se utiliza cuando deseas combinar una tabla consigo misma. Puede ser útil en situaciones donde necesitas relacionar datos dentro de la misma tabla.


Las consultas combinadas JOIN son fundamentales en SQL para trabajar con bases de datos relacionales y extraer información de múltiples tablas de manera eficiente. Puedes personalizar tu consulta según tus necesidades específicas y las relaciones entre tus tablas.

## COMBINACION INTERNA
una combinación interna (INNER JOIN) en SQL es una operación que combina filas de dos o más tablas, incluyendo solo las filas que coinciden en función de una condición de unión específica. En otras palabras, un INNER JOIN recupera solo las filas que tienen valores coincidentes en ambas tablas que estás combinando.

La sintaxis básica de un INNER JOIN es la siguiente:


```sql
SELECT columnas
FROM tabla1
INNER JOIN tabla2 ON tabla1.columna = tabla2.columna;

```

**Donde**:

* **columnas**: Las columnas que deseas seleccionar de las tablas.
* **tabla1 y tabla2**: Los nombres de las tablas que deseas combinar.
* **tabla1.columna y tabla2.columna**: Las columnas en las que deseas basar la unión.

A continuación, un ejemplo práctico de cómo se utiliza un INNER JOIN:

Supongamos que tienes dos tablas, empleados y departamentos, y deseas obtener una lista de empleados junto con el nombre de su departamento. Ambas tablas tienen una columna departamento_id que se utiliza para relacionar a cada empleado con su departamento correspondiente. Puedes utilizar un INNER JOIN para lograr esto de la siguiente manera:


```sql
SELECT empleados.nombre, departamentos.nombre AS nombre_departamento
FROM empleados
INNER JOIN departamentos ON empleados.departamento_id = departamentos.id;

```

**En esta consulta:**

* empleados y departamentos son las tablas que se están combinando.
* empleados.departamento_id y departamentos.id son las columnas que se utilizan para realizar la unión.
* AS nombre_departamento se utiliza para darle un alias al nombre del departamento en el resultado de la consulta, para que sea más legible.

La consulta anterior devolverá una lista de empleados junto con el nombre de su departamento. Sin embargo, ten en cuenta que solo se incluirán las filas donde haya una coincidencia entre empleados.departamento_id y departamentos.id. Si un empleado no tiene un departamento correspondiente, no aparecerá en el resultado.

En resumen, un INNER JOIN en SQL se utiliza para combinar filas de múltiples tablas basadas en una condición de unión y devuelve solo las filas que tienen coincidencias en ambas tablas. Es una herramienta fundamental para recuperar datos relacionados de manera eficiente en una base de datos relacional.



## COMBINACION EXTERNA
Una combinación externa (o JOIN externo) en SQL es una operación que combina filas de dos o más tablas, incluyendo tanto las filas que coinciden en la condición de unión como las filas que no coinciden en una de las tablas. Las combinaciones externas se utilizan para recuperar datos de una tabla incluso cuando no hay coincidencias en la otra tabla.

Existen dos tipos principales de combinaciones externas en SQL:

### LEFT JOIN (Combinación Externa Izquierda)
En un LEFT JOIN, se recuperan todas las filas de la tabla de la izquierda (la primera tabla mencionada en la cláusula JOIN) y las filas coincidentes de la tabla de la derecha (la segunda tabla mencionada en la cláusula JOIN). Si no hay coincidencias en la tabla de la derecha, las columnas correspondientes se rellenan con valores NULL en el resultado.

**Ejemplo de LEFT JOIN:**
```sql
SELECT empleados.nombre, departamentos.nombre AS nombre_departamento
FROM empleados
LEFT JOIN departamentos ON empleados.departamento_id = departamentos.id;

```
En este ejemplo, se recuperarán todas las filas de la tabla empleados y las filas coincidentes de la tabla departamentos. Si un empleado no tiene un departamento correspondiente, la columna nombre_departamento se rellenará con NULL.

### RIGHT JOIN (Combinación Externa Derecha)
En un RIGHT JOIN, se recuperan todas las filas de la tabla de la derecha y las filas coincidentes de la tabla de la izquierda. Si no hay coincidencias en la tabla de la izquierda, las columnas correspondientes se rellenan con valores NULL en el resultado.

**Ejemplo de RIGHT JOIN:**
```sql
SELECT empleados.nombre, departamentos.nombre AS nombre_departamento
FROM empleados
RIGHT JOIN departamentos ON empleados.departamento_id = departamentos.id;

```

En este ejemplo, se recuperarán todas las filas de la tabla departamentos y las filas coincidentes de la tabla empleados. Si un departamento no tiene empleados correspondientes, la columna nombre se rellenará con NULL.

### FULL OUTER JOIN (Combinación Externa Completa)
En un FULL OUTER JOIN, se recuperan todas las filas de ambas tablas, incluyendo las filas coincidentes y las que no coinciden. Si no hay coincidencias en una de las tablas, las columnas correspondientes se rellenan con valores NULL en el resultado.

**Ejemplo de FULL OUTER JOIN:**
```sql
SELECT empleados.nombre, departamentos.nombre AS nombre_departamento
FROM empleados
FULL OUTER JOIN departamentos ON empleados.departamento_id = departamentos.id;

```
En este ejemplo, se recuperarán todas las filas de ambas tablas empleados y departamentos, incluyendo las filas coincidentes y las no coincidentes. Las columnas correspondientes se llenarán con NULL donde no haya coincidencias.

La combinación externa puede ser diestra o siniestra, LEFT OUTER JOIN o RIGHT OUTER JOIN. Con LEFT OUTER JOIN obtenemos todos los registros en la tabla que situemos a la izquierda de la cláusula JOIN, mientras que con RIGHT OUTER JOIN obtenemos el efecto contrario.

Las combinaciones externas son útiles cuando necesitas obtener datos de una tabla incluso si no hay correspondencias en la otra tabla. Ayudan a mantener la integridad de los datos y a asegurarse de que no se pierda información importante en una consulta SQL.


## UNIONES
Las uniones (UNION en SQL) se utilizan para combinar los resultados de dos o más consultas en una sola tabla resultante. La consulta resultante de una unión incluirá todas las filas de las consultas individuales, eliminando duplicados. Las uniones son útiles cuando deseas combinar datos de múltiples tablas o consultas en un solo conjunto de resultados.

Hay algunas reglas clave a tener en cuenta al utilizar UNION en SQL:

* Las consultas individuales deben tener la misma cantidad de columnas.
* Las columnas en cada consulta individual deben tener tipos de datos compatibles.
* Las columnas se seleccionan en el mismo orden en todas las consultas.
* La sintaxis básica de UNION en SQL es la siguiente:

```sql
SELECT columnas
FROM tabla1
WHERE condición
UNION
SELECT columnas
FROM tabla2
WHERE condición;

```

**Donde**:

* **columnas**: Las columnas que deseas seleccionar en ambas consultas.
* **tabla1 y tabla2**: Las tablas o consultas que deseas combinar.
* **condición**: Opcional. Una condición que puedes aplicar en cada consulta individual para filtrar los resultados.

Aquí hay un ejemplo práctico de cómo se utiliza UNION; Supongamos que tienes dos tablas, ventas_2022 y ventas_2023, y deseas combinar las ventas de ambos años en una sola tabla de resultados:

```sql
SELECT producto, cantidad
FROM ventas_2022
WHERE cantidad > 100
UNION
SELECT producto, cantidad
FROM ventas_2023
WHERE cantidad > 100;

```

```sql
+-----------+---------+
| producto  | cantidad|
+-----------+---------+
| Producto1 | 150     |
| Producto2 | 120     |
| Producto3 | 110     |
| Producto4 | 105     |
+-----------+---------+

```


**En esta consulta:**
* Estamos seleccionando las columnas producto y cantidad de ambas tablas ventas_2022 y ventas_2023.
* Aplicamos una condición en cada consulta para seleccionar solo las ventas con una cantidad superior a 100 en ambos años.
* Las filas resultantes de ambas consultas se combinan en una sola tabla resultante y se eliminan los duplicados.

Es importante destacar que UNION elimina las filas duplicadas en el conjunto de resultados final. Si deseas incluir todas las filas, incluidas las duplicadas, puedes utilizar UNION ALL en lugar de UNION.

En resumen, UNION en SQL se utiliza para combinar los resultados de dos o más consultas en una sola tabla resultante, asegurando que las columnas sean compatibles y tengan el mismo orden en todas las consultas individuales. Esto es útil para consolidar datos de múltiples fuentes o tablas en una sola vista.


## CRITERIOS PARA OPTIMIZAR ACCESOS A BD
Cada día se necesita procesar mayor cantidad de datos y obtener de manera más rápida y precisa la información. Muchos de los problemas de rendimiento se deben entre otras cosas al hardware, al software, al motor de base de datos y por sobre todo al diseño, índices y mala formulación de consultas SQL.

En este apartado nos centraremos en estos últimos en donde siguiendo algunas recomendaciones veremos que se puede mejorar el tiempo de respuesta de nuestro motor de BD significativamente.

### A LA HORA DE DISENAR LA BASE DE DATOS
* Las tablas normalizadas permiten reducir al mínimo el espacio ocupado por nuestra base y permiten asegurar la consistencia de la información al mismo tiempo que son muy rápidas para la realización de transacciones, pero generan un mayor tiempo de demora a la hora de consultarlas, ya que se deben realizar generalmente la unión de varias tablas, por lo que en caso de necesidad de altas velocidades de respuesta con grandes volúmenes de datos, un modelo desnormalizado es más que conveniente teniendo en cuenta todas las implicancias del caso.
* Ajustar al máximo el tamaño de los campos ayuda a no desperdiciar espacio.
* Eliminar todo campo que no sea de utilidad, ya que por más que no contenga datos genera retrasos.

### ¿QUE PASA CON LOS INDICES?
Los índices son campos que permiten la búsqueda a partir de dicho campo a una velocidad notablemente superior. Sin embargo, cuentan con la desventaja que hace más lenta la actualización, carga y eliminación de los registros, ya que por cada modificación en la tabla se deberá modificar también el índice, además se debe tener en cuenta el hecho de que los índices también ocupan espacio en disco. Es por esto que no es factible indexar todos los campos de la base y se hace necesario seleccionarlos cuidadosamente. Cabe destacar que por defecto las tablas no contienen índices por lo que la introducción de estos puede llegar a producir mejoras de más del 100% en algunos casos. Los campos que se recomiendan indexar son:

* Claves Primarias.
* Claves Foráneas.
* Campos por los cuales se realizarán búsquedas.
* Campos por los cuales se va a ordenar.

Siempre conviene indexar tablas con gran cantidad de registros y que van a ser consultadas intensamente.

### DONDE ESCRIBIR LAS SENTENCIAS
Siempre **es preferible utilizar consultas almacenadas dentro del motor de base de datos y no dentro de la aplicación**, una consulta almacenada en un procedimiento almacenado, por ejemplo, se ejecuta mucho más rápido y directamente sobre el motor que cualquier consulta externa.
Muchas de las aplicaciones sobre todo de reporte permiten unir y realizar los joins y consultas directamente en la herramienta produciendo una baja de performance realmente considerable. Lo correcto y más eficiente sería generar la consulta en un procedimiento almacenado con todos los joins y guardar el resultado en una tabla temporal, de donde posteriormente, el reporte solo deberá mostrar los datos sin necesidad de trabajarlos primero. Dependiendo los joins que intervengan y los registros involucrados se puede mejorar drásticamente la performance, han habido casos en que reportes que duraban 3 minutos en generarse pasaron a 30 segundos, usando esta técnica.

### ACERCA DE LA FORMULACION DE LAS CONSULTAS
A la hora de ejecutar una consulta SQL la forma en que esta es expresada afecta directamente al motor de BD, pequeños cambios pueden significar la ganancia de muchos segundos o minutos que el usuario debe esperar al momento de ejecutar la consulta. Algunas recomendaciones son:

* No utilizar SELECT * porque el motor debe leer primero la estructura de la tabla antes de ejecutar la sentencia.
* Seleccionar solo aquellos campos que se necesiten. Cada campo extra genera tiempo extra.
* Utilizar Inner Join , left join , right join, para unir las tablas en lugar del where, esto permite que a medida que se declaran las tablas se vayan uniendo mientras que si utilizamos el where el motor genera primero el producto cartesiano de todos los registros de las tablas para luego filtrar las correctas, un trabajo definitivamente lento.
* Especificar el alias de la tabla delante de cada campo definido en el select, esto le ahorra tiempo al motor de tener que buscar a cuál tabla pertenece el campo especificado.
* Evitar el uso de Cast y fórmulas dentro de las consultas, cada fórmula y casteo retrasan el motor considerablemente.
* El orden de ubicación de las tablas en el from debería ir en lo preferible de menor a mayor según el número de registros, de esta manera reducimos la cantidad de revisiones de registros que realiza el motor al unir las tablas a medida que se agregan.

### SOLO CONSULTE LO QUE REALMENTE NECESITE
Filtre tanto como pueda, la cláusula WHERE es la más importante a la hora de la optimización; NUNCA use “SELECT *;” debe especificar los campos que necesita, esto hará su consulta más rápida y llevará a ahorrar ancho de banda (recuerde que Ud. está enviando paquetes por una red, ¿por qué habrá de enviar lo que no necesita?).

Sea cuidadoso con el JOIN, las expresiones JOIN son caras en términos de tiempo, asegúrese de que está usando todas las claves relativas a las tablas que refiere y no aplique JOIN en tablas que no necesita, siempre trate de unir campos indexados.

El tipo de JOIN usado es muy importante también; familiarícese con los tipos (INNER, OUTER, LEFT, RIGHT….)

Las consultas son rápidas, generalmente podrá recuperar cantidad de información en menos de un segundo, incluso usando los joins, ordenando y calculando. Una regla de oro es que si su consulta toma más de un segundo, deberá optimizarla.

El trabajo comenzará con las consultas más necesarias o más usadas, y luego proceder con las que más tiempo toman.

### AGREGUE, REMUEVA O MODIFIQUE INDICES
Si las consultas realizan búsquedas de tablas completas, deberá pensar en el uso de índices para sus tablas, el uso de ellos y de un filtrado adecuado que pueden resolver la mayor parte de las consultas que toman demasiado tiempo.

Todas las claves primarias precisan de índices para realizar los joins más rápidamente, esto también significa que todas las tablas precisan de clave primaria. Se pueden agregar índices en campos que usa seguido para el filtrado con cláusulas de tipo WHERE.

Especialmente usted precisa usar índices en campos de tipo entero, booleano y numérico; en cambio no le será de mucha ayuda en campos de tipo Blob, VarChar y Long String.

El lado negativo de los índices es que se debe tener mucho cuidado con su uso en tablas que se actualizan muy seguido, en estos casos el mantenimiento de los índices puede consumir más tiempo del que realmente ahorran.

Otra herramienta excelente en el mundo de Internet son las tablas de tipo read-only allí los índices funcionan en su mayor potencial, ya que raramente necesitará realizar mantenimiento.

### PROCEDIMIENTOS ALMACENADOS
Los procedimientos almacenados son una alternativa rápida y mejor a las consultas por las siguientes razones:

* Los procedimientos almacenados son compilados (el código SQL es interpretado) haciéndolas una opción mucho más rápida.
* El ahorro de ancho de banda es importante, pues se pueden realizar varias consultas en un mismo procedimiento, además el procedimiento se mantiene en el servidor hasta que el resultado final es obtenido, y es esto únicamente lo que se envía al cliente.
* Los procedimientos almacenados corren dentro del servidor, que usualmente es más rápido.
* Los cálculos en código (VB, Java, C++) no son tan rápidos como en PA en la mayoría de los casos.
* Mantiene el código de acceso a la BD separado de la capa de presentación, lo que la hace más fácil de mantener (modelo de 3 capas) y muchísimo más segura ante ataques como inyección SQL, pues no se tiene acceso directo al código.

Se puede afinar una BD de varias formas, usando estadísticas de optimización, corriendo opciones de optimización, realizando tablas de sólo lectura, etc. Usualmente este trabajo lo realiza un administrador de BD. En la mayoría de los sistemas gestores de bases de datos existen herramientas de optimización. MySQL tiene la herramienta “MySQL query analyzer”, que le permitirá ejecutar consultas y observar su incidencia, para determinar lo que el SGBD hace con sus consultas.

## LA OPTIMIZACION EN LA PRACTICA
Para comprender mejor el concepto de la optimización, veremos a continuación una serie de ejemplos que se aplican en instrucciones SQL, mostrando en primer lugar el código no optimizado y luego el código aplicando los criterios de mejora en la instrucción SQL. Si se quiere consultar el nombre y el salario de los empleados del departamento de ventas:


### EJEMPLO 1
**Consulta original**:
```sql
Select * from Empleados;

```

**Corregido**:
```sql
Select Nombre, Salario 
From Empleados 
Where Dept='Ventas';

```

En la versión corregida, se filtra la información en la BD lo que resulta más rápido, además sólo se solicita la información necesaria, lo que enviará sensiblemente menos información y, por lo tanto, mejorará la performance.

### EJEMPLO 2

**Consulta original**:
```sql
Select Nombre, Salario 
From   Empleados 
Where Dept='Ventas' 
Order By Salario;

```

¿Realmente necesita la cláusula Order by? A menudo se utiliza esta opción para revisar si los datos retornados son correctos, remuévala si no la necesita, ahora si es necesaria úsela en la consulta no en la página.

### EJEMPLO 3

**Original**:

```sql
For i=1 to 2000 call query : Select Salario From Empleados Where EMpID= Parametro(i)

```

**Corregido**:

```sql
Select Salario From Empleados Where EmpID >=1 and EmpID <= 2000; 

```

La primera opción involucra gran transmisión de datos lo que hará más lento el sistema completo, siempre debe realizar el trabajo en la consulta o el procedimiento almacenado, si obliga al sistema a llevar y traer información pierde valioso tiempo. No importa si se piensa que el proceso es tan complicado que es mejor manejarlo en el código de su aplicación, pero rara vez lo es.

### EJEMPLO 4
Se tienen 2 tablas Ordenes y Clientes. Los Clientes pueden tener varias órdenes.
**Original**:
```sql
Select O.Precio, C.Nombre 
From Ordenes O, Clientes C;
```

**Corregido**:
```sql
Select O.Precio, C.Nombre 
From Ordenes O INNER JOIN Clientes C ON O.ClienteID=C.ClienteID;
```

El segundo SQL corregido es preferible al primero por varias razones:

* **Claridad de la Intención**: El segundo SQL utiliza INNER JOIN para combinar las tablas Ordenes y Clientes en función de la columna ClienteID. Esto proporciona una clara intención de que se está realizando una unión entre las dos tablas basada en una relación específica, lo que hace que el código sea más legible y fácil de entender. En el primer SQL, se utilizan tablas separadas por comas, lo que puede resultar en un código menos claro y más propenso a errores.

* **Consistencia y Estándares**: El uso de JOIN sigue los estándares de SQL y se considera una mejor práctica en la mayoría de los casos. Es más consistente con las convenciones de SQL y facilita la comprensión del código para otros desarrolladores.

* **Mantenibilidad**: El segundo SQL es más fácil de mantener y modificar en el futuro. Si necesitas realizar cambios en las condiciones de unión o agregar más tablas a la consulta, es más sencillo hacerlo utilizando la sintaxis de JOIN en lugar de la sintaxis de tablas separadas por comas.

* **Rendimiento**: En algunos sistemas de gestión de bases de datos, la sintaxis de JOIN puede ser más eficiente en términos de rendimiento que la sintaxis de tablas separadas por comas, especialmente cuando se trata de consultas más complejas. Los motores de bases de datos están optimizados para manejar consultas con JOIN de manera eficiente.

* **Legibilidad**: Utilizar INNER JOIN hace que el código sea más legible y autoexplicativo. Indica claramente que se está realizando una operación de unión entre las tablas, lo que facilita a otros desarrolladores comprender la lógica de la consulta.


## ¿QUÉ SON LOS PROCEDIMIENTOS ALMACENADOS?

Los procedimientos almacenados son un tipo de objeto de base de datos que contiene un conjunto de instrucciones SQL predefinidas y almacenadas en el sistema de gestión de bases de datos (DBMS). Estas instrucciones pueden incluir consultas, actualizaciones, inserciones y otras operaciones SQL. Los procedimientos almacenados se almacenan en la base de datos y se pueden ejecutar de forma repetida mediante una llamada desde una aplicación, un lenguaje de programación o directamente desde el gestor de bases de datos.

Los procedimientos almacenados son una parte fundamental de la programación de bases de datos, permitiendo la encapsulación de lógica de negocio en el servidor de bases de datos para mejorar la reutilización, la seguridad, el rendimiento y la mantenibilidad del código. Son especialmente útiles en aplicaciones empresariales donde la gestión de datos y la lógica de negocio son críticas.

Generalmente son escritos en un lenguaje de bases de datos propietario, es decir, cada gestor de base de datos posee su propio lenguaje, por lo que es recomendable revisar el manual del SGBD para conocer la sintaxis a ser utilizada.

Una vez creado un procedimiento almacenado, se puede invocar directamente desde una aplicación, o sustituir el nombre de una tabla o vista, por el nombre de procedimiento en cláusulas SELECT.

Los procedimientos almacenados tienen las siguientes características y beneficios:

* **Reutilización de Código**: Los procedimientos almacenados permiten encapsular lógica de negocio y funcionalidad en un solo lugar. Esto significa que la misma lógica se puede reutilizar en múltiples partes de una aplicación sin necesidad de volver a escribirla.

* **Mayor Seguridad**: Los procedimientos almacenados pueden definir permisos de acceso específicos, lo que permite un control más preciso de quién puede ejecutar ciertas operaciones en la base de datos.

* **Mejor Rendimiento**: Al almacenar el código en el servidor de bases de datos, los procedimientos almacenados pueden ofrecer un mejor rendimiento que enviar consultas SQL desde una aplicación. Esto se debe a que el código se compila y optimiza en el servidor.

* **Facilidad de Mantenimiento**: Los cambios en la lógica de negocio se pueden realizar en un solo lugar, lo que simplifica el mantenimiento y evita la duplicación de código.

* **Transacciones**: Los procedimientos almacenados pueden ser parte de transacciones, lo que garantiza la integridad de los datos al realizar múltiples operaciones en una única transacción.

* **Parametrización**: Los procedimientos almacenados pueden aceptar parámetros, lo que permite la personalización de la operación que se realizará. Los parámetros pueden ser valores que se pasan cuando se llama al procedimiento.

* **Abstracción de la Base de Datos**: Los procedimientos almacenados proporcionan una capa de abstracción sobre la base de datos, lo que facilita la migración a diferentes sistemas de gestión de bases de datos sin cambiar la lógica de la aplicación.

* **Control de Versiones**: Los procedimientos almacenados se pueden gestionar y controlar versiones de la misma manera que otros activos de código fuente.

* **Compilación**: la primera vez que se invoca un SP, el motor lo compila y a partir de ahí, se sigue usando la versión compilada del mismo, hasta que se modifique o se reinicie el servicio de SQL. Esto significa que se tendrá un mejor rendimiento que las consultas directas que usan cadenas con las instrucciones T-SQL, que se compilan cada vez que se invocan.
* **Automatización**: si tenemos un conjunto de instrucciones T-SQL, las cuales queremos ejecutar de manera ordenada, un SP es la mejor manera de hacerlo.
* **Administración**: cuando realizamos aplicaciones con un gran número de líneas de código, y queremos hacer cambios, solo implica modificar un SP y no toda la aplicación, lo que significa solo cambiamos los SP en el servidor y no tenemos que actualizar la aplicación en todos los equipos cliente.
* **Seguridad**: una parte importante es que a los usuarios de nuestra aplicación, sólo les proporcionamos los permisos para ejecutar los procedimientos almacenados y no el acceso a todos los objetos de la base, es decir, si en nuestra aplicación encuentran una vulnerabilidad como “SQL Injection” no se podrá explotar ejecutando SQL directamente.
* **Programabilidad**: los SP admiten el uso de variables y estructuras de control como IF, Bucles, Case, etc., además del manejo de transacción. Permite controlar excepciones.
* **Tráfico de Red**: pueden reducir el tráfico de la red, debido a que se trabaja sobre el motor (en el servidor), y si una operación incluye hacer un trabajo de lectura primero y con base a eso realizar algunas operaciones, esos datos que se obtienen no viajan por la red.
 

### ELEMENTOS DE LOS PROCEDIMIENTOS ALMACENADOS

 

Los procedimientos almacenados están compuestos por algunos de estos elementos:

* Parámetros de entrada.
* Parámetros de salida.
* Declaración de variables.
* Cuerpo del procedimiento.

Un procedimiento almacenado también se puede ejecutar mediante la instrucción EXECUTE PROCEDURE o CALL (según el SGBD que se esté utilizando). Esto lo veremos a detalle más adelante.

 

**¿Dónde utilizarlos?**
Los procedimientos almacenados son muy útiles cuando no se requiere cargar de tráfico la red.

A continuación, se muestran algunos de los posibles usos que pueden darse a estos objetos de la base de datos.

Por ejemplo:

* Si deseamos obtener un reporte complejo que incluya instrucciones condicionales y cálculos complejos con datos obtenidos de varias tablas, un procedimiento almacenado es nuestro mejor aliado.

* También podemos ejecutar complejos procesos que a veces tardan horas cuando son ejecutados desde el cliente, ya que en tales casos la información debe pasar del servidor al cliente y viceversa. Cuando utilizamos un procedimiento almacenado, este es ejecutado por el SGBD que a su vez es ejecutado en la computadora servidor. Casi siempre las computadoras servidores son poderosas máquinas con mucha memoria, discos rápidos y uno o más procesadores también muy rápidos. Por lo tanto, al ejecutar los procesos mediante procedimientos almacenados estamos aprovechando toda esa capacidad de cómputo disponible en el hardware del servidor.


**Principal desventaja**
La principal desventaja de los procedimientos almacenados es la complejidad y la dificultad de mantenimiento que pueden surgir a medida que se vuelven más extensos y se acumula una gran cantidad de lógica de negocio en ellos. A pesar de esta desventaja, muchas organizaciones encuentran que los beneficios de rendimiento, seguridad y reutilización de código superan ampliamente estas consideraciones, especialmente en aplicaciones empresariales complejas.

* **Esclavitud**: Los procedimientos almacenados nos esclavizan al motor de base de datos.Una base de datos con muchos procedimientos almacenados, es prácticamente imposible de migrar a otro motor. Se debe, principalmente, a que los lenguajes de procedimientos almacenados de distintos fabricantes no son compatibles entre sí.
* **Dificultad de Pruebas Unitarias**: Probar procedimientos almacenados de manera unitaria (a nivel de unidad) puede ser complicado, especialmente si involucran múltiples interacciones con la base de datos. Esto puede dificultar la implementación de pruebas unitarias completas en la lógica encapsulada en los procedimientos almacenados.


### CREACIÓN DE PROCEDIMIENTOS ALMACENADOS

Como se mencionó, los procedimientos almacenados si bien son guardados en la base de datos, estos son de código propietario. Esto significa que si tenemos Oracle la sintaxis podría diferir de un MS SQL Server, MySQL y otros gestores de base de datos. Por ello se mostrará a continuación un formato genérico para crear un procedimiento almacenado, enfatizando que en nuestro caso lo importante será el concepto y no la sintaxis, pues para ellos deberá referirse a los manuales correspondientes del SGBD que posea.

Para crear procedimientos almacenados en MySQL, puedes utilizar la sintaxis específica de MySQL. A continuación, se muestra un ejemplo de cómo crear un procedimiento almacenado simple en MySQL:

```sql
DELIMITER //

CREATE PROCEDURE MiProcedimiento()
BEGIN
    -- Código SQL aquí
    SELECT * FROM MiTabla;
END;
//

DELIMITER ;

```

Aquí tienes una explicación paso a paso:

* **DELIMITER //**: Establece el delimitador personalizado como //. Esto es necesario para que MySQL pueda manejar los bloques de código dentro del procedimiento almacenado. Después de definir el procedimiento almacenado, volveremos a establecer el delimitador en su valor predeterminado (;).

*** CREATE PROCEDURE MiProcedimiento()**: Define el procedimiento almacenado con el nombre MiProcedimiento. Puedes incluir parámetros entre los paréntesis si tu procedimiento los requiere.

* **BEGIN y END**: Encierran el cuerpo del procedimiento almacenado. Dentro de este bloque, puedes agregar cualquier código SQL necesario para realizar la lógica del procedimiento almacenado. En este ejemplo, se ha incluido una consulta SELECT simple como ejemplo.

* **DELIMITER ;**: Restablece el delimitador a su valor predeterminado (;) para que puedas ejecutar declaraciones SQL normales nuevamente.

Para crear el procedimiento almacenado, ejecuta este script SQL en tu cliente de MySQL o en una herramienta de administración de bases de datos que admita la ejecución de scripts SQL.

Después de crear el procedimiento almacenado, puedes llamarlo desde tu aplicación o herramienta de gestión de bases de datos utilizando su nombre. También puedes modificar y mantener el procedimiento almacenado según sea necesario.

**Aclaración de los componentes de los procedimientos**

El uso de OR REPLACE permite sobrescribir un procedimiento existente. Si se omite, y el procedimiento existe, se producirá, un error.

La sintaxis es muy parecida a la de un bloque anónimo, salvo porque se reemplaza la sección DECLARE por la secuencia PROCEDURE ... IS en la especificación del procedimiento. En otros casos no es especificada la secuencia “IS”, y se define la secuencia “DECLARE” dentro del segmento BEGIN – END.

Debemos especificar el tipo de datos de cada parámetro. Al especificar el tipo de dato del parámetro no debemos especificar la longitud del tipo.

Los parámetros pueden ser de entrada (IN), de salida (OUT) o de entrada salida (IN OUT). El valor por defecto es IN, y se toma ese valor en caso de que no especifiquemos nada.

La implementación de la lógica en los procedimientos almacenados en SQL implica escribir instrucciones SQL que realicen una serie de tareas específicas dentro del procedimiento. A continuación, se presentan algunos ejemplos de cómo puedes implementar lógica en procedimientos almacenados para realizar tareas comunes:

### IMPLEMENTACIÓN DE LA LÓGICA EN LOS PROCEDIMIENTOS

> Nota: el símbolo @ a la izquierda de la variable es equivalente a decir que es una variable global o pública como es conocida en otros lenguajes.
> 


1. **Selección de Datos (SELECT)**:

   Puedes utilizar la instrucción `SELECT` para recuperar datos de una tabla y, opcionalmente, almacenarlos en variables o devolverlos como resultado del procedimiento. Por ejemplo, para seleccionar datos de una tabla llamada `clientes` y almacenarlos en una variable:

   ```sql
   DECLARE @nombreCliente VARCHAR(50);
   
   SELECT nombre INTO @nombreCliente FROM clientes WHERE id = 1;
   ```

2. **Inserción de Datos (INSERT)**:

   Puedes utilizar la instrucción `INSERT` para agregar nuevos registros a una tabla. Por ejemplo, para insertar un nuevo cliente en una tabla `clientes`:

   ```sql
   INSERT INTO clientes (nombre, correo) VALUES ('Nuevo Cliente', 'nuevo@cliente.com');
   ```

3. **Actualización de Datos (UPDATE)**:

   Puedes utilizar la instrucción `UPDATE` para modificar registros existentes en una tabla. Por ejemplo, para actualizar el nombre de un cliente con un ID específico:

   ```sql
   UPDATE clientes SET nombre = 'Nuevo Nombre' WHERE id = 1;
   ```

4. **Eliminación de Datos (DELETE)**:

   Puedes utilizar la instrucción `DELETE` para eliminar registros de una tabla. Por ejemplo, para eliminar un cliente con un ID específico:

   ```sql
   DELETE FROM clientes WHERE id = 1;
   ```

5. **Lógica de Control (IF-ELSE)**:

   Puedes utilizar declaraciones condicionales como `IF` y `ELSE` para implementar lógica de control en tus procedimientos almacenados. Por ejemplo, para seleccionar datos basados en una condición:

   ```sql
   IF @condicion = 1 THEN
       SELECT * FROM tabla1;
   ELSE
       SELECT * FROM tabla2;
   END IF;
   ```

6. **Bucles (WHILE)**:

   Puedes utilizar bucles como `WHILE` para repetir una serie de instrucciones hasta que se cumpla una condición. Por ejemplo, para recorrer una tabla y realizar una acción para cada fila:

   ```sql
   DECLARE @contador INT;
   SET @contador = 1;
   
   WHILE @contador <= 10 DO
       -- Realizar acción aquí
       SET @contador = @contador + 1;
   END WHILE;
   ```

La declaración de variables dentro del procedimiento almacenado, así como se utiliza para handlers y cursores.

Esta instrucción puede usarse dentro de las etiquetas begin y end las cuales engloban el cuerpo de instrucciones del procedimiento, también es posible asignar un tipo de variable y un valor default.


7. **Gestión de Transacciones**:

   Puedes utilizar transacciones para garantizar que una serie de instrucciones se ejecuten de manera exitosa o se reviertan completamente si ocurre un error. Por ejemplo, para iniciar una transacción y realizar una serie de acciones dentro de ella:

   ```sql
   START TRANSACTION;
   
   -- Instrucciones SQL aquí
   
   COMMIT; -- Confirma la transacción
   -- ROLLBACK; -- Revierte la transacción en caso de error
   ```
#### **CASE, REPEAT & CALL**

La sentencia `CASE` en SQL se utiliza para realizar una evaluación condicional y devolver un valor basado en esa evaluación. Puede ser utilizada en combinación con otras sentencias SQL, como `REPEAT` y `CALL`, para crear lógica más avanzada en tus procedimientos almacenados o consultas. A continuación, te mostraré un ejemplo de cómo podrías usar estas sentencias juntas en MySQL.

Supongamos que tienes una tabla llamada `pedidos` y deseas calcular un descuento en función del valor total de cada pedido y luego repetir una acción en función de ese descuento. Aquí hay un ejemplo de cómo podrías hacerlo utilizando una sentencia `CASE`, `REPEAT`, y `CALL`:

```sql
DELIMITER //

CREATE PROCEDURE ProcesarPedidosConDescuento()
BEGIN
    DECLARE total_pedido DECIMAL(10, 2);
    DECLARE descuento DECIMAL(5, 2);
    
    -- Itera sobre los pedidos
    DECLARE done INT DEFAULT 0;
    DECLARE cur CURSOR FOR SELECT total FROM pedidos;
    DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = 1;
    
    OPEN cur;
    
    read_loop: LOOP
        FETCH cur INTO total_pedido;
        
        IF done THEN
            LEAVE read_loop;
        END IF;
        
        -- Calcula el descuento en función del total del pedido
        SET descuento = CASE
            WHEN total_pedido >= 1000 THEN 0.1 * total_pedido
            WHEN total_pedido >= 500 THEN 0.05 * total_pedido
            ELSE 0
        END CASE;
        
        -- Llama a una función o procedimiento basado en el descuento
        CALL RealizarDescuento(total_pedido, descuento);
    END LOOP;
    
    CLOSE cur;
END;
//

DELIMITER ;
```

En este ejemplo:

- Creamos un procedimiento almacenado llamado `ProcesarPedidosConDescuento` que calcula el descuento para cada pedido y luego llama a un procedimiento llamado `RealizarDescuento` (que debe existir en la base de datos) para realizar alguna acción basada en el descuento.

- Utilizamos un cursor para iterar sobre los pedidos y calcular el descuento para cada uno de ellos.

- La sentencia `CASE` se utiliza para determinar el descuento en función del valor total del pedido. Dependiendo del valor total, se calcula un descuento diferente.

- Llamamos al procedimiento `RealizarDescuento` y pasamos el valor total del pedido y el descuento como argumentos.

Este es un ejemplo básico de cómo combinar las sentencias `CASE`, `REPEAT`, y `CALL` en un procedimiento almacenado en MySQL. La lógica real y las acciones a realizar en función del descuento dependerán de tus necesidades específicas y de la estructura de tu base de datos.

#### **CURSORES**
En SQL, un cursor es una estructura de control que permite a un programa o procedimiento almacenado recorrer y manipular filas de un conjunto de resultados de una consulta SQL de manera secuencial. Los cursores son especialmente útiles cuando necesitas trabajar con una o varias filas de datos en un conjunto de resultados, realizar operaciones fila por fila o aplicar lógica de programación más compleja en la base de datos.

Aquí tienes algunas características clave de los cursores:

1. **Recorrido Secuencial**: Los cursores permiten recorrer las filas de un conjunto de resultados una por una, en un orden específico (por ejemplo, ascendente o descendente), a medida que se avanza a través de ellas.

2. **Selección Personalizada**: Puedes utilizar una consulta SQL para seleccionar un conjunto de resultados que satisfaga ciertos criterios y, luego, usar un cursor para recorrer y trabajar con las filas seleccionadas.

3. **Uso en Procedimientos Almacenados**: Los cursores son comúnmente utilizados en procedimientos almacenados y funciones de bases de datos para realizar operaciones más complejas en los datos.

4. **Declaración, Apertura, Lectura y Cierre**: Para usar un cursor, generalmente se siguen estos pasos:
   - Declaración: Se define el cursor y se especifica la consulta SQL que se utilizará.
   - Apertura: Se abre el cursor para iniciar el recorrido de las filas.
   - Lectura: Se leen las filas una por una y se realizan las operaciones necesarias.
   - Cierre: Se cierra el cursor una vez que se han procesado todas las filas.

5. **Tipos de Cursores**:
   - **Cursores Sensibles**: Permiten detectar cambios realizados en las filas mientras se recorre el conjunto de resultados. Esto es útil para mantener datos actualizados durante el recorrido.
   - **Cursores Insensibles**: No detectan cambios realizados en las filas mientras se recorren. Son más eficientes pero no reflejan cambios en tiempo real.
   - **Cursores de Solo Lectura**: Solo permiten la lectura de filas, no la modificación de datos.
   - **Cursores Actualizables**: Permiten la modificación de datos en las filas del conjunto de resultados.

6. **Ejemplo de Uso**:
   
```sql
DECLARE miCursor CURSOR FOR
SELECT nombre, edad FROM empleados;

OPEN miCursor;

FETCH NEXT FROM miCursor INTO @nombre, @edad;

WHILE @@FETCH_STATUS = 0
BEGIN
   -- Realizar operaciones con @nombre y @edad
   -- ...

FETCH NEXT FROM miCursor INTO @nombre, @edad;
END;

CLOSE miCursor;
DEALLOCATE miCursor;
```

Un cursor en SQL es una herramienta que permite recorrer y manipular filas de un conjunto de resultados de manera secuencial, lo que es útil para realizar operaciones fila por fila o aplicar lógica de programación más compleja en la base de datos. Sin embargo, debes usarlos con cuidado, ya que pueden tener un impacto en el rendimiento y deben cerrarse adecuadamente para liberar recursos.