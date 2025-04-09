# Fundamentos de Organización de Datos – Clase 6: Árboles y Árboles Balanceados

Esta clase se centra en el uso de estructuras de árboles para mejorar la eficiencia en la búsqueda, inserción y eliminación de registros en bases de datos. Se abordan desde árboles binarios hasta árboles multicamino y árboles balanceados (B, B*, B+), incluyendo sus variantes y técnicas de mantenimiento.

---

## 1. Introducción a los Árboles

- **Motivación:**  
  La búsqueda binaria en índices es costosa y mantener índices ordenados resulta complejo. Los árboles ofrecen una solución basada en estructuras de datos en memoria que permiten búsquedas eficientes mediante una estrategia de “divide y vencerás”.

- **Objetivo:**  
  Mejorar la persistencia de datos y reducir el número de accesos a disco mediante el uso de árboles.

---

## 2. Árboles Binarios

- **Definición:**  
  Un árbol binario es una estructura en la que cada nodo tiene a lo sumo dos hijos: izquierdo y derecho.

- **Ejemplo:**  
  Supón que tenemos las claves: `MM, ST, GT, PR, JF, BC, UV, CD, HI, AB, KL, TR, OP, RX, ZR`. Estas se pueden insertar en un árbol binario; sin embargo, si la inserción no se realiza de forma balanceada, el árbol se desbalanceará, afectando la eficiencia en las búsquedas.

- **Problema:**  
  Los árboles binarios se desbalancean fácilmente, lo que incrementa la altura y deteriora la complejidad de búsqueda (teóricamente O(log N) en el mejor caso, pero puede degradarse a O(N) si se vuelve una lista).

---

## 3. Árboles AVL

- **Definición:**  
  Un árbol AVL es un árbol binario de búsqueda auto-balanceado en el que, para cada nodo, la diferencia de altura entre sus subárboles izquierdo y derecho (factor de balance) es, como máximo, 1.

- **Características:**  
  - Permiten inserciones y eliminaciones con un mínimo de reestructuraciones locales (rotaciones).
  - Garantizan una complejidad de búsqueda de aproximadamente 1.44 log₂(N+2).

- **Ejemplo Práctico:**  
  Si se insertan claves de forma aleatoria, las rotaciones (simples o dobles) se aplican para mantener el árbol balanceado. Por ejemplo, la inserción de las claves: `NI, OC, NR, OA, NZ` podría provocar desequilibrios que se corrigen con rotaciones.

---

## 4. Árboles Binarios Paginados

- **Concepto:**  
  Se utilizan cuando se almacenan datos en disco. Los árboles binarios paginados tienen en cuenta la estructura de las páginas y buffers de E/S para minimizar accesos a disco.

- **Problema a Resolver:**  
  Cómo elegir la raíz y construir el árbol de forma balanceada a medida que se leen páginas desde el disco.

---

## 5. Árboles Multicamino

- **Definición:**  
  Son una generalización de los árboles binarios en los que cada nodo puede tener más de dos hijos. Esto reduce la profundidad del árbol y, por lo tanto, el número de accesos a disco.

- **Ejemplo:**  
  En un árbol de orden M, cada nodo puede tener hasta M hijos y M-1 claves. Esto es particularmente útil cuando se manejan grandes volúmenes de datos.

---

## 6. Árboles Balanceados: B, B*, B+

### 6.1 Árboles B

- **Características:**  
  - Orden M: cada nodo (excepto la raíz y las hojas) tiene al menos ⎡M/2⎤ hijos.
  - La raíz tiene al menos 2 hijos (a menos que sea hoja).
  - Todas las hojas están al mismo nivel.
  - Los nodos internos con K hijos contienen K-1 registros.

- **Ventaja:**  
  Permiten búsquedas en O(log N) y son ideales para sistemas de bases de datos en disco.

### 6.2 Árboles B*

- **Características:**  
  - Variante del árbol B en la que cada nodo se llena al menos en 2/3 de su capacidad.
  - Mejoran la utilización del espacio y pueden posponer la creación de nuevas páginas.
  - Utilizan redistribución y concatenación para manejar la eliminación.

### 6.3 Árboles B+

- **Características:**  
  - Todas las claves se almacenan en las hojas, y estas están enlazadas, facilitando búsquedas secuenciales.
  - Los nodos internos solo contienen punteros a las hojas.
  - Son ideales para búsquedas por rango y tienen tiempos de búsqueda muy rápidos.

- **Ejemplo Práctico:**  
  Un árbol B+ de una base de datos bancaria puede indexar transacciones, permitiendo acceder a un rango de fechas de manera eficiente gracias a los enlaces entre las hojas.

---

## 7. Operaciones en Árboles Balanceados

### 7.1 Búsqueda
- **Proceso:**  
  Comienza en la raíz, se comparan claves y se sigue el puntero adecuado hasta llegar a una hoja.
- **Costo:**  
  Depende de la altura del árbol (h), siendo O(h).

### 7.2 Inserción
- **Sin Overflow:**  
  El registro se inserta en un nodo hoja sin romper su capacidad.
- **Con Overflow:**  
  Se divide el nodo, se redistribuyen los registros y se promueve una clave al nodo superior. Esto puede propagarse hasta la raíz, aumentando la altura del árbol.

### 7.3 Eliminación
- **Baja Lógica y Física:**  
  Generalmente, la eliminación se realiza en nodos terminales. Si un nodo cae por debajo del mínimo permitido, se puede redistribuir con un nodo hermano o concatenarse (fusionar) con él.
- **Costo:**  
  En el mejor caso, se requieren h lecturas y una escritura; en el peor caso, se pueden requerir operaciones en cada nivel del árbol.