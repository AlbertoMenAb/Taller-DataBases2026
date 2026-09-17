<div align="center">

# INSTITUTO TECNOLÓGICO SUPERIOR DE MISANTLA
### ING EN SISTEMAS COMPUTACIONALES

---

##  Taller de Bases de Datos
**Reporte de Práctica:** Manejo de CREATE, INSERT, UPDATE and DELETE

---

### Presenta:
| Nombre Completo | Número de Control
| :--- | :---: |
| **MENDOZA ABAD JOSE ALBERTO** | 242T0087 | 

---

**Docente: Dr. IRAHAN OTONIEL JOSÉ GÚZMAN**    
**Semestre: 5to**    
**Fecha de Entrega:** 16-09-2026  

---

</div>

# Práctica de SQL con Python y SQLite

## Índice

1. [Introducción](#1-introducción)
2. [Declaración de conexión y funciones](#2-declaración-de-conexión-y-funciones)
3. [Tabla Comidas](#3-tabla-comidas)
   - [CREATE Comidas](#create-comidas)
   - [INSERT Comidas](#insert-comidas)
   - [UPDATE Comidas](#update-comidas)
   - [DELETE Comidas](#delete-comidas)
4. [Tabla Alumnos](#4-tabla-alumnos)
   - [CREATE Alumno](#create-alumno)
   - [INSERT Alumno](#insert-alumno)
   - [UPDATE Alumno](#update-alumno)
   - [DELETE Alumno](#delete-alumno)
5. [Tabla Productos](#5-tabla-productos)
   - [CREATE Productos](#create-productos)
   - [INSERT Productos](#insert-productos)
   - [UPDATE Productos](#update-productos)
   - [DELETE Productos](#delete-productos)
6. [Conclusión](#6-conclusión)

---

# 1. Introducción

En esta práctica se trabajó con una base de datos utilizando SQLite y Python, con el propósito de comprender y aplicar las operaciones fundamentales para la gestión de información mediante instrucciones SQL. Para ello, se crearon tres tablas con diferentes tipos de información: Comidas, Alumno y Productos. En cada una se aplicaron las operaciones de creación de estructuras, inserción de registros, actualización de datos y eliminación de información mediante las instrucciones CREATE, INSERT, UPDATE y DELETE.

Asimismo, se utilizaron consultas SELECT para comprobar los resultados obtenidos después de cada operación. De esta manera, la práctica permitió relacionar la sintaxis de SQL con situaciones concretas de manejo de información y observar directamente los cambios realizados en una base de datos.

---

# 2. Declaración de conexión y funciones

Para realizar la práctica se estableció inicialmente una conexión con una base de datos SQLite en memoria mediante `sqlite3`, junto con un cursor que permite ejecutar las instrucciones SQL. También se declararon las funciones `run()` y `query()`, las cuales serán utilizadas durante todo el desarrollo de la práctica y, por lo tanto, son comunes para las tres tablas.

La función `run()` permite ejecutar instrucciones que modifican la estructura o los datos de la base de datos, como CREATE, INSERT, UPDATE y DELETE, además de confirmar los cambios mediante `commit()`. Por otro lado, `query()` se utiliza para ejecutar consultas SELECT y mostrar los resultados en forma de tabla mediante `pandas`.

Esta configuración se realiza una sola vez al inicio, ya que las tres tablas utilizan la misma conexión y las mismas funciones.

<div align="center">
  <img src="img/Declaracion-de-conexion-y-funciones.png" alt="Fig. 1 Declaración de conexión y funciones" width="50%">
</div>


---

# 3. Tabla Comidas

En la tabla `Comidas` se realizó un ejercicio de gestión de información relacionada con alimentos, aplicando las operaciones básicas de una base de datos: creación de la tabla, inserción de registros, modificación de datos y eliminación de un registro. Con estas operaciones se comprobó cómo se puede administrar la información almacenada y verificar los cambios mediante consultas.

El código y los resultados obtenidos durante esta parte de la práctica se encuentran disponibles en el siguiente enlace de Google Colab:

[Google Colab - Tabla Comidas](https://colab.research.google.com/drive/1q02gZ-30kb9G-ySwPydSa9gcU0WOgwzY?usp=sharing)

## CREATE Comidas

Para comenzar, se eliminó la tabla `Comidas` en caso de que ya existiera mediante `DROP TABLE IF EXISTS`. Esto permite ejecutar nuevamente la práctica sin que se produzca un conflicto por una tabla creada anteriormente.

Posteriormente, mediante `CREATE TABLE`, se definió la estructura de la tabla, estableciendo las columnas `id`, `nombre`, `categoria`, `precio` y `disponible`, junto con sus respectivos tipos de datos y restricciones. El campo `id` se estableció como clave primaria para identificar de manera única cada comida, mientras que `nombre` y `precio` se definieron como campos obligatorios mediante `NOT NULL`.

Finalmente, se confirmó la creación mediante `conn.commit()` y se mostró el mensaje `"Tablas creadas: Comidas"`, indicando que la operación fue ejecutada correctamente.

### Evidencia

![CREATE Comidas](imagenes/Create_Comidas.png)

---

## INSERT Comidas

Una vez creada la estructura, se utilizaron instrucciones `INSERT` para agregar seis registros a la tabla `Comidas`. Cada registro contiene un identificador, nombre, categoría, precio y disponibilidad.

Los datos representan diferentes alimentos, como Ensalada Rusa, Pollo Frito, Helado, Hamburguesa, Sopa y Tampiqueña, con diferentes categorías y precios. El campo `disponible` utiliza valores booleanos para indicar si cada alimento se encuentra disponible inicialmente.

Después de realizar la inserción, se ejecutó una consulta `SELECT * FROM Comidas` para comprobar que los registros habían sido almacenados correctamente. La función `run()` también muestra el mensaje de confirmación correspondiente a la ejecución de la operación.

### Evidencia

![INSERT Comidas](imagenes/Insert_Comidas.png)

---

## UPDATE Comidas

Posteriormente, se realizó una modificación de los registros utilizando la instrucción `UPDATE`. Primero se estableció como disponible nuevamente cualquier comida cuyo campo `disponible` tuviera el valor `false`. De esta manera, el Helado y la Sopa pasaron a estar disponibles.

Después se realizó una segunda modificación para establecer específicamente como no disponible la Ensalada Rusa, identificándola mediante su `id` igual a 1.

Finalmente, se ejecutó una consulta `SELECT` para comprobar los cambios realizados. El resultado permite verificar que el Helado y la Sopa aparecen ahora como disponibles, mientras que la Ensalada Rusa aparece como no disponible.

### Evidencia

![UPDATE Comidas](imagenes/Update_Comidas.png)

---

## DELETE Comidas

Finalmente, se utilizó la instrucción `DELETE` para eliminar un registro de la tabla. En este caso se eliminó la Ensalada Rusa mediante la condición `WHERE id = 1`, utilizando su identificador para seleccionar únicamente ese registro y evitar afectar a las demás comidas.

Después de ejecutar la eliminación, se realizó nuevamente una consulta `SELECT * FROM Comidas` para comprobar el resultado. En la información obtenida ya no aparece la Ensalada Rusa, mientras que los demás registros permanecen en la tabla, lo que permite comprobar que la eliminación se realizó sobre el registro indicado.

### Evidencia

![DELETE Comidas](imagenes/Delete_Comidas.png)

---

# 4. Tabla Alumnos

En la tabla `Alumno` se trabajó con información de estudiantes, utilizando las operaciones básicas de SQL para crear su estructura, registrar los datos de cinco alumnos, modificar el grado escolar de uno de ellos y eliminar posteriormente el registro de un alumno que se dio de baja.

Estas operaciones permitieron observar de manera práctica cómo se agregan, actualizan y eliminan registros de una tabla, así como la forma de comprobar cada modificación mediante consultas.

El código y los resultados de esta parte de la práctica se encuentran disponibles en el siguiente enlace de Google Colab:

[Google Colab - Tabla Alumno](https://colab.research.google.com/drive/1hR2cYo2o-jkFVCjk8EigaOZYnf9q9EIr?usp=sharing)

## CREATE Alumno

Para crear la tabla `Alumno`, primero se utilizó `DROP TABLE IF EXISTS` para eliminar una tabla con el mismo nombre en caso de que ya existiera, permitiendo ejecutar la práctica nuevamente sin conflictos.

Después, mediante `CREATE TABLE`, se definió la estructura de la tabla con los campos `id_Alumno`, `nombre`, `grado`, `edad` y `promedio`. El campo `id_Alumno` se estableció como clave primaria para identificar de manera única a cada alumno, mientras que los campos `nombre`, `grado`, `edad` y `promedio` se establecieron como obligatorios mediante `NOT NULL`.

Una vez creada la estructura, se confirmó la operación mediante `commit()` y se mostró el mensaje `"Tabla creada: Alumno"`, indicando que la tabla fue creada correctamente.

### Evidencia

![CREATE Alumno](imagenes/Create_Alumno.png)

---

## INSERT Alumno

Una vez creada la tabla, se realizó la inserción de cinco registros mediante la instrucción `INSERT INTO`. En cada registro se proporcionaron los datos correspondientes al identificador, nombre, grado, edad y promedio de cada alumno.

Se agregaron los registros de Estela, Raul, Aurora, Cristina y Tobias, con diferentes grados, edades y promedios. Posteriormente, se utilizó una consulta `SELECT * FROM Alumno` para comprobar que los cinco registros fueron almacenados correctamente y visualizar la información resultante de la inserción.

### Evidencia

![INSERT Alumno](imagenes/Insert_Alumno.png)

---

## UPDATE Alumno

Posteriormente, se realizó una modificación en la información de la tabla mediante `UPDATE`. En este caso, se cambió el grado escolar de Cristina de `4to B` a `5to A`.

Para identificar específicamente el registro que debía modificarse se utilizó la condición `WHERE id_Alumno = 4`, correspondiente al identificador de Cristina.

Finalmente, se ejecutó una consulta `SELECT` utilizando `WHERE grado = '5to A'`, con el propósito de comprobar qué alumnos pertenecen a dicho grado después de realizar la modificación. El resultado permite verificar que Cristina aparece ahora junto con los demás alumnos que pertenecen a `5to A`.

### Evidencia

![UPDATE Alumno](imagenes/Update_Alumno.png)

---

## DELETE Alumno

Finalmente, se utilizó la instrucción `DELETE` para eliminar un registro de la tabla. En este caso se eliminó el registro correspondiente a Tobias, quien se dio de baja de la escuela.

Para seleccionar únicamente su registro se utilizó la condición `WHERE id_Alumno = 5`, ya que ese identificador corresponde a Tobias.

Después de ejecutar la eliminación, se realizó nuevamente una consulta `SELECT * FROM Alumno` para comprobar el estado final de la tabla. Como resultado, el registro de Tobias ya no aparece y permanecen los cuatro alumnos restantes.

### Evidencia

![DELETE Alumno](imagenes/Delete_Alumno.png)

---

# 5. Tabla Productos

En la tabla `Productos` se realizó un ejercicio enfocado en la administración de productos, registrando información como nombre, tipo, precio y existencia.

Durante esta parte de la práctica se creó la tabla, se insertaron cuatro productos, se modificaron sus existencias y se actualizó el precio de uno de ellos mediante una instrucción `UPDATE` con `CASE`. Finalmente, se eliminó uno de los productos y se verificó el estado final de la información mediante una consulta.

El código y los resultados obtenidos se encuentran disponibles en el siguiente enlace de Google Colab:

[Google Colab - Tabla Productos](https://colab.research.google.com/drive/11tPZoljSUlmB-jEgJ1TIZ1dBCAkqZKty?usp=sharing)

## CREATE Productos

Para crear la tabla `Productos`, primero se utilizó `DROP TABLE IF EXISTS` para eliminar una tabla con el mismo nombre en caso de que ya existiera.

Posteriormente, mediante `CREATE TABLE`, se definieron los campos `id_Producto`, `nombre`, `tipo`, `precio` y `existencia`, estableciendo sus respectivos tipos de datos. El campo `id_Producto` se estableció como clave primaria para identificar de manera única cada producto, mientras que `nombre`, `tipo` y `precio` se definieron como campos obligatorios mediante `NOT NULL`.

El campo `existencia` se dejó sin esta restricción para permitir almacenar la cantidad disponible de cada producto.

Finalmente, se confirmó la creación mediante `commit()` y se mostró el mensaje `"Tabla Creada: Productos"`, comprobando que la estructura fue creada correctamente.

### Evidencia

![CREATE Productos](imagenes/Create_Productos.png)

---

## INSERT Productos

Una vez creada la estructura de la tabla, se utilizaron instrucciones `INSERT INTO` para agregar cuatro productos. Para cada registro se especificaron su identificador, nombre, tipo, precio y existencia inicial.

Los productos registrados fueron CocaCola, Monster, Papas Adobadas y Tortillas, todos con una existencia inicial de cero.

Después de realizar la inserción, se ejecutó una consulta `SELECT * FROM Productos` para visualizar los registros y comprobar que los datos fueron almacenados correctamente en la tabla.

### Evidencia

![INSERT Productos](imagenes/Insert_Productos.png)

---

## UPDATE Productos

Posteriormente, se realizó una modificación de los productos mediante una sola instrucción `UPDATE`, utilizando expresiones `CASE` para asignar diferentes valores dependiendo del identificador de cada producto.

En el caso de la CocaCola, identificada con el `id_Producto` 1, se incrementó el precio de `52.99` a `55` y se estableció una existencia de 8 unidades.

Para los demás productos se mantuvo el precio original, mientras que sus existencias fueron modificadas individualmente: Monster quedó con 4 unidades, Papas Adobadas con 6 y Tortillas con 12.

El uso de `ELSE` permitió conservar el valor existente cuando un registro no correspondía a una de las condiciones especificadas. Finalmente, se utilizó `SELECT` para comprobar los cambios realizados y visualizar el nuevo estado de la tabla.

### Evidencia

![UPDATE Productos](imagenes/Update_Productos.png)

---

## DELETE Productos

Finalmente, se utilizó la instrucción `DELETE` para eliminar de la tabla el producto correspondiente a las Papas Adobadas.

Para identificar específicamente el registro que debía eliminarse se utilizó la condición `WHERE id_Producto = 3`.

Después de ejecutar la eliminación, se realizó nuevamente una consulta `SELECT * FROM Productos` para comprobar el resultado. Como consecuencia, el registro de las Papas Adobadas dejó de aparecer, mientras que los registros de CocaCola, Monster y Tortillas permanecieron en la tabla con las modificaciones realizadas anteriormente.

### Evidencia

![DELETE Productos](IMAGE/Delete_Productos.png)

---

# 6. Conclusión

La realización de esta práctica permitió comprender de manera práctica el funcionamiento de las principales operaciones utilizadas para administrar los datos de una base de datos. Mediante las tablas `Comidas`, `Alumno` y `Productos` se pudo practicar la creación de estructuras, el registro de información, la modificación de valores y la eliminación de registros, comprobando cada operación mediante consultas.

También se reforzó el uso de condiciones con `WHERE` y, en el caso de la tabla `Productos`, el uso de `CASE` para realizar diferentes modificaciones dentro de una misma instrucción `UPDATE`.

En conjunto, el ejercicio permitió fortalecer el manejo de SQL y comprender cómo las instrucciones ejecutadas desde Python pueden utilizarse para gestionar y verificar información almacenada en una base de datos.
