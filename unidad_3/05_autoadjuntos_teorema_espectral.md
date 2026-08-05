# Operadores autoadjuntos y teorema espectral

## Objetivos

Al finalizar este bloque, podrás:

1. reconocer operadores autoadjuntos y matrices simétricas o hermitianas;
2. demostrar que sus valores propios son reales;
3. demostrar la ortogonalidad de espacios propios distintos;
4. enunciar y explicar la prueba del teorema espectral;
5. construir una diagonalización ortogonal o unitaria;
6. usar proyectores ortogonales y el cociente de Rayleigh.

Trabajaremos con la convención

$$
\langle x,y\rangle=y^*x,
$$

lineal en la primera entrada. En el caso real, $y^*x=y^Tx$.

## 1. Autoadjuntos, simétricos y hermitianos

### Definición 1.1. Operador autoadjunto

Un operador $T:V\to V$ sobre un espacio con producto interno es
**autoadjunto** si

$$
\boxed{T=T^*.}
$$

Equivalentemente,

$$
\langle Tx,y\rangle=\langle x,Ty\rangle
\qquad\text{para todo }x,y\in V.
$$

### Proposición 1.2. Representación matricial

**Enunciado.** En una base ortonormal:

- sobre $\mathbb R$, $T$ es autoadjunto si y solo si su matriz es
  **simétrica**, $A=A^T$;
- sobre $\mathbb C$, $T$ es autoadjunto si y solo si su matriz es
  **hermitiana**, $A=A^*=\overline A^{\,T}$.

**Prueba.** En una base ortonormal, la matriz del adjunto es $A^*$. Por tanto,
$T=T^*$ equivale a $A=A^*$. En el caso real, la conjugación no cambia las
entradas y queda $A=A^T$. $\square$

:::{admonition} La base debe ser ortonormal
:class: warning
En una base general, la matriz de un operador autoadjunto no tiene por qué ser
simétrica. Si $G$ es la matriz de Gram, la condición correcta es
$A=G^{-1}A^*G$, o equivalentemente $GA=A^*G$.
:::

## 2. Valores propios reales

### Teorema 2.1

**Enunciado.** Todo valor propio de un operador autoadjunto es real.

**Prueba.** Sea $Tv=\lambda v$, con $v\neq0$. Por autoadjunción,

$$
\langle Tv,v\rangle=\langle v,Tv\rangle.
$$

Usando la convención del curso,

$$
\langle Tv,v\rangle
=\langle\lambda v,v\rangle
=\lambda\langle v,v\rangle,
$$

mientras que

$$
\langle v,Tv\rangle
=\langle v,\lambda v\rangle
=\overline\lambda\langle v,v\rangle.
$$

Como $\langle v,v\rangle>0$, se concluye
$\lambda=\overline\lambda$, es decir, $\lambda\in\mathbb R$. $\square$

### Consecuencia 2.2

Una matriz hermitiana compleja posee espectro real. Que sus entradas sean
complejas no obliga a que sus valores propios lo sean.

## 3. Ortogonalidad de espacios propios

### Teorema 3.1

**Enunciado.** Vectores propios de un operador autoadjunto asociados a valores
propios distintos son ortogonales.

**Prueba.** Sean
$Tu=\lambda u$ y $Tv=\mu v$, con $\lambda\neq\mu$. Como ambos valores son
reales,

$$
\lambda\langle u,v\rangle
=\langle Tu,v\rangle
=\langle u,Tv\rangle
=\mu\langle u,v\rangle.
$$

Por tanto,

$$
(\lambda-\mu)\langle u,v\rangle=0.
$$

Como $\lambda\neq\mu$, se obtiene $\langle u,v\rangle=0$. $\square$

### Corolario 3.2

Los espacios propios asociados a valores propios distintos son ortogonales:

$$
E_\lambda\perp E_\mu
\qquad(\lambda\neq\mu).
$$

Dentro de un espacio propio de dimensión mayor que uno, una base obtenida por
eliminación no tiene por qué ser ortogonal. Puede aplicarse Gram–Schmidt
**dentro de ese espacio propio** sin perder la propiedad de ser vector propio,
porque toda combinación lineal de vectores de $E_\lambda$ permanece en
$E_\lambda$.

## 4. Complementos ortogonales invariantes

### Proposición 4.1

**Enunciado.** Si $W$ es invariante bajo un operador autoadjunto $T$, entonces
$W^\perp$ también es invariante bajo $T$.

**Prueba.** Sean $x\in W^\perp$ y $w\in W$. Como $Tw\in W$,

$$
\langle Tx,w\rangle
=\langle x,Tw\rangle
=0.
$$

Esto vale para todo $w\in W$, de modo que $Tx\in W^\perp$. $\square$

En particular, si $v$ es un vector propio, la recta
$\operatorname{span}\{v\}$ y su complemento ortogonal son invariantes.

