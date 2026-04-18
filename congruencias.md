Este documento constituye un cuerpo de conocimiento estructurado sobre la aritmética modular y la teoría de congruencias, analizado desde una perspectiva formal.

---

## 1. Definiciones Formales

### 1.1. Definición de Congruencia

Dados dos números enteros cualesquiera $a$ y $b$, y un número $m$ perteneciente a los naturales no nulos ($m \in \mathbb{N}, m > 0$), se dice que **$a$ es congruente con $b$ en módulo $m$** si y solo si la diferencia $a - b$ es un múltiplo de $m$.

Se denota como: $$a \equiv b \pmod{m} \iff \exists k \in \mathbb{Z} : a - b = k \cdot m$$

### 1.2. Relación con el Resto de la División

Una forma equivalente y fundamental de entender la congruencia es que dos números $a$ y $b$ son congruentes módulo $m$ si y solo si, al ser divididos por $m$, dejan el mismo resto. Esto implica que cualquier número $a$ puede ser representado por su resto $r$ en la división entre $m$: $$a \equiv r \pmod{m}, \text{ donde } 0 \le r < m$$

El conjunto de todos los posibles restos ${0, 1, 2, \dots, m-1}$ se conoce como el **sistema completo de residuos** módulo $m$.

---

## 2. Propiedades Fundamentales

### 2.1. Propiedades de la Relación de Equivalencia

La congruencia es una relación de equivalencia, lo que implica que cumple con:

- **Reflexiva:** $a \equiv a \pmod{m}$ para todo $a$.
- **Simétrica:** Si $a \equiv b \pmod{m}$, entonces $b \equiv a \pmod{m}$.
- **Transitiva:** Si $a \equiv b \pmod{m}$ y $b \equiv c \pmod{m}$, entonces $a \equiv c \pmod{m}$.

### 2.2. Propiedades Aritméticas

Si $a \equiv b \pmod{m}$ y $c \equiv d \pmod{m}$, se verifican las siguientes operaciones miembro a miembro:

1. **Suma y Resta:** $$a \pm c \equiv b \pm d \pmod{m}$$
2. **Multiplicación:** $$a \cdot c \equiv b \cdot d \pmod{m}$$
3. **Potenciación:** Para cualquier $n \in \mathbb{N}$: $$a^n \equiv b^n \pmod{m}$$ _Nota: Esta propiedad es especialmente útil para trabajar con exponentes grandes reduciendo primero la base._
4. **Multiplicación por una constante:** Si $k \in \mathbb{Z}$: $$k \cdot a \equiv k \cdot b \pmod{m}$$

---

## 3. Teoremas Clave

### 3.1. Generalización del Pequeño Teorema de Fermat

Aunque no se nombra explícitamente en todas las fuentes, se demuestra su aplicación práctica. Por ejemplo, se analiza que $n^7 \equiv n \pmod{7}$ para todo $n$ natural. En general, para un número primo $p$: $$a^p \equiv a \pmod{p}$$

### 3.2. Teorema Chino del Resto (TCR)

Este teorema es fundamental para resolver sistemas de ecuaciones en congruencias.

- **Condición de Aplicación:** Los módulos $m_1, m_2, \dots, m_n$ deben ser **coprimos** dos a dos (es decir, el máximo común divisor entre cualquier par es 1).
- **Enunciado:** El sistema tiene una solución única módulo $M$, donde $M = m_1 \cdot m_2 \cdot \dots \cdot m_n$.

**Algoritmo de resolución por construcción de candidato:**

1. Se busca una solución particular $x_0$.
2. Se construye un candidato como suma de productos de los módulos de dos en dos (o omitiendo un módulo por término): $x = k_1(m_2 \cdot m_3) + k_2(m_1 \cdot m_3) + k_3(m_1 \cdot m_2)$.
3. Se ajustan los coeficientes $k_i$ multiplicando por los **inversos modulares** necesarios para que el candidato satisfaga cada ecuación del sistema sin alterar las demás.
4. La solución general es $x \equiv x_0 \pmod{M}$.

---

## 4. Resolución de Ecuaciones de Congruencia

### 4.1. Ecuaciones Lineales de Congruencia

Una ecuación de la forma $ax \equiv b \pmod{m}$ busca hallar los valores de $x$ que satisfacen la relación.

