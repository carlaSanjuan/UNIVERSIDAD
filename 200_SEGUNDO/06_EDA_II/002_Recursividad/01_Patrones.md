# 1) IDEA CENTRAL

1. Secuencial
2. Recurrente
3. Iterativo
4. Recursivo

**Ejemplo:**

No es lo mismo:

los lunes (aparecen cada 7 días, fijo),
que
las tormentas (vuelven, pero no sabes exactamente cuándo).

Ambos “se repiten”, sí.
Pero:

- uno es **iterativo** (regular, consecutivo, periódico),
- el otro es **recurrente** (reaparece, pero sin calendario exacto).

El texto insiste en que esta diferencia no es semántica, sino estructural

# 2) EXPLICACION CATEGORIAS

## SECUENCIAL

Un fenómeno es secuencial cuando:

- tiene un orden inherente,
- hay una progresión,
- cambiar el orden rompe el proceso o el sentido.

No implica necesariamente repetición.

**Ejemplo:** “un niño crece”

Secuencia:

embrión

feto

neonato

infante

niño

adolescente

adulto

¿Por qué es secuencial?

Porque:

- hay orden temporal irreversible,
- cada etapa es cualitativamente distinta,
- no hay repetición cíclica,
- no “vuelve” a ser feto.

👉 Esto es importantísimo: hay progresión, pero no iteración.

## RECURRENTE

Un fenómeno es recurrente cuando:

- reaparece después de desaparecer,
- pero sin periodicidad fija garantizada.

**Ejemplo:** terremotos
- ocurre uno
- pasa tiempo
- puede pasar otro
- no sabes exactamente cuándo

¿Por qué es recurrente?

Porque:

- el fenómeno vuelve,
- pero no hay un ciclo fijo tipo reloj,
- puede haber años o décadas de silencio.

Esto lo distingue del corazón o del semáforo.

### Ojo con la palabra “recurrente”**

El propio texto mete una observación MUY importante:

En matemáticas y algoritmos, “recurrente” a veces significa otra cosa:

- una relación de recurrencia,
-donde el estado n+1 depende del estado n.

**Ejemplo:**

- Fibonacci
- ecuaciones en diferencias
- recurrencias dinámicas

El texto dice:

Ese sentido también es válido, pero es **otro eje** distinto.

Es decir:

aquí “recurrente” = **reaparece eventualmente**
en matemáticas, “recurrente” = **depende del estado anterior**

Esta aclaración es excelente, porque evita mezclar dos usos distintos de la palabra.

## ITERATIVO

Un fenómeno es iterativo cuando:

- la misma estructura operacional se repite,
- de forma consecutiva,
- normalmente con periodicidad regular,
- sin saltos aleatorios entre una instancia y otra.

**Ejemplo:** el corazón
- contracción
- relajación
- contracción
- relajación
- 
¿Por qué es iterativo?

Porque:

- repite el mismo patrón,
- una y otra vez,
- sin interrupciones arbitrarias,
- con regularidad.

El texto dice algo fino:

“Cada latido estructuralmente idéntico al anterior”.

Eso es la esencia de iteración.

## RECURSIVO

Un fenómeno o estructura es recursivo cuando:

- se contiene a sí mismo,
- o la definición del todo incluye instancias del mismo tipo,
- o aparece la misma organización en el todo y en las partes.

**Ejemplo:** un río
- un río recibe afluentes,
- cada afluente es también un río,
- que recibe subafluentes,
- que reciben arroyos…

¿Por qué es recursivo?

Porque:

el patrón “río con ramificaciones” aparece dentro del propio río,
el todo y las partes comparten la misma organización.

Eso es recursividad estructural.

# 3) TEMPORAL VS ESTRUCTURAL

**Secuencial, recurrente e iterativo**

Son principalmente categorías del eje temporal:

- qué ocurre antes/después,
- si vuelve,
- si vuelve regularmente,
- si hay ciclos.

**Recursivo**

Es principalmente del eje estructural:

- cómo está construido algo,
- cómo una parte replica la organización del todo,
- cómo una definición se apoya en sí misma.

Por eso el texto dice:

“Lo recursivo es ortogonal al eje temporal”.

Es decir:

no compite directamente con “iterativo” o “recurrente”,
porque mide otra dimensión.

# 4) RELACION ENTRE CATEGORIAS
- Lo iterativo es necesariamente secuencial
- No todo secuencial es iterativo
- Lo recurrente puede parecer iteraivo, pero no lo es
- Lo recursivo puede coexistir con las otras

