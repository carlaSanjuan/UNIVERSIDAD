# 1) EN QUE CONSISTE UN ESQUEMA TABULAR
Una tabla con dos columnas
- Columna 1: entrada (qué recibe la función)
- Columna 2: salida (qué debería devolver)

**Ejemplo con factorial:**

Entrada n                    0    4    5

Salida factorial(n)=f(n)      1    24   120

La idea es:

- ver un caso base
- ver dos casos cercanos: n-1 y n
- descubrir la relación entre ambos

# 2) LA RECETA GENARAL DEL TEXTO
## PASO 1: Encontrar el caso base

El caso base es el caso más simple, donde:
- ya no hace falta seguir llamando recursivamente
- la respuesta se conoce directamente

Ejemplos típicos:

- números → muchas veces 0
- listas → muchas veces []
- cadenas → muchas veces ""
- listas con mínimo un elemento → a veces [x]
- números de un solo dígito → a veces n < 10

¿Por qué es tan importante?

Porque si no existe un caso base correcto:

- la función nunca termina
- entra en recursión infinita

## PASO 2: Elegir un caso “más grande”

Escoger un ejemplo que no esté pegado al caso base.

Ejemplo:

- si el caso base es 0, no elijas 1, mejor 4 o 5
- así ves mejor el patrón

## PASO 3: Reducir el problema (“descender un orden”)

Tomar un caso n y convertirlo en una versión más pequeña:

- en números: n-1
- en listas: “lista sin el primer elemento”
- en cadenas: “cadena sin el primer carácter”

Esto es la esencia de la recursividad:
```
Resolver un problema grande usando el mismo problema, pero más pequeño.
```

## PASO 4: “Observar en aspa”

Esta es la parte clave del método.

Tienes:

- un caso pequeño: f(n-1)
- un caso grande: f(n)

Y te preguntas:
```
¿Cómo obtengo el resultado grande usando el dato actual y el resultado del caso pequeño?
```
Ejemplo factorial:

f(4) = 24
f(5) = 120

¿Cómo llego de 24 a 120 usando 5?

5 * 24 = 120

Entonces:

f(5) = 5 * f(4)

Generalizando:

factorial(n) = n * factorial(n-1)

Ese “observar en aspa” es simplemente:

mirar la relación entre la entrada actual y el resultado recursivo.

# 3) ESTRUCTURA UNIVERSAL DE UNA FUNCION RECURSIVA

Casi todas las funciones del texto siguen esta forma:
```
funcion f(problema):
    si caso base:
        devolver respuesta directa

    reducir problema
    resolver recursivamente el problema reducido
    combinar resultado recursivo con el dato actual
    devolver resultado
```
O aun mas abstracto:
```
f(x):
    si x es simple:
        devolver base
    si no:
        devolver combinar(x, f(reducir(x)))
```
# 4) EJEMPLOS COMPLETOS
### EJEMPLO 1: Esquema general (README.md/ "esquema")

Para construir una función recursiva:

- Define entradas y salidas
- Encuentra el caso base
- Crea uno o varios casos recursivos
- Reduce el problema
- Descubre cómo se combina

El aso base es demasiado restrictivo y demasiado permisivo.


El caso base deberia ser , el minimo necesario y exactamente el puntoo donde ya no hace falta descomponer mas.

## EJMPLO 2: Factorial

Problema

Calcular:

5! = 5 × 4 × 3 × 2 × 1

Por definición:

0! = 1 

Caso base (CB): factorial(0)=1

Caso recursivo(CR): 5!=5x4x3x2x1

Generalizando: factorial(n)= n*factorial(n-1)

Pseudocodigo:

```
FUNCION factorial(n)

    SI n es 0 ENTONCES
        Devolver 1
    FIN SI

    Devolver n * factorial(n - 1)

FIN FUNCIÓN
```
## EJERCICIO 3. Suma de los N primeros

Problema

Sumar:

1 + 2 + 3 + ... + n

Ejemplo:

sumaNPrimeros(5) = 15

Caso base: sumaNPrimeros(0) = 0

Caso recurrsivo: sumaNPrimeros(5) = 5 + sumaNPrimeros(4)

Generalizando: f(n)= n+f(n-1)

Pseudocodigo:
```
FUNCION sumaNPrimeros(n)

    SI n es 0 ENTONCES
        Devolver 0
    FIN SI

    Devolver n + sumaNPrimeros(n - 1)

FIN FUNCIÓN
```

## EJEMPLO 4: Multiplicacion por sumas

Problema

Calcular a * b usando solo sumas.

Ejemplo:

5 * 4 = 5 + 5 + 5 + 5

Caso base: multiplicar(a, 0) = 0

Caso recursivo: multiplicar(a, b) = a + multiplicar(a, b-1)

Pseudocodigo:
```
FUNCION multiplicar(a, b)

    SI b es 0 ENTONCES
        Devolver 0
    FIN SI

    Devolver a + multiplicar(a, b - 1)

FIN FUNCIÓN
```

## EJEMPLO 5: Potencias (2^n)

Problema

Calcular:

2^n

Ejemplo:

2^5 = 32

Caso base: 2^0 = 1

Caso recursivo: 2^5 = 2 * 2^4

Generalizando: potencia(n) = 2 * potencia(n-1)

## EJEMPLO 6: Sumar digitos

Problema

Sumar todos los dígitos de un número.

Ejemplo:

53421 → 5 + 3 + 4 + 2 + 1 = 15

