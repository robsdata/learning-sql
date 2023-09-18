# **CONSULTAS COMBINADAS**
---


**Preguntas sobre Optimización de Consultas:**

1. ¿Por qué es importante optimizar las instrucciones de acceso a base de datos?
   - Respuesta: Es importante optimizar las instrucciones de acceso a la base de datos para mejorar el rendimiento y la eficiencia de las consultas, lo que reduce el tiempo de respuesta y la carga en el sistema de la base de datos.

2. ¿Qué componentes se pueden identificar para mejorar el acceso a la información en una base de datos?
   - Respuesta: Algunos componentes para mejorar el acceso a la información incluyen la optimización de consultas, el uso de índices, la normalización de datos y la gestión adecuada de la estructura de la base de datos.

**Preguntas sobre Consultas Combinadas:**

3. ¿Cuáles son los tres tipos principales de consultas combinadas en SQL?
   - Respuesta: Los tres tipos principales de consultas combinadas en SQL son la combinación interna (INNER JOIN), la combinación externa (LEFT JOIN, RIGHT JOIN, FULL OUTER JOIN) y las uniones (UNION).

4. ¿Qué cláusula se utiliza para especificar cómo se deben combinar las filas en las consultas combinadas en SQL?
   - Respuesta: La cláusula JOIN se utiliza para especificar cómo se deben combinar las filas en las consultas combinadas en SQL.

5. ¿Qué devuelve una consulta INNER JOIN en SQL?
   - Respuesta: Una consulta INNER JOIN en SQL devuelve solo las filas que tienen coincidencias en ambas tablas que se están combinando.

**Preguntas sobre Combinación Interna:**

6. ¿Qué es una combinación interna (INNER JOIN) en SQL?
   - Respuesta: Una combinación interna (INNER JOIN) en SQL es una operación que combina filas de dos o más tablas basadas en una condición de unión específica, devolviendo solo las filas con valores coincidentes en ambas tablas.

7. ¿Cuál es la sintaxis básica de un INNER JOIN en SQL?
   - Respuesta: La sintaxis básica de un INNER JOIN en SQL es: `SELECT columnas FROM tabla1 INNER JOIN tabla2 ON tabla1.columna = tabla2.columna;`

8. Proporciona un ejemplo práctico de un INNER JOIN en SQL.
   - Respuesta: Un ejemplo podría ser: `SELECT empleados.nombre, departamentos.nombre AS nombre_departamento FROM empleados INNER JOIN departamentos ON empleados.departamento_id = departamentos.id;`

**Preguntas sobre Combinación Externa:**

9. ¿Qué es una combinación externa en SQL y cuál es su propósito?
   - Respuesta: Una combinación externa en SQL es una operación que combina filas de dos o más tablas, incluyendo filas que coinciden en la condición de unión y filas que no coinciden en una de las tablas. Su propósito es recuperar datos incluso cuando no hay coincidencias en una de las tablas.

10. ¿Cuál es la diferencia entre LEFT JOIN y RIGHT JOIN en SQL?
    - Respuesta: La diferencia es que LEFT JOIN recupera todas las filas de la tabla de la izquierda y las filas coincidentes de la tabla de la derecha, mientras que RIGHT JOIN recupera todas las filas de la tabla de la derecha y las filas coincidentes de la tabla de la izquierda.

11. ¿En qué situación utilizarías un FULL OUTER JOIN en SQL?
    - Respuesta: Un FULL OUTER JOIN se utiliza cuando deseas recuperar todas las filas de ambas tablas, incluyendo las filas coincidentes y las que no coinciden en ninguna de las tablas.

**Preguntas sobre Uniones:**

12. ¿Qué son las uniones (UNION) en SQL y cuál es su propósito?
    - Respuesta: Las uniones (UNION) en SQL se utilizan para combinar los resultados de dos o más consultas en una sola tabla resultante. Su propósito es combinar datos de múltiples fuentes o tablas en un conjunto de resultados único.

13. ¿Cuáles son algunas reglas clave al utilizar UNION en SQL?
    - Respuesta: Algunas reglas clave incluyen que las consultas individuales deben tener la misma cantidad de columnas, las columnas deben tener tipos de datos compatibles y las columnas deben seleccionarse en el mismo orden en todas las consultas individuales.

14. ¿Qué hace UNION en SQL en caso de filas duplicadas en las consultas individuales?
    - Respuesta: UNION elimina las filas duplicadas en el conjunto de resultados final.

15. ¿Cuándo utilizarías UNION ALL en lugar de UNION en SQL?
    - Respuesta: UNION ALL se utiliza cuando deseas incluir todas las filas, incluidas las duplicadas, en el conjunto de resultados final. Se usa cuando no deseas eliminar filas duplicadas.