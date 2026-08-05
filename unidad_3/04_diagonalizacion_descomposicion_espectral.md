# Diagonalización y descomposición espectral

## Objetivos

Al finalizar este bloque, podrás:

1. decidir si una matriz es diagonalizable;
2. construir una diagonalización $A=PDP^{-1}$ a partir de bases de espacios propios;
3. reconocer exactamente qué impide diagonalizar una matriz;
4. calcular potencias y funciones de una matriz diagonalizable;
5. construir proyectores espectrales y descomponer el espacio en subespacios propios;
6. interpretar sistemas dinámicos lineales mediante modos propios.

En este bloque diagonalizamos por **semejanza**. La diagonalización ortogonal
de matrices simétricas y el teorema espectral para operadores autoadjuntos se
desarrollarán en C19.

## 1. Matrices semejantes

### Definición 1.1. Semejanza

Dos matrices $A,B\in\mathbb K^{n\times n}$ son **semejantes** si existe una
matriz invertible $P$ tal que

$$
\boxed{A=PBP^{-1}.}
$$

Equivalentemente, $AP=PB$. Matrices semejantes representan el mismo operador
lineal en bases distintas. La semejanza conserva el polinomio característico,
los valores propios y sus multiplicidades, las dimensiones de los espacios
propios, el determinante, la traza y el rango.

### Proposición 1.2. Transporte de espacios propios

**Enunciado.** Si $A=PBP^{-1}$, entonces

$$
E_\lambda(A)=P\,E_\lambda(B).
$$

**Prueba.** Si $Bw=\lambda w$, entonces

$$
A(Pw)=PBP^{-1}Pw=PBw=\lambda Pw.
$$

Así, $P\,E_\lambda(B)\subseteq E_\lambda(A)$. Aplicando el mismo argumento a
$B=P^{-1}AP$ se obtiene la inclusión contraria. $\square$

:::{admonition} El espectro no determina la semejanza
:class: warning
Tener los mismos valores propios, incluso con las mismas multiplicidades
algebraicas, no garantiza que dos matrices sean semejantes. Las dimensiones
de sus espacios propios también deben ser compatibles.
:::

Por ejemplo,

$$
D=\begin{pmatrix}1&0&0\\0&1&0\\0&0&2\end{pmatrix},
\qquad
J=\begin{pmatrix}1&1&0\\0&1&0\\0&0&2\end{pmatrix}
$$

tienen el mismo polinomio característico, pero
$\dim E_1(D)=2$ y $\dim E_1(J)=1$. Por tanto, no son semejantes.

## 2. Qué significa diagonalizar

### Definición 2.1. Matriz diagonalizable

Una matriz $A\in\mathbb K^{n\times n}$ es **diagonalizable sobre
$\mathbb K$** si es semejante a una matriz diagonal: existen $P$ invertible y
$D$ diagonal tales que

$$
\boxed{A=PDP^{-1}.}
$$

La precisión “sobre $\mathbb K$” importa. Una rotación real no trivial no es
diagonalizable sobre $\mathbb R$, aunque sí puede serlo sobre $\mathbb C$.

### Teorema 2.2. Base de vectores propios

**Enunciado.** Una matriz $A$ es diagonalizable si y solo si
$\mathbb K^n$ posee una base formada por vectores propios de $A$.

**Prueba.** Supongamos que
$\mathcal B=(v_1,\ldots,v_n)$ es una base de vectores propios, con
$Av_j=\lambda_jv_j$. Si

$$
P=\begin{pmatrix}v_1&\cdots&v_n\end{pmatrix},
\qquad
D=\operatorname{diag}(\lambda_1,\ldots,\lambda_n),
$$

entonces $AP=PD$. Como $P$ es invertible, $A=PDP^{-1}$.

Recíprocamente, si $A=PDP^{-1}$, entonces $AP=PD$. Al comparar columnas, cada
columna de $P$ es un vector propio de $A$ asociado a la entrada correspondiente
de $D$. Como $P$ es invertible, sus columnas forman una base. $\square$

## 3. Criterios de diagonalización

