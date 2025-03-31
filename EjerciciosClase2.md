## Ejercicios de Normalización

### Ejercicios Prácticos
1. **Convertir a 1FN:**  
   Dada la siguiente tabla:
    ```
    Factura(ID_Factura, Cliente, Productos) 1, Juan, Laptop, Mouse 2, Ana, Teclado
    ```
    **Pregunta:** ¿Cómo convertir esta tabla a Primera Forma Normal (1FN)?

2. **Convertir a 2FN:**  
Dada la siguiente tabla en 1FN:
    ```
    Factura(ID_Factura, Cliente, Dirección, Producto)
    ```
    **Pregunta:** ¿Qué atributos se deben separar para lograr que la tabla cumpla con la Segunda Forma Normal (2FN)?

3. **Convertir a 3FN:**  
Dada la siguiente tabla en 2FN:
    ```
    Empleado(ID_Empleado, Nombre, ID_Departamento, Nombre_Departamento)
    ```
**Pregunta:** ¿Cómo normalizar esta tabla a la Tercera Forma Normal (3FN)?

4. **Ejercicio Extra – Desnormalización:**  
Describe un escenario en el que la desnormalización podría ser beneficiosa y explica cómo se implementaría de forma controlada para mejorar el rendimiento en consultas.

---

## Preguntas de Opción Múltiple

### Primera Forma Normal (1FN)
1. **¿Cuál de las siguientes opciones NO es una regla de la 1FN?**  
- a) Todos los atributos deben ser atómicos.  
- b) No deben existir grupos repetitivos.  
- c) Se eliminan todas las claves foráneas.  
- d) Cada columna debe contener un único tipo de datos.

### Segunda Forma Normal (2FN)
2. **Si una tabla cumple con 1FN pero no con 2FN, significa que…**  
- a) Tiene grupos repetitivos.  
- b) Un atributo no clave depende solo de parte de la clave primaria.  
- c) Tiene dependencias transitivas.  
- d) No tiene clave primaria.

### Tercera Forma Normal (3FN)
3. **¿Qué problema resuelve la 3FN en una base de datos?**  
- a) La existencia de claves foráneas.  
- b) La existencia de dependencias parciales.  
- c) La existencia de dependencias transitivas.  
- d) La eliminación de claves primarias.

### Boyce-Codd Normal Form (BCNF)
4. **¿Qué condición adicional impone la BCNF sobre la 3FN?**  
- a) Todos los atributos deben ser atómicos.  
- b) Todas las dependencias funcionales deben provenir de una clave candidata.  
- c) Todas las claves primarias deben ser únicas.  
- d) Se eliminan todas las claves foráneas.
