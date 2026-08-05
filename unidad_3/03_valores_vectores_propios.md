# Valores y vectores propios

## Objetivos

Al finalizar este bloque, podrás:

1. definir valores y vectores propios de una matriz e interpretarlos como
   direcciones invariantes;
2. calcular el polinomio característico y el espectro de una matriz;
3. obtener una base de cada espacio propio;
4. distinguir multiplicidad algebraica y multiplicidad geométrica;
5. deducir propiedades espectrales de matrices semejantes y de polinomios en
   una matriz;
6. reconocer qué cambia al trabajar sobre $\mathbb R$ o sobre $\mathbb C$.

## 1. Direcciones que una matriz no cambia

### Definición 1.1. Valor propio y vector propio

Sea $A\in\mathbb K^{n\times n}$. Un escalar $\lambda\in\mathbb K$ es un
**valor propio** de $A$ si existe un vector $v\in\mathbb K^n$, $v\neq0$, tal
que

$$
\boxed{Av=\lambda v.}
$$

El vector $v$ se llama **vector propio de $A$ asociado a $\lambda$**.

```{admonition} El vector propio no puede ser cero
:class: warning
La igualdad $A0=\lambda0$ se cumple para cualquier escalar. Exigir
$v\neq0$ hace que la definición contenga información sobre la matriz.
El valor propio sí puede ser cero.
```

```{admonition} Observación: formulación para operadores
:class: note
La misma definición tiene sentido para un operador lineal $T:V\to V$:
$T(v)=\lambda v$ con $v\neq0$. En dimensión finita, una vez elegida una base,
esta igualdad se representa mediante una matriz y vuelve a la definición
anterior. La formulación con operadores permite además hablar de valores
propios en espacios de dimensión infinita, por ejemplo en espacios de
funciones, donde no existe una matriz finita que represente todo el operador.
```

### Interpretación geométrica

La recta $\operatorname{span}\{v\}$ es invariante bajo $A$. Sobre $\mathbb R$:

- si $\lambda>1$, la dirección se estira;
- si $0<\lambda<1$, se contrae;
- si $\lambda<0$, además se invierte el sentido;
- si $\lambda=0$, la dirección colapsa al origen.

Un vector propio no es único: si $v$ es propio y $c\neq0$, entonces $cv$
también lo es para el mismo valor propio.

### Ejemplo 1.2

Para

$$
A=\begin{pmatrix}2&1\\1&2\end{pmatrix},
$$

se tiene

$$
A\begin{pmatrix}1\\1\end{pmatrix}
=3\begin{pmatrix}1\\1\end{pmatrix},
\qquad
A\begin{pmatrix}-1\\1\end{pmatrix}
=1\begin{pmatrix}-1\\1\end{pmatrix}.
$$

Las dos rectas generadas por esos vectores son invariantes.

## 2. Espacios propios

### Definición 2.1. Espacio propio

Para un valor propio $\lambda$ de $A$, su **espacio propio** es

$$
E_\lambda(A)=\{v\in\mathbb K^n:Av=\lambda v\}.
$$

Como $Av=\lambda v$ equivale a $(A-\lambda I)v=0$,

$$
\boxed{E_\lambda(A)=\ker(A-\lambda I).}
$$

Por tanto, $E_\lambda(A)$ es un subespacio. Sus elementos no nulos son
exactamente los vectores propios asociados a $\lambda$.

### Proposición 2.2. El espacio propio es invariante

**Enunciado.** $E_\lambda(A)$ es invariante bajo $A$.

**Prueba.** Si $v\in E_\lambda(A)$, entonces $Av=\lambda v$, que también
pertenece a $E_\lambda(A)$ porque este es un subespacio. $\square$

## 3. Polinomio característico y espectro

Sea $A\in\mathbb K^{n\times n}$. Usaremos el polinomio característico mónico

$$
\boxed{\chi_A(t)=\det(tI-A).}
$$

Algunas notas usan $\det(A-tI)=(-1)^n\chi_A(t)$. Ambos polinomios tienen las
mismas raíces, de modo que producen los mismos valores propios.

### Teorema 3.1. Ecuación característica

**Enunciado.** Son equivalentes:

1. $\lambda$ es valor propio de $A$;
2. $(A-\lambda I)v=0$ tiene una solución no nula;
3. $A-\lambda I$ no es invertible;
4. $\det(A-\lambda I)=0$;
5. $\chi_A(\lambda)=0$.

**Prueba.** Las dos primeras afirmaciones son equivalentes por definición. Un
sistema homogéneo cuadrado tiene una solución no nula si y solo si su matriz
no es invertible, y esto ocurre si y solo si su determinante es cero.
$\square$

