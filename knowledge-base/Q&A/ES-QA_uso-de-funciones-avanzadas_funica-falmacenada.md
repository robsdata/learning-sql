* # **FUNCIONES DE LINEA UNICA Y ALMACENADAS**
---


1. **¿Qué es una función de fila única en SQL y cuál es su característica principal?** Una función de fila única en SQL es una función que opera en una única fila de datos y devuelve un valor por cada fila que cumple con las condiciones de la consulta. Su característica principal es que actúa sobre una sola fila cada vez.

2. **¿Cuál es la diferencia fundamental entre las funciones de fila única y las funciones de agrupación en SQL?** La diferencia fundamental entre las funciones de fila única y las funciones de agrupación en SQL es que las funciones de fila única operan en una única fila a la vez y devuelven un valor por cada fila, mientras que las funciones de agrupación obtienen un resultado a partir de un conjunto de elementos.

3. **Menciona algunos tipos de funciones de fila única en SQL y proporciona ejemplos de cada uno.** Ejemplos de tipos de funciones de fila única en SQL son funciones de caracteres, funciones numéricas, funciones de fecha, funciones de conversión y funciones generales.

1. **¿Cuáles son algunas de las características de las funciones de fila única en SQL?** Algunas características de las funciones de fila única en SQL incluyen que actúan por cada fila retornada por la consulta, retornan un valor por cada fila, pueden retornar un valor de un tipo diferente al original, pueden aceptar uno o más argumentos y pueden ser usadas en las cláusulas SELECT, WHERE y ORDER BY, entre otras.

2. **¿En qué cláusulas de una consulta SQL se pueden utilizar las funciones de fila única?** Las funciones de fila única en SQL se pueden utilizar en las cláusulas SELECT, WHERE y ORDER BY.

3. **¿Qué lenguaje de programación se utiliza en el ejemplo proporcionado para obtener una fila única en MySQL?** El lenguaje de programación utilizado en el ejemplo proporcionado para obtener una fila única en MySQL es Python, utilizando la biblioteca pymysql para interactuar con la base de datos.

4. **Describe los pasos principales para obtener una fila única en MySQL utilizando el ejemplo de código en Python.** Los pasos principales para obtener una fila única en MySQL utilizando el ejemplo de código en Python son: importar el módulo pymysql, establecer la conexión a la base de datos, definir la consulta SQL, ejecutar la consulta, obtener la fila de resultados y procesar los resultados. Luego, se cierra la conexión a la base de datos.

5. **¿Qué funciones comunes de MySQL se mencionan en el texto que se pueden utilizar para realizar consultas y obtener resultados específicos?** Algunas funciones comunes de MySQL mencionadas en el texto que se pueden utilizar para realizar consultas y obtener resultados específicos son: SELECT, COUNT, SUM, AVG, MAX, MIN, CONCAT, DATE_FORMAT, NOW, IFNULL o COALESCE.


6.  **¿Qué son las funciones almacenadas en SQL y cuál es su propósito principal?** Las funciones almacenadas en SQL son bloques de código SQL que se almacenan en la base de datos y se pueden invocar y reutilizar en múltiples consultas. Su propósito principal es encapsular lógica de negocio, mejorar la seguridad y reutilizar código en aplicaciones y sistemas de bases de datos.

7.  **Proporciona un ejemplo de una función almacenada en MySQL y explica sus componentes principales.**

Ejemplo de una función almacenada en MySQL:
   ```sql
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
   END
   ```
   En este ejemplo, se crea una función llamada `CalcularSalarioAnual` que toma dos parámetros de entrada, calcula el salario anual en función de los meses trabajados y el salario mensual, y devuelve el resultado como un valor decimal.