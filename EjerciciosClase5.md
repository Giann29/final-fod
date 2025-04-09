## Preguntas de Opción Múltiple

1. **¿Cuál es la principal ventaja de usar un índice primario?**  
   - A) Permite múltiples registros con la misma clave.  
   - B) Organiza físicamente los datos en la tabla.  
   - C) Elimina la necesidad de índices secundarios.  
   - D) Aumenta el espacio en disco.  
   - **Respuesta:** B

2. **¿Qué estructura de datos es ideal para implementar índices que soporten búsquedas por rangos?**  
   - A) Árbol B+  
   - B) Tabla hash  
   - C) Lista enlazada  
   - D) Archivo secuencial  
   - **Respuesta:** A

3. **En un índice secundario, ¿qué información se almacena típicamente?**  
   - A) Solo la clave secundaria.  
   - B) La clave secundaria y la dirección o referencia a la clave primaria.  
   - C) La clave primaria completa.  
   - D) Un valor hash de la clave.  
   - **Respuesta:** B

4. **¿Cuál es una desventaja de mantener índices?**  
   - A) Disminuyen el rendimiento en las búsquedas.  
   - B) Requieren mantenimiento adicional al insertar, actualizar o eliminar registros.  
   - C) No permiten el acceso directo a los registros.  
   - D) Eliminan la necesidad de claves primarias.  
   - **Respuesta:** B

5. **¿Qué sucede cuando se actualiza un registro y cambia el valor de la clave?**  
   - A) El índice permanece igual.  
   - B) Se debe actualizar y posiblemente reordenar el índice correspondiente.  
   - C) Se elimina el índice automáticamente.  
   - D) La actualización no afecta al índice.  
   - **Respuesta:** B

---

## Ejercicios Prácticos

### Ejercicio 1: Diseño de un Índice Secundario
Dada una tabla `Libros(Código, Título, Autor, Año)`, donde `Código` es la clave primaria, diseña un índice secundario que permita buscar libros por `Autor`.
- **Pregunta:**  
  Explica qué campos contendrá el índice y cómo se relacionarán con la tabla principal.
- **Solución sugerida:**  
  El índice secundario debe contener el campo `Autor` (la clave secundaria) y la dirección del registro (por ejemplo, el NRR) o la clave primaria `Código`. De este modo, al buscar por `Autor`, se puede obtener la referencia al registro en la tabla `Libros`.

### Ejercicio 2: Actualización de Índices
Supón que tienes un índice primario implementado sobre una tabla de empleados. Si se modifica el `Apellido` de un empleado y ese campo forma parte de una clave compuesta, explica los pasos que se deben seguir para actualizar el índice.
- **Pregunta:**  
  Describe el proceso de actualización y la importancia de mantener la forma canónica.
- **Solución sugerida:**  
  Se debe eliminar la entrada antigua del índice y reinsertar el registro con la nueva clave. Es crucial convertir la nueva clave a la forma canónica (por ejemplo, todas en mayúsculas y sin espacios innecesarios) para mantener la consistencia y facilitar la búsqueda.

### Ejercicio 3: Evaluación de Rendimiento
Considera dos métodos de acceso para un archivo:
- **Método A:** Búsqueda secuencial en un archivo sin índices.
- **Método B:** Búsqueda usando un índice primario con búsqueda binaria.
  
Para un archivo de 100,000 registros, calcula el orden de magnitud en cuanto a número de comparaciones para cada método.
- **Pregunta:**  
  ¿Cuál método es más eficiente y por qué?
- **Solución sugerida:**  
  - **Búsqueda Secuencial:** En el peor caso, se realizan hasta 100,000 comparaciones.
  - **Búsqueda Binaria:** Se realizan aproximadamente log2(100,000) ≈ 17 comparaciones.
  Por lo tanto, la búsqueda usando un índice es significativamente más eficiente.

### Ejercicio 4: Implementación de Árbol B+
Explica las diferencias clave entre un árbol B y un árbol B+ y discute en qué escenario específico un árbol B+ es preferible.
- **Pregunta:**  
  Describe las ventajas de usar un árbol B+ en un sistema de bases de datos.
- **Solución sugerida:**  
  En un árbol B, las claves se distribuyen entre nodos internos y hojas; en un árbol B+ todas las claves están en las hojas, que están enlazadas para facilitar recorridos secuenciales. Un árbol B+ es preferible en sistemas donde se realizan muchas búsquedas por rangos o se requiere una lectura secuencial eficiente.