El conjunto de valores propios se llama **espectro** y se denota

$$
\sigma(A)=\{\lambda\in\mathbb K:\chi_A(\lambda)=0\}.
$$

### Procedimiento 3.2. Cálculo exacto

1. Construir $tI-A$.
2. Calcular y factorizar $\chi_A(t)=\det(tI-A)$.
3. Encontrar sus raíces.
4. Para cada raíz $\lambda$, resolver
   $(A-\lambda I)v=0$.
5. Expresar $E_\lambda(A)$ mediante una base.

### Ejemplo 3.3

Para $A$ del Ejemplo 1.2,

$$
\chi_A(t)=
\det\begin{pmatrix}t-2&-1\\-1&t-2\end{pmatrix}
=(t-2)^2-1=(t-1)(t-3).
$$

Luego $\sigma(A)=\{1,3\}$. Además,

$$
E_1(A)=\ker(A-I)=\operatorname{span}\{(-1,1)^T\},
$$

$$
E_3(A)=\ker(A-3I)=\operatorname{span}\{(1,1)^T\}.
$$

## 4. El cuerpo importa

### Ejemplo 4.1. Una rotación

Sea

$$
R_\theta=
\begin{pmatrix}
\cos\theta&-\sin\theta\\
\sin\theta&\cos\theta
\end{pmatrix}.
$$

Entonces

$$
\chi_{R_\theta}(t)=t^2-2(\cos\theta)t+1
$$

y su discriminante es

$$
\Delta=-4\sin^2\theta.
$$

Si $\sin\theta\neq0$, no hay valores propios reales. Sobre $\mathbb C$, sí
existen:

$$
\lambda_1=e^{i\theta},
\qquad
\lambda_2=e^{-i\theta}.
$$

Geométricamente, una rotación real no trivial no deja ninguna recta real
invariante. Este ejemplo muestra que una matriz real no tiene necesariamente
un valor propio real.

### Teorema 4.2. Existencia sobre los complejos

**Enunciado.** Toda matriz compleja de orden $n\geq1$ tiene al menos un valor
propio complejo y tiene $n$ valores propios contando multiplicidades.

**Idea de prueba.** $\chi_A$ tiene grado $n$. Por el teorema fundamental del
álgebra, se factoriza completamente sobre $\mathbb C$.

Para matrices reales, las raíces no reales aparecen en pares conjugados
porque $\chi_A$ tiene coeficientes reales.

## 5. Multiplicidad algebraica y geométrica

### Definición 5.1. Multiplicidad algebraica

Si

$$
\chi_A(t)=(t-\lambda)^m q(t),
\qquad q(\lambda)\neq0,
$$

$m$ es la **multiplicidad algebraica** de $\lambda$, denotada
$m_a(\lambda)$.

### Definición 5.2. Multiplicidad geométrica

La **multiplicidad geométrica** de $\lambda$ es

$$
m_g(\lambda)=\dim E_\lambda(A)
=\dim\ker(A-\lambda I).
$$

Por rango-nulidad,

$$
m_g(\lambda)=n-\operatorname{rango}(A-\lambda I).
$$

### Teorema 5.3. Comparación de multiplicidades

**Enunciado.** Para todo valor propio $\lambda$,

$$
\boxed{1\leq m_g(\lambda)\leq m_a(\lambda).}
$$

**Idea de prueba.** La primera desigualdad sigue de que el espacio propio
contiene un vector no nulo. Sea $g=m_g(\lambda)$ y elijamos una base de
$E_\lambda(A)$, completada a una base de todo el espacio. En esa base, la
matriz tiene la forma

$$
\begin{pmatrix}
\lambda I_g&B\\
0&C
\end{pmatrix}.
$$

Por el determinante de una matriz por bloques triangular,
$(t-\lambda)^g$ divide a $\chi_A(t)$; por tanto, $g\leq m_a(\lambda)$.

### Ejemplo 5.4. Una multiplicidad geométrica insuficiente

Sea

$$
B=\begin{pmatrix}
0&1&0\\
0&0&1\\
0&0&0
\end{pmatrix}.
$$

Como $B$ es triangular,

$$
\chi_B(t)=t^3.
$$

El único valor propio es $0$, con $m_a(0)=3$. Sin embargo,

$$
E_0(B)=\ker(B)=\operatorname{span}\{e_1\},
$$

de modo que $m_g(0)=1$. Solo existe una dirección propia independiente.

## 6. Propiedades fundamentales

### Teorema 6.1. Independencia de vectores propios