Supondremos en esta sección que el polinomio característico de $A$ se
descompone completamente sobre $\mathbb K$:

$$
\chi_A(t)=\prod_{i=1}^r(t-\lambda_i)^{m_a(\lambda_i)},
$$

donde $\lambda_1,\ldots,\lambda_r$ son distintos.

### Teorema 3.1. Criterio por espacios propios

**Enunciado.** Son equivalentes:

1. $A$ es diagonalizable;
2. $\mathbb K^n=E_{\lambda_1}\oplus\cdots\oplus E_{\lambda_r}$;
3. $\sum_{i=1}^r m_g(\lambda_i)=n$;
4. $m_g(\lambda_i)=m_a(\lambda_i)$ para todo $i$.

**Prueba.** Los espacios propios correspondientes a valores distintos forman
una suma directa porque sus bases reunidas son linealmente independientes.
Por tanto, existe una base completa de vectores propios si y solo si la suma de
sus dimensiones es $n$. Esto prueba la equivalencia de 1, 2 y 3.

Además, $1\leq m_g(\lambda_i)\leq m_a(\lambda_i)$ y
$\sum_i m_a(\lambda_i)=n$. En consecuencia,
$\sum_i m_g(\lambda_i)=n$ si y solo si todas las desigualdades son igualdades.
$\square$

### Corolario 3.2. Valores propios distintos

**Enunciado.** Si $A$ tiene $n$ valores propios distintos en $\mathbb K$,
entonces es diagonalizable sobre $\mathbb K$.

**Prueba.** Los vectores propios asociados a valores distintos son linealmente
independientes, por lo que se obtiene una base de $n$ vectores propios.
$\square$

El recíproco es falso: una matriz diagonal puede tener valores repetidos.

### Teorema 3.3. Criterio por un polinomio sin raíces repetidas

**Enunciado.** $A$ es diagonalizable sobre $\mathbb K$ si y solo si existe un
polinomio

$$
q(t)=\prod_{i=1}^r(t-\lambda_i),
$$

con raíces distintas en $\mathbb K$, tal que $q(A)=0$.

**Idea de prueba.** Si $A=PDP^{-1}$, el producto de los factores
correspondientes a las distintas entradas de $D$ anula a $D$ y, por semejanza,
anula a $A$. Para el recíproco, se construyen polinomios de interpolación que
separan las raíces y descomponen cada vector como suma de vectores de los
núcleos $\ker(A-\lambda_iI)$.

Este criterio suele expresarse diciendo que el **polinomio minimal** de una
matriz diagonalizable se descompone en factores lineales sin repetición.

## 4. Procedimiento para diagonalizar

### Algoritmo 4.1

1. Calcular y factorizar $\chi_A(t)$.
2. Verificar que se descompone sobre el cuerpo de trabajo.
3. Para cada valor propio $\lambda$, hallar $m_a(\lambda)$, una base de
   $E_\lambda=\ker(A-\lambda I)$ y $m_g(\lambda)=\dim E_\lambda$.
4. Si algún $m_g(\lambda)<m_a(\lambda)$, detenerse: $A$ no es diagonalizable.
5. Reunir las bases de todos los espacios propios como columnas de $P$.
6. Colocar en $D$ los valores propios en el mismo orden que sus vectores.
7. Verificar $AP=PD$ y, equivalentemente, $P^{-1}AP=D$.

### Ejemplo 4.2. Dos valores propios distintos

Sea

$$
A=\begin{pmatrix}7&1\\2&8\end{pmatrix}.
$$

Su polinomio característico es $\chi_A(t)=(t-6)(t-9)$. Podemos escoger

$$
v_6=\begin{pmatrix}-1\\1\end{pmatrix},
\qquad
v_9=\begin{pmatrix}1\\2\end{pmatrix}.
$$

Entonces

$$
P=\begin{pmatrix}-1&1\\1&2\end{pmatrix},
\qquad
D=\begin{pmatrix}6&0\\0&9\end{pmatrix},
$$

y $AP=PD$, por lo que $A=PDP^{-1}$.

### Ejemplo 4.3. Un valor repetido que sí permite diagonalizar