**Pasos algorítmicos:**

1. **Simplificación (Opcional):** Si $\text{mcd}(a, b, m) = d > 1$, se puede dividir toda la ecuación por $d$. Si $\text{mcd}(a, m) = d$ y $d$ no divide a $b$, la ecuación no tiene solución.
2. **Método de Exhaustión:** Para módulos pequeños, se prueban todos los valores del **sistema completo de residuos** ${0, 1, \dots, m-1}$.
3. **Método del Inverso Modular:** Se busca un número $a^{-1}$ tal que $a \cdot a^{-1} \equiv 1 \pmod{m}$. Multiplicando ambos miembros por $a^{-1}$, se despeja $x$.
    - **Algoritmo de Euclides Extendido:** Se utiliza para encontrar el **inverso modular** cuando el módulo es grande, resolviendo la ecuación diofántica $ax + my = 1$.

---

## 5. Ejemplos Resueltos

### Ejemplo 1: Cálculo de restos con potencias grandes

**Problema:** Determinar si $22^{55} + 55^{22}$ es múltiplo de $7$.

1. Reducimos las bases:
    - $22 \equiv 1 \pmod{7}$ (ya que $22 = 3 \cdot 7 + 1$).
    - $55 \equiv -1 \pmod{7}$ (ya que $55 = 8 \cdot 7 - 1$ o $56-1$).
2. Aplicamos la propiedad de la potencia:
    - $22^{55} \equiv 1^{55} \equiv 1 \pmod{7}$.
    - $55^{22} \equiv (-1)^{22} \equiv 1 \pmod{7}$ (exponente par).
3. Sumamos los resultados:
    - $22^{55} + 55^{22} \equiv 1 + 1 \equiv 2 \pmod{7}$.
4. **Conclusión:** El resto es $2$, por lo tanto, no es múltiplo de $7$.

### Ejemplo 2: Sistema de ecuaciones (Teorema Chino del Resto)

**Problema:** Resolver el sistema: $\begin{cases} x \equiv 1 \pmod{2} \ x \equiv 2 \pmod{3} \end{cases}$

1. Identificar módulos: $m_1=2, m_2=3$. Son **coprimos**.
2. Solución general: $x = x_0 + (2 \cdot 3)t = x_0 + 6t$.
3. Búsqueda de $x_0$:
    - Probamos con la suma de los módulos: $2+3=5$.
    - Verificación:
        - $5 \equiv 1 \pmod{2}$ (Correcto).
        - $5 \equiv 2 \pmod{3}$ (Correcto).
4. **Conclusión:** $x \equiv 5 \pmod{6}$.

### Ejemplo 3: Criterio de divisibilidad entre 3

**Problema:** Demostrar que un número es múltiplo de 3 si la suma de sus cifras lo es.

1. Representación polinómica: $n = d \cdot 10^0 + c \cdot 10^1 + b \cdot 10^2 + a \cdot 10^3$.
2. Análisis modular base 10:
    - $10 \equiv 1 \pmod{3}$.
    - $10^k \equiv 1^k \equiv 1 \pmod{3}$ para todo $k$.
3. Sustitución en el número:
    - $n \equiv d(1) + c(1) + b(1) + a(1) \pmod{3}$.
    - $n \equiv d + c + b + a \pmod{3}$.
4. **Conclusión:** El número $n$ y la suma de sus cifras dejan el mismo resto al dividir por 3. Si la suma es congruente con 0, el número también.

---

## 6. Aplicaciones Prácticas

- **Calendarios:** Cálculo de días de la semana utilizando módulo 7.
- **Cifras Terminales:** Para hallar la última cifra de un número (como una suma de factoriales), se trabaja en módulo 10.
- **Detección de errores:** Aunque no se profundiza en los videos, el uso de congruencias es la base de dígitos verificadores y criptografía como **RSA**, donde la seguridad reside en la dificultad de revertir operaciones en módulos de números **coprimos** muy grandes.

## ¿Cómo se aplica la congruencia para hallar la última cifra?

Para hallar la **última cifra** (o cifra de las unidades) de un número o de una expresión aritmética compleja, la herramienta fundamental es el cálculo del **resto** de la división entre 10, utilizando la aritmética modular en **módulo 10**.

A continuación, se detalla el procedimiento formal, las propiedades aplicadas y ejemplos resueltos basados en las fuentes.

---

## 1. El Principio Fundamental

Cualquier número entero $N$ puede expresarse en relación a su última cifra mediante la congruencia: $$N \equiv r \pmod{10}$$ Donde $r$ representa el **resto** de dividir $N$ entre 10, el cual coincide exactamente con la **cifra de las unidades**. Por ejemplo, para el número 147, al dividirlo entre 10 el cociente es 14 y el resto es 7; por lo tanto, $147 \equiv 7 \pmod{10}$.

---

## 2. Propiedades Aplicadas

Para resolver expresiones con números muy grandes (potencias o sumas extensas), se utilizan las propiedades de la congruencia para simplificar los cálculos antes de operar:

1. **Suma miembro a miembro:** Si $a \equiv b \pmod{10}$ y $c \equiv d \pmod{10}$, entonces $a + c \equiv b + d \pmod{10}$.
2. **Multiplicación y Potenciación:** Permite reducir la base de una potencia a su resto antes de elevarla: $a^n \equiv (a \pmod{10})^n \pmod{10}$.
3. **Anulación de términos:** En sucesiones como los factoriales, los términos se vuelven congruentes con 0 a partir del momento en que el módulo es un divisor del término.

---

## 3. Ejemplo Resuelto: Suma de Factoriales

**Problema:** Hallar la cifra de las unidades del número $n = 1! + 2! + 3! + \dots + 100!$.

**Paso 1: Analizar los primeros términos en módulo 10.**

- $1! = 1 \equiv 1 \pmod{10}$
- $2! = 2 \equiv 2 \pmod{10}$
- $3! = 6 \equiv 6 \pmod{10}$
- $4! = 24 \equiv 4 \pmod{10}$

**Paso 2: Identificar el punto de anulación.** A partir de $5!$, el factor 10 aparece en la descomposición del factorial ($5 \times 4 \times 3 \times 2 \times 1 = 120$). Como $120$ es múltiplo de 10, entonces $5! \equiv 0 \pmod{10}$. Dado que cualquier factorial superior ($6!, 7!, \dots$) contiene a $5!$ como factor, todos ellos también serán múltiplos de 10: $$k! \equiv 0 \pmod{10} \quad \text{para todo } k \ge 5$$

**Paso 3: Sumar las congruencias.** Aplicando la propiedad de la suma miembro a miembro: $$n \equiv 1 + 2 + 6 + 4 + 0 + 0 + \dots + 0 \pmod{10}$$ $$n \equiv 13 \pmod{10}$$ Como $13$ al dividirse entre 10 deja resto 3: $$n \equiv 3 \pmod{10}$$

**Conclusión:** La cifra de las unidades de la suma de los primeros 100 factoriales es **3**.

---

## 4. Aplicación en Potencias y Cuadrados

El uso del módulo 10 también permite demostrar propiedades generales sobre cómo terminan los números. Por ejemplo, si dos números $a$ y $b$ cumplen que su suma es divisible entre 10 ($a + b \equiv 0 \pmod{10}$), se puede demostrar que sus cuadrados $a^2$ y $b^2$ tendrán la **misma cifra final**.

Esto se demuestra viendo que: $$(a+b)(a-b) \equiv 0 \cdot (a-b) \equiv 0 \pmod{10}$$ $$a^2 - b^2 \equiv 0 \pmod{10} \implies a^2 \equiv b^2 \pmod{10}$$ Lo que confirma que ambos cuadrados dejan el mismo resto al dividirse por 10 y, por ende, comparten la misma cifra final.


# ¿Cómo se halla la última cifra de una potencia?

Para hallar la **última cifra** de una potencia, el método más preciso consiste en utilizar la aritmética modular, específicamente trabajando en **módulo 10**. Como se explica en las fuentes, la cifra de las unidades de cualquier número entero es equivalente al resto de su división entre 10,.

A continuación, se describe el procedimiento algorítmico y formal para resolver este tipo de problemas.

---

## 1. Fundamento Teórico

La última cifra de un número $N$ es el valor $r$ tal que: $$N \equiv r \pmod{10}, \quad \text{donde } 0 \le r < 10$$ Para una potencia de la forma $a^n$, el objetivo es encontrar: $$a^n \equiv x \pmod{10}$$ Donde $x$ será la cifra buscada.

---

## 2. Algoritmo Paso a Paso

### Paso 1: Reducción de la Base

Antes de operar con el exponente, se debe simplificar la base $a$ calculando su resto módulo 10. Por la propiedad de la potencia en congruencias, si $a \equiv b \pmod{10}$, entonces $a^n \equiv b^n \pmod{10}$,.

- **Ejemplo:** Si queremos la última cifra de $22^{55}$, primero notamos que $22 \equiv 2 \pmod{10}$. Por lo tanto, $22^{55} \equiv 2^{55} \pmod{10}$.

### Paso 2: Búsqueda de una "Congruencia Buena"

Para manejar exponentes grandes, se exploran las potencias de la base reducida hasta encontrar un resultado que sea **congruente** con $1$, $-1$ o $0$ en el módulo dado,.

- **Caso del 1:** Si $b^k \equiv 1 \pmod{10}$, cualquier potencia posterior de $b^k$ seguirá siendo 1, lo que simplifica enormemente el cálculo,.
- **Caso del -1:** Si $b^k \equiv -1 \pmod{10}$, el resultado será $1$ si el exponente es par y $-1$ (que equivale a 9 en módulo 10) si es impar,.

### Paso 3: Descomposición del Exponente

Una vez hallado ese ciclo o valor especial (digamos $b^k \equiv 1$), se divide el exponente original $n$ entre $k$ para expresar la potencia original de forma descompuesta: $$n = k \cdot q + r \implies a^n \equiv (a^k)^q \cdot a^r \pmod{m}$$ Este paso permite reducir el exponente a un valor mucho más pequeño y manejable,.

---

## 3. Ejemplo de Aplicación Algorítmica

Aunque las fuentes detallan este proceso para otros módulos, la lógica para hallar la última cifra ($mod \ 10$) sigue el mismo rigor mostrado en el cálculo de $3^{5555} \pmod{7}$:

**Problema:** Hallar la última cifra de $3^{5555}$.

1. **Exploración de potencias de la base:**
    - $3^1 \equiv 3 \pmod{10}$
    - $3^2 \equiv 9 \equiv -1 \pmod{10}$ **(¡Congruencia buena encontrada!)**.
2. **Aplicación de la propiedad de potencia:** Elevamos ambos miembros de $3^2 \equiv -1$ a una potencia que se acerque a $5555$. Como $5555 = 2 \cdot 2777 + 1$: $$3^{5555} = (3^2)^{2777} \cdot 3^1$$
3. **Sustitución y resolución:** $$3^{5555} \equiv (-1)^{2777} \cdot 3 \pmod{10}$$ Como el exponente $2777$ es impar, $(-1)^{2777} \equiv -1$: $$3^{5555} \equiv -1 \cdot 3 \equiv -3 \pmod{10}$$
4. **Ajuste al sistema completo de residuos:** Un resto de $-3$ en módulo 10 es equivalente a $10 - 3 = 7$.

**Conclusión:** La última cifra de $3^{5555}$ es **7**.

---

## 4. Observaciones Importantes para Exámenes

- **Ceros deterministas:** Si la base reducida es múltiplo de $10$ (como en los factoriales $n!$ para $n \ge 5$), la potencia siempre terminará en $0$.
- **Propiedad de los cuadrados:** Si dos números suman un múltiplo de 10, sus cuadrados terminan en la misma cifra, ya que $a^2 \equiv b^2 \pmod{10}$ si $a + b \equiv 0 \pmod{10}$,.
- **Inverso Modular:** En ecuaciones más complejas del tipo $ax \equiv b \pmod{10}$, se debe buscar el **inverso modular** de $a$ para despejar $x$, siempre que $a$ y $10$ sean **coprimos**,.

## ¿Qué sucede cuando el exponente es muy grande?

Cuando un exponente es muy grande, los números resultantes se vuelven **inmanejables** o "abismales", superando incluso la cantidad de átomos que componen la Tierra o la capacidad de cualquier calculadora estándar. Sin embargo, mediante la aritmética modular, es posible determinar el resto de estos números sin necesidad de calcular su valor real, siguiendo un proceso de simplificación basado en las propiedades de las congruencias.

A continuación se detalla qué sucede y cómo se procede matemáticamente ante exponentes elevados:

### 1. Inviabilidad de los Métodos Clásicos