**Enunciado.** Vectores propios asociados a valores propios distintos son
linealmente independientes.

**Prueba.** Sean $v_1,\ldots,v_r$ vectores propios asociados a valores
distintos $\lambda_1,\ldots,\lambda_r$. Procedemos por inducción. Si
$\sum_{j=1}^r c_jv_j=0$, aplicamos $A-\lambda_r I$ y obtenemos

$$
\sum_{j=1}^{r-1}c_j(\lambda_j-\lambda_r)v_j=0.
$$

Por la hipótesis inductiva y porque $\lambda_j-\lambda_r\neq0$, se tiene
$c_1=\cdots=c_{r-1}=0$. La igualdad original da $c_r=0$. $\square$

### Teorema 6.2. Matrices semejantes

**Enunciado.** Si $A=PBP^{-1}$, entonces $A$ y $B$ tienen el mismo polinomio
característico y los mismos valores propios con sus multiplicidades
algebraicas.

**Prueba.** Como $tI-A=P(tI-B)P^{-1}$,

$$
\det(tI-A)=\det(P)\det(tI-B)\det(P^{-1})=\det(tI-B).
$$

Además, si $Av=\lambda v$, entonces

$$
B(P^{-1}v)=\lambda(P^{-1}v).
$$

Así, el cambio de base transporta también los espacios propios. $\square$

### Definición 6.3. Evaluación de un polinomio en una matriz

Sea

$$
q(t)=a_0+a_1t+\cdots+a_mt^m
$$

un polinomio y sea $A\in\mathbb K^{n\times n}$. Definimos

$$
\boxed{
q(A)=a_0I+a_1A+\cdots+a_mA^m,
}
$$

donde $A^0=I$.

```{admonition} Atención al término constante
:class: important
El término constante $a_0$ se convierte en $a_0I$, no en el escalar $a_0$ ni
en una matriz que tenga $a_0$ en todas sus entradas. Así todos los sumandos
de $q(A)$ son matrices de orden $n$.
```

### Ejemplo 6.4. Evaluación explícita

Sean

$$
q(t)=2t^2-3t+5,
\qquad
A=\begin{pmatrix}1&1\\0&2\end{pmatrix}.
$$

Como

$$
A^2=\begin{pmatrix}1&3\\0&4\end{pmatrix},
$$

se obtiene

$$
\begin{aligned}
q(A)
&=2A^2-3A+5I\\
&=2\begin{pmatrix}1&3\\0&4\end{pmatrix}
-3\begin{pmatrix}1&1\\0&2\end{pmatrix}
+5\begin{pmatrix}1&0\\0&1\end{pmatrix}\\
&=\begin{pmatrix}4&3\\0&7\end{pmatrix}.
\end{aligned}
$$

### Proposición 6.5. Espectro y operaciones

**Enunciado.** Si $Av=\lambda v$ y $q$ es un polinomio, entonces

$$
q(A)v=q(\lambda)v.
$$

En particular:

1. $\lambda^k$ es valor propio de $A^k$;
2. $q(\lambda)$ es valor propio de $q(A)$;
3. si $A$ es invertible, $\lambda^{-1}$ es valor propio de $A^{-1}$.

**Prueba.** De $A^kv=\lambda^kv$, obtenida por inducción, se sigue la
identidad para cualquier combinación lineal de potencias. Para la inversa,
$Av=\lambda v$ y la invertibilidad implican $\lambda\neq0$; aplicar $A^{-1}$
da $A^{-1}v=\lambda^{-1}v$. $\square$

### Proposición 6.6. Invertibilidad, traza y determinante

**Enunciado.** Contando valores propios complejos con multiplicidad:

$$
\det(A)=\prod_{j=1}^n\lambda_j,
\qquad
\operatorname{tr}(A)=\sum_{j=1}^n\lambda_j.
$$

Además,

$$
A\text{ es invertible}\quad\Longleftrightarrow\quad0\notin\sigma(A).
$$

**Idea de prueba.** Al factorizar
$\chi_A(t)=\prod_j(t-\lambda_j)$ y comparar el término constante y el
coeficiente de $t^{n-1}$ con los obtenidos de $\det(tI-A)$ aparecen las
fórmulas. La equivalencia de invertibilidad sigue de
$0\in\sigma(A)\iff\det(A)=0$.

### Consecuencia 6.7. Matrices triangulares

Los valores propios de una matriz triangular son sus entradas diagonales,
contando multiplicidades, porque

$$
\chi_A(t)=\prod_{j=1}^n(t-a_{jj}).
$$

## 7. El teorema de Cayley--Hamilton

