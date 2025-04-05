# Fundamentos de Organización de Datos - Clase 3

## 1. Tipos de Archivos
- **Archivos como secuencia de bytes:**  
  No poseen estructura definida, se tratan simplemente como una colección de bytes.
  
- **Archivos estructurados:**  
  Contienen registros y campos organizados.  
  - **Registros:** Pueden tener longitud fija o variable.  
  - **Campos:** Son la unidad lógicamente significativa de un registro; pueden ser de longitud fija o tener un indicador de longitud o delimitador para registros de longitud variable.

## 2. Claves en Archivos
- **Definición:**  
  Una **clave** permite identificar un registro de forma única dentro del archivo.
  
- **Tipos de Claves:**
  - **Primaria o Única:** Identifica de manera exclusiva un registro.
  - **Secundaria:** Permite búsquedas alternativas y no necesariamente es única.
  
- **Forma Canónica de una Clave:**  
  Es la representación estándar (por ejemplo, usando solo letras mayúsculas y sin espacios al final) para asegurar la consistencia en el registro de claves.

## 3. Performance en el Acceso a Archivos
- **Acceso Secuencial:**  
  Requiere recorrer registros uno a uno. En el peor caso, puede implicar O(n) comparaciones.
  
- **Acceso Directo:**  
  Permite acceder a un registro en una sola lectura (O(1)), siempre que se conozca la posición exacta (por ejemplo, mediante el Número Relativo de Registro - NRR).

## 4. Métodos de Acceso a Archivos
- **Serie:**  
  Los registros se leen en el orden físico de almacenamiento, uno tras otro.
  
- **Secuencial:**  
  Los registros están organizados por una clave, lo que permite un acceso ordenado.
  
- **Directo:**  
  Se accede al registro deseado de manera inmediata usando una referencia directa (por ejemplo, calculando la posición en base al NRR y la longitud fija).

## 5. Operaciones sobre Archivos
- **Altas, Bajas y Modificaciones:**
  - **Altas:** Agregar nuevos registros.
  - **Bajas:**  
    - **Baja Lógica:** Marca el registro como eliminado, pero no lo borra físicamente.  
    - **Baja Física:** Elimina definitivamente el registro, permitiendo su espacio para ser reutilizado.
  - **Modificaciones:**  
    Pueden generar problemas en registros de longitud variable si el nuevo dato es mayor y no cabe en el espacio asignado inicialmente.

## 6. Viaje de un Byte
Esta sección describe el recorrido de un byte cuando un programa escribe en un archivo:
- **Desde el Programa:**  
  El programa llama a la operación `Write` para escribir el contenido de una variable.
  
- **Administrador de Archivos:**  
  El sistema operativo transfiere la solicitud al administrador de archivos, que verifica la compatibilidad del archivo y localiza la posición física mediante la FAT (File Allocation Table).
  
- **Buffer de E/S:**  
  Se utiliza un buffer en la memoria para agrupar grandes bloques de datos y reducir las operaciones directas al disco.
  
- **Procesador de E/S:**  
  Se encarga de la transmisión de datos entre la memoria y el disco, liberando la CPU.
  
- **Controlador de Disco:**  
  Recibe la instrucción y transfiere el byte de forma física, posicionándose en el sector, pista y cilindro correctos.
  
Este flujo garantiza que, a pesar de la "lenta" velocidad de acceso al almacenamiento secundario, la operación se realice de forma eficiente.

## 7. Eliminación y Recuperación de Espacio
- **Eliminación de Registros:**
  - **Baja Lógica:** Se coloca una marca especial en el registro para indicar que ha sido eliminado. Es sencilla de implementar, pero el espacio no se recupera automáticamente.
  - **Baja Física:** Se copia el contenido a un nuevo archivo omitiendo los registros marcados, lo que permite liberar espacio, pero puede ser costoso en términos de tiempo y procesamiento.

- **Recuperación de Espacio:**
  - **Para Registros de Longitud Fija:**  
    Se puede utilizar una lista o pila en el encabezado (header) que indique las posiciones de registros eliminados, facilitando la reutilización del espacio.
  - **Para Registros de Longitud Variable:**  
    La búsqueda del registro eliminado que tenga el tamaño adecuado es más compleja y puede generar fragmentación:
    - **Fragmentación Interna:** Espacio asignado pero no completamente utilizado.
    - **Fragmentación Externa:** Espacio libre entre registros, que no se puede utilizar si no coincide con el tamaño requerido.
  
- **Estrategias de Colocación en Registros de Longitud Variable:**
  - **Primer Ajuste:** Se asigna el primer espacio encontrado que sea suficientemente grande.
  - **Mejor Ajuste:** Se busca el espacio que se aproxime más al tamaño necesario.
  - **Peor Ajuste:** Se selecciona la entrada más grande, utilizando solo lo necesario y dejando el resto libre.

## 8. Consideraciones en Cambios y Actualizaciones
- **Modificaciones:**  
  Especialmente en registros de longitud variable, las actualizaciones pueden generar problemas si el nuevo registro excede el espacio disponible.  
- **Claves Duplicadas o Cambio de Clave:**  
  Se deben implementar controles para evitar la inserción de claves duplicadas y manejar correctamente la modificación de una clave que afecte el orden o la ubicación del registro.