Sea

$$
S=\begin{pmatrix}
2&1&1\\
1&2&1\\
1&1&2
\end{pmatrix}.
$$

Sus valores propios son $1$, con multiplicidad algebraica $2$, y $4$, con
multiplicidad algebraica $1$. Además,

$$
E_1=\operatorname{span}\{(-1,0,1)^T,(-1,1,0)^T\},
\qquad
E_4=\operatorname{span}\{(1,1,1)^T\}.
$$

Como $m_g(1)=2=m_a(1)$ y $m_g(4)=1=m_a(4)$, las tres columnas reunidas forman
una matriz invertible $P$ y $S=PDP^{-1}$ con
$D=\operatorname{diag}(1,1,4)$.

En C19 retomaremos este ejemplo para elegir una base **ortonormal** y obtener
una diagonalización ortogonal.

### Ejemplo 4.4. Una matriz que no es diagonalizable

Para

$$
B=\begin{pmatrix}4&1&0\\0&4&0\\0&0&2\end{pmatrix},
$$

$m_a(4)=2$, pero
$E_4(B)=\operatorname{span}\{e_1\}$ tiene dimensión $1$. Falta una dirección
propia asociada a $4$; por tanto, $B$ no es diagonalizable.

## 5. La diagonalización no es única

Aunque una matriz sea diagonalizable, $P$ y $D$ no son únicos:

1. se pueden reordenar las columnas de $P$ si se reordenan de la misma manera
   las entradas de $D$;
2. cada vector propio puede multiplicarse por un escalar no nulo;
3. si un espacio propio tiene dimensión mayor que uno, puede elegirse cualquier
   base de ese espacio.

La información esencial es la descomposición del espacio en espacios propios,
no una matriz $P$ particular.

## 6. Potencias, inversas y funciones de matrices

### Proposición 6.1. Potencias

**Enunciado.** Si $A=PDP^{-1}$, entonces, para todo entero $k\geq0$,

$$
\boxed{A^k=PD^kP^{-1}.}
$$

Si $A$ es invertible, la fórmula también vale para enteros negativos.

**Prueba.** En
$A^2=(PDP^{-1})(PDP^{-1})=PD^2P^{-1}$ se cancelan los factores centrales. La
fórmula general sigue por inducción. $\square$

### Proposición 6.2. Polinomios y funciones

**Enunciado.** Si $A=PDP^{-1}$ y $f$ está definida en los valores propios,
entonces

$$
\boxed{f(A)=P\,f(D)\,P^{-1}},
$$

donde

$$
f(D)=\operatorname{diag}(f(\lambda_1),\ldots,f(\lambda_n)).
$$

Para polinomios, la afirmación se deduce de la Proposición 6.1. La misma
fórmula define funciones como $e^A$ y, cuando se elige una rama apropiada,
raíces o logaritmos de matrices diagonalizables.

### Ejemplo 6.3. Exponencial matricial

Para la matriz del Ejemplo 4.2,

$$
e^{tA}
=P\begin{pmatrix}e^{6t}&0\\0&e^{9t}\end{pmatrix}P^{-1}.
$$

Esta matriz resuelve
$x'(t)=Ax(t)$ mediante $x(t)=e^{tA}x(0)$.

## 7. Proyectores espectrales

Supongamos que $A$ es diagonalizable y tiene valores propios distintos
$\lambda_1,\ldots,\lambda_r$.

### Definición 7.1. Proyector espectral

Definimos

$$
\boxed{
\Pi_i=
\prod_{j\neq i}
\frac{A-\lambda_jI}{\lambda_i-\lambda_j}.
}
$$

Cada $\Pi_i$ es un polinomio en $A$.

### Teorema 7.2. Descomposición espectral general

**Enunciado.** Los proyectores espectrales satisfacen:

1. $\operatorname{Im}(\Pi_i)=E_{\lambda_i}$;
2. $\Pi_i^2=\Pi_i$;
3. $\Pi_i\Pi_j=0$ si $i\neq j$;
4. $\sum_i\Pi_i=I$;
5. $A=\sum_i\lambda_i\Pi_i$;
6. $f(A)=\sum_i f(\lambda_i)\Pi_i$ para todo polinomio $f$.