Pseudocodigo:
```
función sumaDigitos(n):
    SI n < 10:
        retornar n
    FIN SI

    numeroDeDígitos = contar_dígitos(n)
    divisor = 10^(numeroDeDígitos - 1)
    primerDígito = n / divisor
    resto = n % divisor

    retornar primerDígito + sumaDigitos(resto)
```

## EJMPLO 7: Contar de 0 hasta N

Problema

Generar una cadena:

"0, 1, 2, 3, ..., n"

Aunque el ejemplo de tabla parece tener una pequeña inconsistencia visual (pone 1,2,3,4), el pseudocódigo sí construye desde 0.

Caso base: contar(0) = "0"

Caso recursivo: contar(5) = contar(4) + ", " + "5"

General: f(n) = f(n-1) + ", " + n

Pseudocodigo:
```
FUNCION contar(n)

    SI n es 0 ENTONCES
        Devolver "0"
    FIN SI

    Devolver contar(n - 1) + ", " + n

FIN FUNCIÓN
```
## EJEMPLO 8: Contar en reversa

Problema

Construir:

"n, n-1, ..., 0"

Ejemplo:

contarEnReversa(5) = "5, 4, 3, 2, 1, 0"

Caso base: contarEnReversa(0) = "0"

Caso recursivo: contarEnReversa(5) = "5, " + contarEnReversa(4)

General: f(n) = n + ", " + f(n-1)

Pseudocodigo:
```
FUNCION contarEnReversa(n)

    SI n es 0 ENTONCES
        Devolver "0"
    FIN SI

    Devolver n + ", " + contarEnReversa(n - 1)

FIN FUNCIÓN
```

## EJEMPLO 9: Invertir cadena

Problema

Dada "abcd", devolver "dcba".

Caso base:cadena vacía "" devuelve ""

Descomposición

- cabeza = primer carácter
- resto = cadena sin el primer carácter

Para "abcd":

- cabeza = "a"
- resto = "bcd"

Caso recursivo: invertir("abcd") = invertir("bcd") + "a"

Genaral: f(cadena) = f(resto) + cabeza

Pseudocodigo:
```
FUNCION invertirCadena(cadena)

    SI longitud(cadena) es 0 ENTONCES
        Devolver ""
    FIN SI

    cabeza = primer carácter de cadena
    resto = subcadena desde la posición 1 hasta el final

    Devolver invertirCadena(resto) + cabeza

FIN FUNCIÓN
```

## EJEMPLO 10: Contar apariciones

Problema

Contar cuántas veces aparece una letra en una cadena.

Ejemplo:

"ada" con letra "a" → 2
```
FUNCION contarApariciones(cadena, letra)

    SI cadena está vacía ENTONCES
        Devolver 0
    FIN SI

    cabeza = primer carácter de cadena
    resto = subcadena desde posición 1 hasta el final

    SI cabeza es igual a letra ENTONCES
        Devolver 1 + contarApariciones(resto, letra)
    SI NO
        Devolver contarApariciones(resto, letra)
    FIN SI

FIN FUNCIÓN
```
# 5) COMO RESOLVER CUALQUIER EJERCICIO

## 1. ¿Cuál es el caso más pequeño posible? (caso base)
- número: 0 o 1
- lista: [] o [x]
- cadena: ""

## 2. ¿Cómo reduzco el problema?
- número → n-1
- lista → quitar cabeza
- cadena → quitar primer carácter
- número con dígitos → quitar último o primer dígito

## 3. ¿Qué significa f(problema reducido)?

Esto es clave.

Ejemplo:
```
sumaNumerosLista(resto) significa:
```
“la suma de todo excepto la cabeza”
```
invertirCadena(resto) significa:
```
“la inversión de la cadena sin el primer carácter”

## 4. ¿Cómo uso el dato actual + el resultado recursivo?
- sumar
- multiplicar
- concatenar antes
- concatenar después
- decidir si agregar o no
- comparar

# 6)RESUMEN DE TODOS LOS EJERCICIO EN UNA TABLA MENTAL

| Ejercicio         | Caso base                      | Reducción        | Combinación                        |
| ----------------- | ------------------------------ | ---------------- | ---------------------------------- |
| factorial         | `n == 0 → 1`                   | `n-1`            | `n * f(n-1)`                       |
| sumaNPrimeros     | `n == 0 → 0`                   | `n-1`            | `n + f(n-1)`                       |
| multiplicar(a,b)  | `b == 0 → 0`                   | `b-1`            | `a + f(a,b-1)`                     |
| potencia(2^n)     | `n == 0 → 1`                   | `n-1`            | `2 * f(n-1)`                       |
| sumarDigitos      | `n < 10 → n`                   | quitar un dígito | `digito + f(resto)`                |
| contar            | `n == 0 → "0"`                 | `n-1`            | `f(n-1) + ", " + n`                |
| contarEnReversa   | `n == 0 → "0"`                 | `n-1`            | `n + ", " + f(n-1)`                |
| invertirCadena    | `"" → ""`                      | quitar cabeza    | `f(resto) + cabeza`                |
| contarApariciones | `"" → 0`                       | quitar cabeza    | `1 + f(resto)` o `f(resto)`        |
| sumaNumerosLista  | `[] → 0`                       | quitar cabeza    | `cabeza + f(resto)`                |
| filtrarLista      | `[] → []`                      | quitar cabeza    | `[cabeza] + f(resto)` o `f(resto)` |
| encontrarElemento | `[] → false` o cabeza coincide | quitar cabeza    | seguir buscando                    |
| maximo            | `[x] → x`                      | quitar cabeza    | `max(cabeza, f(resto))`            |
| listaOrdenada     | `[]` o `[x]` → true            | quitar cabeza    | `cabeza < sig && f(resto)`         |
