# Fundamentos de Bases de Datos – Clase 5

## 1. Índices en Bases de Datos

Los índices son estructuras auxiliares que aceleran la recuperación de registros en una base de datos. Funcionan de manera similar al índice de un libro, permitiendo ubicar rápidamente la posición de un registro sin recorrer toda la tabla.

### 1.1 Concepto de Índice
- **Definición:**  
  Un índice es una estructura de datos (normalmente compuesta por una clave y un campo de referencia) que facilita la búsqueda rápida de registros en un archivo de datos.
- **Ejemplo:**  
  En una tabla de `Clientes(ID, Nombre, Ciudad)`, un índice primario se crea sobre `ID` y un índice secundario podría crearse sobre `Ciudad` para facilitar la búsqueda por localidad.
- **Ventajas:**  
  - Acelera las búsquedas y consultas.
  - Mejora el rendimiento de las operaciones de lectura.
- **Desventajas:**  
  - Ocupa espacio adicional.
  - Requiere mantenimiento al insertar, actualizar o eliminar registros.

---

## 2. Tipos de Índices

### 2.1 Índices Primarios
- Se crean sobre la **clave primaria** de una tabla.
- Organizan físicamente los datos según los valores de la clave.
- **Ejemplo:**  
  Para la tabla `Libros(Código, Título, Autor)`, si `Código` es la clave primaria, el índice primario organizará físicamente los registros según `Código`.

### 2.2 Índices Secundarios
- Se crean sobre campos que **no son la clave primaria**.
- No alteran el orden físico de los registros, pero facilitan búsquedas alternativas.
- **Ejemplo:**  
  En la misma tabla `Libros`, se puede crear un índice secundario sobre `Autor` para buscar todos los libros de un determinado autor.
- **Implementación:**  
  Pueden usarse estructuras como arreglos con vectores de punteros o listas invertidas.  
  - **Lista invertida:** Cada entrada contiene la clave secundaria (ej.: "Beethoven") y una lista de referencias (punteros) a los registros con esa clave.

---

## 3. Organización de Archivos

### 3.1 Archivos Secuenciales
- Los registros se almacenan en un orden fijo, lo que facilita las búsquedas secuenciales.
- **Ejemplo:**  
  Un archivo de registros de ventas ordenado cronológicamente.
  
### 3.2 Archivos Indexados
- Se mantiene un índice sobre el archivo de datos para acelerar las búsquedas.
- **Ejemplo:**  
  Un archivo de empleados que utiliza un índice primario sobre `ID_Empleado` y un índice secundario sobre `Apellido` para búsquedas rápidas.

### 3.3 Archivos Hash
- Utilizan una función de dispersión para determinar la ubicación de un registro.
- Son muy eficientes para búsquedas exactas, pero no para rangos.
- **Ejemplo:**  
  Una base de datos de usuarios donde se calcula un hash a partir del nombre de usuario para ubicar rápidamente el registro correspondiente.

---

## 4. Estructuras de Índices: Árboles B y B+

### 4.1 Árbol B
- Es una estructura balanceada en la que cada nodo puede contener múltiples claves y punteros.
- **Ejemplo:**  
  Un árbol B que almacena claves numéricas (ej.: IDs) y permite inserciones y búsquedas en tiempo logarítmico.

### 4.2 Árbol B+
- Variante del árbol B: todas las claves se encuentran en las hojas y estas están enlazadas entre sí.
- **Ejemplo:**  
  En una base de datos de registros bancarios, un árbol B+ permite búsquedas rápidas por rango de fechas, ya que las hojas enlazadas facilitan la lectura secuencial.

---

## 5. Costos de Acceso

### 5.1 Sin Índices
- Las búsquedas requieren recorrer el archivo de manera secuencial, con un costo de **O(N)** en el peor caso.
- **Ejemplo:**  
  Buscar un cliente en un archivo sin índice puede requerir revisar todos los registros.

### 5.2 Con Índices
- Se puede emplear búsqueda binaria o estructuras de árbol, reduciendo significativamente el tiempo de acceso (por ejemplo, a **O(log N)** o **O(1)** en caso de acceso directo con hash).
- **Ejemplo:**  
  Con un índice primario sobre `ID`, se puede usar búsqueda binaria para encontrar un cliente en pocos pasos.

---

## 6. Operaciones Básicas con Índices

### 6.1 Inserción
- **Proceso:**  
  Al agregar un nuevo registro, se inserta la entrada en el archivo de datos y se actualiza el índice.
- **Ejemplo:**  
  Insertar un nuevo libro en la tabla `Libros` implica agregar el registro y luego insertar la nueva clave en el índice primario y, si existe, en el índice secundario.

### 6.2 Actualización
- **Sin cambio de clave:**  
  No se altera el índice si la clave permanece igual.
- **Con cambio de clave:**  
  Se debe actualizar y reorganizar el índice.
- **Ejemplo:**  
  Si se modifica el `Autor` de un libro, se debe actualizar el índice secundario correspondiente.

### 6.3 Eliminación
- **Proceso:**  
  Se elimina el registro en el archivo de datos y se actualiza el índice (se elimina o marca la entrada correspondiente).
- **Ejemplo:**  
  Al eliminar un libro, se remueve la entrada del registro en el índice primario y secundario para evitar referencias a datos inexistentes.

---

## 7. Persistencia y Mantenimiento de Índices

- **Persistencia:**  
  En sistemas donde el índice es muy grande, puede almacenarse en disco y cargarse en memoria mediante estructuras jerárquicas (como árboles B+).
- **Mantenimiento:**  
  Cada operación de inserción, actualización o eliminación debe reflejarse en el índice.
- **Ejemplo:**  
  Un sistema de gestión de bases de datos actualiza el índice secundario cada vez que se modifica un campo relevante en la tabla.
