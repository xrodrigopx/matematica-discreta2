# Aritmética Modular y Teoría de Congruencias

> **Fuente:** https://www.youtube.com/playlist?list=PL9lU_vBIadAza60esGrXuFaKj3mmL1nRA

---

## 1. Definiciones Formales

### 1.1. Definición de Congruencia

Dados dos números enteros cualesquiera $a$ y $b$, y un número $m$ perteneciente a los naturales no nulos ($m \in \mathbb{N}, m > 0$), se dice que **$a$ es congruente con $b$ en módulo $m$** si y solo si la diferencia $a - b$ es un múltiplo de $m$.

Se denota como:

$$a \equiv b \pmod{m} \iff \exists k \in \mathbb{Z} : a - b = k \cdot m$$

### 1.2. Relación con el Resto de la División

Una forma equivalente y fundamental de entender la congruencia es que dos números $a$ y $b$ son congruentes módulo $m$ si y solo si, al ser divididos por $m$, dejan el mismo resto. Esto implica que cualquier número $a$ puede ser representado por su resto $r$ en la división entre $m$:

$$a \equiv r \pmod{m}, \text{ donde } 0 \le r < m$$

El conjunto de todos los posibles restos $\{0, 1, 2, \dots, m-1\}$ se conoce como el **sistema completo de residuos** módulo $m$.

---

## 2. Propiedades Fundamentales

### 2.1. Propiedades de la Relación de Equivalencia

La congruencia es una relación de equivalencia, lo que implica que cumple con:

- **Reflexiva:** $a \equiv a \pmod{m}$ para todo $a$.
- **Simétrica:** Si $a \equiv b \pmod{m}$, entonces $b \equiv a \pmod{m}$.
- **Transitiva:** Si $a \equiv b \pmod{m}$ y $b \equiv c \pmod{m}$, entonces $a \equiv c \pmod{m}$.

### 2.2. Propiedades Aritméticas

Si $a \equiv b \pmod{m}$ y $c \equiv d \pmod{m}$, se verifican las siguientes operaciones miembro a miembro:

1. **Suma y Resta:**
   $$a \pm c \equiv b \pm d \pmod{m}$$

2. **Multiplicación:**
   $$a \cdot c \equiv b \cdot d \pmod{m}$$

3. **Potenciación:** Para cualquier $n \in \mathbb{N}$:
   $$a^n \equiv b^n \pmod{m}$$
   
   *Nota: Esta propiedad es especialmente útil para trabajar con exponentes grandes reduciendo primero la base.*

4. **Multiplicación por una constante:** Si $k \in \mathbb{Z}$:
   $$k \cdot a \equiv k \cdot b \pmod{m}$$

---

## 3. Teoremas Clave

### 3.1. Teorema Chino del Resto (TCR)

El Teorema Chino del Resto es la herramienta principal para resolver sistemas de ecuaciones lineales de congruencia con diferentes módulos.

- **Condición de Existencia y Unicidad:** Para que el sistema tenga una solución única, los módulos ($m_1, m_2, \dots, m_n$) deben ser **coprimos** dos a dos ($\text{mcd}=1$). La solución es única módulo $M = \prod m_i$.

- **Algoritmo de Construcción:**
  1. Se define un candidato $x_0$ como la suma de productos de los módulos excluyendo el propio. Para tres ecuaciones: $x_0 = k_1(m_2 m_3) + k_2(m_1 m_3) + k_3(m_1 m_2)$.
  2. Al analizar $x_0 \pmod{m_1}$, los términos con $m_1$ se anulan.
  3. Se ajusta cada $k_i$ con el **inverso modular** correspondiente.

### 3.2. Aplicación y Generalización del Pequeño Teorema de Fermat

Aunque el nombre del teorema no siempre se menciona, su aplicación práctica es constante para probar propiedades de todos los números naturales.

- **Enunciado Aplicado:** Para un número primo $p$, se cumple que $n^p \equiv n \pmod{p}$ para todo $n \in \mathbb{N}$. Esto implica que $n^p - n$ es siempre un **múltiplo** de $p$.

- **Reducción por Sistema Completo de Residuos:** Dado que cualquier número $n$ es congruente con uno de los restos $\{0, 1, 2, \dots, p-1\}$, para demostrar una propiedad para *todos* los naturales, basta con probarla para estos $p$ casos.

- **Ejemplo de Exponente Séptimo:** Las fuentes demuestran que $n^7 - n \equiv 0 \pmod{7}$ evaluando únicamente los restos del 0 al 6.

