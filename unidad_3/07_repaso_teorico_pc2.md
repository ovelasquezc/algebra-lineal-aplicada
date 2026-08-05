# Repaso teórico para la PC2

## Cómo usar esta hoja

La PC2 cierra la Unidad 3. Esta hoja organiza los resultados que debes poder
**enunciar**, **aplicar** y **justificar**; no reemplaza las hojas de teoría de
cada clase. Después de estudiarla, resuelve la
[guía de preparación](07_preparacion_pc2.md) sin software y usa el
[laboratorio](07_laboratorio_preparacion_pc2.ipynb) para verificar cálculos.

En cada resultado distingue las hipótesis, la conclusión y el argumento que
las conecta.

```{admonition} Alcance
:class: important
La preparación comprende transformaciones lineales, operadores y adjuntos,
subespacios invariantes, valores propios, diagonalización, teorema espectral
y formas cuadráticas. La descomposición en valores singulares pertenece a la
Unidad 4 y no forma parte de este bloque.
```

## 1. Transformaciones lineales y matrices

### Definición 1.1. Transformación lineal

Una función $T:V\to W$ es lineal si

$$
T(\alpha u+\beta v)=\alpha T(u)+\beta T(v)
$$

para todo $u,v\in V$ y todo $\alpha,\beta$ en el cuerpo de escalares.

### Teorema 1.2. Una transformación queda determinada por una base

**Enunciado.** Si $\mathcal B=(b_1,\ldots,b_n)$ es una base de $V$, asignar
arbitrariamente los vectores $T(b_j)\in W$ determina una única transformación
lineal $T:V\to W$.

**Prueba.** Todo $v\in V$ tiene una expresión única
$v=\sum_jc_jb_j$. La linealidad obliga a definir
$T(v)=\sum_jc_jT(b_j)$; la unicidad de las coordenadas hace que la definición
sea consistente. $\square$

### Regla 1.3. Matriz relativa a bases

Para bases $\mathcal B=(b_1,\ldots,b_n)$ de $V$ y $\mathcal C$ de $W$,

$$
\boxed{
[T]_{\mathcal C\leftarrow\mathcal B}
=\begin{bmatrix}
[T(b_1)]_{\mathcal C}&\cdots&[T(b_n)]_{\mathcal C}
\end{bmatrix}.}
$$

Por tanto,

$$
[T(v)]_{\mathcal C}
=[T]_{\mathcal C\leftarrow\mathcal B}[v]_{\mathcal B}.
$$

Si $S:W\to Z$, entonces

$$
[S\circ T]_{\mathcal D\leftarrow\mathcal B}
=[S]_{\mathcal D\leftarrow\mathcal C}
[T]_{\mathcal C\leftarrow\mathcal B}.
$$

### Teorema 1.4. Rango-nulidad

**Enunciado.** Si $V$ es de dimensión finita,

$$
\boxed{\dim\ker(T)+\dim\operatorname{Im}(T)=\dim V.}
$$

**Idea de prueba.** Se extiende una base del núcleo a una base del dominio.
Las imágenes de los vectores añadidos forman una base de la imagen.

### Criterio 1.5. Isomorfismo

Si $\dim V=\dim W=n$, son equivalentes:

1. $T$ es inyectiva;
2. $T$ es sobreyectiva;
3. $T$ es invertible;
4. $\ker(T)=\{0\}$;
5. cualquier matriz cuadrada de $T$ es invertible.

## 2. Operadores, adjuntos e invariancia

### Definición 2.1. Subespacio invariante

Para un operador $T:V\to V$, un subespacio $U\subseteq V$ es
$T$-invariante si

$$
T(U)\subseteq U.
$$

Si una base comienza con una base de $U$, la matriz del operador tiene forma

$$
[T]=\begin{pmatrix}A&B\\0&C\end{pmatrix}.
$$

El bloque inferior izquierdo es cero porque las imágenes de los vectores de
$U$ permanecen en $U$.

### Teorema 2.2. Existencia del adjunto

**Enunciado.** En espacios con producto interno de dimensión finita, para
cada $T:V\to W$ existe un único $T^*:W\to V$ tal que

$$
\boxed{\langle T v,w\rangle_W=\langle v,T^*w\rangle_V}
$$

para todo $v\in V$ y $w\in W$.

En bases ortonormales reales, $[T^*]=[T]^T$; en el caso complejo,
$[T^*]=[T]^H$.

### Proposición 2.3. Reglas del adjunto

**Enunciado.** Siempre que las composiciones tengan sentido,

$$
(S+T)^*=S^*+T^*,\qquad
(\alpha T)^*=\overline\alpha T^*,\qquad
(ST)^*=T^*S^*,\qquad
(T^*)^*=T.
$$

**Idea de prueba.** Se aplica repetidamente la identidad que define al adjunto
y se usa su unicidad.

### Proposición 2.4. Núcleo e imagen del adjunto

**Enunciado.**

$$
\boxed{\ker(T^*)=\operatorname{Im}(T)^\perp,\qquad
\operatorname{Im}(T^*)=\ker(T)^\perp.}
$$

**Prueba de la primera igualdad.** $w\in\ker(T^*)$ si y solo si
$\langle v,T^*w\rangle=0$ para todo $v$, lo que equivale a
$\langle Tv,w\rangle=0$ para todo $v$. Esto dice precisamente que
$w\perp\operatorname{Im}(T)$. La segunda igualdad se obtiene aplicando la
primera a $T^*$ y tomando complementos ortogonales. $\square$

### Matriz del adjunto en bases no ortonormales

Si $G_V$ y $G_W$ son las matrices de Gram de las bases usadas y
$A=[T]_{\mathcal C\leftarrow\mathcal B}$, entonces

$$
\boxed{[T^*]_{\mathcal B\leftarrow\mathcal C}
=G_V^{-1}A^T G_W.}
$$

## 3. Valores y vectores propios

### Definición 3.1

El escalar $\lambda$ es un valor propio de $A$ si existe $v\neq0$ tal que

$$
Av=\lambda v.
$$

El espacio propio correspondiente es

$$
E_\lambda=\ker(A-\lambda I).
$$

### Teorema 3.2. Polinomio característico

**Enunciado.**

$$
\lambda\text{ es valor propio}
\quad\Longleftrightarrow\quad
\det(A-\lambda I)=0.
$$

**Prueba.** Existe $v\neq0$ con $(A-\lambda I)v=0$ si y solo si
$A-\lambda I$ tiene núcleo no trivial, y esto equivale a que sea singular.
$\square$

### Proposición 3.3. Invariantes por semejanza

**Enunciado.** Si $B=P^{-1}AP$, entonces $A$ y $B$ tienen el mismo polinomio
característico y, por tanto, los mismos valores propios con las mismas
multiplicidades algebraicas.

**Prueba.**

$$
\det(B-\lambda I)
=\det\!\bigl(P^{-1}(A-\lambda I)P\bigr)
=\det(A-\lambda I).
$$

Además, si $Av=\lambda v$, entonces $P^{-1}v$ es vector propio de $B$.
$\square$

### Multiplicidades

La multiplicidad algebraica $m_a(\lambda)$ es la multiplicidad de $\lambda$
como raíz del polinomio característico. La multiplicidad geométrica es

$$
m_g(\lambda)=\dim E_\lambda.
$$

Siempre

$$
1\leq m_g(\lambda)\leq m_a(\lambda).
$$

## 4. Diagonalización

### Teorema 4.1. Criterios equivalentes

**Enunciado.** Para $A\in\mathbb F^{n\times n}$ son equivalentes:

1. $A=PDP^{-1}$ para alguna $P$ invertible y alguna $D$ diagonal;
2. existe una base de $\mathbb F^n$ formada por vectores propios de $A$;
3. la suma de las dimensiones de los espacios propios es $n$;
4. para cada valor propio,
   $m_g(\lambda)=m_a(\lambda)$, y el polinomio característico se descompone
   en factores lineales sobre $\mathbb F$.

**Idea de prueba.** Las columnas de $P$ satisfacen $AP=PD$. Por tanto, son
vectores propios si y solo si $D$ es diagonal; $P$ es invertible si y solo si
esas columnas forman una base.

### Corolario 4.2. Valores propios distintos

Una matriz $n\times n$ con $n$ valores propios distintos es diagonalizable.
La recíproca es falsa: una matriz diagonal puede repetir entradas.

### Aplicaciones

Si $A=PDP^{-1}$, entonces

$$
A^k=PD^kP^{-1},
\qquad
p(A)=Pp(D)P^{-1}.
$$

Si los valores propios distintos son $\lambda_1,\ldots,\lambda_r$, los
proyectores espectrales son

$$
P_j=\prod_{k\neq j}\frac{A-\lambda_kI}{\lambda_j-\lambda_k},
\qquad
A=\sum_{j=1}^r\lambda_jP_j.
$$

## 5. Autoadjuntos y teorema espectral

### Teorema 5.1. Realidad del espectro

**Enunciado.** Todo valor propio de un operador autoadjunto es real.

**Prueba.** Si $Av=\lambda v$ y $v\neq0$, entonces

$$
\lambda\langle v,v\rangle
=\langle Av,v\rangle
=\langle v,Av\rangle
=\overline\lambda\langle v,v\rangle.
$$

Como $\langle v,v\rangle>0$, resulta $\lambda=\overline\lambda$. $\square$

### Teorema 5.2. Ortogonalidad de espacios propios

**Enunciado.** Si $A=A^*$, $Av=\lambda v$, $Aw=\mu w$ y
$\lambda\neq\mu$, entonces $v\perp w$.

**Prueba.**

$$
\lambda\langle v,w\rangle
=\langle Av,w\rangle
=\langle v,Aw\rangle
=\mu\langle v,w\rangle.
$$

Por tanto, $(\lambda-\mu)\langle v,w\rangle=0$. $\square$

### Teorema 5.3. Teorema espectral real

**Enunciado.** Para una matriz real $A$ son equivalentes:

1. $A=A^T$;
2. existe una matriz ortogonal $Q$ y una matriz diagonal real $D$ tales que
   $$A=QDQ^T.$$

**Idea de prueba.** Se obtiene un vector propio unitario, su complemento
ortogonal es invariante y se aplica inducción. La recíproca se comprueba
transponiendo $QDQ^T$.

### Teorema 5.4. Cociente de Rayleigh

**Enunciado.** Si $A=A^T$ y $x\neq0$,

$$
\lambda_{\min}\leq
\frac{x^TAx}{x^Tx}
\leq\lambda_{\max}.
$$

Los extremos se alcanzan exactamente en las direcciones propias extremas.

**Idea de prueba.** Se escribe $x=Qz$ en una base ortonormal de vectores
propios. El cociente es un promedio ponderado de los valores propios con
pesos $z_i^2/\|z\|^2$.

## 6. Formas cuadráticas

### Definición 6.1 y regla de construcción

Toda forma cuadrática real se escribe de manera única como

$$
Q(x)=x^TAx,
\qquad A=A^T.
$$

El coeficiente de $x_ix_j$, $i\neq j$, se divide entre las entradas
$a_{ij}$ y $a_{ji}$; por ello cada una recibe la mitad del coeficiente
cruzado.

### Teorema 6.2. Clasificación espectral

**Enunciado.** Si $A=A^T$, el signo de $Q_A(x)=x^TAx$ se determina por los
signos de sus valores propios:

| Espectro | Clasificación |
|---|---|
| todos positivos | definida positiva |
| no negativos y alguno cero | semidefinida positiva |
| todos negativos | definida negativa |
| no positivos y alguno cero | semidefinida negativa |
| positivos y negativos | indefinida |

**Prueba.** Si $A=QDQ^T$ y $z=Q^Tx$, entonces

$$
x^TAx=z^TDz=\sum_i\lambda_i z_i^2.
$$

La clasificación se lee de los signos de los coeficientes. Recíprocamente,
evaluar la forma en un vector propio unitario recupera cada $\lambda_i$.
$\square$

### Teorema 6.3. Criterio de Sylvester

**Enunciado.** Una matriz simétrica $A$ es definida positiva si y solo si
todos sus menores principales líderes son positivos. Es definida negativa si
y solo si esos menores alternan signos:

$$
(-1)^k\Delta_k>0,
\qquad k=1,\ldots,n.
$$

Para semidefinitud no basta sustituir $>$ por $\geq$ en este criterio.

### Teorema 6.4. Ley de inercia de Sylvester

**Enunciado.** Si $C$ es invertible, $A$ y $C^TAC$ tienen el mismo número de
valores propios positivos, negativos y cero.

La congruencia preserva la inercia, pero no necesariamente los valores
propios. No debe confundirse con la semejanza $P^{-1}AP$.

## 7. Mapa de decisiones

| Si te piden... | Empieza por... | Comprueba al final... |
|---|---|---|
| matriz de $T$ | imágenes de una base y sus coordenadas | tamaños y orden de bases |
| núcleo e imagen | sistemas homogéneos y columnas pivote | rango-nulidad |
| adjunto | identidad de producto interno | dirección de dominio y codominio |
| valores propios | $\det(A-\lambda I)$ | $\operatorname{tr}A$ y $\det A$ |
| diagonalizar | bases de todos los espacios propios | $AP=PD$ y $P$ invertible |
| diagonalizar una simétrica | vectores propios ortonormales | $P^TP=I$ |
| clasificar una forma | matriz simétrica y espectro | vectores que exhiban los signos |
| extremos en la esfera | valores propios extremos | puntos propios unitarios |

## 8. Errores que debes detectar

1. Aceptar al vector cero como vector propio.
2. Confundir $Av=\lambda v$ con que cada entrada de $v$ se multiplica por un
   escalar distinto.
3. Concluir diagonalización solo porque el polinomio característico se
   factoriza.
4. Usar $P^{-1}=P^T$ sin haber construido una base ortonormal.
5. Ortogonalizar vectores propios pertenecientes a valores propios distintos
   sin aprovechar que, para una matriz simétrica, ya son ortogonales.
6. Colocar completo el coeficiente de un término cruzado en cada entrada de
   la matriz de una forma cuadrática.
7. Confundir semejanza con congruencia.
8. Clasificar una forma semidefinida usando solo menores líderes no negativos.