Los algoritmos tradicionales de división o criterios de divisibilidad resultan ineficientes para exponentes grandes. Por ejemplo, un número como $55^{22}$ tiene casi 40 cifras y $22^{55}$ tiene alrededor de 70 cifras. Operar con ellos directamente es impracticable, pero la congruencia permite extraer información (como el resto) de forma directa.

### 2. El Poder de la Reducción de la Base

Lo primero que sucede es que se aplica la propiedad de la potencia: si $a \equiv b \pmod{m}$, entonces $a^n \equiv b^n \pmod{m}$. Esto permite sustituir una base grande por su resto, que es un número mucho más pequeño y manejable.

- **Ejemplo:** Para analizar $2222^{5555} \pmod{7}$, primero se reduce la base: $2222 \equiv 3 \pmod{7}$.

### 3. Búsqueda de "Congruencias Buenas" ($\pm 1$)

El objetivo principal cuando el exponente es grande es encontrar una potencia de la base que sea congruente con $1$ o $-1$ respecto al módulo.

- **Caso del 1:** Si se halla que $a^k \equiv 1 \pmod{m}$, entonces cualquier múltiplo del exponente $k$ mantendrá el resultado como $1$, ya que $1^n = 1$ para cualquier $n$.
- **Caso del -1:** Si $a^k \equiv -1 \pmod{m}$, el resultado de elevarlo a una potencia $n$ dependerá únicamente de si $n$ es **par** ($1$) o **impar** ($-1$).

### 4. Algoritmo de Descomposición del Exponente

Cuando el exponente $n$ no es una potencia directa de una "congruencia buena", se utiliza el algoritmo de la división para descomponerlo. Si sabemos que $a^k \equiv \pm 1$, dividimos el exponente grande $n$ entre $k$: $$n = k \cdot q + r$$ Donde $q$ es el cociente y $r$ es el resto. Esto permite reescribir la potencia como: $$a^n = (a^k)^q \cdot a^r$$ En términos de congruencia: $$a^n \equiv (\pm 1)^q \cdot a^r \pmod{m}$$ Este proceso reduce un exponente de miles de cifras a uno extremadamente pequeño (el resto $r$).

### 5. Análisis de Ciclos y Restos

Para exponentes variables (como $n$ en $11^n$), se observa que el comportamiento de los restos suele ser cíclico o permite factorizaciones estratégicas que simplifican la expresión hasta convertirla en un múltiplo del módulo (congruente con $0$).

---

## 1. Problemas de Múltiplos y Divisibilidad

Estos ejercicios requieren demostrar si una expresión dada es divisible por un número específico para valores naturales de $n$.

- **Ejercicio 1.1:** Probar si el número $22^{55} + 55^{22}$ es **múltiplo** de $7$.
- **Ejercicio 1.2:** Investigar si para todo $n \in \mathbb{N}$ se cumple que $n^7 - n$ es un **múltiplo** de $7$,.
- **Ejercicio 1.3:** Investigar si para todo $n \in \mathbb{N}$ se cumple que $5^{3n+1} + 2 \cdot 7^{2n+1}$ es **múltiplo** de $19$.
- **Ejercicio 1.4:** Demostrar que para todo $n \in \mathbb{N}$, la expresión $2^{2n+5} \cdot 3^n + 1$ es siempre un número **múltiplo** de $11$.
- **Ejercicio 1.5:** Investigar si la suma de potencias $2222^{5555} + 5555^{2222}$ es **múltiplo** de $7$.

---

## 2. Cifras Terminales y Calendarios

Problemas enfocados en hallar restos específicos (módulo 10 o módulo 7) para aplicaciones prácticas.

- **Ejercicio 2.1:** Si hoy es lunes, determinar qué día de la semana será dentro de $14,735$ días,.
- **Ejercicio 2.2:** Determinar qué día de la semana será dentro de $23,916$ días si hoy es lunes.
- **Ejercicio 2.3:** Calcular la **cifra de las unidades** (última cifra) del número resultante de la suma de los primeros 100 factoriales: $N = 1! + 2! + 3! + \dots + 100!$.

---

## 3. Demostraciones Teóricas y Propiedades

Ejercicios de carácter formal sobre las propiedades de la congruencia y criterios de divisibilidad.

