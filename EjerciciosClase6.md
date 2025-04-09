
## Preguntas de Opción Múltiple

1. **¿Cuál es la característica principal de un árbol AVL?**  
   - A) Permite tener más de dos hijos por nodo.  
   - B) Es un árbol binario auto-balanceado donde la diferencia de altura entre subárboles es a lo sumo 1.  
   - C) Utiliza hashing para distribuir las claves.  
   - D) Almacena todas las claves en las hojas.  
   - **Respuesta:** B

2. **En un árbol B de orden M, ¿cuál es el número mínimo de hijos que debe tener un nodo no raíz?**  
   - A) M  
   - B) M-1  
   - C) ⎡M/2⎤  
   - D) ⎣M/2⎦  
   - **Respuesta:** C

3. **¿Cuál es una ventaja del árbol B+ frente al árbol B?**  
   - A) Permite búsquedas exactas en O(1).  
   - B) Almacena todas las claves en las hojas, lo que facilita la búsqueda por rangos.  
   - C) No requiere mantenimiento durante las inserciones.  
   - D) Utiliza menos espacio en disco eliminando los punteros.  
   - **Respuesta:** B

4. **¿Qué acción se realiza en un árbol balanceado cuando se produce un overflow en un nodo hoja?**  
   - A) Se elimina el nodo.  
   - B) Se reestructura mediante una división y se promueve una clave al nodo padre.  
   - C) Se ignora el nuevo registro.  
   - D) Se reordena el árbol de manera completa.  
   - **Respuesta:** B

5. **En un árbol binario, ¿cuál es el principal problema que se busca resolver con árboles AVL?**  
   - A) La complejidad de inserción en disco.  
   - B) La falta de índices secundarios.  
   - C) El desbalanceo que puede degradar la complejidad de búsqueda.  
   - D) El uso excesivo de memoria RAM.  
   - **Respuesta:** C

---

## Ejercicios Prácticos

### Ejercicio 1: Construcción de un Árbol Binario
Dadas las claves: `NI, OC, NR, OA, NZ`, construye un árbol binario de búsqueda.  
- **Pregunta:**  
  - Dibuja el árbol resultante y explica cómo afecta la inserción en orden a su balance.

### Ejercicio 2: Rotación en Árbol AVL
Supón que en un árbol AVL se insertan las claves: `30, 20, 10`.  
- **Pregunta:**  
  - Explica qué tipo de rotación se debe aplicar para mantener el árbol balanceado y dibuja el árbol antes y después de la rotación.

### Ejercicio 3: Inserción en un Árbol B+
Dado un árbol B+ de orden 5, inserta las siguientes claves en orden: `43, 2, 53, 88, 75, 80, 15, 49, 60, 20, 57, 24`.  
- **Pregunta:**  
  - Describe el proceso de inserción, indicando cuándo se produce una división de nodo y muestra el árbol resultante (puedes simplificar dibujándolo en forma esquemática).

### Ejercicio 4: Análisis de Altura en Árboles Balanceados
Considera un árbol B de orden 512 con 1,000,000 de registros.  
- **Pregunta:**  
  - Utilizando la cota \( h \leq 1 + \log_{(M/2)}((N+1)/2) \), calcula la altura aproximada del árbol y comenta cuántas lecturas se requerirían en el peor caso para una búsqueda.