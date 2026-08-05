# Operadores, adjunto y subespacios invariantes

## Objetivos

Al finalizar este bloque, podrás:

1. reconocer subespacios invariantes y construir la restricción de un operador;
2. interpretar la forma por bloques de una matriz a partir de la invariancia;
3. definir y calcular el operador adjunto;
4. relacionar núcleo, imagen y complemento ortogonal mediante el adjunto;
5. reconocer proyecciones ortogonales y operadores autoadjuntos.

Trabajaremos en espacios vectoriales de dimensión finita sobre
$\mathbb K=\mathbb R$ o $\mathbb C$, provistos de producto interno. Mantenemos
la convención

$$
\langle x,y\rangle=y^*x,
$$

lineal en la primera entrada. En el caso real, $y^*x=y^Tx$.

## 1. Operadores lineales

### Definición 1.1. Operador lineal

Un **operador lineal** sobre $V$ es una transformación lineal

$$
T:V\longrightarrow V.
$$

La palabra operador destaca que el dominio y el codominio son el mismo
espacio. Esto permite iterar $T$, formar polinomios en $T$ y preguntar qué
partes de $V$ se conservan bajo su acción.

### Ejemplo 1.2

Son operadores:

- la derivación $D:\mathcal P_n\to\mathcal P_n$, $D(p)=p'$;
- una rotación de $\mathbb R^2$;
- la proyección ortogonal $P_W:V\to V$ sobre un subespacio $W$;
- $T_A:\mathbb K^n\to\mathbb K^n$, $T_A(x)=Ax$, para una matriz cuadrada $A$.

En cambio, una matriz rectangular representa una transformación lineal, pero
no un operador sobre un único espacio.

## 2. Subespacios invariantes

### Definición 2.1. Invariancia

Sea $T:V\to V$ un operador. Un subespacio $W\subseteq V$ es **invariante bajo
$T$** si

$$
\boxed{T(W)\subseteq W.}
$$

Esto significa que todo vector que empieza en $W$ permanece en $W$ después
de aplicar $T$.

### Ejemplos 2.2

1. $\{0\}$ y $V$ son invariantes para todo operador.
2. $\ker(T)$ es invariante porque $x\in\ker(T)$ implica $T(x)=0\in\ker(T)$.
3. $\operatorname{Im}(T)$ es invariante porque
   $T(Tx)=T^2x\in\operatorname{Im}(T)$.
4. Para $D:\mathcal P_n\to\mathcal P_n$, cada $\mathcal P_k$, con $k\leq n$,
   es invariante.
5. Si $Tv=\lambda v$, entonces $\operatorname{span}\{v\}$ es invariante.

```{admonition} Cuidado con la igualdad
:class: warning
La condición es $T(W)\subseteq W$, no necesariamente $T(W)=W$. Por ejemplo,
la derivación envía $\mathcal P_k$ dentro de $\mathcal P_{k-1}$.
```

### Definición 2.3. Restricción

Si $W$ es invariante bajo $T$, la regla

$$
T|_W:W\longrightarrow W,
\qquad T|_W(w)=T(w),
$$

es un operador sobre $W$, llamado **restricción de $T$ a $W$**.

### Proposición 2.4. Invariancia y forma por bloques

**Enunciado.** Sea $\dim V=n$, sea $\dim W=k$ y supongamos que $W$ es
invariante bajo $T$. Si una base $\mathcal B_W=(w_1,\ldots,w_k)$ de $W$ se
completa a una base

$$
\mathcal B=(w_1,\ldots,w_k,z_1,\ldots,z_{n-k})
$$

de $V$, entonces

$$
[T]_{\mathcal B}=
\begin{pmatrix}
A_W&B\\
0&C
\end{pmatrix},
$$

donde $A_W=[T|_W]_{\mathcal B_W}$.

**Prueba.** Para $j\leq k$, la invariancia da $T(w_j)\in W$. Por ello las
primeras $k$ columnas de $[T]_{\mathcal B}$ no tienen componentes en las
últimas $n-k$ posiciones. Es exactamente el bloque inferior izquierdo nulo.
$\square$

### Corolario 2.5. Descomposición en subespacios invariantes

**Enunciado.** Si $V=W\oplus Z$ y tanto $W$ como $Z$ son invariantes bajo
$T$, una base adaptada a la suma directa produce

$$
[T]_{\mathcal B}=
\begin{pmatrix}
[T|_W]&0\\
0&[T|_Z]
\end{pmatrix}.
$$