- **Ejercicio 3.1:** Demostrar que si la suma de dos números enteros positivos $a$ y $b$ es divisible entre 10 ($a + b \equiv 0 \pmod{10}$), entonces sus cuadrados $a^2$ y $b^2$ tienen la misma **cifra final**,.
- **Ejercicio 3.2:** Demostrar que si la suma de los cuadrados de dos números enteros ($a^2 + b^2$) es divisible por 3, entonces necesariamente $a$ y $b$ deben ser ambos divisibles por 3.
- **Ejercicio 3.3:** Demostrar formalmente el **criterio de divisibilidad entre 3**: un número es múltiplo de 3 si y solo si la suma de sus dígitos es múltiplo de 3,.
- **Ejercicio 3.4:** Verificar mediante la definición de congruencia ($a - b = k \cdot m$) las siguientes relaciones:
    - $21 \equiv -3 \pmod{8}$
    - $-7 \equiv -22 \pmod{5}$
    - $62 \equiv 6 \pmod{7}$
    - $22 \equiv 8 \pmod{7}$
    - $31 \equiv 10 \pmod{7}$

---

## 4. Ecuaciones Lineales de Congruencia

Hallar el conjunto de soluciones enteras (o el **sistema completo de residuos**) para las siguientes incógnitas.

- **Ejercicio 4.1:** $x \equiv 4 \pmod{7}$.
- **Ejercicio 4.2:** $3x \equiv 2 \pmod{7}$.
- **Ejercicio 4.3:** $4x \equiv 7 \pmod{5}$.
- **Ejercicio 4.4:** $6x \equiv 3 \pmod{4}$.
- **Ejercicio 4.5:** $4x \equiv 2 \pmod{6}$.
- **Ejercicio 4.6:** $2x \equiv 1 \pmod{6}$.

---

### 5. Sistemas de Ecuaciones en Congruencias
Resolución de sistemas utilizando el Teorema Chino del Resto o métodos de sustitución/igualación con módulos coprimos.

---

#### Ejercicio 5.1
Resolver el sistema de dos ecuaciones:
$$
\begin{cases} 
x \equiv 1 \pmod{2} \\ 
x \equiv 2 \pmod{3} 
\end{cases}
$$

#### Ejercicio 5.2
Resolver el sistema:
$$
\begin{cases} 
x \equiv 2 \pmod{3} \\ 
x \equiv 1 \pmod{5} 
\end{cases}
$$

#### Ejercicio 5.3
Resolver el sistema con coeficientes:
$$
\begin{cases} 
x \equiv -1 \pmod{7} \\ 
2x \equiv 5 \pmod{11} 
\end{cases}
$$

#### Ejercicio 5.4
Resolver el sistema de tres ecuaciones:
$$
\begin{cases} 
x \equiv 2 \pmod{3} \\ 
x \equiv 3 \pmod{5} \\ 
x \equiv 1 \pmod{7} 
\end{cases}
$$

#### Ejercicio 5.5
Resolver el siguiente sistema complejo:
$$
\begin{cases} 
2x \equiv 1 \pmod{7} \\ 
x \equiv 1 \pmod{5} \\ 
2x \equiv 32 \pmod{6} \\ 
4x \equiv 6 \pmod{2} 
\end{cases}
$$

---

# Mas ejercicios

**Ejercicios de práctica de Aritmética modular**

**1)** Determina los últimos dos dígitos de $7^{25} + 25^7$.

**2)** Probar que el número inmediatamente posterior a cualquier potencia de 5 es múltiplo de 2 pero no de 4.

**3)** Calcula el último dígito de las siguientes potencias: $6^{20}$, $7^{93}$ y $23^{189}$.


**4)** Calcula el resto de las siguientes divisiones:

**(a)** $7^{512} : 11$; **(b)** $3^{47} : 23$; **(c)** $3^{15} : 17$; **(d)** $125^{4577} : 13$; **(e)** $11^{954} : 20$; **(f)** $(140^{1221} + 28^{753}) : 13$.

**5)** Calcula el residuo de $84^{1234}$ en los módulos $2$, $5$ y $7$.

**6)** Demuestra que para cualquier $n \in \mathbb{Z}$ las últimas cifras de $n$ y $n^5$ son iguales.

**7)** Probar que $7^{2n} + 16n - 1$ es múltiplo de $16$.


---
