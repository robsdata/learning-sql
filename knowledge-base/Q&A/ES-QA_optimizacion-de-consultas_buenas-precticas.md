# **OPTIMIZACION DE CONSULTAS**
---

1. **¿Qué ventajas tiene el uso de tablas desnormalizadas en comparación con las tablas normalizadas en términos de velocidad de consulta?** Las tablas desnormalizadas pueden ofrecer una mayor velocidad de consulta en casos de grandes volúmenes de datos y altas velocidades de respuesta debido a que evitan la necesidad de unir varias tablas, pero pueden generar inconsistencias en la información.

2. **¿Cuáles son los campos que se recomiendan indexar en una base de datos?** Se recomienda indexar los siguientes campos:
- Claves Primarias.
- Claves Foráneas.
- Campos por los cuales se realizarán búsquedas.
- Campos por los cuales se va a ordenar.

3. **¿Por qué se sugiere evitar el uso de consultas externas en aplicaciones y en su lugar usar consultas almacenadas dentro del motor de base de datos?** Las consultas almacenadas ejecutan más rápido y directamente en el motor de base de datos, lo que mejora significativamente el rendimiento. Las consultas externas pueden generar una baja de rendimiento considerable al realizar joins y consultas directamente en la aplicación.

4. **¿Qué recomendaciones se mencionan para optimizar la formulación de consultas SQL?**
Algunas recomendaciones para optimizar consultas SQL incluyen:
- Evitar el uso de "SELECT *" y seleccionar solo los campos necesarios.
- Utilizar Inner Join, left join, right join en lugar del where para unir tablas.
- Especificar el alias de la tabla delante de cada campo definido en el select.
- Evitar el uso de Cast y fórmulas dentro de las consultas.
- Ordenar las tablas en el from de menor a mayor según el número de registros.

5. **¿Qué se recomienda hacer si una consulta SQL toma más de un segundo en ejecutarse?** Si una consulta SQL toma más de un segundo en ejecutarse, se recomienda optimizarla. El trabajo debe comenzar con las consultas más necesarias o más usadas y luego proceder con las que más tiempo toman, aplicando las recomendaciones mencionadas anteriormente para mejorar el rendimiento.