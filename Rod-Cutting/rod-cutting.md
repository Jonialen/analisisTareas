# Rod-Cutting

Realizado por: José Mérida, Jonathan Díaz, Luis Padilla

---

## Ejercicio 3: Identifique las decisiones y los subproblemas en el *rod-cutting problem*

### Decisión

Para cortar un tubo en piezas que maximicen la ganancia, se empieza haciendo un primer corte en alguna posición $i$, lo que produce un trozo de longitud $i$ con ganancia $p_i$. La decisión es, entonces, dónde se hace el primer corte al tubo, es decir, qué longitud $i$ se elige para el primer trozo.

### Subproblemas

Si se tiene un tubo de longitud $n$ y se corta en la posición $i$ (para $0 \leq i \leq n$), se producen dos "subtubos". Suponiendo que el corte en $i$ lleva a la solución óptima, los subtubos que se producen tienen longitud $i$ y $n - i$.

Los subproblemas son:

- Cortar óptimamente el subtubo de longitud $i$
- Cortar óptimamente el subtubo de longitud $n - i$

---

## Ejercicio 4: Demuestre que el *rod-cutting problem* exhibe subestructura óptima

### Demostración (por contradicción)

Se supone que los subtubos producidos no son cortados óptimamente y que, luego de cortarlos, se obtienen de ellos las ganancias $a$ y $b$.

De acuerdo con la suposición del ejercicio anterior, el corte inicial en $i$ produce la ganancia máxima, que en este caso sería:

$$a + b$$

Sin embargo, como no se cortaron los subtubos óptimamente, deben existir ganancias $x > a$ e $y > b$ que se obtendrían si se cortaran los subtubos de manera óptima. Con esos cortes, la ganancia total sería:

$$x + y$$

que es mayor que $a + b$.

Esto contradice la suposición de que la solución con ganancias $a + b$ es la óptima, a pesar de que se inició con el corte $i$. Por lo tanto, si el corte inicial produce la solución óptima, es necesario que los subtubos también sean cortados de manera óptima.

Esto demuestra que el *rod-cutting problem* exhibe subestructura óptima: la solución óptima de un tubo de longitud $n$ depende de las soluciones óptimas de los subtubos que se generan al hacer el primer corte.