**Idea de prueba.** Las imágenes de los vectores de la base de $W$ no tienen
componente en $Z$, y las imágenes de los vectores de la base de $Z$ no tienen
componente en $W$.

Esta observación anticipa la diagonalización: encontrar muchos subespacios
invariantes pequeños permite separar un problema grande en problemas menores.

## 3. El operador adjunto

### Teorema 3.1. Existencia y unicidad del adjunto

**Enunciado.** Para todo operador lineal $T:V\to V$ existe un único operador
$T^*:V\to V$ tal que

$$
\boxed{\langle Tx,y\rangle=\langle x,T^*y\rangle
\quad\text{para todo }x,y\in V.}
$$

$T^*$ se llama **operador adjunto** de $T$.

**Idea de prueba.** Elijamos una base ortonormal y sea $A$ la matriz de $T$.
Entonces

$$
\langle Ax,y\rangle=y^*Ax=(A^*y)^*x
=\langle x,A^*y\rangle.
$$

Por tanto, la matriz de $T^*$ en esa base es $A^*$. Si dos operadores
satisficieran la identidad, la diferencia de sus valores sería ortogonal a
todo vector y tendría que ser cero; esto prueba la unicidad. $\square$

### Regla 3.2. Cálculo en una base ortonormal

Si $\mathcal B$ es ortonormal y $A=[T]_{\mathcal B}$, entonces

$$
\boxed{[T^*]_{\mathcal B}=A^*=\overline A^{\,T}.}
$$

En espacios reales, $A^*=A^T$. La fórmula no debe aplicarse sin más en una
base que no sea ortonormal.

### Proposición 3.3. Propiedades del adjunto

**Enunciado.** Para operadores $S,T$ y un escalar $\alpha$:

1. $(S+T)^*=S^*+T^*$;
2. $(\alpha T)^*=\overline\alpha\,T^*$;
3. $(ST)^*=T^*S^*$;
4. $(T^*)^*=T$;
5. si $T$ es invertible, $(T^{-1})^*=(T^*)^{-1}$.

**Prueba.** Las cuatro primeras identidades se obtienen al sustituir en la
definición y usar las propiedades del producto interno. Para la última,

$$
I=(T^{-1}T)^*=T^*(T^{-1})^*,
$$

y análogamente $(T^{-1})^*T^*=I$. $\square$

### 3.1. Una base no ortonormal

Sea $\mathcal B$ una base cualquiera y sea su matriz de Gram

$$
G=\big(\langle b_j,b_i\rangle\big)_{i,j}.
$$

En coordenadas, $\langle x,y\rangle=[y]_{\mathcal B}^*G[x]_{\mathcal B}$.
Si $A=[T]_{\mathcal B}$, entonces

$$
\boxed{[T^*]_{\mathcal B}=G^{-1}A^*G.}
$$

Así, transponer o conjugar-transponer representa el adjunto directamente solo
cuando $G=I$, es decir, en una base ortonormal.

## 4. Núcleo, imagen y ortogonalidad

### Teorema 4.1. Relaciones fundamentales

**Enunciado.** Para una transformación lineal $T:V\to W$ entre espacios con
producto interno de dimensión finita,

$$
\boxed{(\operatorname{Im}T)^\perp=\ker(T^*)}
$$

y

$$
\boxed{(\ker T)^\perp=\operatorname{Im}(T^*).}
$$

**Prueba.** Un vector $y\in W$ pertenece a $(\operatorname{Im}T)^\perp$ si y
solo si

$$
0=\langle Tx,y\rangle=\langle x,T^*y\rangle
\quad\text{para todo }x\in V.
$$

Esto ocurre si y solo si $T^*y=0$, y prueba la primera igualdad. Aplicándola a
$T^*$ se obtiene

$$
(\operatorname{Im}T^*)^\perp=\ker T.
$$

Al tomar complementos ortogonales y usar dimensión finita se obtiene la
segunda igualdad. $\square$

### Teorema 4.2. Invariancia y complemento ortogonal

**Enunciado.** Si $W$ es invariante bajo $T$, entonces $W^\perp$ es
invariante bajo $T^*$.

**Prueba.** Sean $x\in W^\perp$ y $w\in W$. Como $Tw\in W$,

$$
\langle T^*x,w\rangle=\langle x,Tw\rangle=0.
$$

Por tanto, $T^*x\in W^\perp$. $\square$

### Ejemplo 4.3

Para

