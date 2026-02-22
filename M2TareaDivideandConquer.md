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
   T(n - a) + T(a) + cn,
   $$

   donde $a \ge 1$, $c > 0$; ambas constantes. Puede suponer que $n$ es múltiplo de $a$.

4. **Use el Master Method (si es posible)** para dar cotas ajustadas a las siguientes recurrencias:

   a.
   $$
   T(n) = 2T\left(\frac{n}{4}\right) + \sqrt{n}
   $$

   b.
   $$
   T(n) = 4T\left(\frac{n}{2}\right) + n^2 \log_2 n
   $$

5. **Dé una recurrencia** que cumpla con las condiciones del tercer caso del *Master Method* excepto la condición de regularidad.

6. Sea $G = (V, E)$ un grafo dirigido. Deseamos determinar si existe un camino que conecte a dos nodos $u, v \in V$; esto se conoce como el **problema de conectividad-st** o **STCON**. El algoritmo de Savitch, presentado a continuación, determina si existe un camino con tamaño máximo $2^i$ entre dos nodos $u, v$ del grafo $G$: