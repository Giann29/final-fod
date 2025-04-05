
# Preguntas de Opción Múltiple

### 1. ¿Cuál de las siguientes afirmaciones sobre claves es correcta?
- a) La clave secundaria siempre es única.  
- b) La clave primaria puede repetirse en ciertos casos.  
- c) Una clave canónica sigue reglas de estandarización. ✅  
- d) No es posible usar claves en archivos.

### 2. ¿Qué técnica de acceso es más eficiente para recuperar registros específicos si se conoce su ubicación?
- a) Secuencial.  
- b) Directo. ✅  
- c) Serie.  
- d) Búsqueda lineal.

### 3. ¿Qué significa que un archivo tenga registros de longitud variable?
- a) Que todos los registros ocupan la misma cantidad de bytes.  
- b) Que los registros pueden variar en tamaño. ✅  
- c) Que solo algunos registros tienen claves únicas.  
- d) Que los registros no pueden ser ordenados.

### 4. ¿Cuál es una ventaja del acceso secuencial?
- a) Es el método más rápido en cualquier caso.  
- b) Permite encontrar registros con O(1) accesos.  
- c) Es útil cuando se deben leer todos los registros de un archivo. ✅  
- d) No requiere estructura de claves.

---

# Ejercicios Prácticos

## Ejercicio 1: Identificación de Claves
Dado el siguiente conjunto de datos, identifica una posible clave primaria y justifica tu elección.

| ID | Nombre | Dirección    | Teléfono  |
|----|--------|--------------|-----------|
| 1  | Juan   | Calle A 123  | 123-4567  |
| 2  | María  | Calle B 456  | 234-5678  |
| 3  | Pedro  | Calle C 789  | 123-4567  |

**Pregunta:**  
- ¿Cuál de las columnas sería la mejor opción para clave primaria? ¿Por qué?

**Solución:**  
La mejor opción para la clave primaria es la columna **ID** porque:
- **Unicidad:** Cada ID es único para cada registro.
- **Estabilidad:** El ID es invariable, mientras que los demás atributos (como el nombre o teléfono) pueden repetirse o cambiar.
- **Eficiencia:** Permite búsquedas rápidas y evita ambigüedades.

---

## Ejercicio 2: Comparación de Métodos de Acceso
Dado un archivo con 10,000 registros, compara el número de lecturas necesarias en cada método de acceso:

1. **Acceso Secuencial:** Se busca el registro 7,500.  
2. **Acceso Directo:** Se conoce la posición exacta del registro 7,500.

**Pregunta:**  
- ¿Cuántas lecturas se requieren en cada caso (en promedio) y por qué?

**Solución:**
- **Acceso Secuencial:**  
  En el acceso secuencial, se recorre la lista de registros desde el inicio hasta el registro deseado.  
  - **En el peor caso:** Se realizan 7,500 lecturas (si se encuentra al final del recorrido).  
  - **En promedio:** Se necesitan aproximadamente 7,500 lecturas, ya que se asume que se recorre la secuencia hasta llegar al registro buscado.

- **Acceso Directo:**  
  Con acceso directo, al conocer la posición exacta del registro (por ejemplo, mediante un cálculo basado en la longitud fija del registro), se realiza una única lectura.  
  - **Lecturas necesarias:** **1** lectura.


---

## Ejercicio 3: Estrategias de Eliminación y Recuperación de Espacio
Un archivo almacena registros de longitud fija de 128 bytes. Se requiere eliminar un registro sin afectar la estructura.

**Pregunta:**  
- Describe dos estrategias para la eliminación (lógica y física) y comenta sus ventajas y desventajas, considerando la reutilización del espacio.

**Solución:**  
Existen dos estrategias:

1. **Eliminación Lógica:**  
   - **Procedimiento:**  
     Se marca el registro como eliminado (por ejemplo, con un flag especial) sin borrarlo físicamente.
   - **Ventajas:**  
     - Rápido y sencillo de implementar.
     - Permite revertir la eliminación si es necesario.
   - **Desventajas:**  
     - El espacio no se recupera inmediatamente, lo que puede generar desperdicio de espacio hasta que se realice una compactación.

2. **Eliminación Física:**  
   - **Procedimiento:**  
     Se copia el contenido del archivo a uno nuevo, omitiendo los registros marcados como eliminados, o se reorganiza el archivo para compactar y liberar el espacio.
   - **Ventajas:**  
     - Se recupera el espacio de manera inmediata.
   - **Desventajas:**  
     - Puede ser costoso en términos de tiempo y procesamiento, especialmente para archivos grandes.
     - Requiere un proceso de reordenamiento o compactación.

---

## Ejercicio 4: Problemas en Registros de Longitud Variable
Se dispone de un archivo de registros de longitud variable. Durante una actualización, un registro modificado crece más allá del espacio asignado.

**Pregunta:**  
- ¿Qué problemas pueden surgir y qué soluciones se podrían aplicar (por ejemplo, desnormalización o reubicación) para gestionar este escenario?

**Solución:**  
**Problemas potenciales:**
- **Incapacidad de Reutilizar el Espacio Actual:**  
  Si el registro crece y el espacio asignado es insuficiente, no se puede escribir en el mismo lugar.
- **Fragmentación:**  
  La reubicación de registros puede generar espacios libres de tamaños variados, lo que provoca fragmentación interna o externa.

**Soluciones posibles:**
1. **Reubicación del Registro:**  
   - Mover el registro a un espacio libre que sea lo suficientemente grande, y actualizar el índice o puntero correspondiente.
   - Esto puede implicar el uso de un sistema de “enlaces” o punteros que indiquen la nueva ubicación.
2. **Reescritura al Final del Archivo:**  
   - Escribir el registro actualizado al final del archivo y dejar una referencia (o marcador) en el lugar original.
   - Ventaja: No se afecta la estructura actual del archivo.  
   - Desventaja: Puede generar un crecimiento del archivo y fragmentación si se hacen muchas actualizaciones.
3. **Reorganización Periódica:**  
   - Programar un proceso de compactación que reorganice los registros y elimine la fragmentación acumulada.

Cada solución tiene implicaciones en rendimiento y complejidad, por lo que la elección dependerá de la frecuencia de actualizaciones y del tamaño del archivo.