### 3.3. Teorema de Simplificación

- **Regla de la División:** No se puede dividir una congruencia por un factor común sin precaución:

$$\frac{a}{d}x \equiv \frac{b}{d} \pmod{\frac{m}{d}}$$

- **El Inverso Modular:** Se busca $a^{-1}$ tal que $a \cdot a^{-1} \equiv 1 \pmod{m}$.
  - *Ejemplo:* En el módulo 7, el inverso de 2 es 4, ya que $2 \times 4 = 8 \equiv 1 \pmod{7}$.
  - *Ejemplo:* En el módulo 11, el inverso de 2 es 6, ya que $2 \times 6 = 12 \equiv 1 \pmod{11}$.

### 3.4. Teorema de la Cifra Final (Módulo 10)

Este teorema establece que la cifra de las unidades de cualquier número es su residuo al ser dividido por 10.

- **Propiedad de los Cuadrados:** Si $a + b \equiv 0 \pmod{10}$, entonces $a^2 \equiv b^2 \pmod{10}$.

- **Punto de Anulación en Factoriales:** En sumas de factoriales, el término $n! \equiv 0 \pmod{10}$ para todo $n \ge 5$.

### 3.5. Criterio de Divisibilidad Universal

A través de la congruencia, se demuestra que un número $N$ y la suma de sus cifras dejan el mismo resto en la división por 3 (o por 9), porque las potencias de 10 son siempre congruentes con 1 en esos módulos: $10^k \equiv 1^k \equiv 1 \pmod{3}$.

---

## 4. Resolución de Ecuaciones de Congruencia

### 4.1. Ecuaciones Lineales de Congruencia

Una ecuación de la forma $ax \equiv b \pmod{m}$ busca hallar los valores de $x$ que satisfacen la relación.

**Pasos algorítmicos:**

1. **Simplificación (Opcional):** Si $\gcd(a, b, m) = d > 1$, se puede dividir toda la ecuación por $d$. Si $\gcd(a, m) = d$ y $d$ no divide a $b$, la ecuación no tiene solución.

2. **Método de Exhaustión:** Para módulos pequeños, se prueban todos los valores del **sistema completo de residuos** $\{0, 1, \dots, m-1\}$.

3. **Método del Inverso Modular:** Se busca un número $a^{-1}$ tal que $a \cdot a^{-1} \equiv 1 \pmod{m}$. Multiplicando ambos miembros por $a^{-1}$, se despeja $x$.
   - **Algoritmo de Euclides Extendido:** Se utiliza para encontrar el **inverso modular** cuando el módulo es grande.

---

## 5. Ejemplos Resueltos

### Ejemplo 1: Cálculo de restos con potencias grandes

**Problema:** Determinar si $22^{55} + 55^{22}$ es múltiplo de $7$.

**Solución:**

1. Reducimos las bases:
   - $22 \equiv 1 \pmod{7}$ (ya que $22 = 3 \cdot 7 + 1$)
   - $55 \equiv -1 \pmod{7}$ (ya que $55 = 8 \cdot 7 - 1$)

2. Aplicamos la propiedad de la potencia:
   - $22^{55} \equiv 1^{55} \equiv 1 \pmod{7}$
   - $55^{22} \equiv (-1)^{22} \equiv 1 \pmod{7}$ (exponente par)

3. Sumamos los resultados:
   - $22^{55} + 55^{22} \equiv 1 + 1 \equiv 2 \pmod{7}$

**Conclusión:** El resto es $2$, por lo tanto, no es múltiplo de $7$.

### Ejemplo 2: Sistema de ecuaciones (Teorema Chino del Resto)

**Problema:** Resolver el sistema:

$$
\begin{cases}
x \equiv 1 \pmod{2} \\
x \equiv 2 \pmod{3}
\end{cases}
$$

**Solución:**

1. Identificar módulos: $m_1=2, m_2=3$. Son **coprimos**.
2. Solución general: $x = x_0 + (2 \cdot 3)t = x_0 + 6t$
3. Búsqueda de $x_0$:
   - Probamos con la suma de los módulos: $2+3=5$
   - Verificación:
     - $5 \equiv 1 \pmod{2}$ ✓
     - $5 \equiv 2 \pmod{3}$ ✓

**Conclusión:** $x \equiv 5 \pmod{6}$

### Ejemplo 3: Criterio de divisibilidad entre 3