### Teorema 7.1. Cayley–Hamilton

**Enunciado.** Toda matriz satisface su propio polinomio característico:

$$
\boxed{\chi_A(A)=0.}
$$

Aquí $\chi_A(A)$ se interpreta mediante la Definición 6.3. En particular, el
término constante de $\chi_A(t)$ multiplica a la matriz identidad.

La demostración general requiere herramientas algebraicas adicionales y no
presupone que la matriz sea diagonalizable. Aquí lo usaremos para reducir
potencias altas.

### Ejemplo 7.2

Si

$$
A=\begin{pmatrix}2&1\\1&2\end{pmatrix},
\qquad
\chi_A(t)=t^2-4t+3,
$$

Cayley–Hamilton da

$$
A^2-4A+3I=0,
\qquad
A^2=4A-3I.
$$

Por ello toda potencia de $A$ puede reducirse a una combinación de $A$ e
$I$. En el bloque siguiente obtendremos una fórmula más directa mediante
diagonalización.

## 8. Matrices especiales y restricciones sobre el espectro

Sea $\lambda$ un valor propio de $A$.

1. Si $A^2=A$ (**idempotente**), entonces $\lambda\in\{0,1\}$.
2. Si $A^2=I$ (**involutiva**), entonces $\lambda\in\{-1,1\}$.
3. Si $A^k=0$ para algún $k$ (**nilpotente**), entonces $\lambda=0$.
4. Si $A$ es ortogonal o unitaria, entonces $|\lambda|=1$.

**Prueba.** Las tres primeras afirmaciones se obtienen aplicando la
Proposición 6.5 a los polinomios $t^2-t$, $t^2-1$ y $t^k$. Para la última, si
$Av=\lambda v$, la preservación de la norma da
$\|v\|=\|Av\|=|\lambda|\|v\|$; como $v\neq0$, $|\lambda|=1$. $\square$

## 9. Puente hacia la diagonalización

Si una matriz de orden $n$ posee $n$ vectores propios linealmente
independientes, estos forman una base. En esa base, la acción del operador es
diagonal. El bloque siguiente precisará:

- cuándo existen suficientes vectores propios;
- por qué la igualdad $m_g(\lambda)=m_a(\lambda)$ es decisiva;
- cómo construir $A=PDP^{-1}$ y usarla para calcular funciones de $A$.

## 10. Ejercicios

1. Para $A=\begin{pmatrix}2&1\\1&2\end{pmatrix}$, calcula el polinomio
   característico, los valores propios y una base de cada espacio propio.
   *(PC2 2026-I.)*
2. Para
   $B=\begin{pmatrix}0&1&0\\0&0&1\\0&0&0\end{pmatrix}$, compara las
   multiplicidades algebraica y geométrica del valor propio $0$.
   *(PC2 2026-I.)*
3. Explica primero desde la geometría y después desde el polinomio
   característico por qué una rotación real no trivial de ángulo
   $-\pi/2<\theta<\pi/2$ no tiene valores propios reales.
   *(PC2 2025-I, adaptado.)*
4. Si $A=PBP^{-1}$ y $Av=\lambda v$, encuentra un vector propio de $B$
   asociado a $\lambda$. *(PC2 2025-I y lista PC2 2026-I.)*
5. Si los valores propios de una matriz real $B$ de orden $3$ son $0,1,2$,
   determina, cuando sea posible, $\det(B)$, $\operatorname{tr}(B)$,
   $\operatorname{rango}(B)$ y los valores propios de $(B^2+I)^{-1}$.
   Explica por qué los valores propios de $B^TB$ no quedan determinados solo
   con esos datos. *(Lista PC2 2026-I.)*
6. Si $Av=2v$ y $C=-A^3+5A-2I$, demuestra que $v$ es vector propio de $C$ y
   encuentra el valor propio correspondiente. *(Presentación de clase.)*
7. Los cuadrados mágicos
   $M_3=\begin{pmatrix}4&9&2\\3&5&7\\8&1&6\end{pmatrix}$ y
   $M_4=\begin{pmatrix}1&14&8&11\\15&4&10&5\\12&7&13&2\\6&9&3&16\end{pmatrix}$
   tienen sumas comunes $15$ y $34$. Sin calcular determinantes, encuentra un
   vector propio para cada matriz. *(Presentación de clase.)*
8. Construye ejemplos de matrices de orden $2$ que satisfagan:
   (a) $0$ es valor propio pero la matriz no es cero;
   (b) tiene dos valores propios reales distintos pero no es simétrica;
   (c) es real y sus valores propios no son reales. *(Lista PC2 2026-I.)*
