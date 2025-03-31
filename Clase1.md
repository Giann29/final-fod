# Fundamentos de Organización de Datos - Clase 1

### ¿Qué es una Base de Datos?
Es una **colección de datos relacionados** que sirven a múltiples aplicaciones. Un dato representa hechos conocidos que pueden registrarse y que tienen un significado.

### Propiedades de una Base de Datos
1. Representa aspectos del **mundo real** o un *universo de discurso*.
2. Es una **colección coherente** de datos con significado.
3. Se diseña para un **propósito específico** y usuarios concretos.
4. Se almacena en **archivos en dispositivos de almacenamiento persistente**.

---

## 📑 Archivos: Conceptos Fundamentales

### Definición
Un **archivo** es:
- Una **colección de registros** en almacenamiento secundario.
- Un **conjunto de datos** almacenados para un propósito específico.

### Organización del Hardware
- **Almacenamiento primario (RAM) vs. almacenamiento secundario (disco).**
- Componentes del disco: **Platos, superficies, pistas, sectores y cilindros.**

### Organización de Archivos
- **Campo:** Unidad más pequeña de un archivo.
- **Registro:** Conjunto de campos que definen un elemento del archivo.

---

## 🔑 Tipos de Acceso a Archivos

### Acceso Secuencial
- **Físico:** Los registros se acceden uno tras otro en orden físico.
- **Lógico (indizado):** Se accede según un índice lógico (ejemplo: guía telefónica).

### Acceso Directo
- Se accede a un registro específico sin recorrer los anteriores.

### Tipos de Archivos según Acceso
- **Serie:** Se accede en orden físico (secuencial físico).
- **Secuencial:** Ordenado por una clave (secuencial lógico).
- **Directo:** Se accede a un registro específico.

---

## 🛠️ Operaciones con Archivos

### Buffers
- **Memoria intermedia** entre el archivo y el programa.
- **Gestionados por el sistema operativo**.

### Operaciones Básicas
1. **Crear** → `Rewrite(nombre_logico);`
2. **Abrir** → `Reset(nombre_logico);`
3. **Leer/Escribir**
   - `Read(nombre_logico, variable);`
   - `Write(nombre_logico, variable);`
4. **Cerrar** → `Close(nombre_logico);`
5. **Buscar posición** → `Seek(nombre_logico, posición);`
6. **Funciones adicionales**
   - `EOF(nombre_logico);` (fin de archivo)
   - `FileSize(nombre_logico);` (tamaño del archivo)
   - `FilePos(nombre_logico);` (posición actual)

---

## 📝 Ejercicios de Programación

### Ejemplo 1: Crear un Archivo

```pascal
Program Generar_Archivo;
type archivo = file of integer;
var arc_logico: archivo;
    nro: integer;
    arc_fisico: string[12];

begin
    write('Ingrese el nombre del archivo:');
    read(arc_fisico);
    assign(arc_logico, arc_fisico);
    rewrite(arc_logico);
    read(nro);
    while nro <> 0 do begin
        write(arc_logico, nro);
        read(nro);
    end;
    close(arc_logico);
end.
