# Demostración: Merge Sort es $O(n \log_2 n)$ usando el Método de Sustitución

## Planteamiento del Problema

Queremos demostrar que el algoritmo *Merge Sort* tiene complejidad temporal $O(n \log_2 n)$ utilizando el **método de sustitución**.

La recurrencia que modela el tiempo de ejecución de *Merge Sort* es:

$$T(n) = 2T\left(\frac{n}{2}\right) + n, \quad T(1) = 1$$

Debemos probar que $T(n) = O(n \log_2 n)$.

---

## Paso 1: Hipótesis de Inducción Inicial (Problema)

Intentamos primero con la hipótesis más natural:

> **Hipótesis inicial:** Existe $c > 0$ tal que $T(n) \le c \, n \log_2 n$ para todo $n \ge 1$.

### Verificación del Caso Base ($n = 1$)

Para $n = 1$:

$$T(1) = 1$$

Según la hipótesis:

$$T(1) \le c \cdot 1 \cdot \log_2 1 = c \cdot 1 \cdot 0 = 0$$

Esto implica:

$$1 \le 0$$

**Contradicción.** La hipótesis no funciona porque $\log_2 1 = 0$ hace que la cota sea cero, pero $T(1) = 1$.

---

## Paso 2: Modificación de la Hipótesis de Inducción

Para resolver el problema del caso base, agregamos un término aditivo de orden menor.

> **Nueva hipótesis:** Existe $c > 0$ tal que:
> $$T(n) \le c \, n \log_2 n + n$$
> para todo $n \ge 1$.

El término adicional $+n$ es de orden inferior a $n \log_2 n$ (cuando $n \to \infty$), por lo que no afecta la clasificación asintótica $O(n \log_2 n)$.

---

## Paso 3: Verificación del Caso Base con la Nueva Hipótesis

Para $n = 1$:

$$T(1) = 1$$

Evaluamos la hipótesis:

$$c \cdot 1 \cdot \log_2 1 + 1 = c \cdot 0 + 1 = 1$$

Por lo tanto:

$$T(1) = 1 \le 1$$

**El caso base se cumple** para cualquier $c > 0$.

---

## Paso 4: Paso Inductivo

### Hipótesis Inductiva

Asumimos que para todo $k < n$:

$$T(k) \le c \, k \log_2 k + k$$

### Demostración para $n$

Partimos de la recurrencia:

$$T(n) = 2T\left(\frac{n}{2}\right) + n$$

Aplicamos la hipótesis inductiva a $T\left(\frac{n}{2}\right)$:

$$T\left(\frac{n}{2}\right) \le c \cdot \frac{n}{2} \cdot \log_2\left(\frac{n}{2}\right) + \frac{n}{2}$$

Sustituimos en la recurrencia:

$$T(n) \le 2\left[c \cdot \frac{n}{2} \cdot \log_2\left(\frac{n}{2}\right) + \frac{n}{2}\right] + n$$

Simplificamos:

$$T(n) \le c \, n \log_2\left(\frac{n}{2}\right) + n + n$$

$$T(n) \le c \, n \log_2\left(\frac{n}{2}\right) + 2n$$

---