$$
A=\begin{pmatrix}2&1\\0&3\end{pmatrix},
\qquad W=\operatorname{span}\{e_1\},
$$

$W$ es invariante bajo $A$. Sin embargo, $W^\perp=\operatorname{span}\{e_2\}$
no es invariante bajo $A$, pues $Ae_2=(1,3)^T$. Sí es invariante bajo
$A^T$, ya que $A^Te_2=3e_2$, como afirma el teorema.

## 5. Autoadjuntos y proyecciones ortogonales

### Definición 5.1. Operador autoadjunto

Un operador es **autoadjunto** si

$$
\boxed{T=T^*.}
$$

En una base ortonormal, su matriz es simétrica en el caso real
($A=A^T$) y hermitiana en el caso complejo ($A=A^*$).

### Proposición 5.2. Una primera consecuencia

**Enunciado.** Si $T$ es autoadjunto y $W$ es invariante bajo $T$, entonces
$W^\perp$ también es invariante bajo $T$.

**Prueba.** Por el Teorema 4.2, $W^\perp$ es invariante bajo $T^*$. Como
$T^*=T$, es invariante bajo $T$. $\square$

En consecuencia, $V=W\oplus W^\perp$ produce una matriz por bloques diagonal.
Esta propiedad será central cuando estudiemos el teorema espectral.

### Proposición 5.3. Proyección ortogonal

**Enunciado.** Sea $P_W$ la proyección ortogonal sobre $W$. Entonces:

1. $P_W^2=P_W$;
2. $P_W^*=P_W$;
3. $\operatorname{Im}(P_W)=W$;
4. $\ker(P_W)=W^\perp$.

**Prueba.** Todo $x$ se escribe de manera única como $x=w+z$, con $w\in W$ y
$z\in W^\perp$, y $P_Wx=w$. Aplicar dos veces la proyección no cambia $w$,
lo que prueba 1, y las afirmaciones 3 y 4 son inmediatas. Si
$x=w_x+z_x$ e $y=w_y+z_y$, entonces

$$
\langle P_Wx,y\rangle=\langle w_x,w_y\rangle
=\langle x,P_Wy\rangle,
$$

por lo que $P_W^*=P_W$. $\square$

Si las columnas de $Q$ forman una base ortonormal de $W$, entonces

$$
P_W=QQ^*.
$$

## 6. Ejercicios

1. Sea $T(x,y,z)=(2x+y,y,3z)$. Determina si
   $W=\operatorname{span}\{e_1,e_2\}$ es invariante y escribe la matriz de
   $T$ en bloques respecto de $W\oplus W^\perp$. *(Elaboración propia.)*
2. Sea $A=\begin{pmatrix}1&2\\0&1\end{pmatrix}$. Encuentra todos los
   subespacios invariantes de dimensión uno y decide si sus complementos
   ortogonales también son invariantes bajo $A$. *(Elaboración propia.)*
3. Demuestra directamente que, si $W$ es invariante bajo un operador
   autoadjunto $T$, entonces $W^\perp$ también lo es. Explica cómo se
   descompone la matriz de $T$. *(Final 2025-I, adaptado.)*
4. En $\mathbb R^2$ con producto interno
   $\langle x,y\rangle_G=y^TGx$, donde
   $G=\operatorname{diag}(1,2)$, calcula el adjunto de
   $A=\begin{pmatrix}0&1\\1&0\end{pmatrix}$. Verifica la identidad definitoria
   con vectores generales. *(Elaboración propia.)*
5. Prueba que todo operador $T$ puede escribirse como suma de un operador
   autoadjunto y uno anti-autoadjunto:
   $T=\frac12(T+T^*)+\frac12(T-T^*)$. *(Elaboración propia.)*
6. Sea $P$ una matriz real. Prueba que $P$ representa una proyección
   ortogonal si y solo si $P^2=P$ y $P^T=P$. *(Material de proyecciones de la
   Unidad 2, generalizado.)*

## 7. Ideas que deben quedar claras

- Un subespacio invariante permite restringir un operador y obtener una forma
  matricial por bloques.
- El adjunto está definido por el producto interno; la transpuesta conjugada
  es su matriz únicamente en bases ortonormales.
- El adjunto conecta imagen y núcleo mediante complementos ortogonales.
- Para un operador autoadjunto, la invariancia de $W$ trae consigo la de
  $W^\perp$.
- Las proyecciones ortogonales son simultáneamente idempotentes y
  autoadjuntas.
