# **ANALISIS DE ALGORITMOS**

## 1) El análisis de algoritmos sirve para:

- Prever escalabilidad
- Comparar soluciones
- Detectar cuellos de botella (el componente, proceso o fragmento de código que limita el rendimiento total del programa.)
- Elegir estructuras de datos adecuadas
- Diseñar software que siga funcionando cuando crece

## 2)¿QUÉ ES LA COMPLEJIDAD?

La **complejidad temporal** es una forma de expresar cómo crece el número de operaciones en función del tamaño de la entrada.

Normalmente usamos:

n = tamaño del problema

**Ejemplo:**

si tienes un array de 100 elementos, entonces n = 100

si tienes una matriz 50×50, el tamaño puede modelarse según el contexto

La notación **Big O** describe el comportamiento asintótico del algoritmo, no mide exactitud, mide crecimiento, por lo que se eliminan las constantes

## 3)TERMINO DOMINANTE

El **término dominante** es el término de la fórmula que:

- crece más rápido
- y por tanto determina el comportamiento del algoritmo para valores grandes de n

## 4) PROCESO CORRECTO PARA ANALIZAR UN ALGORITMO ITERATIVO

### Paso 1: Escribir la fórmula completa (o identificar componentes)

Debes observar el código y separar:

- operaciones constantes
- bucles
- bucles anidados
- partes que se ejecutan secuencialmente
- llamadas a otros algoritmos (como ordenar)

### Paso 2: Comparar términos

Si el algoritmo tiene varias partes, por ejemplo:

una parte 
𝑂
(
𝑛
)
O(n)
luego otra 
𝑂
(
𝑛
log
⁡
𝑛
)
O(nlogn)
luego una 
𝑂
(
1
)
O(1)

La complejidad total será:


O(n)+O(nlogn)+O(1)

Ahora comparas cuál crece más.

### Paso 3: Simplificar

Reglas de simplificación:

eliminar constantes multiplicativas
eliminar términos menores
quedarte con el dominante

## 5) JERARQUÍA DE CRECIMIENTO (MUY IMPORTANTE)

De menor a mayor:

𝑂
(
1
)
<
𝑂
(
log
⁡
𝑛
)
<
𝑂
(
𝑛
)
<
𝑂
(
𝑛
log
⁡
𝑛
)
<
𝑂
(
𝑛
2
)
<
𝑂
(
𝑛
3
)
<
𝑂
(
2
𝑛
)
<
𝑂
(
𝑛
!
)

## Significado intuitivo de cada una
### O(1) — Constante

El coste no depende de n.
```
a = 1;
b = 2;
c = a + b;
```
(son unas pocas operaciones fijas)
### O(log n) — Logarítmica

Cada paso reduce el problema a una fracción (normalmente a la mitad).

### O(n) — Lineal

Recorres los elementos una vez.
```
for (int i = 0; i < n; i++) {
    // operación constante
}
```
(se ejecuta **n** veces)

### O(n log n) — Lineal logarítmica

Suele aparecer cuando:

haces trabajo lineal en cada nivel
y hay 
log
⁡
𝑛
 niveles

 ### O(n²) — Cuadrática

Típico de:

- comparar todos con todos
- dos bucles anidados

```
for (int i = 0; i < n; i++) {
    for (int j = 0; j < n; j++) {
        // operación constante
    }
}
```
(son dos bucles anidados **n*n=n^2**)

```
for (int i = 0; i < n; i++) {
    for (int j = i + 1; j < n; j++) {
        // operación constante
    }
}
```
(Esto no es exactamente 
**𝑛
⋅
𝑛**
, pero sí es del mismo orden.)

**EJEMPLO:**
- Comparar todos los pares
  
### O(n³) — Cúbica

Tres dimensiones / tres niveles de anidamiento / todos los tripletes.
```
for (int i = 0; i < n; i++) {
    for (int j = 0; j < n; j++) {
        for (int k = 0; k < n; k++) {
            // operación constante
        }
    }
}
```
(tres bucles anidados)

### O(2ⁿ) — Exponencial

Cada nuevo elemento duplica el espacio de posibilidades.

**EJEMPLO:** 
- interruptores ON/OFF, duplica las combinaciones
- Torre de Hanoi

### O(n!) — Factorial

Crece brutalmente.
Suele aparecer en permutaciones completas.

## EJEMPLO COMPLETO 1: suma de elementos de un array
```
static int sumArray(int[] array) {
    int sum = 0; // O(1)
    for(int i = 0; i < array.length; i++) { // O(n)
        sum = sum + array[i]; // O(n)
    }
    return sum; //O(1)
}
```
RESULTADO: O(1)+O(n)+O(n)+O(1) =O(n)

(se mira cada elemento exactamente 1 vez)

## EJEMPLO COMPLETO 2: Encontrar el maximo
```
static int findMax(int[] array) {
    int max = array[0]; //O(1)
    for (int i = 1; i < array.length; i++) { // O(n)
        if (array[i] > max) { // O(n)
            max = array[i]; // O(n)
        }
    }
    return max; // O(1)
}
```
RESULTADO: O(1)+O(n)+O(n)+O(n)+O(1) =O(n)

## EJEMPLO COMPLETO 3: Buscar un par que sume un objetivo
codigo(resumen)
```
for (int i = 0; i < array.length - 1; i++) {
    for (int j = i + 1; j < array.length; j++) {
        if (array[i] + array[j] == target) {
            return ...
        }
    }
}
```
RESULTADO: O(n^2) (hay 2 bucles anidados)

## EJEMPLO COMPLETO 4: Busqueda binaria
codigo (idea)
```
while (left <= right) {
    int mid = ...
    if (array[mid] == target) ...
    if (array[mid] < target) left = mid + 1;
    else right = mid - 1;
}
```
RESULTADO: como es una busqueda binaria el resultado rera logaritmico O(log n)

## EJEMPLO COMPLETO 5: Ordenar y luego clacular promedio

cuando hay Merge Sort, el Big O sera; O(n log n); sera el mayor y el dominante de la solucion

# 6) BUSQUEDA LINEAL VS BUSQUEDA BINARIA
### Busqueda lineal
- peor caso: mirar todos
- coste:
𝑂
(
𝑛
)

### Busqueda binaria
- requiere array ordenado
- descarta la mitad cada vez
𝑂
(
log
⁡
𝑛
)

**ejemplo**

Con 

n=10000:

lineal ≈ 10,000 revisiones

binaria ≈ 
log
⁡
2
(
10000
)
≈
13.29


Es una diferencia brutal.

👉 Esta es una de las mejores demostraciones de que:

La organización de los datos cambia el algoritmo posible. 

# 7) ORGANIZAR DATOS

La misma información, organizada de forma distinta, permite estrategias distintas.

### Ejemplo de agenda telefónica
**Desordenada**
- solo puedes revisar uno por uno
- eso es como búsqueda lineal

O(n)

**Ordenada**
- puedes “abrir por la mitad”
- eso es como búsqueda binaria

O(logn)

**Ordenada + separada por letras**
- reduces aún más el espacio de búsqueda
- es como usar un índice o una estructura auxiliar

# 8) DIVIDE Y VENCERÁS: POR QUÉ APARECE O(log n) Y O(n log n)

## Caso 1: Solo dividir y elegir una mitad → O(log n)

**Ejemplo:**

búsqueda binaria

Cada paso:
- partes el problema
- solo sigues con una mitad

## Caso 2: Dividir en mitades y luego combinar todo → O(n log n)

**Ejemplo:**

Merge Sort

Hay:
- logn niveles de división
- y en cada nivel el trabajo total es lineal

# 9) TIPS DE IDENTIFICACIÓN RÁPIDA
### Regla 1

1 bucle simple → normalmente O(n)

### Regla 2

2 bucles anidados → normalmente O(n²)

### Regla 3

3 bucles anidados → normalmente O(n³)

### Regla 4

Si cada iteración reduce a la mitad → normalmente O(log n)

### Regla 5

Si haces varias fases seguidas, te quedas con la más costosa. O(nlogn)

### Regla 6

Exponencial siempre aplasta a polinomial

2^n≫n^5

### Regla 7

Entre polinomios, manda el mayor exponente.

n^4≫n^2

# 10) LIMITACIONES DEL BIG O

Big O NO dice el tiempo real exacto

Big O:

- ignora constantes
- ignora detalles de implementación
- ignora hardware
- ignora caché, predicción de saltos, memoria, compilador, JVM, etc.

### Ejemplo real importantísimo

**Insertion Sort (O(n²))** puede ser más rápido que **Merge Sort (O(n log n))** en arrays pequeños.

¿Por qué?

menos overhead
muy simple
muy cache-friendly
menos asignaciones
mejor constante oculta

Por eso muchos algoritmos reales hacen:

“si el subarray es pequeño, usa Insertion Sort”

**Big O Sí te da:**
- comparación de escalabilidad
- intuición de crecimiento
- lenguaje común entre programadores
- detección de patrones malos
- capacidad de prever problemas a gran escala
**Big O No te da:**
- tiempo exacto
- ganador absoluto para inputs pequeños
- coste real de memoria caché
- coste de I/O
- impacto de librerías / compilador / JVM / CPU

# 11) PARADIGMAS ALGORITMICOS
**1. Fuerza bruta:** Probar todas las posibilidades o revisar todo.
**2. Divide y venceras:** Dividir el problema en subproblemas más pequeños, resolverlos y combinar
**3.Voraces (Greedy):** Tomar la mejor decisión local en cada paso.
**4.Backtracking:** Explorar posibilidades y retroceder si una rama no sirve.
**5.Programacion dinamica:** Resolver subproblemas repetidos una sola vez y guardar resultados.

# 12)ELECCION PEDAGOGICA

La intuición que deberías ganar es esta:

Cuando veas código, deberías empezar a pensar automáticamente:

“Esto recorre todo el array una vez” → O(n)
“Aquí hay dos bucles anidados” → O(n²)
“Aquí se ordena antes de buscar” → probablemente O(n log n)
“Esto reduce el rango a la mitad” → O(log n)
“Aquí prueba todas las combinaciones” → cuidado, puede ser exponencial
