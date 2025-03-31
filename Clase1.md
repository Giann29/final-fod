# Fundamentos de Organización de Datos - Clase 1

## 1. Conceptos Básicos de Bases de Datos

### Definición
- **Base de Datos (BD):**  
  Es una colección organizada de datos relacionados, diseñada para servir a múltiples aplicaciones y representar aspectos del mundo real.

### Propiedades de una Base de Datos
1. **Representación del Mundo Real:**  
   La BD refleja un *universo de discurso*, es decir, aspectos relevantes del entorno o negocio.
2. **Coherencia y Significado:**  
   Los datos deben estar organizados de forma lógica y con significado inherente.
3. **Propósito Específico:**  
   Se diseña para satisfacer necesidades particulares de usuarios y aplicaciones.
4. **Almacenamiento Persistente:**  
   Los datos se guardan en archivos en dispositivos de almacenamiento secundario (discos, SSD, etc.).

### Ejemplos de Aplicaciones Prácticas
- Sistemas de gestión empresarial, bases de datos para e-commerce, sistemas de información hospitalaria, entre otros, que requieren almacenar y procesar grandes volúmenes de datos de forma eficiente.

---

## 2. Archivos: Conceptos Fundamentales

### Definición y Organización
- **Archivo:**  
  Conjunto de registros almacenados en un dispositivo de almacenamiento secundario para un propósito específico.
- **Componentes:**
  - **Campo:** Unidad mínima y lógicamente significativa de un registro.
  - **Registro:** Conjunto de campos que conforman un dato completo dentro del archivo.

### Organización del Hardware
- **Discos:**  
  Están compuestos por:
  - **Platos**
  - **Superficies**
  - **Pistas**
  - **Sectores**
  - **Cilindros**
- **Comparación:**  
  Se diferencia el almacenamiento primario (RAM) del secundario (disco).

---

## 3. Tipos de Acceso a Archivos

### Métodos de Acceso
- **Acceso Secuencial:**  
  - **Físico:** Los registros se leen en el orden en que están almacenados.
  - **Lógico o Indizado:** Se utiliza un índice para acceder a los registros en un orden determinado (como una guía telefónica).

- **Acceso Directo (Hashing):**  
  Permite acceder a un registro específico sin leer los registros previos.

### Tabla Comparativa de Métodos de Acceso

| **Método de Acceso**           | **Descripción**                                                    | **Ventajas**                                      | **Uso Común**                              |
|--------------------------------|--------------------------------------------------------------------|---------------------------------------------------|--------------------------------------------|
| **Secuencial Físico**          | Lectura en el orden físico de almacenamiento.                      | Simple, ideal para archivos pequeños.             | Archivos de texto o registros sin índice.  |
| **Secuencial Lógico (Indizado)** | Uso de un índice para organizar y acceder a los registros.         | Búsqueda más rápida que el acceso físico.          | Directorios telefónicos, índices de libros.|
| **Directo (Hashing)**          | Acceso inmediato a un registro específico.                         | Muy eficiente en búsquedas puntuales.              | Bases de datos con consultas de alta performance. |

---

## 4. Buffers y Operaciones con Archivos

### Gestión de Buffers
- **Buffers:**  
  Memoria intermedia que almacena temporalmente los datos leídos o a escribir en disco.
- **Importancia:**  
  Optimiza el acceso a datos, ya que reduce la cantidad de operaciones de E/S (entrada/salida) en disco.
- **Gestión:**  
  El sistema operativo se encarga de la manipulación y asignación de estos buffers.

### Operaciones Básicas en Archivos (en Pascal)
1. **Declaración:**  
   - Variable: `var archivo: file of Tipo_de_dato;`
   - Tipo: `type archivo = file of Tipo_de_dato;`
2. **Asignación y Apertura:**  
   - **Assign:** Asocia un nombre lógico a un archivo físico.
   - **Rewrite:** Abre un archivo en modo escritura (creación).
   - **Reset:** Abre un archivo en modo lectura (o lectura-escritura).
3. **Lectura/Escritura:**  
   - **Read:** Extrae datos del archivo a una variable.
   - **Write:** Escribe datos en el archivo a partir de una variable.
4. **Cierre:**  
   - **Close:** Finaliza la operación con el archivo y pone una marca de fin de archivo (EOF).
5. **Operaciones Adicionales:**  
   - **EOF:** Función para verificar el fin del archivo.
   - **FileSize:** Retorna el tamaño del archivo.
   - **FilePos:** Devuelve la posición actual del puntero.
   - **Seek:** Mueve el puntero a una posición específica (la numeración comienza en 0).

---

## 5. Ejemplos Prácticos en Pascal

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
```

### Ejemplo 2: Leer y Presentar un Archivo
```pascal
Procedure Recorrido(var arc_logico: archivo);
var nro: integer;
begin
    reset(arc_logico);
    while not eof(arc_logico) do begin
        read(arc_logico, nro);
        write(nro);
    end;
    close(arc_logico);
end;

```

### Ejemplo 3: Modificar Datos de un Archivo
```pascal
Type registro = record
    Nombre: string[20];
    Direccion: string[20];
    Salario: real;
End;

Empleados = file of registro;

Procedure actualizar(var Emp: empleados);
var E: registro;
begin
    Reset(Emp);
    while not eof(Emp) do begin
        Read(Emp, E);
        E.salario := E.salario * 1.1;
        Seek(Emp, FilePos(Emp) - 1);
        Write(Emp, E);
    end;
    close(Emp);
end;