## 5. Teorema espectral

### Teorema 5.1. Caso real

**Enunciado.** Para $A\in\mathbb R^{n\times n}$, son equivalentes:

1. $A$ es simétrica;
2. existe una matriz ortogonal $Q$ y una matriz diagonal real $D$ tales que
   $$
   \boxed{A=QDQ^T;}
   $$
3. $\mathbb R^n$ posee una base ortonormal de vectores propios de $A$.

### Prueba

**De 2 a 1.** Si $A=QDQ^T$, con $D^T=D$, entonces

$$
A^T=(QDQ^T)^T=QD^TQ^T=QDQ^T=A.
$$

**Equivalencia entre 2 y 3.** Si las columnas
$q_1,\ldots,q_n$ de $Q$ forman una base ortonormal de vectores propios y
$Aq_j=\lambda_jq_j$, entonces

$$
AQ=QD,
\qquad
D=\operatorname{diag}(\lambda_1,\ldots,\lambda_n).
$$

Como $Q^{-1}=Q^T$, resulta $A=QDQ^T$. El argumento recíproco se obtiene
comparando las columnas de $AQ=QD$.

**De 1 a 3: idea completa por inducción.**

1. **Caso base.** En dimensión uno, todo operador es multiplicación por un
   escalar y cualquier vector unitario forma una base ortonormal propia.
2. **Existencia de una dirección propia.** En la esfera unitaria, la función
   continua
   $$
   x\longmapsto\langle Ax,x\rangle
   $$
   alcanza un máximo. Los multiplicadores de Lagrange aplicados a la
   restricción $\langle x,x\rangle=1$ dan
   $$
   Av=\lambda v
   $$
   para algún vector unitario $v$.
3. **Reducción de dimensión.** El espacio
   $W=v^\perp$ tiene dimensión $n-1$ y es invariante por la Proposición 4.1.
   La restricción $A|_W$ continúa siendo autoadjunta.
4. **Hipótesis inductiva.** Existe una base ortonormal de $W$ formada por
   vectores propios de $A|_W$. Al añadir $v$, se obtiene una base ortonormal de
   todo $\mathbb R^n$ formada por vectores propios.

Esto completa la prueba. $\square$

### Teorema 5.2. Caso complejo

**Enunciado.** Para $A\in\mathbb C^{n\times n}$, son equivalentes:

1. $A$ es hermitiana;
2. existe una matriz unitaria $U$ y una matriz diagonal **real** $D$ tales que
   $$
   \boxed{A=UDU^*;}
   $$
3. $\mathbb C^n$ posee una base ortonormal de vectores propios de $A$.

La prueba sigue la misma estructura. La matriz es unitaria cuando
$U^*U=I$, por lo que $U^{-1}=U^*$.

## 6. Construcción de la diagonalización ortogonal

### Algoritmo 6.1

1. Verificar $A=A^T$ en el caso real o $A=A^*$ en el complejo.
2. Calcular los valores propios y una base de cada espacio propio.
3. Para cada espacio propio de dimensión mayor que uno, aplicar Gram–Schmidt a
   su base.
4. Normalizar todos los vectores.
5. Formar $Q$ con esos vectores como columnas y colocar en $D$ sus valores
   propios en el mismo orden.
6. Verificar
   $$
   Q^TQ=I,\qquad AQ=QD,\qquad Q^TAQ=D
   $$
   en el caso real; reemplazar $Q^T$ por $U^*$ en el complejo.

No se aplica Gram–Schmidt mezclando vectores de valores propios distintos:
estos ya son ortogonales. Se aplica únicamente dentro de cada espacio propio
repetido.

## 7. Ejemplo completo

Sea

$$
A=
\begin{pmatrix}
6&2&2\\
2&3&1\\
2&1&3
\end{pmatrix}.
$$

Sus valores propios son $8$, con multiplicidad uno, y $2$, con multiplicidad
dos. Una base ortonormal de vectores propios es

$$
u_8=\frac1{\sqrt6}(2,1,1)^T,
$$

$$
u_{2,1}=\frac1{\sqrt2}(0,1,-1)^T,
\qquad
u_{2,2}=\frac1{\sqrt3}(-1,1,1)^T.
$$

Si

$$
Q=\begin{pmatrix}u_8&u_{2,1}&u_{2,2}\end{pmatrix},
\qquad
D=\operatorname{diag}(8,2,2),
$$

entonces

$$
Q^TQ=I,
\qquad
Q^TAQ=D,
\qquad
A=QDQ^T.
$$

Geométricamente, $A$ escala por $8$ sobre la recta generada por $(2,1,1)$ y
por $2$ sobre su plano ortogonal.

## 8. Descomposición espectral ortogonal

Agrupemos los vectores propios ortonormales de cada valor propio. Si las
columnas de $Q_\lambda$ forman una base ortonormal de $E_\lambda$, definimos

