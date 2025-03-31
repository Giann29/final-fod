# **Fundamentos de Bases de Datos - Clase 1**

## **Resumen Detallado**

### **1. Definición de Base de Datos**
Una **Base de Datos (BD)** es una colección organizada de datos interrelacionados que representan aspectos del mundo real. Su diseño permite que múltiples aplicaciones accedan a los datos de manera eficiente y segura.

### **2. Propiedades de una Base de Datos**
- **Coherencia y Significado:** Los datos almacenados deben tener sentido y estar correctamente relacionados.
- **Uso Específico:** Cada BD está diseñada para cumplir un propósito y servir a un conjunto de usuarios.
- **Almacenamiento Persistente:** La BD se guarda en dispositivos de almacenamiento permanente (disco duro, SSD, etc.).

### **3. Conceptos sobre Archivos**
Un **archivo** es una colección de registros almacenados en un medio secundario. Se compone de:
- **Campos:** Unidades básicas de información dentro de un registro.
- **Registros:** Conjunto de campos relacionados.
- **Estructuras de acceso:** Formas en que los datos pueden ser recuperados del archivo.

### **4. Tipos de Acceso a Archivos**
- **Secuencial:** Los registros se acceden en el orden en que fueron almacenados.
- **Secuencial Indizado:** Usa un índice auxiliar para encontrar registros más rápido.
- **Directo (Hashing):** Acceso inmediato a registros sin recorrer otros datos.

### **5. Uso de Archivos en Pascal**
En Pascal, los archivos se manejan con funciones específicas:
- **Declaración:** `var archivo: file of tipo;`
- **Apertura:** `Assign(archivo, 'nombre.dat');`
- **Modo Escritura:** `Rewrite(archivo);`
- **Modo Lectura:** `Reset(archivo);`
- **Lectura y Escritura:** `Read(archivo, variable); Write(archivo, dato);`
- **Cierre:** `Close(archivo);`

---

## **Ejercicios de Práctica**

### **Ejercicio 1: Conceptos Básicos**
1. ¿Cuál de las siguientes opciones describe mejor una base de datos?
   - a) Una colección de archivos sin relación entre sí.
   - b) Un conjunto de datos organizados y relacionados.
   - c) Un programa de gestión de datos.
   - d) Un sistema operativo especializado.

2. ¿Cuál de estas NO es una propiedad de una base de datos?
   - a) Coherencia y significado.
   - b) Uso específico.
   - c) Almacenamiento temporal.
   - d) Almacenamiento persistente.

### **Ejercicio 2: Tipos de Acceso a Archivos**
3. Si tienes un archivo donde los datos deben ser recuperados en el orden en que fueron almacenados, ¿qué estructura de acceso usarías?
   - a) Secuencial  
   - b) Indizado  
   - c) Directo  
   - d) Hashing  

4. ¿Cuál de los siguientes métodos permite acceder a los datos sin necesidad de recorrer toda la estructura?
   - a) Acceso secuencial  
   - b) Acceso secuencial indizado  
   - c) Acceso directo  
   - d) Ninguno de los anteriores  

### **Ejercicio 3: Programación en Pascal**
5. En Pascal, ¿qué instrucción se usa para asociar un archivo con un nombre en el sistema?
   - a) `Assign`  
   - b) `Open`  
   - c) `Read`  
   - d) `Write`  

6. ¿Cuál de las siguientes opciones indica correctamente el orden de operaciones para escribir en un archivo en Pascal?
   - a) `Assign -> Rewrite -> Write -> Close`  
   - b) `Assign -> Reset -> Write -> Close`  
   - c) `Assign -> Rewrite -> Read -> Close`  
   - d) `Assign -> Write -> Close`  

---

Cuando termines los ejercicios, revisa tus respuestas y corrige cualquier error. ¡Sigue practicando para fortalecer tu comprensión! 🚀
