# Espacios vectoriales reales, conjuntos afines y suma directa

## Objetivos

Al finalizar este tema, el estudiante podrá:

1. reconocer espacios y subespacios vectoriales reales fuera de $\mathbb R^n$;
2. distinguir un subespacio de una traslación afín;
3. calcular la suma y la intersección de dos subespacios;
4. decidir si una suma es directa;
5. relacionar suma directa, unicidad de descomposición y dimensión.

En las clases anteriores, las propiedades se estudiaron principalmente en
$\mathbb R^n$. Ahora se enuncian para un espacio vectorial real general. No se
introducen números complejos en esta unidad.

## 1. Espacio vectorial real

### Definición 1.1. Espacio vectorial

Un **espacio vectorial real** es un conjunto no vacío $V$ con una suma de
vectores y un producto por escalares reales que, para cualesquiera
$u,v,w\in V$ y $\lambda,\mu\in\mathbb R$, cumplen:

1. **Cierre aditivo:** $u+v\in V$.
2. **Conmutatividad:** $u+v=v+u$.
3. **Asociatividad aditiva:** $(u+v)+w=u+(v+w)$.
4. **Vector cero:** existe $0_V\in V$ tal que $v+0_V=v$.
5. **Inverso aditivo:** para cada $v$ existe $-v$ tal que $v+(-v)=0_V$.
6. **Cierre escalar:** $\lambda v\in V$.
7. **Compatibilidad escalar:** $(\lambda\mu)v=\lambda(\mu v)$ y $1v=v$.
8. **Distributividad:** $\lambda(u+v)=\lambda u+\lambda v$ y
   $(\lambda+\mu)v=\lambda v+\mu v$.

```{admonition} Los vectores no siempre son listas de números
:class: note
Una matriz, un polinomio o una función pueden ser vectores. Las operaciones y
los axiomas, no la apariencia de los objetos, determinan la estructura.
```

### Ejemplo 1.2. Espacios frecuentes

- $\mathbb R^n$, con las operaciones usuales.
- $M_{m\times n}(\mathbb R)$, el espacio de matrices reales de tamaño
  $m\times n$.
- $\mathcal P_n$, los polinomios reales de grado a lo sumo $n$.
- $\mathcal F(X,\mathbb R)$, las funciones de un conjunto $X$ en $\mathbb R$.

Por ejemplo, $(1,t,t^2)$ es una base de $\mathcal P_2$ y
$\dim(\mathcal P_2)=3$.

## 2. Criterio de subespacio

### Teorema 2.1. Criterio de combinación lineal

**Enunciado.** Sea $W$ un subconjunto no vacío de un espacio vectorial real
$V$. Entonces $W$ es subespacio de $V$ si y solo si

$$
\alpha u+\beta v\in W
\qquad
\text{para todos }u,v\in W\text{ y }\alpha,\beta\in\mathbb R.
$$

**Prueba.** Si $W$ es subespacio, la condición se obtiene de sus cerraduras.
Recíprocamente, tomando $\alpha=\beta=0$ se obtiene $0_V\in W$; con
$(\alpha,\beta)=(1,1)$ se obtiene cierre bajo suma, y con $\beta=0$ se obtiene
cierre bajo producto escalar. Los demás axiomas se heredan de $V$. $\square$

### Proposición 2.2. Intersecciones

**Enunciado.** La intersección de cualquier familia no vacía de subespacios de
$V$ es un subespacio de $V$.

**Prueba.** El vector cero pertenece a todos los subespacios. Si $u$ y $v$
pertenecen a la intersección, cada combinación $\alpha u+\beta v$ pertenece a
cada subespacio y, por tanto, a la intersección. $\square$

### Proposición 2.3. El generado es el menor subespacio

**Enunciado.** Para $S\subseteq V$, $\operatorname{span}(S)$ es el menor
subespacio que contiene a $S$.

**Idea de prueba.** Las combinaciones lineales son estables bajo nuevas
combinaciones lineales. Además, cualquier subespacio que contenga a $S$ debe
contener todas esas combinaciones.

## 3. Subconjuntos afines

### Definición 3.1. Conjunto afín

Un subconjunto no vacío $A\subseteq V$ es **afín** si, para $x,y\in A$ y
$t\in\mathbb R$,

$$
(1-t)x+ty\in A.
$$

La suma de los coeficientes es $1$. Esto distingue una combinación afín de una
combinación lineal.

### Teorema 3.2. Caracterización por traslación

**Enunciado.** Un conjunto no vacío $A$ es afín si y solo si existen
$x_0\in V$ y un subespacio $W\leq V$ tales que

$$
A=x_0+W=\{x_0+w:w\in W\}.
$$

En ese caso, para cualquier $x_0\in A$, el espacio de direcciones es
$W=A-x_0$.

**Prueba.** Si $A$ es afín y $x_0\in A$, las combinaciones afines permiten
verificar que $A-x_0$ contiene al cero y es cerrado bajo combinaciones
lineales. Luego $A=x_0+(A-x_0)$. Recíprocamente, si $x=x_0+u$ e $y=x_0+v$,
entonces

$$
(1-t)x+ty=x_0+((1-t)u+tv)\in x_0+W.
$$

$\square$

Un conjunto afín es subespacio exactamente cuando contiene al vector cero.
Así, una recta que no pasa por el origen es afín, pero no es subespacio.

### Proposición 3.3. Conjunto de soluciones de $Ax=b$

