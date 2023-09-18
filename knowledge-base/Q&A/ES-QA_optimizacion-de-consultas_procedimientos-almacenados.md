# **PROCEDIMIENTOS ALMACENADOS**
---


1. **¿Qué son los procedimientos almacenados en una base de datos?**
   
   Los procedimientos almacenados son objetos de base de datos que contienen instrucciones SQL predefinidas y se almacenan en el sistema de gestión de bases de datos (DBMS). Estas instrucciones pueden incluir consultas, actualizaciones, inserciones y otras operaciones SQL.

2. **¿Cuál es el propósito principal de los procedimientos almacenados?**

   El propósito principal de los procedimientos almacenados es encapsular la lógica de negocio en el servidor de bases de datos. Esto mejora la reutilización, la seguridad, el rendimiento y la mantenibilidad del código en aplicaciones que interactúan con la base de datos.

3. **¿En qué se diferencian los procedimientos almacenados de las consultas SQL regulares?**

   Los procedimientos almacenados son fragmentos de código SQL que se almacenan en la base de datos y se pueden invocar desde aplicaciones, mientras que las consultas SQL regulares se envían directamente a la base de datos desde la aplicación sin ser almacenadas previamente.

4. **¿Cuáles son los beneficios de utilizar procedimientos almacenados en una aplicación?**

   Los beneficios de utilizar procedimientos almacenados incluyen la reutilización de código, la seguridad mejorada, el rendimiento mejorado, la facilidad de mantenimiento, la gestión de transacciones, la parametrización, la abstracción de la base de datos, el control de versiones y la compilación.

5. **¿Qué tipos de operaciones SQL se pueden incluir en un procedimiento almacenado?**

   En un procedimiento almacenado se pueden incluir consultas (SELECT), actualizaciones (UPDATE), inserciones (INSERT), eliminaciones (DELETE) y otras operaciones SQL, así como lógica de control y programación.

6. **¿Cómo se llama el lenguaje en el que se suelen escribir los procedimientos almacenados?**

   Los procedimientos almacenados se suelen escribir en un lenguaje de bases de datos propietario. Cada sistema de gestión de bases de datos (DBMS) tiene su propio lenguaje de procedimientos almacenados.

7. **¿Qué es la reutilización de código y cómo se logra con los procedimientos almacenados?**

   La reutilización de código significa que la misma lógica de negocio se puede utilizar en múltiples partes de una aplicación sin necesidad de volver a escribirla. Se logra con los procedimientos almacenados al encapsular la lógica en un solo lugar, lo que permite su ejecución repetida desde diferentes partes de la aplicación.

8. **¿Cómo contribuyen los procedimientos almacenados a una mayor seguridad en una base de datos?**

   Los procedimientos almacenados permiten definir permisos de acceso específicos, lo que permite un control más preciso de quién puede ejecutar ciertas operaciones en la base de datos, mejorando así la seguridad.

9. **¿Cuál es la ventaja en términos de rendimiento de ejecutar procedimientos almacenados en el servidor de bases de datos?**

   Los procedimientos almacenados se compilan y optimizan en el servidor de bases de datos, lo que puede ofrecer un mejor rendimiento que enviar consultas SQL desde una aplicación, ya que no requieren compilación repetida.

10. **¿Por qué es más fácil realizar el mantenimiento de la lógica de negocio en un procedimiento almacenado?**

    El mantenimiento es más fácil porque los cambios en la lógica de negocio se pueden realizar en un solo lugar, evitando la duplicación de código en diferentes partes de la aplicación.
