
## **Ejercicios de Práctica**

### **Ejercicio 1: Tipos de Búsqueda**
Se tiene un archivo de 1,000,000 de registros. Si se busca un dato que está al final del archivo, ¿cuántas comparaciones se necesitan en cada caso?
1. **Búsqueda Secuencial**
2. **Búsqueda Binaria**
3. **Búsqueda Directa con NRR**

_Responde con el número de comparaciones aproximadas en cada método._

---

### **Ejercicio 2: Ordenación Externa**
Un archivo de 10 GB debe ser ordenado, pero la memoria RAM solo permite almacenar 1 GB. ¿Cuál es la mejor estrategia para ordenarlo?

Opciones:
A) Cargar todo en RAM y ordenar.  
B) Usar un índice y mantener los datos desordenados.  
C) Partir el archivo en fragmentos, ordenar cada parte y luego hacer un merge.  
D) Ordenarlo manualmente con un editor de texto.  

---

## **Preguntas de Opción Múltiple**

### **Pregunta 1**
¿Cuál de las siguientes afirmaciones es **falsa** sobre la búsqueda binaria?

A) Requiere que los registros sean de longitud fija.  
B) Su complejidad es \( O(N) \).  
C) Se basa en dividir repetidamente el archivo en mitades.  
D) Solo puede aplicarse si el archivo está ordenado.  

**Respuesta:** B) La complejidad de la búsqueda binaria es \( O(\log_2 N) \), no \( O(N) \).

---

### **Pregunta 2**
¿Cuál es la principal ventaja de la búsqueda directa sobre la búsqueda secuencial?

A) Reduce el número de accesos a disco.  
B) No requiere que los registros sean de longitud fija.  
C) Funciona mejor en archivos no ordenados.  
D) No necesita conocer el NRR.  

**Respuesta:** A) La búsqueda directa reduce significativamente los accesos a disco.

---

### **Pregunta 3**
¿Cuál es la estrategia más eficiente para ordenar archivos extremadamente grandes?

A) Ordenación en RAM.  
B) Algoritmos de mezcla (merge-sort) en almacenamiento externo.  
C) Ordenar usando hojas de cálculo.  
D) Mantener el archivo desordenado y buscar con fuerza bruta.  

**Respuesta:** B) Merge-sort externo es la mejor opción para archivos grandes que no caben en RAM.