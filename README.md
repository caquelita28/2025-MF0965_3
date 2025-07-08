Prmero realizamos el fork del repositorio.
Desde my sql compruebo la tabla sakila.customer.
Intento insertar y actualizar la bbdd real desde mySQL
CREATE TABLE world AS
SELECT * FROM sakila WHERE 1=0; -- Crea la estructura sin datos

-- Insertar los datos de la tabla original en la nueva tabla
INSERT INTO sakila
SELECT * FROM world;


### **Ejercicio: CRUD de Países con Tkinter** (6 puntos)

En este ejercicio vais a adaptar la aplicación original de gestión de clientes (“sakila customer”) para trabajar con las tablas `world.country` y `world.city` de la base de datos MySQL.
Sigue los siguientes pasos y organiza cada conjunto de cambios en un **commit independiente**.

---

#### Requisitos generales (Git)

- Mantener la **separación en capas** (UI, Service, Persistence).
- Cada cambio significativo debe ir en un **commit** aparte con mensaje descriptivo. **Cabe la posibiliodad de hacer más commits de los indicados**
- Prueba las operaciones de inserción y actualización en la base de datos real.
- Documenta brevemente en el README cómo ejecutar la aplicación y las dependencias necesarias.

#### Listado de países

*Tiempo estimado 20 minutos*

- Adaptar la capa de persistencia y la lógica de negocio para consultar la tabla `country`.

- La consulta SQL deberá devolver estos campos:

  1. `country.Code`
  2. `country.Name`
  3. `country.Population`

- Mostrar esos resultados en el `Treeview` de la UI.

> **Commit #1:** “Adapta la consulta a world.country de países”.

#### Capitales

*Tiempo estimado 20 minutos*

- Adaptar la capa de persistencia y la lógica de negocio para consultar la tabla `country` junto con la tabla `city` (capital).

- La consulta SQL deberá devolver estos campos:

  1. `country.Code`
  2. `country.Name`
  3. `country.Population`
  4. `city`.`Name` como Capital
  5. `city`.`POPULATION` como Población Capital

- Mostrar esos resultados en el `Treeview` de la UI.

> **Commit #2:** “Mostrar Pais y Capital”.

---

#### Panel de Alta / Edición de Países

*Tiempo estimado 30 minutos*

- Crear una nueva ventana (o diálogo) que sirva para **añadir** o **editar** un país.
- En esta ventana se deberán ver todos los campos del País

> **Commit #2:** “Crear panel de alta/edición de país”.

---

#### Conexión de botones “Añadir” / “Editar”

*Tiempo estimado 20 minutos*

- Modificar los botones de la UI principal para que:
  - Al pulsar **Añadir**, abra el formulario en modo “nuevo país”.
  - Al pulsar **Editar**, abra el mismo formulario rellenado con los datos del país seleccionado.
  - El panel de país tendrá un botón de `Guardar` con un callback que se le pasará como parámetro al instanciarse

> **Commit #4:** “Conectar botones Añadir/Editar al panel de país”.

#### Acción de “Añadir” / “Editar”

*Tiempo estimado 20 minutos*

- Definir un **callback** que se ejecute al pulsar “Guardar” y que invoque al `CountryService` para:
  - Insertar un nuevo registro en `country`
  - O actualizar los datos de un país existente
- Tras guardar los cambios, el `Treeview` deberá refrescarse automáticamente para reflejar la inserción o la actualización.

> **Commit #5:** “Guardar Añade/Editar los paises. Se refresca el listado”.

---