# 5) ERROR HABITUAL

Muchísima gente define recursión así:

“Una función recursiva es una función que se llama a sí misma.”

El texto dice:

- eso no es falso,
- pero está mal ordenado conceptualmente.

¿Por qué?

Porque eso describe el mecanismo (la llamada a sí misma),
pero no el origen estructural.

La versión correcta del texto sería:
- Primero detectas que el dato o problema tiene estructura recursiva
- Entonces una solución recursiva aparece de forma natural
- Como consecuencia, la función se llama a sí misma

O sea:

No es un truco sintáctico
Es una correspondencia estructural

# 6) ISOMORFISMO NATURAL

**Ejemplo intuitivo**

Si un árbol está compuesto por:

- un nodo
- y subárboles

…entonces procesarlo naturalmente es:

- procesa el nodo
- procesa cada subárbol

Eso se parece a:
```
procesar(árbol):
    procesa raíz
    procesa(subárbol izquierdo)
    procesa(subárbol derecho)
```
La estructura del algoritmo copia la estructura del dato.

Eso es lo que quieren decir con “isomorfismo natural”.

# 7) EJEMPLO COMPLETO

El texto usa una lista enlazada:
``
class Nodo {
    private int valor;
    private Nodo siguiente;
}

```
**¿Por qué esto es recursivo?**

Porque la definición dice:

Un Nodo tiene:

- un valor
- y un siguiente que también es un Nodo

Es decir:

- el tipo se define usando el mismo tipo.

Eso es recursividad estructural.

## EJEMPLO 1: contar nodos
``
public int contar(Nodo nodo) {
    if (nodo == null) {
        return 0;
    } else {
        return 1 + contar(nodo.siguiente);
    }
}
```
**caso base:**
```
if (nodo == null) {
    return 0;
}
```
Si no hay nodo:

- la lista terminó
- hay 0 elementos

👉 Toda recursión necesita una condición de terminación.

**caso recursivo**
```
return 1 + contar(nodo.siguiente);
```
Significa:

- el nodo actual cuenta como 1
-y el resto de la lista lo delegas a:
- contar(nodo.siguiente)

Es decir:

- “cuento este nodo”
- “dejo que la misma lógica cuente el resto”

👉 Esto refleja exactamente la estructura:

una lista es:
- un nodo
- otra lista

# 8) METODO TABULAR

Aunque aquí no desarrolla ese método, por el contexto parece referirse a una herramienta para estructurar el problema antes de implementar.

Probablemente algo como:

- identificar casos base,
- identificar subproblema,
- identificar cómo se combina,
- identificar invariantes o forma del dato.

En recursión, una tabla así suele incluir:

- Entrada
- Caso base
- Subestructura
- Llamada recursiva
- Combinación del resultado
- Condición de terminación

👉 O sea: antes de programar, modelas.

# 9) QUE ESTRUCTURA SUGIERE CADA CATEGORIA

## SECUENCIAL (PIPELINE/ FLUJO LINEAL)

Útil cuando:

- hay pasos ordenados
- cada fase transforma el estado
```
analizar();
diseniar();
implementar();
probar();
```
```
estado = fase1(estado);
estado = fase2(estado);
estado = fase3(estado);
```
## RECURRENTE (EVENTOS/ REINTENTOS/ MODELOS PROBABILISTICOS)

Útil cuando:

- algo reaparece eventualmente
- no con calendario fijo

**Ejemplo:**

- reintentos de red
- llegadas de eventos
- alarmas intermitentes
- sistemas basados en eventos

No suele modelarse como for simple.

## ITERATIVO (BUCLES, FOR & WHILE)

REPITE UNA ACCION SOBRE UNA SECUENCIA DE PASOS.

Útil cuando:

- repites una misma operación
- cada vuelta es análoga a la anterior
```
for (int i = 0; i < n; i++) {
    procesar(i);
}
```
```
while (encendido) {
    latir();
}
```
## RECURSIVO (FUNCIONES SUBESTRUCTURADAS)

RESUELVE EL PROBLEMA POR DESCOMPOSICION ESTRUTURAL.

Útil cuando:

- el dato está anidado
- árbol, lista, carpetas, expresiones, JSON, DOM…
```
procesar(nodo) {
   procesar(hijos...);
}
```

# 10) RESUMEN POR CATEGORIA

Secuencial = hay orden y progresión.

Recurrente = vuelve, pero de forma irregular.

Iterativo = repite el mismo ciclo de forma regular y consecutiva.

Recursivo = el todo contiene partes organizadas como el todo.
