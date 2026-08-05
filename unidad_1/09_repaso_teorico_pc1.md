# Repaso teórico para la PC1

## Cómo usar esta hoja

Esta hoja reúne definiciones y resultados centrales de la Unidad 1. No
reemplaza las clases: organiza la teoría que debe poder **enunciarse**,
**interpretarse** y, cuando corresponda, **demostrarse**.

Para cada resultado conviene distinguir:

1. las hipótesis;
2. la conclusión;
3. una idea de prueba;
4. un procedimiento o una consecuencia.

El [material de ejercicios](09_preparacion_pc1.md) permite practicar después
de estudiar esta síntesis. El
[laboratorio](09_laboratorio_preparacion_pc1.ipynb) sirve únicamente para
comprobar cálculos.

## 1. Geometría de $\mathbb R^n$

### Definición 1.1. Producto interno usual

Para $x,y\in\mathbb R^n$,

$$
\langle x,y\rangle=x^Ty=\sum_{i=1}^n x_i y_i.
$$

Dos vectores son ortogonales si $\langle x,y\rangle=0$.

### Proposición 1.2. Propiedades del producto interno

**Enunciado.** Para $x,y,z\in\mathbb R^n$ y $\alpha,\beta\in\mathbb R$:

1. **Simetría:** $\langle x,y\rangle=\langle y,x\rangle$.
2. **Linealidad:**
   $\langle\alpha x+\beta y,z\rangle
   =\alpha\langle x,z\rangle+\beta\langle y,z\rangle$.
3. **Positividad:** $\langle x,x\rangle\geq0$.
4. **Definición positiva:** $\langle x,x\rangle=0$ si y solo si $x=0$.

### Definición 1.3. Norma, distancia y ángulo

$$
\|x\|=\sqrt{\langle x,x\rangle},
\qquad
d(x,y)=\|x-y\|.
$$

Si $x,y\neq0$, su ángulo $\theta\in[0,\pi]$ satisface

$$
\cos\theta=\frac{\langle x,y\rangle}{\|x\|\|y\|}.
$$

### Proposición 1.4. Propiedades de la norma

**Enunciado.** Para $x,y\in\mathbb R^n$ y $\lambda\in\mathbb R$:

1. **No negatividad:** $\|x\|\geq0$.
2. **Definición positiva:** $\|x\|=0$ si y solo si $x=0$.
3. **Homogeneidad:** $\|\lambda x\|=|\lambda|\|x\|$.
4. **Desigualdad triangular:** $\|x+y\|\leq\|x\|+\|y\|$.

### Teorema 1.5. Desigualdad de Cauchy–Schwarz

**Enunciado.** Para $x,y\in\mathbb R^n$,

$$
|\langle x,y\rangle|\leq\|x\|\|y\|.
$$

Hay igualdad si y solo si $x$ y $y$ son linealmente dependientes.

**Idea de prueba.** Si $y\neq0$, la cantidad

$$
0\leq\left\|x-\frac{\langle x,y\rangle}{\|y\|^2}y\right\|^2
$$

se expande y se reordena para obtener la desigualdad. Si $y=0$, el resultado
es inmediato.

### Teorema 1.6. Desigualdad triangular

**Enunciado.** $\|x+y\|\leq\|x\|+\|y\|$.

**Prueba.** Usando Cauchy–Schwarz,

$$
\begin{aligned}
\|x+y\|^2
&=\|x\|^2+2\langle x,y\rangle+\|y\|^2\\
&\leq\|x\|^2+2\|x\|\|y\|+\|y\|^2\\
&=(\|x\|+\|y\|)^2.
\end{aligned}
$$

Ambos lados son no negativos, por lo que se puede tomar raíz cuadrada.
$\square$

## 2. Matrices, sistemas y eliminación

Una matriz $A\in\mathbb R^{m\times n}$ define la aplicación lineal

$$
A:\mathbb R^n\to\mathbb R^m,
\qquad x\mapsto Ax.
$$

Sus columnas permiten leer

$$
Ax=x_1A_1+\cdots+x_nA_n.
$$

Así, resolver $Ax=b$ equivale a decidir si $b$ es combinación lineal de las
columnas de $A$.

### Definición 2.1. Operaciones elementales por filas

1. Intercambiar dos filas.
2. Multiplicar una fila por un escalar no nulo.
3. Sumar a una fila un múltiplo de otra.

### Teorema 2.2. Conservación del conjunto solución

**Enunciado.** Las operaciones elementales aplicadas a la matriz aumentada
$[A\mid b]$ no cambian el conjunto solución del sistema.

**Idea de prueba.** Cada operación corresponde a reemplazar una ecuación por
otra equivalente y tiene una operación inversa.

### Definición 2.3. Rango

El rango de una matriz es el número de pivotes de su forma escalonada. También
es la dimensión del espacio generado por sus columnas y la dimensión del
espacio generado por sus filas.

### Teorema 2.4. Criterio de Rouché–Capelli

Para $A\in\mathbb R^{m\times n}$:

1. $Ax=b$ es compatible si y solo si
   $\operatorname{rango}(A)=\operatorname{rango}([A\mid b])$.
2. Si es compatible, tiene solución única si y solo si
   $\operatorname{rango}(A)=n$.
3. Si es compatible y $\operatorname{rango}(A)<n$, tiene infinitas soluciones
   con $n-\operatorname{rango}(A)$ parámetros libres.

## 3. Generación, independencia, base y dimensión

### Definición 3.1. Combinación y espacio generado

Una combinación lineal de $v_1,\ldots,v_k$ es
$\alpha_1v_1+\cdots+\alpha_kv_k$. El conjunto de todas las combinaciones es

$$
\operatorname{span}\{v_1,\ldots,v_k\}.
$$

Es el menor subespacio que contiene a esos vectores.

### Definición 3.2. Independencia lineal

$v_1,\ldots,v_k$ son linealmente independientes si

$$
\alpha_1v_1+\cdots+\alpha_kv_k=0
\quad\Longrightarrow\quad
\alpha_1=\cdots=\alpha_k=0.
$$

Si $A=[v_1\ \cdots\ v_k]$, esto equivale a $\ker(A)=\{0\}$ y a
$\operatorname{rango}(A)=k$.

### Definición 3.3. Base y dimensión

Una base de $V$ es una familia que genera $V$ y es linealmente independiente.
La dimensión de un espacio finito es el número de vectores de cualquiera de
sus bases.

### Teorema 3.4. Unicidad de coordenadas

**Enunciado.** Si $\mathcal B=(v_1,\ldots,v_n)$ es una base, cada $x\in V$
admite una única expresión

$$
x=\alpha_1v_1+\cdots+\alpha_nv_n.
$$

**Prueba.** Si existieran dos expresiones, al restarlas se obtendría una
combinación lineal nula. La independencia de la base obliga a que todos los
coeficientes correspondientes coincidan. $\square$

## 4. Espacios vectoriales y subespacios

Los elementos de un espacio vectorial no tienen que ser columnas: pueden ser
matrices, polinomios o funciones. La estructura depende de las operaciones y
de los axiomas.

### Definición 4.1. Espacio vectorial real

Un conjunto no vacío $V$, con suma y multiplicación por escalares reales, es un
espacio vectorial real si, para $u,v,w\in V$ y
$\lambda,\mu\in\mathbb R$, cumple:

1. $u+v\in V$.
2. $u+v=v+u$.
3. $(u+v)+w=u+(v+w)$.
4. Existe $0_V$ tal que $v+0_V=v$.
5. Para cada $v$ existe $-v$ tal que $v+(-v)=0_V$.
6. $\lambda v\in V$.
7. $(\lambda\mu)v=\lambda(\mu v)$ y $1v=v$.
8. $\lambda(u+v)=\lambda u+\lambda v$ y
   $(\lambda+\mu)v=\lambda v+\mu v$.

Ejemplos: $\mathbb R^n$, $M_{m\times n}(\mathbb R)$,
$\mathcal P_n$ y espacios de funciones reales.

### Teorema 4.2. Criterio de subespacio

**Enunciado.** Un subconjunto no vacío $W\subseteq V$ es subespacio si y solo
si

$$
\alpha u+\beta v\in W
$$

para todos $u,v\in W$ y $\alpha,\beta\in\mathbb R$.

**Idea de prueba.** Una dirección es consecuencia de las cerraduras. En la
otra, elecciones particulares de $\alpha$ y $\beta$ producen el cero, los
inversos, las sumas y los múltiplos escalares.

Consecuencias útiles:

