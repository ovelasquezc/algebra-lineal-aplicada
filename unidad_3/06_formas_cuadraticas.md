# Formas cuadráticas y clasificación por signo

## Objetivos

Al finalizar este bloque, podrás:

1. construir la matriz simétrica asociada a una forma cuadrática;
2. reducir una forma cuadrática a suma y diferencia de cuadrados;
3. clasificarla mediante sus valores propios;
4. aplicar los criterios de Sylvester;
5. interpretar cambios de variables como congruencias;
6. relacionar positividad, matrices de Gram y optimización convexa.

## 1. De un polinomio a una matriz simétrica

### Definición 1.1. Forma cuadrática

Una **forma cuadrática** sobre $\mathbb R^n$ es una función
$Q:\mathbb R^n\to\mathbb R$ de la forma

$$
\boxed{Q(x)=x^TAx}
$$

para alguna matriz $A\in\mathbb R^{n\times n}$.

En coordenadas,

$$
Q(x_1,\ldots,x_n)=\sum_{i=1}^n a_{ii}x_i^2
+2\sum_{i<j}a_{ij}x_ix_j
$$

cuando $A$ es simétrica.

### Regla 1.2. Coeficientes cruzados

El coeficiente de $x_ix_j$, con $i\neq j$, se reparte entre las posiciones
$(i,j)$ y $(j,i)$. Por ejemplo,

$$
Q(x,y)=5x^2+4xy+y^2
$$

tiene como matriz simétrica asociada

$$
A=\begin{pmatrix}5&2\\2&1\end{pmatrix}.
$$

### Proposición 1.3. Basta la parte simétrica

**Enunciado.** Para toda matriz real $A$,

$$
x^TAx=x^T\left(\frac{A+A^T}{2}\right)x.
$$

**Prueba.** Escribamos

$$
A=\frac{A+A^T}{2}+\frac{A-A^T}{2}=A_s+A_a.
$$

$A_s$ es simétrica y $A_a$ antisimétrica. El escalar $x^TA_ax$ satisface

$$
x^TA_ax=(x^TA_ax)^T=x^TA_a^Tx=-x^TA_ax,
$$

por lo que es cero. $\square$

Así, cada forma cuadrática posee una única matriz **simétrica** asociada.
También puede recuperarse mediante

$$
A=\frac12\nabla^2Q,
$$

porque la Hessiana de una forma cuadrática es constante.

## 2. Cambio ortogonal y suma de cuadrados

Sea $A=A^T$. Por el teorema espectral,

$$
A=PDP^T,
\qquad
P^TP=I,
$$

con $D=\operatorname{diag}(\lambda_1,\ldots,\lambda_n)$. Si definimos el
cambio ortogonal de variables

$$
z=P^Tx,
\qquad x=Pz,
$$

entonces

$$
\boxed{
Q(x)=x^TAx
=z^TDz
=\lambda_1z_1^2+\cdots+\lambda_nz_n^2.
}
$$

La rotación o reflexión $P$ elimina los términos cruzados sin alterar
longitudes ni ángulos.

### Ejemplo 2.1

Para

$$
Q(x,y)=x^2-3xy+y^2,
\qquad
A=\begin{pmatrix}1&-3/2\\-3/2&1\end{pmatrix},
$$

los valores propios son $-1/2$ y $5/2$. En coordenadas ortonormales adecuadas,

$$
Q=-\frac12z_1^2+\frac52z_2^2.
$$

La forma toma valores positivos y negativos.

## 3. Clasificación por signo

### Definición 3.1

Sea $A=A^T$ y $Q_A(x)=x^TAx$.

1. $A$ es **definida positiva**, $A\succ0$, si
   $Q_A(x)>0$ para todo $x\neq0$.
2. $A$ es **semidefinida positiva**, $A\succeq0$, si
   $Q_A(x)\geq0$ para todo $x$.
3. $A$ es **definida negativa**, $A\prec0$, si
   $Q_A(x)<0$ para todo $x\neq0$.
4. $A$ es **semidefinida negativa**, $A\preceq0$, si
   $Q_A(x)\leq0$ para todo $x$.
5. $A$ es **indefinida** si existen $u,v$ tales que
   $Q_A(u)>0$ y $Q_A(v)<0$.

### Teorema 3.2. Criterio espectral

**Enunciado.** La clasificación depende de los signos de los valores propios:

| Signos del espectro | Clasificación |
|---|---|
| todos positivos | definida positiva |
| todos no negativos y alguno cero | semidefinida positiva |
| todos negativos | definida negativa |
| todos no positivos y alguno cero | semidefinida negativa |
| hay positivos y negativos | indefinida |

**Prueba.** En coordenadas espectrales,

$$
Q(x)=\sum_i\lambda_i z_i^2.
$$

Si todos los valores propios tienen el signo indicado, la conclusión es
inmediata. Recíprocamente, al evaluar $Q$ en un vector propio unitario $u_i$ se
obtiene $Q(u_i)=\lambda_i$, de modo que la definición obliga a los signos
correspondientes. $\square$

### Consecuencia 3.3. Núcleo de una forma semidefinida

Si $A\succeq0$, entonces

$$
x^TAx=0\quad\Longleftrightarrow\quad Ax=0.
$$

**Prueba.** En coordenadas espectrales, una suma
$\sum_i\lambda_i z_i^2$, con $\lambda_i\geq0$, es cero si y solo si
$z_i=0$ para cada $\lambda_i>0$. Esto equivale a pertenecer al espacio propio
de valor cero. $\square$

## 4. Criterios de Sylvester

Sea $A_k$ la submatriz principal superior izquierda de orden $k$ y
$\Delta_k=\det(A_k)$.

### Teorema 4.1. Definición positiva

**Enunciado.** Para una matriz simétrica $A$ son equivalentes:

1. $A\succ0$;
2. todos sus valores propios son positivos;
3. sus menores principales líderes satisfacen
   $$
   \boxed{\Delta_1>0,\ldots,\Delta_n>0.}
   $$

### Teorema 4.2. Definición negativa

**Enunciado.** $A\prec0$ si y solo si

$$
\boxed{(-1)^k\Delta_k>0,\qquad k=1,\ldots,n.}
$$

Es decir, $\Delta_1<0,\Delta_2>0,\Delta_3<0,\ldots$.

**Idea de prueba.** El criterio se obtiene mediante eliminación simétrica o
una factorización $A=LDL^T$. Para definición positiva, los pivotes de $D$ son
positivos y

$$
\Delta_k=d_1\cdots d_k.
$$

:::{admonition} Cuidado con la semidefinitud
:class: warning
Reemplazar $>$ por $\geq$ en los menores principales **líderes** no caracteriza
la semidefinitud. Por ejemplo,
$A=\operatorname{diag}(0,-1)$ tiene $\Delta_1=\Delta_2=0$, pero no es
semidefinida positiva. Para caracterizar $A\succeq0$ mediante determinantes
deben ser no negativos **todos** los menores principales, no solo los líderes.
:::

## 5. Congruencia e inercia

Un cambio de variables invertible $x=Cy$ transforma

$$
Q_A(x)=x^TAx
$$

en

$$
Q_A(Cy)=y^T(C^TAC)y.
$$

Las matrices $A$ y $C^TAC$ se llaman **congruentes**.

### Teorema 5.1. Ley de inercia de Sylvester

**Enunciado.** Una congruencia invertible conserva el número de valores
propios positivos, negativos y cero, aunque no conserva sus valores.

La terna

$$
(n_+,n_-,n_0)
$$

se llama **inercia** de la forma cuadrática. Determina su clasificación.

:::{admonition} Congruencia no es semejanza
:class: note
La semejanza $P^{-1}AP$ conserva valores propios. La congruencia $C^TAC$
conserva la forma cuadrática bajo un cambio de variables y preserva solo la
inercia.
:::

## 6. Ejemplo con parámetros

Consideremos

$$
Q(x,y,z)=x^2+y^2+z^2+2axz.
$$

Su matriz simétrica es

$$
A(a)=
\begin{pmatrix}
1&0&a\\
0&1&0\\
a&0&1
\end{pmatrix},
$$

con valores propios

$$
1,\qquad1+a,\qquad1-a.
$$

Por tanto:

- si $|a|<1$, $Q$ es definida positiva;
- si $|a|=1$, es semidefinida positiva;
- si $|a|>1$, es indefinida.

Para $a=2$,

$$
Q=(x+2z)^2+y^2-3z^2,
$$

lo que exhibe directamente sus signos positivo y negativo.

## 7. Matrices de Gram y factorizaciones

### Proposición 7.1

**Enunciado.** Para toda matriz $B$,

$$
B^TB\succeq0.
$$

Además, $B^TB\succ0$ si y solo si las columnas de $B$ son linealmente
independientes.

**Prueba.**

$$
x^TB^TBx=\|Bx\|^2\geq0.
$$

La igualdad ocurre si y solo si $Bx=0$. Por tanto, es estrictamente positiva
para $x\neq0$ exactamente cuando $\ker(B)=\{0\}$. $\square$

### Teorema 7.2. Factorización semidefinida

**Enunciado.** Si $A=A^T\succeq0$, existe $B$ tal que

$$
\boxed{A=BB^T.}
$$

**Prueba.** Por el teorema espectral,
$A=PDP^T$, con $\lambda_i\geq0$. Definimos

$$
B=PD^{1/2},
\qquad
D^{1/2}=\operatorname{diag}(\sqrt{\lambda_1},\ldots,\sqrt{\lambda_n}).
$$

Entonces $BB^T=PD^{1/2}D^{1/2}P^T=A$. $\square$

Si $A\succ0$, también existe la factorización de Cholesky
$A=LL^T$, con $L$ triangular inferior y diagonal positiva.

## 8. Propiedades de la positividad

### Proposición 8.1

**Enunciado.**

1. Si $A\succ0$ y $B\succ0$, entonces $A+B\succ0$.
2. Si $A\succ0$ y $C$ es invertible, entonces $C^TAC\succ0$.
3. Si $A\succeq0$ y $C$ es cualquiera, entonces $C^TAC\succeq0$.
4. Si $A\succ0$, entonces $A^{-1}\succ0$.

**Prueba.** Para 1,

$$
x^T(A+B)x=x^TAx+x^TBx>0
$$

si $x\neq0$. Para 2 y 3,

$$
x^TC^TACx=(Cx)^TA(Cx).
$$

Si $C$ es invertible, $x\neq0$ implica $Cx\neq0$. Para 4, los valores propios
de $A^{-1}$ son los recíprocos positivos de los de $A$. $\square$

Si $C$ es singular, $C^TAC$ no puede ser definida positiva: cualquier vector
no nulo de $\ker(C)$ produce valor cero.

## 9. Optimización cuadrática

Sea

$$
f(x)=\frac12x^TAx-b^Tx,
\qquad A=A^T.
$$

Entonces

$$
\nabla f(x)=Ax-b,
\qquad
\nabla^2f(x)=A.
$$

### Teorema 9.1

**Enunciado.** Si $A\succ0$, $f$ tiene un único mínimo global en

$$
\boxed{x^*=A^{-1}b,}
$$

y

$$
\boxed{
f(x)-f(x^*)
=\frac12(x-x^*)^TA(x-x^*)\geq0.
}
$$

Además,

$$
f(x^*)=-\frac12b^TA^{-1}b.
$$

**Prueba.** La ecuación estacionaria es $Ax=b$, que tiene solución única.
Al sustituir $x=x^*+h$ y usar $Ax^*=b$, los términos lineales se cancelan y
queda $\frac12h^TAh>0$ para $h\neq0$. $\square$

La definición positiva convierte el sistema lineal $Ax=b$ en un problema de
minimización estrictamente convexa.

## 10. Cierre de la Unidad 3

La progresión conceptual de la unidad puede resumirse así:

$$
\text{operador}
\longrightarrow
\text{subespacios invariantes}
\longrightarrow
\text{espectro}
\longrightarrow
\text{diagonalización}
\longrightarrow
\text{formas cuadráticas}.
$$

La matriz diagonal revela los modos independientes de un operador; en una
forma cuadrática, sus signos describen curvatura, extremos y direcciones
planas.

## 11. Ejercicios

1. Para
   $Q(x,y,z)=x^2+y^2+z^2+2axz$, clasifica la forma para todo $a$ y, cuando
   $a=2$, escríbela como suma y diferencia de cuadrados.
   *(PC2 2025-II y lista PC2 2026-I.)*
2. Sea
   $Q=(x-y)^2+(y-z)^2+(x+z)^2$. Encuentra su matriz, sus valores propios y un
   cambio ortogonal que la reduzca a forma diagonal. *(Lista PC2 2026-I.)*
3. Clasifica
   $Q(x,y)=x^2-3xy+y^2$ y determina sus extremos sobre el círculo unitario.
   *(Lista PC2 2026-I.)*
4. Estudia el signo de
   $Q=\alpha x_1^2+x_2^2+x_3^2+2\beta x_2x_3$, con $\alpha\neq0$, en función
   de $\alpha$ y $\beta$. *(Presentación de clase y lista PC2 2026-I.)*
5. Demuestra que la suma de dos matrices simétricas definidas positivas es
   definida positiva. *(Lista PC2 2026-I.)*
6. Si $A\succ0$ y $C$ es invertible, demuestra que $C^TAC\succ0$. Explica qué
   cambia si $C$ es singular. *(Lista PC2 2026-I.)*
7. Si $A\succeq0$, construye $B$ tal que $A=BB^T$ mediante el teorema
   espectral. *(Lista PC2 2026-I.)*
8. Para una matriz $X$, demuestra que $G=X^TX$ es semidefinida positiva y
   caracteriza cuándo es definida positiva. *(EP M3 2026-I.)*
9. Minimiza
   $f(x_1,x_2)=x_1^2-x_1x_2+x_2^2-b_1x_1-b_2x_2$
   y expresa el valor mínimo en términos de $b$. *(Presentación de clase.)*
