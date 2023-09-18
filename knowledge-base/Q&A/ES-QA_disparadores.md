# **DISPARADORES DE BASE DE DATOS**
---

1. **¿Qué son los disparadores en bases de datos?**
   - Los disparadores, también conocidos como "triggers" en inglés, son objetos de base de datos que se utilizan en sistemas de gestión de bases de datos (DBMS) para automatizar acciones o ejecutar código en respuesta a eventos específicos que ocurren en una tabla o vista de la base de datos.

2. **¿Cuál es el propósito principal de los disparadores?**
   - El propósito principal de los disparadores es automatizar acciones en respuesta a eventos específicos en una tabla o vista de la base de datos, lo que permite ejecutar lógica personalizada antes o después de las operaciones en la base de datos.

3. **¿Qué eventos pueden desencadenar un disparador en una tabla?**
   - Los eventos que pueden desencadenar un disparador en una tabla incluyen INSERT (inserción de nuevos registros), UPDATE (actualización de registros existentes) y DELETE (eliminación de registros).

4. **¿Qué es una condición de disparo en el contexto de los disparadores?**
   - Una condición de disparo es una especificación opcional que determina cuándo se debe ejecutar un disparador. Permite definir lógica más específica para determinar cuándo se debe activar el disparador.

5. **¿Cuáles son los tres tipos principales de disparadores según el momento de activación?**
   - Los tres tipos principales de disparadores según el momento de activación son:
     - Disparadores "BEFORE" (Antes).
     - Disparadores "AFTER" (Después).
     - Disparadores "INSTEAD OF" (En lugar de).

6. **¿Cuál es la diferencia entre los disparadores "BEFORE" y "AFTER"?**
   - Los disparadores "BEFORE" se ejecutan antes de que se realice la operación en la tabla, mientras que los disparadores "AFTER" se ejecutan después de que se haya completado la operación en la tabla.

7. **¿Qué es un disparador "INSTEAD OF" y en qué contexto se utiliza?**
   - Un disparador "INSTEAD OF" se utiliza en el contexto de vistas (views) para indicar al sistema de gestión de bases de datos (DBMS) qué acción o conjunto de acciones debe llevar a cabo en lugar de realizar las operaciones que invoca el disparador. Esto permite personalizar el comportamiento de una vista.

8. **¿Qué es un disparador de esquema en bases de datos?**
   - Un disparador de esquema se utiliza para controlar operaciones en el nivel de esquema de la base de datos, como crear tablas, alterar tablas, eliminar tablas, auditar cambios y más. Proporciona seguridad adicional y control sobre las operaciones DDL (Data Definition Language).

9. **¿Cuál es la función de los disparadores de nivel de base de datos?**
   - Los disparadores de nivel de base de datos se activan en eventos de la base de datos, como errores, inicios de sesión, conexiones y desconexiones. Se utilizan para automatizar el mantenimiento de la base de datos o realizar acciones de auditoría.

10. **¿Cuál es la diferencia entre los disparadores de nivel de fila y los de nivel de instrucción?**
    - Los disparadores de nivel de fila se ejecutan una vez para cada fila afectada por una instrucción DML (Data Manipulation Language), mientras que los disparadores de nivel de instrucción se ejecutan una vez para cada instrucción DML.

11. **¿Qué tipo de acciones pueden realizar los disparadores en una base de datos?**
    - Los disparadores pueden realizar acciones como ejecutar código SQL personalizado, validar datos, registrar cambios en una tabla de auditoría y realizar acciones de registro o notificación.

12. **¿Cuáles son algunas aplicaciones prácticas de los disparadores en bases de datos?**
    - Algunas aplicaciones prácticas de los disparadores incluyen la validación de datos, la auditoría de cambios, el mantenimiento de la integridad referencial, la notificación de eventos y más.

13. **¿Qué son los eventos que pueden activar un disparador?**
    - Los eventos que pueden activar un disparador incluyen la inserción de un nuevo registro, la actualización de información y la eliminación de registros en una tabla.

14. **¿Cuáles son las ventajas de utilizar disparadores en bases de datos?**
    - Algunas ventajas de utilizar disparadores son la generación automática de valores derivados, la prevención de transacciones inválidas, la auditoría sofisticada, el mantenimiento de la sincronía en tablas replicadas y la automatización de tareas.

15. **¿Qué consideraciones se deben tener en cuenta al trabajar con disparadores, especialmente los recursivos?**
    - Al trabajar con disparadores, especialmente los recursivos, es importante tener cuidado con las operaciones que puedan generar nuevos disparadores. Además, es crucial comprender el flujo de ejecución de los disparadores para evitar bucles infinitos y asegurarse de que la lógica sea eficiente.