- todo subespacio contiene al vector cero;
- una ecuación lineal homogénea define un subespacio;
- una ecuación lineal no homogénea compatible suele definir un conjunto afín,
  no un subespacio;
- la intersección de subespacios es subespacio;
- la unión de dos subespacios no suele ser subespacio.

## 5. Núcleo, imagen y rango–nulidad

### Definición 5.1. Núcleo e imagen

Para $A\in\mathbb R^{m\times n}$,

$$
\ker(A)=\{x\in\mathbb R^n:Ax=0\},
$$

$$
\operatorname{Im}(A)=\{Ax:x\in\mathbb R^n\}
=\operatorname{Col}(A)\subseteq\mathbb R^m.
$$

El núcleo y la imagen son subespacios de espacios diferentes.

### Teorema 5.2. Rango–nulidad

**Enunciado.** Si $A$ tiene $n$ columnas,

$$
\operatorname{rango}(A)+\operatorname{nulidad}(A)=n.
$$

**Idea de prueba.** Las variables pivote corresponden al rango y las variables
libres generan el núcleo. Cada columna es pivote o libre.

### Teorema 5.3. Estructura de las soluciones

**Enunciado.** Si $Ax=b$ es compatible y $x_p$ es una solución particular,

$$
\{x:Ax=b\}=x_p+\ker(A).
$$

**Prueba.** $Ax=b$ equivale a $A(x-x_p)=0$. Por tanto,
$x-x_p\in\ker(A)$. $\square$

## 6. Determinante e invertibilidad

El determinante se define solo para matrices cuadradas. Es multilineal en las
columnas, alternante y satisface $\det(I)=1$.

```{admonition} Escalar una fila frente a escalar toda la matriz
:class: warning
Multiplicar una sola fila por $\lambda$ multiplica el determinante por
$\lambda$. Si $A$ es $n\times n$, multiplicar **toda** la matriz produce

$$
\det(\lambda A)=\lambda^n\det(A),
$$

porque se han multiplicado sus $n$ filas por $\lambda$.
```

### Proposición 6.1. Operaciones elementales y determinante

1. Intercambiar filas cambia el signo.
2. Multiplicar una fila por $\lambda$ multiplica el determinante por
   $\lambda$.
3. Sumar a una fila un múltiplo de otra no cambia el determinante.

### Teorema 6.2. Producto

**Enunciado.** Para matrices cuadradas del mismo orden,

$$
\det(AB)=\det(A)\det(B).
$$

Si $A$ es invertible, entonces
$\det(A^{-1})=1/\det(A)$.

### Teorema 6.3. Teorema de la matriz invertible

Para $A\in\mathbb R^{n\times n}$, son equivalentes:

1. $A$ es invertible.
2. $\det(A)\neq0$.
3. $\operatorname{rango}(A)=n$.
4. $\operatorname{rref}(A)=I_n$.
5. Las columnas de $A$ son linealmente independientes.
6. Las columnas de $A$ generan $\mathbb R^n$.
7. $\ker(A)=\{0\}$.
8. Para todo $b\in\mathbb R^n$, $Ax=b$ tiene solución única.

```{admonition} La hipótesis cuadrada es esencial
:class: warning
Para una matriz rectangular, tener columnas independientes no implica alcanzar
todo el codominio. Separe siempre inyectividad, sobreyectividad e
invertibilidad.
```

## 7. Conjuntos afines y suma directa

### Definición 7.1. Conjunto afín

Un conjunto no vacío $H$ es afín si contiene todas las combinaciones

$$
(1-t)x+ty,
\qquad x,y\in H,quad t\in\mathbb R.
$$

### Teorema 7.2. Caracterización afín

**Enunciado.** $H$ es afín si y solo si existen un punto $x_0$ y un subespacio
$W$ tales que

$$
H=x_0+W.
$$

Un conjunto afín es subespacio exactamente cuando contiene al vector cero.

### Definición 7.3. Suma de subespacios

$$
U+W=\{u+w:u\in U,\ w\in W\}.
$$

### Teorema 7.4. Criterio de suma directa

**Enunciado.** Son equivalentes:

1. $U+W=U\oplus W$.
2. $U\cap W=\{0\}$.
3. Cada vector de $U+W$ posee una única descomposición $u+w$.

**Prueba.** Si $u_1+w_1=u_2+w_2$, entonces
$u_1-u_2=w_2-w_1\in U\cap W$. La intersección trivial equivale a que ambas
diferencias sean cero. $\square$