**Enunciado.** Si $Ax=b$ es compatible y $x_p$ es una solución particular,
entonces

$$
\{x:Ax=b\}=x_p+\ker(A).
$$

**Prueba.** Si $Ax=b$, entonces $A(x-x_p)=0$, de modo que
$x-x_p\in\ker(A)$. La implicación inversa se obtiene de
$A(x_p+z)=b$ para $z\in\ker(A)$. $\square$

Por eso un sistema compatible indeterminado tiene un conjunto solución afín;
su espacio de direcciones es el núcleo.

## 4. Suma de subespacios

### Definición 4.1. Suma

Para subespacios $U,W\leq V$,

$$
U+W=\{u+w:u\in U,\ w\in W\}.
$$

### Proposición 4.2. La suma es subespacio

**Enunciado.** $U+W$ es el menor subespacio de $V$ que contiene a $U\cup W$.

**Prueba.** Es no vacío. Si $u_i\in U$ y $w_i\in W$, entonces

$$
\alpha(u_1+w_1)+\beta(u_2+w_2)
=(\alpha u_1+\beta u_2)+(\alpha w_1+\beta w_2)\in U+W.
$$

Todo subespacio que contenga a $U$ y a $W$ contiene además cada suma $u+w$.
$\square$

Si las columnas de $B_U$ y $B_W$ son bases de $U$ y $W$, respectivamente,
entonces

$$
U+W=\operatorname{Col}\!\begin{bmatrix}B_U&B_W\end{bmatrix}.
$$

## 5. Suma directa

### Definición 5.1. Suma directa

La suma $U+W$ es **directa**, y se escribe $U\oplus W$, si cada vector de la
suma posee una única descomposición $v=u+w$ con $u\in U$ y $w\in W$.

### Teorema 5.2. Criterio de intersección

**Enunciado.** Para subespacios $U,W\leq V$, son equivalentes:

1. $U+W=U\oplus W$.
2. $U\cap W=\{0_V\}$.
3. $u_1+w_1=u_2+w_2$ implica $u_1=u_2$ y $w_1=w_2$.

**Prueba.** Si la suma es directa y $z\in U\cap W$, entonces
$z+0=0+z$ son dos descomposiciones, luego $z=0$. Si la intersección es trivial
y $u_1+w_1=u_2+w_2$, entonces $u_1-u_2=w_2-w_1$ pertenece a la intersección;
por tanto, ambas diferencias son cero. La tercera afirmación es precisamente
la unicidad exigida en la definición. $\square$

### Teorema 5.3. Fórmula de dimensión

**Enunciado.** Si $U$ y $W$ son de dimensión finita,

$$
\dim(U+W)=\dim U+\dim W-\dim(U\cap W).
$$

**Idea de prueba.** Parta de una base de $U\cap W$, extiéndala a una base de
$U$ y a una base de $W$, y reúna los vectores añadidos una sola vez. El
conjunto resultante es una base de $U+W$.

### Corolario 5.4. Dimensión de una suma directa

**Enunciado.** Si $U\cap W=\{0\}$, entonces

$$
\dim(U\oplus W)=\dim U+\dim W.
$$

En particular, si además $\dim U+\dim W=\dim V$, entonces $V=U\oplus W$.

## 6. Criterios matriciales

Suponga que $B_U$ y $B_W$ tienen como columnas bases de $U,W\subseteq
\mathbb R^n$, y sea $B=[B_U\ B_W]$.

1. $\dim(U+W)=\operatorname{rango}(B)$.
2. La suma es directa si y solo si
   $\operatorname{rango}(B)=\dim U+\dim W$.
3. $\dim(U\cap W)=\dim U+\dim W-\operatorname{rango}(B)$.
4. $\mathbb R^n=U\oplus W$ si y solo si $B$ es cuadrada e invertible.

La ecuación $B_Ua=B_Wb$ equivale a

$$
\begin{bmatrix}B_U&-B_W\end{bmatrix}
\begin{bmatrix}a\\b\end{bmatrix}=0.
$$

Sus soluciones describen los vectores de $U\cap W$. Si $B_U$ y $B_W$ son
bases y la única solución es $a=b=0$, la suma es directa.

## 7. Ejemplo integrado

Sean

$$
U=\operatorname{span}\{(1,0,0),(0,1,0)\},\qquad
W=\operatorname{span}\{(0,0,1)\}.
$$

La matriz reunida es $I_3$, de rango $3$. Por ello
$U\cap W=\{0\}$ y $\mathbb R^3=U\oplus W$. Cada vector satisface

$$
(x,y,z)=(x,y,0)+(0,0,z),
$$

y esta descomposición es única.

En cambio, si $W'=\operatorname{span}\{(1,1,0)\}$, entonces $W'\subset U$.
Por tanto, $U+W'=U$ y la suma no es directa.

## 8. Comprobación conceptual

1. ¿Por qué $\{p\in\mathcal P_3:p(0)=0\}$ es subespacio?
2. ¿Por qué $\{p\in\mathcal P_3:p(0)=1\}$ es afín pero no subespacio?
3. Si $\dim U=3$, $\dim W=4$ y $\dim(U+W)=6$, ¿cuánto vale
   $\dim(U\cap W)$? ¿La suma es directa?
4. Si $V=U\oplus W$, explique por qué las bases de $U$ y $W$, reunidas,
   forman una base de $V$.