**Problema:** Demostrar que un número es múltiplo de 3 si la suma de sus cifras lo es.

**Solución:**

1. Representación polinómica: $n = d \cdot 10^0 + c \cdot 10^1 + b \cdot 10^2 + a \cdot 10^3$

2. Análisis modular:
   - $10 \equiv 1 \pmod{3}$
   - $10^k \equiv 1^k \equiv 1 \pmod{3}$ para todo $k$

3. Sustitución en el número:
   - $n \equiv d(1) + c(1) + b(1) + a(1) \pmod{3}$
   - $n \equiv d + c + b + a \pmod{3}$

**Conclusión:** El número $n$ y la suma de sus cifras dejan el mismo resto al dividir por 3.

---

## 6. Hallando la Última Cifra de una Potencia

### Fundamento Teórico

La última cifra de un número $N$ es el valor $r$ tal que:

$$N \equiv r \pmod{10}, \quad \text{donde } 0 \le r < 10$$

Para una potencia de la forma $a^n$, el objetivo es encontrar:

$$a^n \equiv x \pmod{10}$$

### Algoritmo Paso a Paso

**Paso 1: Reducción de la Base**

Simplifica la base $a$ calculando su resto módulo 10. Si $a \equiv b \pmod{10}$, entonces $a^n \equiv b^n \pmod{10}$.

Ejemplo: Para $22^{55}$, notamos que $22 \equiv 2 \pmod{10}$. Por lo tanto, $22^{55} \equiv 2^{55} \pmod{10}$.

**Paso 2: Búsqueda de una "Congruencia Buena"**

Explora las potencias de la base reducida hasta encontrar un resultado que sea congruente con $1$, $-1$ o $0$.

**Paso 3: Descomposición del Exponente**

Una vez hallado ese ciclo, si $b^k \equiv 1$, divide el exponente original entre $k$:

$$n = k \cdot q + r \implies a^n \equiv (a^k)^q \cdot a^r \pmod{m}$$

### Ejemplo: Última cifra de $3^{5555}$

1. **Exploración de potencias:**
   - $3^1 \equiv 3 \pmod{10}$
   - $3^2 \equiv 9 \equiv -1 \pmod{10}$ *(¡Congruencia buena!)*

2. **Aplicación:** Como $5555 = 2 \cdot 2777 + 1$:
   $$3^{5555} = (3^2)^{2777} \cdot 3^1$$

3. **Sustitución:**
   $$3^{5555} \equiv (-1)^{2777} \cdot 3 \pmod{10}$$
   Como $2777$ es impar: $(-1)^{2777} \equiv -1$
   $$3^{5555} \equiv -1 \cdot 3 \equiv -3 \equiv 7 \pmod{10}$$

**Conclusión:** La última cifra de $3^{5555}$ es **7**.

---

## 7. Exponentes Muy Grandes

Cuando un exponente es muy grande, los números resultantes se vuelven inmanejables. Sin embargo, mediante la aritmética modular, es posible determinar el resto sin calcular el valor real.

### Proceso de Simplificación

1. **Reducción de la Base:** Sustituir una base grande por su resto módulo $m$.
   - Ejemplo: $2222^{5555} \equiv 3^{5555} \pmod{7}$ (ya que $2222 \equiv 3 \pmod{7}$)

2. **Búsqueda de Ciclos:** Encontrar una potencia $a^k \equiv 1 \pmod{m}$ o $a^k \equiv -1 \pmod{m}$.

3. **Descomposición:** Expresar $n = k \cdot q + r$ para reducir el exponente.

4. **Análisis de Paridad:** Si $a^k \equiv -1$, el resultado depende de si $q$ es par o impar.

---

## 8. Aplicaciones Prácticas

- **Calendarios:** Cálculo de días de la semana utilizando módulo 7
- **Cifras Terminales:** Para hallar la última cifra (módulo 10)
- **Detección de errores:** Dígitos verificadores y criptografía RSA

---

## 9. Suma de Factoriales (Ejemplo: Última Cifra)

**Problema:** Hallar la cifra de las unidades de $n = 1! + 2! + 3! + \dots + 100!$

**Solución:**

1. **Primeros términos en módulo 10:**
   - $1! = 1 \equiv 1 \pmod{10}$
   - $2! = 2 \equiv 2 \pmod{10}$
   - $3! = 6 \equiv 6 \pmod{10}$
   - $4! = 24 \equiv 4 \pmod{10}$

