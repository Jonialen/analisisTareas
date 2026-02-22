1. **Use el método de substitución para determinar la solución a la siguiente recurrencia:**

   $$
   T(n) = 4T\left(\frac{n}{2}\right) + n.
   $$

   La solución de acuerdo con el *Master Method* es $\Theta(n^2)$, pero usar la hipótesis $cn^2$ falla. Realice el procedimiento bajo esa hipótesis para comprobar que falla y luego modifique la hipótesis para que funcione.

2. **Resuelva la recurrencia**

   $$
   T(n) = 3T(\sqrt{n}) + \log_2 n.
   $$

   Para hacerlo demuestre primero que se puede convertir en

   $$
   S(m) = 3S\left(\frac{m}{2}\right) + m;
   $$

   y luego resuelva esta recurrencia con el método de substitución. Con este resultado pruebe la respuesta para la recurrencia original.

   *Hint:* note que, en $S(m)$, $m$ parece ocupar el lugar que $\log_2 n$ tiene en $T(n)$.

3. **Use un árbol de recursión** para proveer una cota ajustada a la recurrencia

   $$
   T(n) = T(n - a) + T(a) + cn,
   $$

   donde $a \ge 1$, $c > 0$; ambas constantes. Puede suponer que $n$ es múltiplo de $a$.

   **Solución:**

   Para analizar esta recurrencia mediante un árbol de recursión, observemos primero la estructura de las llamadas recursivas:

   - En cada nivel, la recurrencia hace dos llamadas: $T(n-a)$ y $T(a)$
   - El costo no recursivo en cada nivel es $cn$
   - La llamada $T(a)$ es constante y llega a la base rápidamente
   - La llamada $T(n-a)$ reduce el problema en $a$ unidades

   **Construcción del árbol:**

   ```
   Nivel 0:              cn                     Costo: cn
                        /  \
   Nivel 1:       c(n-a)    T(a)                Costo: c(n-a) + T(a)
                  /  \
   Nivel 2:   c(n-2a)  T(a)                     Costo: c(n-2a) + T(a)
              /  \
   Nivel 3: c(n-3a) T(a)                        Costo: c(n-3a) + T(a)
            ...
   Nivel k: T(a)  (varios T(a))                 Costo base
   ```

   **Análisis por niveles:**

   - **Nivel 0:** costo = $cn$
   - **Nivel 1:** costo = $c(n-a) + T(a)$
   - **Nivel 2:** costo = $c(n-2a) + T(a)$
   - **Nivel i:** costo = $c(n-ia) + T(a)$

   El árbol tiene profundidad $k = \frac{n}{a}$ (ya que en cada nivel reducimos $a$ hasta llegar a la base).

   **Suma total de costos:**

   $$
   T(n) = \sum_{i=0}^{n/a - 1} [c(n - ia) + T(a)]
   $$

   Separando la suma:

   $$
   T(n) = \sum_{i=0}^{n/a - 1} c(n - ia) + \sum_{i=0}^{n/a - 1} T(a)
   $$

   Para la primera suma:
   $$
   \sum_{i=0}^{n/a - 1} c(n - ia) = c \sum_{i=0}^{n/a - 1} (n - ia) = c\left[n \cdot \frac{n}{a} - a \sum_{i=0}^{n/a - 1} i\right]
   $$

   Usando $\sum_{i=0}^{k-1} i = \frac{k(k-1)}{2}$ con $k = \frac{n}{a}$:

   $$
   = c\left[\frac{n^2}{a} - a \cdot \frac{\frac{n}{a}(\frac{n}{a}-1)}{2}\right] = c\left[\frac{n^2}{a} - \frac{n(n-a)}{2a}\right]
   $$

   $$
   = c\left[\frac{2n^2 - n(n-a)}{2a}\right] = c\left[\frac{2n^2 - n^2 + na}{2a}\right] = c\left[\frac{n^2 + na}{2a}\right] = \frac{cn^2}{2a} + \frac{cn}{2}
   $$

   Para la segunda suma:
   $$
   \sum_{i=0}^{n/a - 1} T(a) = \frac{n}{a} \cdot T(a) = \Theta(n)
   $$

   (ya que $T(a)$ es una constante)

   **Conclusión:**

   $$
   T(n) = \frac{cn^2}{2a} + \frac{cn}{2} + \Theta(n) = \Theta(n^2)
   $$

   Por lo tanto, la cota ajustada para esta recurrencia es **$T(n) = \Theta(n^2)$**.

