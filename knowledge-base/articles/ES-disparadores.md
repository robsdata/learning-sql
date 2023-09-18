# ¿QUÉ SON LOS DISPARADORES?
---
Los disparadores, también conocidos como "triggers" en inglés, son objetos de base de datos que se utilizan en sistemas de gestión de bases de datos (DBMS) para automatizar acciones o ejecutar código en respuesta a eventos específicos que ocurren en una tabla o vista de la base de datos. Los disparadores se activan automáticamente cuando se cumple una condición o evento definido, como una inserción, actualización o eliminación de datos en una tabla.

Aquí tienes una explicación más detallada sobre los disparadores:

1. **Eventos Desencadenantes**: Los disparadores se asocian con eventos específicos que ocurren en una tabla, como INSERT (inserción de nuevos registros), UPDATE (actualización de registros existentes) o DELETE (eliminación de registros). Cuando se produce uno de estos eventos en la tabla asociada, el disparador se activa.

2. **Condición de Disparo**: Además del evento, un disparador se puede configurar para que se active solo si se cumple una cierta condición o conjunto de condiciones. Esto permite definir lógica más específica para determinar cuándo se debe ejecutar el disparador.

3. **Tipo de Disparador**:
   - **Disparadores Antes (BEFORE)**: Se ejecutan antes de que se realice la operación en la tabla. Pueden utilizarse para validar datos o realizar modificaciones previas a la inserción, actualización o eliminación de registros.
   - **Disparadores Después (AFTER)**: Se ejecutan después de que se haya completado la operación en la tabla. Pueden utilizarse para realizar acciones posteriores, como auditar cambios.
   - **Disparadores INSTEAD OF**: Puede utilizar INSTEAD OF para indicar al SGBD lo que tiene que hacer en lugar de realizar las acciones que invoca el disparador. Por ejemplo, podría usar un disparador INSTEAD OF en una vista para gestionar las inserciones en una tabla o para actualizar múltiples tablas que son parte de una vista.
   - **Disparadores de esquema**: puede crear disparadores sobre operaciones en el nivel de esquema tales como create table, alter table, drop table, audit, rename, truncate y revoke. Puede incluso, crear disparadores para impedir que los usuarios eliminen sus propias tablas. En su mayor parte, los disparadores de nivel de esquema proporcionan dos capacidades: impedir operaciones DDL y proporcionar una seguridad adicional que controle las operaciones DDL cuando estas se producen.
   - **Disparadores en nivel de base de datos**: Puede crear disparadores que se activen al producirse sucesos de la base de datos, incluyendo errores, inicios de sesión, conexiones y desconexiones. Puede utilizar este tipo de disparador para automatizar el mantenimiento de la base de datos o las acciones de auditoría.
   - **Disparadores de nivel de fila**: se ejecutan una vez para cada fila afectada por una instrucción DML. Los disparadores de nivel de fila se crean utilizando la cláusula for each row en el comando CREATE TRIGGER.
   - **Disparadores de nivel de instrucción**: se ejecutan una vez para cada instrucción DML. Por ejemplo, si una única instrucción INSERT inserta 500 filas en una tabla un disparador de nivel de instrucción, para dicha tabla sólo se ejecutará una vez. Los disparadores de nivel de instrucción son el tipo predeterminado que se crea con el comando CREATE TRIGGER.

4. **Acciones del Disparador**: Los disparadores pueden realizar una variedad de acciones, como:
   - Ejecutar código SQL personalizado.
   - Validar datos antes de que se realice la operación.
   - Registrar cambios en una tabla de auditoría.
   - Realizar acciones de registro o notificación.

5. **Aplicaciones Prácticas**:
   - Validación de Datos: Los disparadores pueden garantizar que los datos ingresados en una tabla cumplan con ciertas reglas o restricciones antes de la inserción.
   - Auditoría de Cambios: Los disparadores pueden llevar un registro de las modificaciones realizadas en una tabla para fines de auditoría y seguimiento.
   - Mantenimiento de Integridad Referencial: Los disparadores pueden garantizar la integridad referencial en la base de datos, como garantizar que no se eliminen registros relacionados en cascada.
   - Notificación de Eventos: Los disparadores pueden generar notificaciones o alertas automáticas en respuesta a eventos específicos.

6. **Ejemplos de Eventos**: Algunos ejemplos de eventos que pueden activar disparadores incluyen:
   - Inserción de un nuevo pedido en una tabla de pedidos.
   - Actualización de información de un empleado en una tabla de empleados.
   - Eliminación de un cliente de una tabla de clientes.

los disparadores son objetos de base de datos utilizados para automatizar acciones en respuesta a eventos específicos en una tabla. Permiten la ejecución de lógica personalizada antes o después de las operaciones en la base de datos y son una herramienta poderosa para garantizar la integridad de los datos, auditar cambios y automatizar tareas en un sistema de gestión de bases de datos.

## CARACTERÍSTICAS DE LOS TRIGGERS
Los triggers permiten “disparar” (ejecutar) procedimientos almacenados cada vez que se realice una acción sobre los datos de una tabla. Esta acción puede consistir en la inserción, modificación o eliminación de un registro. De esta manera, podemos indicar que se ejecuten acciones sobre los datos de la tabla o de otras tablas, cada vez que se modifican, agregan o eliminan datos de una tabla.

### EJEMPLOS
**Ventajas de los triggers**
Algunos usos de los triggers son:

* Generación automática de valores derivados de una columna.
* Prevención de transacciones inválidas.
* Proporciona auditorías sofisticadas.
* Mantener la sincronía en tablas replicadas.
* Generación de estadísticas de acceso.
* Publicar información de los eventos generados por la base de datos, las actividades de los usuarios o de las estructuras SQL que se han ejecutado.
* Actualizar totales de la suma de campos de una tabla en otra.
* El mantenimiento de la aplicación se reduce, los cambios a triggers se reflejan automáticamente en todas las aplicaciones que tienen que ver con la tabla sin necesidad de recompilar.

**Consideraciones sobre triggers**
* Los triggers no tienen parámetros de entrada. Los únicos valores de entrada con los que pueden trabajar son los del registro que han insertado, modificado o eliminado.
* Los triggers no devuelven valores como los procedimientos almacenados. Sólo pueden modificar otras tablas o los mismos valores del registro agregado o modificado (obviamente, el eliminado no).
* Hay que tener especial cuidado con los triggers recursivos, es decir, aquellos que puedan realizar operaciones que lancen nuevos triggers.

**Tipos y sub tipos**
Dependiendo de la acción sobre la cual queremos que actúen, se pueden crear tres tipos de triggers:

* Al insertar un registro.
* Al modificar un registro.
* Al eliminar un registro.

Cada uno de estos tipos se puede dividir a su vez en dos subtipos: antes y después de la acción.

- **BEFORE**: Este tipo de trigger se debe ejecutar cuando, 
  - La acción del trigger debe determinar si le permite finalizar a la sentencia de disparo.
  - Si se deben verificar valores específicos de columnas antes de completar una sentencia de disparo INSERT o UPDATE.
- **AFTER**: Se debe emplear este tipo de trigger cuando:
  - Se quiere completar la sentencia de disparo antes de ejecutar la acción del trigger.
  - Si ya existe un trigger BEFORE un AFTER puede realizar diferentes acciones con la misma sentencia de disparo.

En consecuencia, podemos disponer de hasta seis tipos distintos de triggers:

* BEFORE INSERT. Antes de insertar un registro.
* AFTER INSERT. Después de insertar un registro.
* BEFORE UPDATE. Antes de modificar un registro.
* AFTER UPDATE. Después de modificar un registro.
* BEFORE DELETE. Antes de eliminar un registro.
* AFTER DELETE. Después de eliminar un registro.

## CREACION DE TRIGGERS

Para crear disparadores (triggers) en MySQL, debes seguir una sintaxis específica y definir cuándo y cómo deseas que se active el trigger. Aquí tienes los pasos básicos para crear un trigger en MySQL:

**Nota**: Los detalles exactos y las capacidades de los triggers pueden variar según la versión de MySQL que estés utilizando. Los ejemplos a continuación están basados en la sintaxis general de MySQL.

1. **Elegir el Momento de Activación**:
   - Un trigger se puede activar antes (BEFORE) o después (AFTER) de una operación como INSERT, UPDATE o DELETE en una tabla. Debes decidir cuándo quieres que se active el trigger.

2. **Definir el Evento**:
   - Especifica el evento que activará el trigger. Puede ser un evento de INSERT, UPDATE o DELETE.

3. **Seleccionar la Tabla**:
   - Indica en qué tabla se activará el trigger.

4. **Especificar la Condición (Opcional)**:
   - Puedes definir una condición que determine cuándo se ejecutará el trigger. Por ejemplo, puedes configurar el trigger para que se active solo si se cumplen ciertas condiciones específicas.

5. **Especificar el Cuerpo del Trigger**:
   - El cuerpo del trigger contiene las acciones que se realizarán cuando el trigger se active. Puedes incluir código SQL personalizado para llevar a cabo las acciones deseadas.

6. **Sintaxis General**:
   - Aquí está la sintaxis general para crear un trigger en MySQL:

   ```sql
   CREATE TRIGGER nombre_trigger
   {BEFORE | AFTER} {INSERT | UPDATE | DELETE} ON nombre_tabla
   [FOR EACH ROW]
   [WHEN condicion]
   BEGIN
       -- Código SQL aquí
   END;
   ```

   - `nombre_trigger`: El nombre que le das al trigger (debe ser único en la base de datos).
   - `{BEFORE | AFTER}`: Indica si el trigger se activará antes o después del evento.
   - `{INSERT | UPDATE | DELETE}`: Especifica el tipo de evento que activará el trigger.
   - `nombre_tabla`: La tabla en la que se activará el trigger.
   - `[FOR EACH ROW]`: Esta cláusula se utiliza para indicar que el trigger opera en cada fila afectada por la operación.
   - `[WHEN condicion]`: Una condición opcional que determina cuándo se ejecutará el trigger.
   - `BEGIN` y `END`: Encierran el cuerpo del trigger, donde se coloca el código SQL personalizado.
   - Variables posibles para update 
     - :old que hace referencia a los valores anteriores.
     - :new que hace referencia a los nuevos valores de actualización de la fila.

7. **Ejemplo de Creación de Trigger**:
   - Aquí hay un ejemplo de creación de un trigger que se activa antes de una inserción en una tabla llamada `pedidos`:

   ```sql
   CREATE TRIGGER antes_de_insertar_pedido
   BEFORE INSERT ON pedidos
   FOR EACH ROW
   BEGIN
       -- Código SQL personalizado aquí
       INSERT INTO registro_pedidos (mensaje) VALUES ('Nuevo pedido insertado');
   END;
   ```

   En este ejemplo, cuando se inserta un nuevo registro en la tabla `pedidos`, el trigger `antes_de_insertar_pedido` se activa antes de la inserción y registra un mensaje en la tabla `registro_pedidos`.

Una vez que hayas definido y creado tu trigger, se activará automáticamente cuando se cumplan las condiciones especificadas. Los triggers son útiles para automatizar acciones y lógica de base de datos en respuesta a eventos específicos. Asegúrate de entender completamente cómo funcionan los triggers antes de utilizarlos en tu base de datos, ya que pueden tener un impacto significativo en el comportamiento de tus tablas.

### INSTEAD OF

En SQL, especialmente en el contexto de bases de datos relacionales, la cláusula "INSTEAD OF" se utiliza en el contexto de "disparadores de sustitución" o "triggers INSTEAD OF". Los triggers INSTEAD OF son utilizados principalmente en sistemas de bases de datos para modificar el comportamiento de una sentencia DML (Data Manipulation Language) como INSERT, UPDATE o DELETE cuando se realiza en una vista (view).

La cláusula "INSTEAD OF" se usa para especificar qué acción o conjunto de acciones se deben llevar a cabo en lugar de la operación original en la vista. Esto permite que el usuario realice operaciones en una vista, pero en realidad, se ejecutan otras operaciones definidas por el trigger INSTEAD OF en la vista subyacente.

Aquí hay un ejemplo para aclarar el concepto:

Supongamos que tienes una vista llamada `MiVista` que combina datos de varias tablas y te permite realizar operaciones de inserción. Puedes crear un trigger INSTEAD OF en esa vista para definir qué sucede cuando alguien intenta insertar datos en ella.

```sql
CREATE TRIGGER trigger_insercion_instead_of
INSTEAD OF INSERT ON MiVista
FOR EACH ROW
BEGIN
    -- Código SQL personalizado aquí
    -- Define cómo se deben insertar los datos en las tablas subyacentes
    INSERT INTO Tabla1 (columna1, columna2) VALUES (NEW.valor1, NEW.valor2);
    INSERT INTO Tabla2 (columna3, columna4) VALUES (NEW.valor3, NEW.valor4);
    -- Puedes realizar otras acciones según tus necesidades
END;
```

En este ejemplo:

- Cuando alguien intenta insertar datos en `MiVista`, el trigger INSTEAD OF `trigger_insercion_instead_of` se activa en lugar de realizar la operación de inserción directamente en la vista.

- El trigger define cómo se deben insertar los datos en las tablas subyacentes (`Tabla1` y `Tabla2`) en lugar de insertarlos directamente en la vista.

- `NEW` se refiere a los valores que se están intentando insertar en la vista, y puedes usarlos para realizar las inserciones en las tablas subyacentes.

Los triggers INSTEAD OF son útiles cuando necesitas controlar y personalizar cómo se realizan las operaciones en vistas que combinan datos de múltiples tablas o cuando deseas aplicar lógica personalizada antes de que se realicen las operaciones en la vista.

Es importante tener en cuenta que la sintaxis y la funcionalidad de los triggers INSTEAD OF pueden variar según el sistema de gestión de bases de datos (DBMS) que estés utilizando. Por lo tanto, consulta la documentación de tu DBMS específico para obtener detalles precisos sobre cómo crear y utilizar triggers INSTEAD OF en tu entorno.

#### MYSQL | DISPARADORES DE SUSTITUCION

MySQL no admite la cláusula "INSTEAD OF" directamente en la creación de triggers. La cláusula "INSTEAD OF" se utiliza comúnmente en otros sistemas de gestión de bases de datos (DBMS) como SQL Server o PostgreSQL en el contexto de triggers en vistas (views) para controlar lo que sucede en lugar de una operación DML (Data Manipulation Language) en una vista. Sin embargo, MySQL tiene un enfoque diferente para resolver este tipo de problemas.

En MySQL, puedes lograr resultados similares mediante el uso de vistas actualizables y procedimientos almacenados. Aquí hay un enfoque general para abordar este escenario:

1. **Vistas Actualizables**: Crea una vista actualizable que combine datos de varias tablas y permita realizar operaciones DML (INSERT, UPDATE, DELETE) en ella. MySQL admite vistas actualizables si se cumplen ciertos requisitos, como tener una clave primaria en la vista y seguir reglas específicas de actualización.

2. **Procedimientos Almacenados**: Utiliza procedimientos almacenados (stored procedures) para manejar las operaciones de inserción, actualización o eliminación en lugar de la cláusula "INSTEAD OF". Dentro de los procedimientos almacenados, puedes controlar cómo se actualizan las tablas subyacentes según tus necesidades.

3. **Ejemplo**: Aquí hay un ejemplo simplificado de cómo podrías abordar la inserción de datos en una vista actualizable en MySQL utilizando un procedimiento almacenado:

   ```sql
   -- Crear una vista actualizable
   CREATE VIEW MiVista AS SELECT * FROM Tabla1 JOIN Tabla2 ON Tabla1.id = Tabla2.id;

   -- Crear un procedimiento almacenado para manejar inserciones en la vista
   DELIMITER //

   CREATE PROCEDURE InsertarEnMiVista(valor1 INT, valor2 VARCHAR(50))
   BEGIN
       -- Realizar validaciones o lógica personalizada aquí
       INSERT INTO Tabla1 (columna1, columna2) VALUES (valor1, valor2);
   END;
   //

   DELIMITER ;
   ```

En este ejemplo, la vista `MiVista` combina datos de `Tabla1` y `Tabla2`, y el procedimiento almacenado `InsertarEnMiVista` se encarga de realizar la inserción en `Tabla1`. Puedes agregar lógica personalizada en el procedimiento almacenado según tus necesidades.

Ten en cuenta que MySQL 8.0 y versiones posteriores pueden admitir ciertas funcionalidades de triggers en vistas, pero la cláusula "INSTEAD OF" no es una característica estándar en MySQL para manejar vistas actualizables. Es importante consultar la documentación específica de MySQL y las versiones más recientes para obtener información actualizada sobre esta funcionalidad.
