# **Fundamentos de Bases de Datos - Clase 2**

## **1. Modelos de Bases de Datos**
Los modelos de bases de datos definen la forma en que los datos se organizan y se relacionan dentro del sistema. Existen varios tipos:

### **1.1 Modelo Jerárquico**
- Organiza la información en una estructura de árbol.
- Cada nodo padre puede tener múltiples hijos, pero cada hijo solo puede tener un padre.
- Se usa en sistemas antiguos como IBM IMS.
- **Ventajas:** Eficiente para búsquedas en estructuras fijas y bien definidas.
- **Desventajas:** Poca flexibilidad para relaciones complejas.

### **1.2 Modelo de Red**
- Permite relaciones más flexibles que el modelo jerárquico.
- Un nodo puede tener múltiples padres y múltiples hijos.
- Usado en el sistema IDMS de CODASYL.
- **Ventajas:** Mayor flexibilidad en la representación de relaciones.
- **Desventajas:** Mayor complejidad en la implementación y mantenimiento.

### **1.3 Modelo Relacional**
- Es el más utilizado en la actualidad.
- Representa la información en **tablas** (relaciones) con **filas** (tuplas) y **columnas** (atributos).
- Se basa en el álgebra relacional y usa **claves primarias** y **foráneas** para relacionar tablas.
- Ejemplo de SGBD: **MySQL, PostgreSQL, Oracle, SQL Server**.
- **Ventajas:** Fácil de usar, con soporte teórico sólido y gran cantidad de herramientas.
- **Desventajas:** Puede requerir complejos procesos de normalización para evitar redundancias.

### **1.4 Modelo Orientado a Objetos**
- Integra los principios de la programación orientada a objetos con bases de datos.
- Permite almacenar estructuras de datos complejas como listas y objetos anidados.
- **Ventajas:** Maneja de forma natural relaciones complejas y jerárquicas.
- **Desventajas:** Menor estandarización y adopción en comparación con el modelo relacional.

---

## **2. Diseño de Bases de Datos**
El diseño de bases de datos consta de varias fases, que aseguran que la estructura final sea eficiente, escalable y se adapte a las necesidades del usuario:

### **2.1 Recolección de Requisitos**
- Identificar las necesidades del usuario y los datos relevantes.
- Reunir información mediante entrevistas, encuestas y análisis de procesos.

### **2.2 Modelo Conceptual**
- Representación abstracta mediante diagramas **Entidad-Relación (ER)**.
- Se identifican:
  - **Entidades**: Objetos principales (Ejemplo: Cliente, Producto).
  - **Atributos**: Propiedades de las entidades (Ejemplo: Nombre, Precio).
  - **Relaciones**: Conexiones entre entidades (Ejemplo: Un cliente realiza pedidos).
- **Sugerencia:** Usar herramientas de modelado (como ER/Studio, Lucidchart o Draw.io) para visualizar el modelo.

### **2.3 Modelo Lógico**
- Traduce el modelo conceptual a un formato que pueda ser implementado en un **Sistema de Gestión de Bases de Datos (SGBD)**.
- Se representa en términos de **tablas, claves primarias y claves foráneas**.
- **Consideración:** Durante este paso se definen restricciones y reglas de integridad.

### **2.4 Modelo Físico**
- Define cómo se almacenarán los datos en disco.
- Se optimiza el rendimiento a través de **índices, particionamiento y normalización**.
- **Aspectos a considerar:** Estrategias de indexación, distribución de datos y uso de memoria caché para mejorar el acceso a la información.

---

## **3. Normalización**
La normalización es un proceso para organizar los datos y minimizar la redundancia, asegurando la integridad y consistencia de la información. Se divide en varias **formas normales**:

### **3.1 Primera Forma Normal (1FN)**
#### **Reglas:**
1. Todos los atributos deben ser **atómicos** (no divisibles).
2. No deben existir **grupos repetitivos** en una tabla.
3. Cada columna debe contener un único tipo de datos.
- **Ejemplo (No normalizado)**:
    ```
    Clientes(ID, Nombre, Teléfonos) 1, Juan, 12345, 67890 2, Ana, 54321
    ```
- El campo **"Teléfonos"** contiene múltiples valores (no es atómico).

    #### **Corrección (En 1FN)**

    ```
    Clientes(ID, Nombre, Teléfono) 1, Juan, 12345 1, Juan, 67890 2, Ana, 54321
    ```
    - Se ha creado una nueva fila para cada número de teléfono.