### Teorema 7.5. Fórmula de dimensión

**Enunciado.** En dimensión finita,

$$
\dim(U+W)=\dim U+\dim W-\dim(U\cap W).
$$

En particular, si la suma es directa,
$\dim(U\oplus W)=\dim U+\dim W$.

## 8. Coordenadas y cambio de base

Sea $\mathcal B=(v_1,\ldots,v_n)$ una base. Si
$x=\alpha_1v_1+\cdots+\alpha_nv_n$, definimos

$$
[x]_{\mathcal B}=(\alpha_1,\ldots,\alpha_n)^T.
$$

$x$ es el vector; $[x]_{\mathcal B}$ es una columna que depende de la base.

### Proposición 8.1. Matriz de una base

En $\mathbb R^n$, si
$M_{\mathcal B}=[v_1\ \cdots\ v_n]$, entonces

$$
x=M_{\mathcal B}[x]_{\mathcal B},
\qquad
[x]_{\mathcal B}=M_{\mathcal B}^{-1}x.
$$

### Teorema 8.2. Cambio de base

**Enunciado.** Para bases $\mathcal B$ y $\mathcal C$,

$$
[x]_{\mathcal C}
=P_{\mathcal B\to\mathcal C}[x]_{\mathcal B},
\qquad
P_{\mathcal B\to\mathcal C}
=M_{\mathcal C}^{-1}M_{\mathcal B}.
$$

La columna $j$ de $P_{\mathcal B\to\mathcal C}$ es
$[v_j]_{\mathcal C}$.

Propiedades:

1. $P_{\mathcal B\to\mathcal B}=I$.
2. $P_{\mathcal C\to\mathcal B}=P_{\mathcal B\to\mathcal C}^{-1}$.
3. $P_{\mathcal B\to\mathcal D}
   =P_{\mathcal C\to\mathcal D}P_{\mathcal B\to\mathcal C}$.

### Teorema 8.3. Matriz relativa de una transformación

Si $A$ representa $T:\mathbb R^n\to\mathbb R^m$ en bases canónicas, entonces

$$
[T]_{\mathcal C\leftarrow\mathcal B}
=M_{\mathcal C}^{-1}AM_{\mathcal B}.
$$

La dirección de las flechas ayuda a ordenar los factores.

## 9. Red de equivalencias y distinciones

### Para una matriz rectangular

$$
\begin{aligned}
\text{columnas LI}
&\Longleftrightarrow \ker(A)=\{0\}\\
&\Longleftrightarrow \operatorname{rango}(A)=n,
\end{aligned}
$$

pero esto no garantiza que $Ax=b$ sea compatible para todo $b$ si $m>n$.

### Para una matriz cuadrada

Las condiciones anteriores equivalen además a invertibilidad, determinante no
nulo, generación de todo el espacio y solución única para cada término
independiente.

### No confundir

| Conceptos | Diferencia |
|---|---|
| RREF y matriz original | Tienen el mismo espacio fila, pero no necesariamente el mismo espacio columna |
| Subespacio y conjunto afín | El subespacio contiene al cero; una traslación no necesariamente |
| Generar y ser independiente | Generar evita que falten direcciones; independencia evita redundancias |
| $x$ y $[x]_{\mathcal B}$ | El primero es el vector; el segundo depende del sistema de coordenadas |
| $U+W$ y $U\oplus W$ | La segunda exige unicidad, equivalente a intersección trivial |
| Cálculo y prueba | Un ejemplo verifica un caso; no demuestra un enunciado universal |

## 10. Resultados que conviene poder demostrar

Antes de la PC1, practica sin consultar las notas:

1. Cauchy–Schwarz a partir de una norma cuadrática no negativa.
2. Desigualdad triangular a partir de Cauchy–Schwarz.
3. Criterio de subespacio.
4. Independencia de una familia ortogonal de vectores no nulos.
5. Unicidad de coordenadas respecto de una base.
6. Estructura $x_p+\ker(A)$ del conjunto solución.
7. Criterio $U\cap W=\{0\}$ para una suma directa.
8. Fórmula de cambio de base siguiendo las coordenadas de entrada y salida.

En una prueba, escribe primero el **enunciado** y después la **prueba** o la
**idea de prueba**. No mezcles el resultado que se desea demostrar con los
pasos usados para obtenerlo.
