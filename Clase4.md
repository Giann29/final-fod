# **Fundamentos de Organización de Datos - Clase 4**

## **1. Búsqueda de Información**
La búsqueda de información en archivos implica dos factores clave:
- **Número de comparaciones:** Cuántas veces se compara un dato antes de encontrarlo.
- **Número de accesos:** Cuántas operaciones en disco se requieren.

Para mejorar el rendimiento, se pueden usar métodos más eficientes de búsqueda.

### **1.1 Métodos de Búsqueda**
1. **Búsqueda Secuencial**
   - Se recorre el archivo desde el principio hasta encontrar el dato.
   - Ineficiente para archivos grandes.
   - Su desempeño es **O(N)** en el peor caso.

2. **Búsqueda Directa**
   - Se accede directamente a la posición deseada si se conoce el **Número de Registro Relativo (NRR)**.
   - Mucho más rápida, pero requiere que los registros sean de **longitud fija** y acceso estructurado.

3. **Búsqueda Binaria**
   - **Precondiciones:**
     - El archivo debe estar **ordenado** por clave.
     - Los registros deben tener **longitud fija**.
   - Se divide el archivo en mitades sucesivas, reduciendo el espacio de búsqueda.
   - **Complejidad:** \( O(\log_2 N) \), lo que la hace mucho más rápida que la secuencial.

---

## **2. Clasificación de Archivos**
Ordenar un archivo permite mejorar el rendimiento de la búsqueda binaria, pero tiene un costo en almacenamiento y procesamiento.

### **2.1 Métodos de Clasificación**
1. **Ordenación en RAM**
   - Si el archivo cabe en memoria RAM, se puede ordenar directamente.
   - Muy eficiente, pero limitada por el tamaño de la RAM.

2. **Ordenación mediante claves en RAM**
   - Solo las claves se almacenan en RAM, permitiendo ordenar sin mover los datos.
   - Reduce la carga en memoria, pero requiere múltiples accesos a disco.

3. **Ordenación Externa**
   - Para archivos que no caben en RAM, se usa un método en **tres pasos**:
     1. **Dividir** el archivo en partes más pequeñas.
     2. **Ordenar** cada parte por separado.
     3. **Fusionar (merge)** las partes ordenadas para reconstruir el archivo final.

### **2.2 Problemas de la Clasificación**
- **Mantener el archivo ordenado tiene un costo.**
- **Búsqueda binaria mejora la búsqueda secuencial, pero sigue requiriendo múltiples accesos a disco.**
- **No siempre es viable reordenar todo el archivo**, por lo que se pueden usar estructuras más eficientes como **árboles B+**.