4. **Use el Master Method (si es posible)** para dar cotas ajustadas a las siguientes recurrencias:

   a.
   $$
   T(n) = 2T\left(\frac{n}{4}\right) + \sqrt{n}
   $$

   **Solución:**

   Para aplicar el Master Theorem, identificamos los parámetros de la recurrencia en la forma:
   $$
   T(n) = aT\left(\frac{n}{b}\right) + f(n)
   $$

   En este caso:
   - $a = 2$ (número de subproblemas)
   - $b = 4$ (factor de reducción del tamaño)
   - $f(n) = \sqrt{n} = n^{1/2}$ (costo de dividir/combinar)

   **Paso 1:** Calculamos $n^{\log_b a}$:
   $$
   n^{\log_b a} = n^{\log_4 2} = n^{1/2}
   $$

   (porque $\log_4 2 = \frac{\log 2}{\log 4} = \frac{\log 2}{2\log 2} = \frac{1}{2}$)

   **Paso 2:** Comparamos $f(n)$ con $n^{\log_b a}$:
   $$
   f(n) = n^{1/2} \quad \text{vs} \quad n^{\log_4 2} = n^{1/2}
   $$

   Son iguales: $f(n) = \Theta(n^{\log_b a})$

   **Paso 3:** Aplicamos el **Caso 2** del Master Theorem:

   Cuando $f(n) = \Theta(n^{\log_b a})$, la solución es:
   $$
   T(n) = \Theta(n^{\log_b a} \log n) = \Theta(n^{1/2} \log n) = \Theta(\sqrt{n} \log n)
   $$

   **Respuesta:** $T(n) = \Theta(\sqrt{n} \log n)$

   ---

   b.
   $$
   T(n) = 4T\left(\frac{n}{2}\right) + n^2 \log_2 n
   $$

   **Solución:**

   Identificamos los parámetros:
   - $a = 4$ (número de subproblemas)
   - $b = 2$ (factor de reducción)
   - $f(n) = n^2 \log_2 n$ (costo adicional)

   **Paso 1:** Calculamos $n^{\log_b a}$:
   $$
   n^{\log_b a} = n^{\log_2 4} = n^2
   $$

   **Paso 2:** Comparamos $f(n)$ con $n^{\log_b a}$:
   $$
   f(n) = n^2 \log_2 n \quad \text{vs} \quad n^{\log_2 4} = n^2
   $$

   Aquí vemos que:
   $$
   f(n) = n^2 \log_2 n = n^{\log_b a} \cdot \log n = \Theta(n^{\log_b a} \log n)
   $$

   Esto no corresponde exactamente a ninguno de los tres casos básicos del Master Theorem en su forma estándar. Sin embargo, existe una **extensión del Caso 2** para cuando $f(n) = \Theta(n^{\log_b a} \log^k n)$ con $k \geq 0$.

   **Caso 2 Extendido:** Si $f(n) = \Theta(n^{\log_b a} \log^k n)$ para algún $k \geq 0$, entonces:
   $$
   T(n) = \Theta(n^{\log_b a} \log^{k+1} n)
   $$

   En nuestro caso, $k = 1$, por lo tanto:
   $$
   T(n) = \Theta(n^2 \log^{1+1} n) = \Theta(n^2 \log^2 n)
   $$

   **Respuesta:** $T(n) = \Theta(n^2 \log^2 n)$

   **Nota:** Si el Master Theorem básico no permite esta forma, podemos verificar usando el árbol de recursión o el método de sustitución para confirmar que efectivamente $T(n) = \Theta(n^2 \log^2 n)$.

5. **Dé una recurrencia** que cumpla con las condiciones del tercer caso del *Master Method* excepto la condición de regularidad.

6. Sea $G = (V, E)$ un grafo dirigido. Deseamos determinar si existe un camino que conecte a dos nodos $u, v \in V$; esto se conoce como el **problema de conectividad-st** o **STCON**. El algoritmo de Savitch, presentado a continuación, determina si existe un camino con tamaño máximo $2^i$ entre dos nodos $u, v$ del grafo $G$: