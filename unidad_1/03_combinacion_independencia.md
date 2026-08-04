# Combinación e independencia lineal

## Objetivos

Al finalizar este tema, el estudiante podrá:

1. decidir si un vector es combinación lineal de otros;
2. describir el conjunto generado por una familia de vectores;
3. identificar relaciones de dependencia lineal;
4. usar pivotes y rango para seleccionar vectores independientes;
5. interpretar geométricamente generación e independencia en
   $\mathbb R^2$ y $\mathbb R^3$.

## 1. Combinaciones lineales

### Definición 1.1. Combinación lineal

Sean $v_1,\ldots,v_r\in\mathbb R^n$. Un vector $v\in\mathbb R^n$ es una
**combinación lineal** de $v_1,\ldots,v_r$ si existen escalares
$\alpha_1,\ldots,\alpha_r\in\mathbb R$ tales que

$$
v=\alpha_1v_1+\cdots+\alpha_rv_r.
$$

Los números $\alpha_i$ son los **coeficientes** o **ponderaciones** de la
combinación.

### Ejemplo 1.2

El vector $(3,7,1)^T$ es combinación lineal de

$$
v_1=\begin{bmatrix}1\\2\\3\end{bmatrix},\qquad
v_2=\begin{bmatrix}-2\\0\\4\end{bmatrix},\qquad
v_3=\begin{bmatrix}-1\\1\\1\end{bmatrix},
$$

porque

$$
2v_1-2v_2+3v_3
=\begin{bmatrix}3\\7\\1\end{bmatrix}.
$$

### Definición 1.3. Conjunto generado

El conjunto de todas las combinaciones lineales de
$v_1,\ldots,v_r$ se denomina **espacio generado** y se denota

$$
\operatorname{span}\{v_1,\ldots,v_r\}
=\left\{
\alpha_1v_1+\cdots+\alpha_rv_r:
\alpha_1,\ldots,\alpha_r\in\mathbb R
\right\}.
$$

También se usa la notación $\operatorname{gen}\{v_1,\ldots,v_r\}$.

### Proposición 1.4. Pertenencia y sistemas lineales

**Enunciado.** Sea

$$
A=\begin{bmatrix}v_1&\cdots&v_r\end{bmatrix}.
$$

Entonces

$$
v\in\operatorname{span}\{v_1,\ldots,v_r\}
\quad\Longleftrightarrow\quad
A\alpha=v
$$

tiene solución.

**Prueba.** El producto matriz-vector se desarrolla por columnas:

$$
A\alpha
=\alpha_1v_1+\cdots+\alpha_rv_r.
$$

Por tanto, resolver $A\alpha=v$ equivale exactamente a encontrar los
coeficientes de una combinación lineal que produzca $v$. $\square$

```{admonition} Conexión con Gauss–Jordan
:class: note
La pregunta “¿pertenece $v$ al espacio generado?” se responde reduciendo la
matriz aumentada $[A\mid v]$. Si aparece una fila contradictoria, $v$ no
pertenece al espacio generado.
```

## 2. Interpretación geométrica

Sean $u,v\in\mathbb R^3$.

- Si $u=v=0$, generan solamente $\{0\}$.
- Si uno es múltiplo del otro y alguno es no nulo, generan una recta que pasa
  por el origen.
- Si no son paralelos, generan un plano que pasa por el origen.

Si se añade un vector $w$:

- cuando $w\in\operatorname{span}\{u,v\}$, el conjunto generado no cambia;
- cuando $w\notin\operatorname{span}\{u,v\}$, los tres vectores generan
  $\mathbb R^3$.

La geometría anticipa la idea de dependencia: un vector que ya se obtiene con
los anteriores no aporta una dirección nueva.

## 3. Independencia lineal

### Definición 3.1. Independencia lineal

Los vectores $v_1,\ldots,v_r\in\mathbb R^n$ son **linealmente
independientes** si la ecuación

$$
\alpha_1v_1+\cdots+\alpha_rv_r=0
$$

tiene como única solución

$$
\alpha_1=\cdots=\alpha_r=0.
$$

Si existe una solución con al menos un coeficiente no nulo, los vectores son
**linealmente dependientes**.

La solución nula siempre existe. La pregunta es si existen soluciones
**no triviales**.

### Teorema 3.2. Caracterización de la dependencia

**Enunciado.** Una familia $v_1,\ldots,v_r$ con $r\geq2$ es linealmente
dependiente si, y solo si, alguno de sus vectores es combinación lineal de los
otros.

**Prueba.** Si la familia es dependiente, existen escalares no todos nulos
tales que

$$
\alpha_1v_1+\cdots+\alpha_rv_r=0.
$$

Elija un índice $k$ con $\alpha_k\neq0$. Entonces

$$
v_k=-\sum_{j\neq k}\frac{\alpha_j}{\alpha_k}v_j,
$$

de modo que $v_k$ es combinación de los demás.

Recíprocamente, si

$$
v_k=\sum_{j\neq k}\beta_jv_j,
$$

entonces

$$
\sum_{j\neq k}\beta_jv_j-v_k=0
$$

es una relación con coeficiente $-1$ para $v_k$ y, por tanto, no trivial.
$\square$

### Corolario 3.3. Añadir un vector redundante

**Enunciado.** Si
$w\in\operatorname{span}\{v_1,\ldots,v_r\}$, entonces

$$
\operatorname{span}\{v_1,\ldots,v_r,w\}
=\operatorname{span}\{v_1,\ldots,v_r\}.
$$

Además, la familia $v_1,\ldots,v_r,w$ es linealmente dependiente.

**Prueba.** Toda combinación que usa $w$ puede reescribirse sustituyendo su
expresión en términos de $v_1,\ldots,v_r$. La dependencia se sigue del teorema
anterior. $\square$

## 4. Criterios matriciales

Sea

$$
A=\begin{bmatrix}v_1&\cdots&v_r\end{bmatrix}
\in\mathbb R^{n\times r}.
$$

### Teorema 4.1. Criterio del sistema homogéneo

**Enunciado.** Son equivalentes:

1. $v_1,\ldots,v_r$ son linealmente independientes;
2. $A\alpha=0$ tiene solamente la solución $\alpha=0$;
3. todas las columnas de $A$ son columnas pivote;
4. $\operatorname{rango}(A)=r$.

**Prueba.** Las afirmaciones 1 y 2 son la misma definición escrita en forma
matricial. El sistema homogéneo tiene solución única si, y solo si, no hay
variables libres; esto sucede si, y solo si, cada columna contiene un pivote.
El número de pivotes es el rango, lo que prueba la equivalencia con 4.
$\square$

### Corolario 4.2. Criterios según el número de vectores

Sean $v_1,\ldots,v_r\in\mathbb R^n$.

1. Si $r>n$, la familia es linealmente dependiente.
2. Si $r=n$, la familia es linealmente independiente si, y solo si, la matriz
   $A=[v_1\ \cdots\ v_n]$ es invertible.
3. Si $r<n$, la familia es linealmente independiente si, y solo si,
   $\operatorname{rango}(A)=r$.

**Idea de prueba.** Una matriz con $n$ filas no puede tener más de $n$ pivotes.
En el caso cuadrado, tener un pivote en cada columna equivale a reducir $A$ a
$I_n$, que equivale a la invertibilidad.

Más adelante se incorporará el criterio equivalente $\det(A)\neq0$ para el
caso cuadrado, una vez desarrollado el determinante.

## 5. Columnas pivote y relaciones entre columnas

Las operaciones por filas transforman $A$ en $EA$, donde $E$ es invertible.
Por ello,

$$
\alpha_1v_1+\cdots+\alpha_rv_r=0
\quad\Longleftrightarrow\quad
\alpha_1Ev_1+\cdots+\alpha_rEv_r=0.
$$

Las relaciones lineales entre columnas se conservan durante la reducción.

### Teorema 5.1. Selección mediante columnas pivote

**Enunciado.** Si las columnas pivote de $\operatorname{rref}(A)$ tienen
índices $j_1,\ldots,j_s$, entonces las columnas **originales**

$$
v_{j_1},\ldots,v_{j_s}
$$

son linealmente independientes y generan todas las columnas de $A$.

**Idea de prueba.** En la matriz reducida, las columnas pivote son
independientes y cada columna no pivote es combinación de las columnas pivote.
Como la transformación por filas es invertible, las mismas relaciones se
cumplen entre las columnas originales.

```{admonition} Precaución importante
:class: warning
Para obtener generadores del espacio de columnas de $A$, se eligen las
columnas pivote de la **matriz original**, no las columnas de la matriz
reducida. Las operaciones por filas conservan las relaciones entre columnas,
pero en general cambian el espacio de columnas como subconjunto de
$\mathbb R^n$.
```

### Ejemplo 5.2

Sea

$$
A=
\begin{bmatrix}
1&1&4&4&18\\
1&1&4&1&6\\
-1&1&0&2&12\\
1&1&4&1&6
\end{bmatrix},
$$

y suponga que

$$
\operatorname{rref}(A)=
\begin{bmatrix}
1&0&2&0&-1\\
0&1&2&0&3\\
0&0&0&1&4\\
0&0&0&0&0
\end{bmatrix}.
$$

Las columnas pivote son $1,2,4$. Por tanto,
$v_1,v_2,v_4$ son linealmente independientes y generan todas las columnas.
Además,

$$
v_3=2v_1+2v_2,
\qquad
v_5=-v_1+3v_2+4v_4.
$$

## 6. Consecuencias útiles

### Proposición 6.1. Propiedades de familias independientes y dependientes

1. Una familia que contiene al vector cero es linealmente dependiente.
2. Todo subconjunto de una familia linealmente independiente es linealmente
   independiente.
3. Toda familia que contiene una subfamilia linealmente dependiente es
   linealmente dependiente.
4. Si $v_1,\ldots,v_r$ son linealmente independientes y
   $w\notin\operatorname{span}\{v_1,\ldots,v_r\}$, entonces
   $v_1,\ldots,v_r,w$ son linealmente independientes.

**Pruebas.**

1. El coeficiente $1$ para el vector cero y coeficientes cero para los demás
   producen una relación no trivial.
2. Una relación no trivial en un subconjunto se ampliaría con coeficientes
   cero y produciría una relación no trivial en toda la familia.
3. Una relación no trivial en la subfamilia sigue siendo una relación no
   trivial en la familia mayor.
4. Si existiera una relación no trivial y el coeficiente de $w$ fuera no nulo,
   se podría despejar $w$ como combinación de los anteriores. Si ese
   coeficiente fuera cero, quedaría una relación no trivial entre
   $v_1,\ldots,v_r$. Ambos casos contradicen las hipótesis. $\square$

### Proposición 6.2. Vectores ortogonales no nulos

**Enunciado.** Si $v_1,\ldots,v_r$ son no nulos y ortogonales dos a dos,
entonces son linealmente independientes.

**Prueba.** Suponga

$$
\alpha_1v_1+\cdots+\alpha_rv_r=0.
$$

Al tomar producto interno con $v_k$ se obtiene

$$
\alpha_k\|v_k\|^2=0,
$$

porque $\langle v_j,v_k\rangle=0$ cuando $j\neq k$. Como $v_k\neq0$,
$\|v_k\|^2>0$ y, por tanto, $\alpha_k=0$. Esto vale para cada $k$.
$\square$

### Proposición 6.3. Transformaciones invertibles

**Enunciado.** Si $v_1,\ldots,v_r$ son linealmente independientes y $B$ es
invertible, entonces $Bv_1,\ldots,Bv_r$ son linealmente independientes.

**Prueba.** Si

$$
\alpha_1Bv_1+\cdots+\alpha_rBv_r=0,
$$

entonces

$$
B(\alpha_1v_1+\cdots+\alpha_rv_r)=0.
$$

Multiplicando por $B^{-1}$ se obtiene una relación entre los $v_i$, que obliga
a que todos los coeficientes sean cero. $\square$

## 7. Ejemplo con parámetro

Para $n>1$, sean $v_1,\ldots,v_n\in\mathbb R^n$ tales que el elemento $i$ de
$v_i$ es $1$ y todos sus demás elementos son $a$. La matriz de columnas es

$$
A=(1-a)I_n+a\mathbf 1\mathbf 1^T,
$$

donde $\mathbf 1=(1,\ldots,1)^T$.

- Para todo vector $x$ cuya suma de componentes es cero,
  $Ax=(1-a)x$.
- Para $\mathbf 1$,
  $A\mathbf 1=(1+(n-1)a)\mathbf 1$.

La familia es linealmente independiente exactamente cuando ambos factores son
no nulos:

$$
a\neq1,
\qquad
a\neq-\frac{1}{n-1}.
$$

Este argumento usa solamente subespacios reales invariantes; la teoría general
de valores propios se desarrollará más adelante.

## 8. Ejercicios

1. Decida si $(2,0)^T$ es combinación lineal de $(3,3)^T$ y $(-1,1)^T$.
   Si lo es, determine los coeficientes.
2. Pruebe que alguno de
   $u=(1,1,1)^T$, $v=(1,2,1)^T$ y $w=(2,1,2)^T$ es combinación lineal de los
   otros dos.
3. Encuentre generadores para

   $$
   U=\{(x,y,z,w)\in\mathbb R^4:
   x+z+3w=0,\ y+2z-4w=0\}.
   $$

4. Decida si cada familia es linealmente independiente:

   - $(1,-1)^T,(3,0)^T$;
   - $(1,0)^T,(0,1)^T,(4,9)^T$;
   - $(1,0,-2)^T,(0,1,3)^T,(-5,1,2)^T$.

5. Si $u,v$ son linealmente independientes, pruebe que
   $v,v+\alpha u$ son linealmente independientes para todo $\alpha\neq0$.
6. ¿La unión de dos familias linealmente independientes es necesariamente
   linealmente independiente? ¿Qué ocurre con la intersección? Justifique con
   pruebas o contraejemplos.
