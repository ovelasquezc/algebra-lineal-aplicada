# Coordenadas y cambio de base

## Objetivos

Al finalizar este tema, el estudiante podrá:

1. distinguir un vector de su columna de coordenadas;
2. obtener coordenadas respecto de una base;
3. construir e interpretar una matriz de cambio de base;
4. representar una transformación lineal en bases del dominio y codominio;
5. verificar que distintas matrices pueden describir la misma transformación.

## 1. Coordenadas respecto de una base

Sea $V$ un espacio vectorial real de dimensión $n$ y
$\mathcal B=(v_1,\ldots,v_n)$ una base. Cada $x\in V$ se escribe de manera
única como

$$
x=\alpha_1v_1+\cdots+\alpha_nv_n.
$$

### Definición 1.1. Vector de coordenadas

El **vector de coordenadas** de $x$ en la base $\mathcal B$ es

$$
[x]_{\mathcal B}=
\begin{bmatrix}\alpha_1\\ \vdots\\ \alpha_n\end{bmatrix}\in\mathbb R^n.
$$

```{admonition} No confundir el vector con sus coordenadas
:class: warning
$x$ pertenece a $V$; $[x]_{\mathcal B}$ pertenece a $\mathbb R^n$. Las
coordenadas cambian al cambiar la base, pero el vector geométrico o abstracto
sigue siendo el mismo.
```

### Teorema 1.2. Aplicación de coordenadas

**Enunciado.** La aplicación

$$
\phi_{\mathcal B}:V\to\mathbb R^n,
\qquad x\mapsto[x]_{\mathcal B},
$$

es un isomorfismo lineal.

**Prueba.** La linealidad se obtiene de la unicidad de la representación:

$$
[\lambda x+\mu y]_{\mathcal B}
=\lambda[x]_{\mathcal B}+\mu[y]_{\mathcal B}.
$$

Cada columna de $\mathbb R^n$ determina una combinación única de los vectores
de $\mathcal B$, así que la aplicación es biyectiva. $\square$

## 2. Matriz de una base en $\mathbb R^n$

Si los vectores de $\mathcal B$ están escritos en coordenadas canónicas,
definimos

$$
M_{\mathcal B}=\begin{bmatrix}v_1&\cdots&v_n\end{bmatrix}.
$$

La matriz es invertible y cumple

$$
x=M_{\mathcal B}[x]_{\mathcal B},
\qquad
[x]_{\mathcal B}=M_{\mathcal B}^{-1}x.
$$

La primera fórmula **reconstruye** el vector; la segunda **extrae** sus
coordenadas.

### Ejemplo 2.1

Para $\mathcal B=((1,1),(1,-1))$ y $x=(5,1)$,

$$
M_{\mathcal B}=
\begin{bmatrix}1&1\\1&-1\end{bmatrix},
\qquad
[x]_{\mathcal B}=
\begin{bmatrix}3\\2\end{bmatrix}.
$$

En efecto, $(5,1)=3(1,1)+2(1,-1)$.

## 3. Cambio de base

Sean $\mathcal B$ y $\mathcal C$ dos bases de $V$.

### Definición 3.1. Matriz de cambio de base

La matriz de cambio de $\mathcal B$ a $\mathcal C$ es la matriz
$P_{\mathcal B\to\mathcal C}$ que satisface

$$
[x]_{\mathcal C}
=P_{\mathcal B\to\mathcal C}[x]_{\mathcal B}
\qquad\text{para todo }x\in V.
$$

En $\mathbb R^n$,

$$
\boxed{P_{\mathcal B\to\mathcal C}
=M_{\mathcal C}^{-1}M_{\mathcal B}}.
$$

**Idea de prueba.** Se sigue el recorrido

$$
[x]_{\mathcal B}
\xrightarrow{\ M_{\mathcal B}\ }x
\xrightarrow{\ M_{\mathcal C}^{-1}\ }[x]_{\mathcal C}.
$$

La columna $j$ de $P_{\mathcal B\to\mathcal C}$ es
$[v_j]_{\mathcal C}$, donde $v_j$ es el $j$-ésimo vector de $\mathcal B$.
Esta interpretación permite construir la matriz aun cuando $V$ no sea
literalmente $\mathbb R^n$.

### Proposición 3.2. Propiedades

**Enunciado.** Para bases $\mathcal B,\mathcal C,\mathcal D$:

1. $P_{\mathcal B\to\mathcal B}=I$.
2. $P_{\mathcal C\to\mathcal B}=P_{\mathcal B\to\mathcal C}^{-1}$.
3. $P_{\mathcal B\to\mathcal D}
   =P_{\mathcal C\to\mathcal D}P_{\mathcal B\to\mathcal C}$.