### **3.2 Segunda Forma Normal (2FN)**
#### **Reglas:**
1. Debe estar en **1FN**.
2. Todos los atributos **no clave** deben depender **totalmente** de la clave primaria.
- **Ejemplo de tabla en 1FN pero no en 2FN**:
    ```
    Pedidos(ID_Pedido, ID_Cliente, Cliente, Dirección)
    ```
- **Cliente y Dirección** dependen de **ID_Cliente**, no de **ID_Pedido**.

#### **Corrección (En 2FN)**
- Se deben separar en dos tablas:
  ```
  Pedidos(ID_Pedido, ID_Cliente) 
  Clientes(ID_Cliente, Cliente, Dirección)
  ```
  - Ahora, **Cliente y Dirección** dependen solo de **ID_Cliente**.

### **3.3 Tercera Forma Normal (3FN)**
#### **Reglas:**
1. Debe estar en **2FN**.
2. No debe haber **dependencias transitivas** (un atributo no clave no debe depender de otro atributo no clave).

- **Ejemplo de tabla en 2FN pero no en 3FN**:
    ```
    Empleados(ID_Empleado, Nombre, ID_Departamento, Nombre_Departamento)
    ```
- **Nombre_Departamento** depende de **ID_Departamento**, no de **ID_Empleado**.

#### **Corrección (En 3FN)**
- Se deben separar en:
  ```
  Empleados(ID_Empleado, Nombre, ID_Departamento) 
  Departamentos(ID_Departamento, Nombre_Departamento)
  ```
    - Ahora, **Nombre_Departamento** está en una tabla separada.

### **3.4 Forma Normal de Boyce-Codd (BCNF)**
#### **Reglas:**
1. Debe estar en **3FN**.
2. **Cada determinante** debe ser una clave candidata.

#### **Ejemplo (No en BCNF)**
```
Profesores(ID_Profesor, ID_Curso, Aula)
```
- Un **curso** siempre se dicta en la **misma aula**, pero un **profesor** puede dictar varios cursos.
- **ID_Curso → Aula** (Aula depende solo de Curso, no de Profesor).

#### **Corrección (En BCNF)**
- Se separan en:
    ```
    Profesores(ID_Profesor, ID_Curso) Cursos(ID_Curso, Aula)
    ```
    - Ahora, **Aula** depende solo de **ID_Curso**.
---

### **3.5 Ventajas y Desventajas de la Normalización**
#### **Ventajas:**
- **Reducción de Redundancia:** Evita almacenar información duplicada.
- **Integridad de los Datos:** Minimiza anomalías de actualización, inserción y eliminación.
- **Eficiencia en el Almacenamiento:** Menor uso de espacio al evitar datos duplicados.
- **Mantenimiento Sencillo:** Facilita cambios y actualizaciones en la estructura de la base de datos.

#### **Desventajas:**
- **Complejidad de las Consultas:** Pueden requerirse múltiples joins, lo que afecta el rendimiento en consultas complejas.
- **Rendimiento:** En algunos casos, la alta normalización puede impactar negativamente la velocidad de recuperación de datos.
- **Desnormalización Necesaria:** En sistemas de alta demanda, puede ser necesario aplicar desnormalización para mejorar el rendimiento.

---

## **4. Desnormalización**
- **Definición:** Proceso inverso a la normalización, donde se introducen redundancias controladas para mejorar el rendimiento de las consultas.
- **Aplicación:** Se utiliza cuando la performance es crítica y las consultas requieren menos joins.
- **Ejemplo Práctico:** En sistemas de informes o análisis de grandes volúmenes de datos, se puede optar por una desnormalización parcial para agilizar las consultas.

---

## **5. Integridad y Seguridad de los Datos**
### **5.1 Integridad de Entidad**
- Cada fila en una tabla debe tener un identificador único (clave primaria).

### **5.2 Integridad Referencial**
- Se deben respetar las relaciones entre tablas a través de **claves foráneas**.
- Ejemplo: Si en la tabla "Pedidos" hay un campo "ID_Cliente", este debe existir en la tabla "Clientes".

### **5.3 Seguridad**
- Se implementan **usuarios y permisos** para restringir el acceso a los datos.
- **Ejemplo en SQL:**
  ```sql
  GRANT SELECT ON Clientes TO usuario1;
  REVOKE INSERT ON Clientes FROM usuario1;