2. **Punto de anulación:** Para $k \ge 5$:
   $$k! \equiv 0 \pmod{10}$$
   (porque contiene los factores 2 y 5)

3. **Suma de congruencias:**
   $$n \equiv 1 + 2 + 6 + 4 + 0 + 0 + \dots + 0 \pmod{10}$$
   $$n \equiv 13 \equiv 3 \pmod{10}$$

**Conclusión:** La cifra de las unidades es **3**.

---

## 10. Ejercicios Propuestos

### Problemas de Múltiplos y Divisibilidad

1. Probar que $22^{55} + 55^{22}$ es múltiplo de $7$
2. Investigar si para todo $n \in \mathbb{N}$: $n^7 - n$ es múltiplo de $7$
3. Investigar si para todo $n \in \mathbb{N}$: $5^{3n+1} + 2 \cdot 7^{2n+1}$ es múltiplo de $19$
4. Demostrar que para todo $n \in \mathbb{N}$: $2^{2n+5} \cdot 3^n + 1$ es múltiplo de $11$
5. Investigar si $2222^{5555} + 5555^{2222}$ es múltiplo de $7$

### Cifras Terminales y Calendarios

1. Si hoy es lunes, ¿qué día será dentro de $14,735$ días?
2. Si hoy es lunes, ¿qué día será dentro de $23,916$ días?
3. Calcular la cifra de las unidades de $1! + 2! + 3! + \dots + 100!$

### Demostraciones Teóricas

1. Demostrar que si $a + b \equiv 0 \pmod{10}$, entonces $a^2 \equiv b^2 \pmod{10}$
2. Demostrar que si $a^2 + b^2 \equiv 0 \pmod{3}$, entonces $a \equiv 0 \pmod{3}$ y $b \equiv 0 \pmod{3}$
3. Demostrar formalmente el criterio de divisibilidad entre 3
4. Verificar mediante la definición de congruencia:
   - $21 \equiv -3 \pmod{8}$
   - $-7 \equiv -22 \pmod{5}$
   - $62 \equiv 6 \pmod{7}$

### Ecuaciones Lineales de Congruencia

Hallar todas las soluciones enteras:

1. $x \equiv 4 \pmod{7}$
2. $3x \equiv 2 \pmod{7}$
3. $4x \equiv 7 \pmod{5}$
4. $6x \equiv 3 \pmod{4}$
5. $4x \equiv 2 \pmod{6}$
6. $2x \equiv 1 \pmod{6}$

### Sistemas de Ecuaciones en Congruencias

1. 
$$
\begin{cases}
x \equiv 1 \pmod{2} \\
x \equiv 2 \pmod{3}
\end{cases}
$$

2. 
$$
\begin{cases}
x \equiv 2 \pmod{3} \\
x \equiv 1 \pmod{5}
\end{cases}
$$

3. 
$$
\begin{cases}
x \equiv -1 \pmod{7} \\
2x \equiv 5 \pmod{11}
\end{cases}
$$

4. 
$$
\begin{cases}
x \equiv 2 \pmod{3} \\
x \equiv 3 \pmod{5} \\
x \equiv 1 \pmod{7}
\end{cases}
$$

5. 
$$
\begin{cases}
2x \equiv 1 \pmod{7} \\
x \equiv 1 \pmod{5} \\
2x \equiv 32 \pmod{6} \\
4x \equiv 6 \pmod{2}
\end{cases}
$$

### Ejercicios Adicionales de Práctica

1. Determina los últimos dos dígitos de $7^{25} + 25^7$
2. Probar que el número inmediatamente posterior a cualquier potencia de 5 es múltiplo de 2 pero no de 4
3. Calcula el último dígito de: $6^{20}$, $7^{93}$ y $23^{189}$
4. Calcula el resto de:
   - (a) $7^{512} \div 11$
   - (b) $3^{47} \div 23$
   - (c) $3^{15} \div 17$
   - (d) $125^{4577} \div 13$
   - (e) $11^{954} \div 20$
   - (f) $(140^{1221} + 28^{753}) \div 13$
5. Calcula el residuo de $84^{1234}$ en los módulos $2$, $5$ y $7$
6. Demuestra que para cualquier $n \in \mathbb{Z}$ las últimas cifras de $n$ y $n^5$ son iguales
7. Probar que $7^{2n} + 16n - 1$ es múltiplo de $16$

---

**Última actualización:** $(18-04-2026)$
