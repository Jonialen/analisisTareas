
## 5 Argumente por que, para constantes reales cualquiera $a$ $y$ $b > 0$, $(n + a)^b = \Theta(n^b)$

**Enunciado:**  $a$ y $b > 0$, $(n + a)^b = \Theta(n^b)$

**Forma Expandida (Hint):**

Utilizando una generalización del Teorema del Binomio se puede expresar la función como:

$$(n+a)^b = \left[ n \left(1 + \frac{a}{n}\right) \right]^b = n^b \left(1 + \frac{a}{n}\right)^b$$

Si expandimos el término $\left(1 + \frac{a}{n}\right)^b$ usando series de Taylor, se obtiene:

$$(n+a)^b = n^b \left( 1 + b\left(\frac{a}{n}\right) + \frac{b(b-1)}{2!}\left(\frac{a}{n}\right)^2 + \dots \right)$$
$$(n+a)^b = n^b + abn^{b-1} + \dots$$

En el análisis, los términos de orden inferior ($n^{b-1}, n^{b-2}, \dots$) se vuelven insignificantes frente al término dominante $n^b$ cuando $n \to \infty$.

**Prueba mediante Límite:**

Se calcula el límite del cociente entre la función y su propuesta asintótica:

$$L = \lim_{n \to \infty} \frac{(n+a)^b}{n^b} = \lim_{n \to \infty} \left( \frac{n+a}{n} \right)^b = \lim_{n \to \infty} \left( 1 + \frac{a}{n} \right)^b$$
Sabemos que $\lim_{n \to \infty} \frac{a}{n} = 0$ para cualquier constante real $a$.

$$L = (1 + 0)^b = 1$$

Dado que el límite es una constante positiva $0 < L < \infty$, por definición de $\Theta$:
$$(n+a)^b = \Theta(n^b)$$
---

## 6 ¿Es $2^{n+1} = O(2^n)$? ¿Es $2^{2n} = O(2^n)$?

**Enunciado:** ¿Es $2^{n+1} = O(2^n)$? ¿Es $2^{2n} = O(2^n)$?

### Parte A: $2^{n+1} = O(2^n)$

**Demostración:**

Se busca $c > 0, n_0$ tales que $2^{n+1} \le c \cdot 2^n$.

$$2^{n+1} = 2^1 \cdot 2^n = 2 \cdot 2^n$$

Si se selecciona $c \ge 2$ y $n_0 = 1$:

$$2 \cdot 2^n \le c \cdot 2^n$$

La desigualdad se mantiene.

**Respuesta:**

Si, $2^{n+1} = O(2^n)$.

### Parte B: $2^{2n} = O(2^n)$

**Demostración:**

Se simplifica la expresion izquierda:

$$2^{2n} = (2^2)^n = 4^n$$

Por lo que:

$$4^n = O(2^n)$$

Entonces $\exists c$ tal que $4^n \le c \cdot 2^n$.

Dividiendo por $2^n$:

$$\frac{4^n}{2^n} \le c \implies 2^n \le c$$

Esto implica que la función $2^n$ está acotada por una constante $c$, lo cual es falso ya que $\lim_{n \to \infty} 2^n = \infty$.

**Respuesta:** 
No. $2^{2n} \neq O(2^n)$

---

## 7. Demuestre las siguientes propiedades:

### Inciso a

**Proposición:** $f(n) = \Theta(g(n)) \iff f(n) = O(g(n)) \land f(n) = \Omega(g(n))$.

**Demostración:**

**($\Rightarrow$) Si es $\Theta$, entonces es $O$ y $\Omega$:**

Por definición de $\Theta(g(n))$, existen $c_1, c_2, n_0$ tales que para todo $n \ge n_0$:

$$0 \le c_1 g(n) \le f(n) \le c_2 g(n)$$

La parte derecha $f(n) \le c_2 g(n)$ satisface la definición de $O(g(n))$.

La parte izquierda $c_1 g(n) \le f(n)$ satisface la definición de $\Omega(g(n))$.

**($\Leftarrow$) Si es $O$ y $\Omega$, entonces es $\Theta$:**

$f(n) = O(g(n)) \implies f(n) \le c_2 g(n)$ para $n \ge n_a$.

$f(n) = \Omega(g(n)) \implies f(n) \ge c_1 g(n)$ para $n \ge n_b$.

Sea $n_0 = \max(n_a, n_b)$. Para $n \ge n_0$ ambas desigualdades son ciertas simultáneamente, recuperando la definición de $\Theta$.

### Inciso b

**Proposición:** $o(g(n)) \cap \omega(g(n)) = \emptyset$.

**Demostración por Contradicción:**

Se supone que existe una función $f(n)$ tal que $f(n) \in o(g(n))$ y $f(n) \in \omega(g(n))$.

Por definición de $o(g(n))$ (MIT Lecture Notes):

$$\lim_{n \to \infty} \frac{f(n)}{g(n)} = 0$$
Por definición de $\omega(g(n))$:

$$\lim_{n \to \infty} \frac{f(n)}{g(n)} = \infty$$

Una función bien definida no puede tender a $0$ y a $\infty$ al mismo tiempo cuando $n \to \infty$.

$$\therefore o(g(n)) \cap \omega(g(n)) = \emptyset$$

### Inciso c

**Proposición:** $f(n) = O(g(n)) \implies \log_2 f(n) = O(\log_2 g(n))$.

**Demostración:**

Existe $c, n_0$ tal que $f(n) \le c \cdot g(n)$ para $n \ge n_0$.

Se aplica $\log_2$
$$\log_2 f(n) \le \log_2(c \cdot g(n))$$
$$\log_2 f(n) \le \log_2 c + \log_2 g(n)$$

Para demostrar que es $O(\log_2 g(n))$, se necesita acotar $\log_2 c$ en terminos de $\log_2 g(n)$.

Dado que $\log_2 g(n) \ge 1$, cualquier constante $K = \log_2 c$ puede ser acotada por $|K| \cdot \log_2 g(n)$.

Sustituyendo:
$$\log_2 f(n) \le |K| \cdot \log_2 g(n) + 1 \cdot \log_2 g(n)$$
$$\log_2 f(n) \le (|K| + 1) \log_2 g(n)$$

Sea la nueva constante $C' = |K| + 1$.
$$\log_2 f(n) \le C' \cdot \log_2 g(n)$$
$$\therefore \log_2 f(n) = O(\log_2 g(n))$$