**Idea de prueba.** Si $v\in E_{\lambda_k}$, sustituir $A$ por $\lambda_k$ en
el polinomio que define $\Pi_i$ produce

$$
\Pi_i v=
\begin{cases}
v,&k=i,\\
0,&k\neq i.
\end{cases}
$$

Como los espacios propios generan todo el espacio, las identidades quedan
determinadas por su acción sobre una base de vectores propios.

:::{admonition} No necesariamente son proyecciones ortogonales
:class: note
Los proyectores $\Pi_i$ son idempotentes, pero en una diagonalización general
no tienen por qué ser autoadjuntos. Para matrices simétricas, C19 mostrará que
los espacios propios son ortogonales y los proyectores espectrales sí son
ortogonales.
:::

### Ejemplo 7.3

Para $A$ con valores propios $6$ y $9$,

$$
\Pi_6=\frac{A-9I}{6-9},
\qquad
\Pi_9=\frac{A-6I}{9-6}.
$$

Entonces

$$
I=\Pi_6+\Pi_9,
\qquad
A=6\Pi_6+9\Pi_9,
$$

y $A^k=6^k\Pi_6+9^k\Pi_9$.

## 8. Dinámica discreta y modos propios

Consideremos $x_{k+1}=Ax_k$. Si $A$ es diagonalizable y
$x_0=c_1v_1+\cdots+c_nv_n$, entonces

$$
\boxed{
x_k=A^kx_0
=c_1\lambda_1^kv_1+\cdots+c_n\lambda_n^kv_n.
}
$$

Cada término es un **modo propio**:

- $|\lambda_i|<1$: el modo decae;
- $|\lambda_i|=1$: permanece acotado en magnitud;
- $|\lambda_i|>1$: crece;
- $\lambda_i<0$: alterna de sentido;
- $\lambda_i$ complejo: combina escala y rotación.

La diagonalización convierte un sistema acoplado en ecuaciones escalares
independientes para las coordenadas propias.

## 9. Ejercicios

1. Verifica directamente $AP=PD$ para
   $A=\begin{pmatrix}7&1\\2&8\end{pmatrix}$,
   $P=\begin{pmatrix}-1&1\\1&2\end{pmatrix}$ y
   $D=\operatorname{diag}(6,9)$. *(Presentación de clase.)*
2. Diagonaliza
   $S=\begin{pmatrix}2&1&1\\1&2&1\\1&1&2\end{pmatrix}$ usando las bases de
   espacios propios dadas en el texto. Verifica $P^{-1}SP=D$.
   *(Presentación de clase.)*
3. Decide si
   $B=\begin{pmatrix}0&1&0\\0&0&1\\0&0&0\end{pmatrix}$ es diagonalizable y
   explica exactamente qué falla. *(PC2 2026-I.)*
4. Para
   $C=\begin{pmatrix}4&1&0\\0&4&0\\0&0&2\end{pmatrix}$, compara
   multiplicidades y calcula $C^5$ sin suponer que es diagonalizable.
   *(PC2 2026-I.)*
5. Construye dos matrices de orden $3$ con valores propios $1,1,2$ que no sean
   semejantes. Justifica usando las dimensiones de sus espacios propios.
   *(Lista PC2 2026-I, adaptado.)*
6. Si $A=PDP^{-1}$, demuestra que
   $(A^2+I)^{-1}=P(D^2+I)^{-1}P^{-1}$ cuando la inversa existe.
   *(Lista PC2 2026-I, generalizado.)*
7. Construye los proyectores $\Pi_6$ y $\Pi_9$ del Ejemplo 7.3 y verifica las
   seis propiedades del Teorema 7.2. *(Elaboración a partir de la presentación
   de clase.)*
8. Sea $x_{k+1}=Ax_k$, con
   $A=P\operatorname{diag}(1/2,3/2)P^{-1}$. Describe qué condiciones sobre
   $x_0$ hacen que $x_k$ converja a cero. *(Elaboración propia.)*