**Prueba.** Las tres identidades se obtienen aplicando las matrices a una
columna arbitraria $[x]_{\mathcal B}$ y usando la unicidad de las coordenadas.
$\square$

### Ejemplo 3.3

Sean

$$
\mathcal B=((1,0),(1,1)),\qquad
\mathcal C=((2,1),(0,1)).
$$

Entonces

$$
P_{\mathcal B\to\mathcal C}
=M_{\mathcal C}^{-1}M_{\mathcal B}
=\frac12\begin{bmatrix}1&1\\-1&1\end{bmatrix}.
$$

Para $x=(3,5)$, $[x]_{\mathcal B}=(-2,5)^T$ y

$$
[x]_{\mathcal C}
=P_{\mathcal B\to\mathcal C}[x]_{\mathcal B}
=\begin{bmatrix}3/2\\7/2\end{bmatrix}.
$$

## 4. Matriz de una transformación en bases elegidas

Sea $T:U\to W$, con base $\mathcal B=(b_1,\ldots,b_n)$ en el dominio y
base $\mathcal C=(c_1,\ldots,c_m)$ en el codominio.

### Definición 4.1. Matriz relativa

La matriz $[T]_{\mathcal C\leftarrow\mathcal B}$ es la única matriz que cumple

$$
[T(x)]_{\mathcal C}
=[T]_{\mathcal C\leftarrow\mathcal B}[x]_{\mathcal B}.
$$

Su columna $j$ es $[T(b_j)]_{\mathcal C}$. Por ello su tamaño es $m\times n$.

### Teorema 4.2. Fórmula desde bases canónicas

**Enunciado.** Si $U=\mathbb R^n$, $W=\mathbb R^m$ y $A$ es la matriz de $T$
en bases canónicas, entonces

$$
\boxed{[T]_{\mathcal C\leftarrow\mathcal B}
=M_{\mathcal C}^{-1}AM_{\mathcal B}}.
$$

**Prueba.** Para cualquier $x$,

$$
[T(x)]_{\mathcal C}
=M_{\mathcal C}^{-1}T(x)
=M_{\mathcal C}^{-1}AM_{\mathcal B}[x]_{\mathcal B}.
$$

Por unicidad de la matriz que representa la transformación, se obtiene la
fórmula. $\square$

## 5. Cambio simultáneo en dominio y codominio

Si ya conocemos $[T]_{\mathcal C\leftarrow\mathcal B}$ y elegimos bases nuevas
$\mathcal B'$ y $\mathcal C'$, entonces

$$
[T]_{\mathcal C'\leftarrow\mathcal B'}
=P_{\mathcal C\to\mathcal C'}
[T]_{\mathcal C\leftarrow\mathcal B}
P_{\mathcal B'\to\mathcal B}.
$$

Observe las direcciones: primero se pasa de las coordenadas nuevas del dominio
a las antiguas; al final se pasa de las coordenadas antiguas del codominio a
las nuevas.

## 6. Operadores y matrices semejantes

Si $T:V\to V$ y se usa la misma base en dominio y codominio, escribimos
$[T]_{\mathcal B}$. Para cambiar de $\mathcal B$ a $\mathcal C$,

$$
[T]_{\mathcal C}
=P_{\mathcal B\to\mathcal C}
[T]_{\mathcal B}
P_{\mathcal C\to\mathcal B}.
$$

Como $P_{\mathcal C\to\mathcal B}=P_{\mathcal B\to\mathcal C}^{-1}$,
las dos matrices son **semejantes**. Describen el mismo operador desde dos
sistemas de coordenadas.

```{admonition} Orden de los factores
:class: warning
La multiplicación de matrices no es conmutativa. Antes de memorizar una
fórmula, escriba qué tipo de coordenadas recibe y cuáles entrega cada factor.
```

## 7. Bases ortonormales

Si las columnas de $Q$ forman una base ortonormal de $\mathbb R^n$, entonces

$$
Q^{-1}=Q^T,
\qquad
[x]_{\mathcal B}=Q^Tx.
$$

Esta simplificación se retomará al estudiar proyecciones, mínimos cuadrados y
diagonalización ortogonal.

## 8. Comprobación conceptual

1. Explique por qué las columnas de $P_{\mathcal B\to\mathcal C}$ son
   coordenadas en $\mathcal C$, no en $\mathcal B$.
2. Si $[x]_{\mathcal B}=(2,-1)^T$, ¿puede saberse cuál es $x$ sin conocer
   $\mathcal B$?
3. Verifique las dimensiones de cada factor en
   $M_{\mathcal C}^{-1}AM_{\mathcal B}$ cuando $T:\mathbb R^3\to\mathbb R^2$.
4. ¿Por qué matrices semejantes pueden ser distintas y representar el mismo
   operador?