$$
\Pi_\lambda=Q_\lambda Q_\lambda^*.
$$

### Teorema 8.1

**Enunciado.** Para un operador autoadjunto:

1. $\Pi_\lambda$ es la proyección ortogonal sobre $E_\lambda$;
2. $\Pi_\lambda^*=\Pi_\lambda$ y $\Pi_\lambda^2=\Pi_\lambda$;
3. $\Pi_\lambda\Pi_\mu=0$ si $\lambda\neq\mu$;
4. $\sum_\lambda\Pi_\lambda=I$;
5. $A=\sum_\lambda\lambda\Pi_\lambda$;
6. $f(A)=\sum_\lambda f(\lambda)\Pi_\lambda$.

**Prueba.** La fórmula $Q_\lambda Q_\lambda^*$ es la proyección ortogonal
sobre el espacio columna de $Q_\lambda$. Los espacios propios distintos son
ortogonales y su suma es todo el espacio por el teorema espectral. Las demás
identidades siguen de evaluar ambos lados sobre cada espacio propio.
$\square$

### Ejemplo 8.2

En el ejemplo anterior,

$$
\Pi_8=u_8u_8^T,
\qquad
\Pi_2=u_{2,1}u_{2,1}^T+u_{2,2}u_{2,2}^T=I-\Pi_8.
$$

Por tanto,

$$
\boxed{A=8\Pi_8+2\Pi_2=2I+6\Pi_8.}
$$

Esta expresión permite calcular inmediatamente

$$
A^k=8^k\Pi_8+2^k\Pi_2
$$

y, como los valores propios son positivos, la raíz cúbica autoadjunta

$$
A^{1/3}=2\Pi_8+\sqrt[3]{2}\,\Pi_2.
$$

## 9. Cociente de Rayleigh

Para $x\neq0$, definimos

$$
R_A(x)=\frac{\langle Ax,x\rangle}{\langle x,x\rangle}.
$$

### Teorema 9.1. Cotas espectrales

**Enunciado.** Si $A$ es autoadjunta y
$\lambda_{\min}\leq\lambda_{\max}$ son sus valores propios extremos, entonces

$$
\boxed{
\lambda_{\min}
\leq R_A(x)
\leq\lambda_{\max}.
}
$$

La igualdad inferior ocurre exactamente para
$x\in E_{\lambda_{\min}}\setminus\{0\}$, y la superior para
$x\in E_{\lambda_{\max}}\setminus\{0\}$.

**Prueba.** Escribamos $x=\sum_j c_ju_j$ en una base ortonormal propia. Entonces

$$
R_A(x)
=\frac{\sum_j\lambda_j|c_j|^2}{\sum_j|c_j|^2}.
$$

Es un promedio ponderado de los valores propios, con pesos no negativos. Por
ello queda entre el menor y el mayor. La caracterización de la igualdad se
obtiene cuando todo el peso se concentra en el espacio propio extremo.
$\square$

Este resultado conecta el teorema espectral con problemas de optimización y
con la clasificación de formas cuadráticas, que se desarrollará en C20.

## 10. Ejercicios

1. Demuestra que todo valor propio de una matriz hermitiana es real y que
   espacios propios distintos son ortogonales. *(Presentación de clase,
   generalizada al caso complejo.)*
2. Completa la prueba por inducción del teorema espectral real, justificando la
   existencia de un máximo del cociente de Rayleigh y la invariancia de
   $v^\perp$. *(Final 2025-I, adaptado.)*
3. Para
   $A=\begin{pmatrix}6&2&2\\2&3&1\\2&1&3\end{pmatrix}$, construye $Q$ y $D$,
   verifica $A=QDQ^T$ y calcula $A^6$. *(PC2 2025-I y lista PC2 2026-I.)*
4. Para la misma matriz, construye su raíz cúbica autoadjunta y verifica que
   su cubo es $A$. *(PC2 2025-I.)*
5. Da un ejemplo de una matriz diagonalizable real que no sea simétrica y
   explica por qué no puede diagonalizarse mediante una matriz ortogonal.
   *(Elaboración a partir de las presentaciones.)*
6. Prueba que una matriz real representa una proyección ortogonal si y solo si
   es simétrica e idempotente. Deduce que sus valores propios son $0$ y $1$.
   *(Material de proyecciones y presentación de clase.)*
7. Sea
   $H=\begin{pmatrix}2&i\\-i&2\end{pmatrix}$. Verifica que es hermitiana,
   encuentra una base ortonormal de vectores propios y construye
   $H=UDU^*$. *(Elaboración propia.)*
8. Para una matriz simétrica con valores propios $-2,1,5$, determina el mínimo
   y el máximo de $x^TAx$ sobre la esfera unitaria y caracteriza dónde se
   alcanzan. *(Final 2025-I, adaptado.)*
