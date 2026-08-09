# Vectores, geometría de $\mathbb R^n$, matrices y sistemas

Esta hoja reúne la teoría necesaria para las dos primeras clases. El cuaderno
asociado se reserva para cálculos, visualizaciones y experimentos.

## Objetivos

Al terminar este bloque podrás:

- operar con vectores de $\mathbb R^n$ y matrices reales;
- interpretar norma, distancia, producto punto y ángulo;
- aplicar la desigualdad de Cauchy-Schwarz;
- reconocer la compatibilidad dimensional de productos matriciales;
- usar las propiedades algebraicas del producto matricial y operar por bloques;
- escribir un sistema lineal como $Ax=b$;
- resolver sistemas diagonales y triangulares.

## 1. Vectores en $\mathbb R^n$

El espacio $\mathbb R^n$ es el conjunto de todas las listas ordenadas de $n$
números reales:

$$
\mathbb R^n=\{(x_1,\ldots,x_n):x_i\in\mathbb R\}.
$$

Dos vectores son iguales si coinciden componente a componente. Aunque podamos
escribir un vector como fila, cuando lo usemos en productos matriciales lo
representaremos como columna:

$$
x=\begin{bmatrix}x_1\\ \vdots\\ x_n\end{bmatrix}.
$$

### Suma y multiplicación por escalares

Si $x,y\in\mathbb R^n$ y $\alpha\in\mathbb R$, definimos

$$
x+y=(x_1+y_1,\ldots,x_n+y_n),
\qquad
\alpha x=(\alpha x_1,\ldots,\alpha x_n).
$$

Para $x,y,z\in\mathbb R^n$ y $\alpha,\beta\in\mathbb R$, estas operaciones
satisfacen:

1. **asociatividad de la suma:** $(x+y)+z=x+(y+z)$;
2. **conmutatividad de la suma:** $x+y=y+x$;
3. **vector cero:** existe $0=(0,\ldots,0)$ tal que $x+0=x$;
4. **inverso aditivo:** existe $-x$ tal que $x+(-x)=0$;
5. **compatibilidad de escalares:** $\alpha(\beta x)=(\alpha\beta)x$;
6. **identidad escalar:** $1x=x$;
7. **distributividad respecto de vectores:**
   $\alpha(x+y)=\alpha x+\alpha y$;
8. **distributividad respecto de escalares:**
   $(\alpha+\beta)x=\alpha x+\beta x$.

Además, definimos la resta mediante $x-y=x+(-y)$.

### Múltiplos y paralelismo

Dos vectores no nulos $x$ e $y$ son paralelos si uno es múltiplo escalar del
otro. Es decir, existe $\alpha\in\mathbb R$ tal que $y=\alpha x$.

- Si $\alpha>0$, tienen la misma orientación.
- Si $\alpha<0$, tienen orientaciones opuestas.
- El valor $|\alpha|$ describe el cambio de longitud.

## 2. Norma, distancia y vectores unitarios

### Definición 2.1. Norma euclidiana

La **norma euclidiana** de $x\in\mathbb R^n$ es el número real

$$
\|x\|=\sqrt{x_1^2+\cdots+x_n^2}.
$$

Geométricamente, $\|x\|$ representa la longitud del vector $x$.

### Proposición 2.2. Propiedades de la norma

Para todos $x,y\in\mathbb R^n$ y $\alpha\in\mathbb R$, se cumplen las
siguientes propiedades:

1. **No negatividad:** $\|x\|\geq0$.
2. **Definición positiva:** $\|x\|=0\Longleftrightarrow x=0$.
3. **Homogeneidad absoluta:** $\|\alpha x\|=|\alpha|\,\|x\|$.
4. **Desigualdad triangular:** $\|x+y\|\leq\|x\|+\|y\|$.

La propiedad 4 requiere la desigualdad de Cauchy-Schwarz y se probará en el
Teorema 3.5.

#### Verificación de las propiedades 1-3

**Propiedad 1.** Como cada $x_i^2\geq0$, tenemos
$x_1^2+\cdots+x_n^2\geq0$. Su raíz cuadrada también es no negativa.

**Propiedad 2.** La igualdad $\|x\|=0$ equivale a

$$
x_1^2+\cdots+x_n^2=0.
$$

Una suma de cuadrados de números reales es cero solamente cuando cada término
es cero. Por tanto, $x_1=\cdots=x_n=0$, es decir, $x=0$. La implicación inversa
es inmediata.

**Propiedad 3.** Por definición,

$$
\begin{aligned}
\|\alpha x\|
&=\sqrt{(\alpha x_1)^2+\cdots+(\alpha x_n)^2}\\
&=\sqrt{\alpha^2}\sqrt{x_1^2+\cdots+x_n^2}\\
&=|\alpha|\,\|x\|.
\end{aligned}
$$

### Definición 2.3. Distancia euclidiana

La **distancia euclidiana** entre $x$ e $y$ es la norma de su diferencia:

$$
d(x,y)=\|x-y\|.
$$

### Proposición 2.4. Propiedades de la distancia

Para todos $x,y,z\in\mathbb R^n$:

1. $d(x,y)\geq0$;
2. $d(x,y)=0$ si y solo si $x=y$;
3. $d(x,y)=d(y,x)$;
4. $d(x,z)\leq d(x,y)+d(y,z)$.

#### Idea de prueba

Las tres primeras propiedades se deducen de las propiedades 1-3 de la norma.
Para la cuarta, se escribe

$$
x-z=(x-y)+(y-z)
$$

y se aplica la desigualdad triangular de la norma.

### Definición 2.5. Normalización

Si $x\ne0$, la **normalización** de $x$ es

$$
\widehat x=\frac{x}{\|x\|}.
$$

Por homogeneidad,

$$
\|\widehat x\|
=\left\|\frac{1}{\|x\|}x\right\|
=\frac{1}{\|x\|}\|x\|=1.
$$

Además, $x=\|x\|\widehat x$. Un vector de norma uno se llama **unitario**. El
vector cero no puede normalizarse porque la expresión exigiría dividir entre
$\|0\|=0$.

## 3. Producto punto y ángulos

### Definición 3.1. Producto punto

El **producto punto** o producto interno usual de $x,y\in\mathbb R^n$ es

$$
\langle x,y\rangle=x^Ty=\sum_{i=1}^n x_i y_i.
$$

### Proposición 3.2. Propiedades del producto punto

Para $x,y,z\in\mathbb R^n$ y $\alpha,\beta\in\mathbb R$:

1. **Simetría:**

$$
\langle x,y\rangle=\langle y,x\rangle,
$$

2. **Linealidad en la primera variable:**

$$
\langle \alpha x+\beta z,y\rangle
=\alpha\langle x,y\rangle+\beta\langle z,y\rangle,
$$

3. **Linealidad en la segunda variable:**

$$
\langle x,\alpha y+\beta z\rangle
=\alpha\langle x,y\rangle+\beta\langle x,z\rangle,
$$

4. **No negatividad:**

$$
\langle x,x\rangle\geq0,
$$

5. **Definición positiva:**

$$
\langle x,x\rangle=0\Longleftrightarrow x=0.
$$

#### Verificación

Las propiedades 1-3 se obtienen distribuyendo productos y sumas componente a
componente. Las propiedades 4 y 5 se deducen de

$$
\langle x,x\rangle=x_1^2+\cdots+x_n^2.
$$

En particular, la norma se recupera del producto punto:

$$
\|x\|=\sqrt{\langle x,x\rangle}.
$$

### Teorema 3.3. Desigualdad de Cauchy-Schwarz


Para todo $x,y\in\mathbb R^n$,

$$
|\langle x,y\rangle|\leq \|x\|\,\|y\|.
$$

Además, hay igualdad si y solo si $x$ e $y$ son linealmente dependientes.

#### Prueba

Si $y=0$, ambos lados son cero y la desigualdad es inmediata. Supongamos ahora
que $y\ne0$. Para todo $t\in\mathbb R$,

$$
f(t)=\|x-ty\|^2\geq0.
$$

Al usar las propiedades del producto punto,

$$
f(t)=\|x\|^2-2t\langle x,y\rangle+t^2\|y\|^2.
$$

Esta función cuadrática alcanza su mínimo en

$$
t_*=\frac{\langle x,y\rangle}{\|y\|^2}.
$$

Como $f(t_*)\geq0$,

$$
0\leq
\|x\|^2-\frac{\langle x,y\rangle^2}{\|y\|^2}.
$$

Multiplicando por $\|y\|^2>0$ obtenemos

$$
\langle x,y\rangle^2\leq\|x\|^2\|y\|^2.
$$

Al tomar raíces cuadradas se concluye que

$$
|\langle x,y\rangle|\leq\|x\|\|y\|.
$$

Hay igualdad exactamente cuando $f(t_*)=0$, es decir, cuando
$x-t_*y=0$. Esto equivale a que $x$ es múltiplo de $y$. El caso $y=0$ también
corresponde a dependencia lineal.

### Definición 3.4. Ángulo entre vectores

Si $x$ e $y$ son no nulos, Cauchy-Schwarz garantiza que

$$
-1\leq\frac{\langle x,y\rangle}{\|x\|\|y\|}\leq1.
$$

Por ello podemos definir el ángulo $\theta\in[0,\pi]$ mediante

$$
\cos\theta=\frac{\langle x,y\rangle}{\|x\|\|y\|}.
$$

El signo del producto punto permite anticipar el tipo de ángulo:

| Condición | Interpretación |
|---|---|
| $\langle x,y\rangle>0$ | ángulo agudo |
| $\langle x,y\rangle=0$ | ángulo recto |
| $\langle x,y\rangle<0$ | ángulo obtuso |

Cuando $\langle x,y\rangle=0$, decimos que $x$ e $y$ son **ortogonales** y
escribimos $x\perp y$.

### Teorema 3.5. Desigualdad triangular


Para todos $x,y\in\mathbb R^n$,

$$
\|x+y\|\leq\|x\|+\|y\|.
$$

Además, hay igualdad si y solo si uno de los vectores es cero o existe
$\lambda\geq0$ tal que $y=\lambda x$.

#### Prueba

Usando Cauchy-Schwarz,

$$
\begin{aligned}
\|x+y\|^2
&=\|x\|^2+2\langle x,y\rangle+\|y\|^2\\
&\leq \|x\|^2+2|\langle x,y\rangle|+\|y\|^2\\
&\leq \|x\|^2+2\|x\|\|y\|+\|y\|^2\\
&=(\|x\|+\|y\|)^2.
\end{aligned}
$$

Ambos lados son no negativos; por tanto, podemos tomar raíces cuadradas y
obtener

$$
\|x+y\|\leq\|x\|+\|y\|.
$$

Para que haya igualdad deben ocurrir simultáneamente
$\langle x,y\rangle\geq0$ y la igualdad en Cauchy-Schwarz. Esto sucede cuando
los vectores tienen la misma dirección, incluyendo los casos en que alguno es
cero.

### Corolario 3.6. Desigualdad triangular inversa


Para todos $x,y\in\mathbb R^n$,

$$
\big|\|x\|-\|y\|\big|\leq\|x-y\|.
$$

#### Prueba

Por la desigualdad triangular,

$$
\|x\|=\|(x-y)+y\|\leq\|x-y\|+\|y\|,
$$

de donde $\|x\|-\|y\|\leq\|x-y\|$. Intercambiando $x$ e $y$ obtenemos
$\|y\|-\|x\|\leq\|x-y\|$. Las dos desigualdades juntas producen el resultado.

## 4. Matrices

Una matriz real de $m$ filas y $n$ columnas es un arreglo

$$
A=[a_{ij}]\in\mathbb R^{m\times n}.
$$

El primer índice identifica la fila y el segundo la columna. Dos matrices son
iguales si tienen las mismas dimensiones y sus entradas correspondientes son
iguales.

### Operaciones básicas

Si $A,B\in\mathbb R^{m\times n}$ y $\alpha\in\mathbb R$,

$$
(A+B)_{ij}=a_{ij}+b_{ij},
\qquad
(\alpha A)_{ij}=\alpha a_{ij}.
$$

### Producto matriz-vector

Si $A\in\mathbb R^{m\times n}$ y $x\in\mathbb R^n$, entonces

$$
Ax\in\mathbb R^m.
$$

Si las columnas de $A$ son $a_1,\ldots,a_n$, el producto puede interpretarse
como

$$
Ax=x_1a_1+\cdots+x_na_n.
$$

Esta interpretación conectará posteriormente sistemas lineales, combinaciones
lineales y espacios generados.

### Producto de matrices

Si $A\in\mathbb R^{m\times n}$ y $B\in\mathbb R^{n\times p}$, el producto
$AB\in\mathbb R^{m\times p}$ se define por

$$
(AB)_{ij}=\sum_{k=1}^n a_{ik}b_{kj}.
$$

Las dimensiones interiores deben coincidir:

$$
(m\times n)(n\times p)=m\times p.
$$

```{admonition} El producto matricial no es conmutativo
:class: warning
Aunque $AB$ y $BA$ estén ambos definidos y tengan el mismo tamaño, en general
$AB\neq BA$. Por ejemplo, si

$$
A=\begin{bmatrix}1&1\\0&1\end{bmatrix},
\qquad
B=\begin{bmatrix}1&0\\1&1\end{bmatrix},
$$

entonces

$$
AB=\begin{bmatrix}2&1\\1&1\end{bmatrix},
\qquad
BA=\begin{bmatrix}1&1\\1&2\end{bmatrix}.
$$

Además, para matrices rectangulares puede ocurrir que uno de los productos ni
siquiera esté definido. Por tanto, nunca debe cambiarse el orden de los
factores sin una justificación específica.
```

### Definición 4.1. Matriz identidad

La **matriz identidad de orden $n$** es la matriz cuadrada

$$
I_n=
\begin{bmatrix}
1&0&\cdots&0\\
0&1&\cdots&0\\
\vdots&\vdots&\ddots&\vdots\\
0&0&\cdots&1
\end{bmatrix}
=[\delta_{ij}]_{i,j=1}^n,
$$

donde $\delta_{ij}$ es la **delta de Kronecker**:

$$
\delta_{ij}=
\begin{cases}
1,& i=j,\\
0,& i\neq j.
\end{cases}
$$

Si $A\in\mathbb R^{m\times n}$, las identidades que pueden multiplicarla son
$I_m\in\mathbb R^{m\times m}$ por la izquierda e
$I_n\in\mathbb R^{n\times n}$ por la derecha. Se cumple
$I_mA=A=AI_n$. Asimismo, $I_nx=x$ para todo $x\in\mathbb R^n$.

### Proposición 4.2. Propiedades algebraicas de las matrices

Siempre que las dimensiones hagan que las operaciones estén definidas, se
cumplen las siguientes propiedades:

1. **Asociatividad de la suma:** $(A+B)+C=A+(B+C)$.
2. **Conmutatividad de la suma:** $A+B=B+A$.
3. **Matriz cero y opuesto:** $A+0=A$ y $A+(-A)=0$.
4. **Reglas para escalares:** $\alpha(A+B)=\alpha A+\alpha B$,
   $(\alpha+\beta)A=\alpha A+\beta A$,
   $\alpha(\beta A)=(\alpha\beta)A$ y $1A=A$.
5. **Distributividad respecto de la suma de matrices:**
   $A(B+C)=AB+AC$.
6. **Distributividad por el otro lado:** $(A+B)C=AC+BC$.
7. **Asociatividad del producto:** $(AB)C=A(BC)$.
8. **Compatibilidad del producto con escalares:**
   $\alpha(AB)=(\alpha A)B=A(\alpha B)$.

Las propiedades 5--7 son fundamentales: permiten expandir, reagrupar y
factorizar productos matriciales sin modificar el orden de los factores. No se
puede, en cambio, intercambiarlos como si fueran números, pues generalmente
$AB\neq BA$.

**Idea de prueba de la asociatividad.** Si
$A\in\mathbb R^{m\times n}$, $B\in\mathbb R^{n\times p}$ y
$C\in\mathbb R^{p\times q}$, entonces

$$
\begin{aligned}
((AB)C)_{ij}
&=\sum_{\ell=1}^{p}\left(\sum_{k=1}^{n}a_{ik}b_{k\ell}\right)c_{\ell j}\\
&=\sum_{k=1}^{n}a_{ik}\left(\sum_{\ell=1}^{p}b_{k\ell}c_{\ell j}\right)
=(A(BC))_{ij}.
\end{aligned}
$$

La igualdad se obtiene reagrupando productos de números reales y cambiando el
orden de dos sumas finitas. Las distributividades se verifican de forma
análoga, entrada por entrada.

### Teorema 4.3. Multiplicación de matrices por bloques

Sea $A\in\mathbb R^{m\times p}$ dividida en $q$ filas de bloques y $s$
columnas de bloques:

$$
A=
\begin{bmatrix}
A_{11}&A_{12}&\cdots&A_{1s}\\
A_{21}&A_{22}&\cdots&A_{2s}\\
\vdots&\vdots&\ddots&\vdots\\
A_{q1}&A_{q2}&\cdots&A_{qs}
\end{bmatrix},
\qquad
A_{ij}\in\mathbb R^{m_i\times p_j},
$$

donde $m_1+\cdots+m_q=m$ y $p_1+\cdots+p_s=p$. Sea también
$B\in\mathbb R^{p\times n}$ dividida en $s$ filas de bloques y $r$
columnas de bloques:

$$
B=
\begin{bmatrix}
B_{11}&B_{12}&\cdots&B_{1r}\\
B_{21}&B_{22}&\cdots&B_{2r}\\
\vdots&\vdots&\ddots&\vdots\\
B_{s1}&B_{s2}&\cdots&B_{sr}
\end{bmatrix},
\qquad
B_{jk}\in\mathbb R^{p_j\times n_k},
$$

donde $n_1+\cdots+n_r=n$. Estas particiones son **conformables** porque el
ancho $p_j$ de la $j$-ésima columna de bloques de $A$ coincide con la altura
$p_j$ de la $j$-ésima fila de bloques de $B$.

Entonces $C=AB\in\mathbb R^{m\times n}$ puede calcularse por bloques. Su
partición tiene $q$ filas y $r$ columnas de bloques,

$$
C=
\begin{bmatrix}
C_{11}&C_{12}&\cdots&C_{1r}\\
C_{21}&C_{22}&\cdots&C_{2r}\\
\vdots&\vdots&\ddots&\vdots\\
C_{q1}&C_{q2}&\cdots&C_{qr}
\end{bmatrix},
\qquad
C_{ik}\in\mathbb R^{m_i\times n_k},
$$

y cada bloque se obtiene mediante

$$
\boxed{C_{ik}=\sum_{j=1}^{s}A_{ij}B_{jk}},
\qquad
i=1,\ldots,q,
\quad k=1,\ldots,r.
$$

**Idea de prueba.** La fórmula usual del producto se aplica a las filas de $A$
y las columnas de $B$. Al agrupar el índice interior según las $s$ particiones
de tamaños $p_1,\ldots,p_s$, cada grupo de sumandos es precisamente el
producto $A_{ij}B_{jk}$.

En el caso de dos filas y dos columnas de bloques, el resultado toma la forma

$$
\begin{bmatrix}A&B\\ C&D\end{bmatrix}
\begin{bmatrix}E&F\\ G&H\end{bmatrix}
=
\begin{bmatrix}
AE+BG&AF+BH\\
CE+DG&CF+DH
\end{bmatrix},
$$

siempre que todos los productos indicados estén definidos. Las líneas que
separan bloques no bastan por sí solas: la conformabilidad de las particiones
es indispensable.

### Definición 4.4. Matriz transpuesta

La **transpuesta** de $A=[a_{ij}]\in\mathbb R^{m\times n}$ es la matriz
$A^T\in\mathbb R^{n\times m}$ definida por $(A^T)_{ij}=a_{ji}$.

### Proposición 4.5. Propiedades de la transposición

Para matrices de dimensiones compatibles y $\alpha\in\mathbb R$:

1. **Transpuesta de una transpuesta:** $(A^T)^T=A$.
2. **Transpuesta de una suma:** $(A+B)^T=A^T+B^T$.
3. **Compatibilidad con escalares:** $(\alpha A)^T=\alpha A^T$.
4. **Transpuesta de un producto:** $(AB)^T=B^TA^T$.

En la última propiedad se invierte el orden de los factores.

### Definición 4.6. Matriz invertible e inversa

Una matriz cuadrada $A\in\mathbb R^{n\times n}$ es **invertible** si existe
$B\in\mathbb R^{n\times n}$ tal que

$$
AB=BA=I_n.
$$

Una matriz $B$ con esta propiedad se llama una **inversa** de $A$.

### Proposición 4.7. Unicidad de la inversa

Si $A$ es invertible, su inversa es única y se denota por $A^{-1}$.

**Prueba.** Si $B$ y $C$ son inversas de $A$, entonces
$B=B(AC)=(BA)C=C$. $\square$

### Proposición 4.8. Sistemas con matriz invertible

Si $A\in\mathbb R^{n\times n}$ es invertible, entonces, para cada
$b\in\mathbb R^n$, el sistema $Ax=b$ tiene la única solución
$x=A^{-1}b$.

**Prueba.** El vector $A^{-1}b$ es solución porque
$A(A^{-1}b)=(AA^{-1})b=b$. Si $y$ es cualquier solución, entonces
$y=A^{-1}(Ay)=A^{-1}b$. $\square$

Esta proposición es conceptualmente importante, pero no se recomienda calcular
$A^{-1}$ para resolver cada sistema. La eliminación y las factorizaciones
matriciales suelen ser procedimientos más eficientes y numéricamente más
estables. Más adelante relacionaremos invertibilidad, pivotes, determinante,
núcleo y rango.

## 5. Sistemas de ecuaciones lineales

Un sistema lineal de $m$ ecuaciones y $n$ incógnitas tiene la forma

$$
\begin{aligned}
a_{11}x_1+a_{12}x_2+\cdots+a_{1n}x_n&=b_1,\\
a_{21}x_1+a_{22}x_2+\cdots+a_{2n}x_n&=b_2,\\
&\ \vdots\\
a_{m1}x_1+a_{m2}x_2+\cdots+a_{mn}x_n&=b_m.
\end{aligned}
$$

En forma matricial se escribe

$$
Ax=b,
$$

donde

$$
A=
\begin{bmatrix}
a_{11}&a_{12}&\cdots&a_{1n}\\
a_{21}&a_{22}&\cdots&a_{2n}\\
\vdots&\vdots&&\vdots\\
a_{m1}&a_{m2}&\cdots&a_{mn}
\end{bmatrix}
\in\mathbb R^{m\times n},
$$

$$
x=\begin{bmatrix}x_1\\x_2\\\vdots\\x_n\end{bmatrix}
\in\mathbb R^n,
\qquad
b=\begin{bmatrix}b_1\\b_2\\\vdots\\b_m\end{bmatrix}
\in\mathbb R^m.
$$

La fila $i$ de $A$ contiene los coeficientes de la ecuación $i$. La columna
$j$ contiene el efecto de la incógnita $x_j$ sobre todas las ecuaciones.

Usando las columnas $a_1,\ldots,a_n$ de $A$, el sistema también expresa el
problema de combinación lineal

$$
x_1a_1+\cdots+x_na_n=b.
$$

La matriz aumentada del sistema es

$$
[A\mid b]=
\left[
\begin{array}{cccc|c}
a_{11}&a_{12}&\cdots&a_{1n}&b_1\\
a_{21}&a_{22}&\cdots&a_{2n}&b_2\\
\vdots&\vdots&&\vdots&\vdots\\
a_{m1}&a_{m2}&\cdots&a_{mn}&b_m
\end{array}
\right].
$$

Manipular simultáneamente las filas de $A$ y las entradas de $b$ equivale a
trabajar directamente con $[A\mid b]$.

### Definición 5.1. Matriz diagonal, sistemas diagonales y notación $\operatorname{diag}$

Dados $d_1,\ldots,d_n\in\mathbb R$, se define

$$
\operatorname{diag}(d_1,\ldots,d_n)
=
\begin{bmatrix}
d_1&0&\cdots&0\\
0&d_2&\cdots&0\\
\vdots&\vdots&\ddots&\vdots\\
0&0&\cdots&d_n
\end{bmatrix}.
$$

Una matriz cuadrada es **diagonal** si todas sus entradas fuera de la diagonal
principal son cero; es decir, si tiene esta forma para ciertos
$d_1,\ldots,d_n$.

Un sistema diagonal tiene la forma

$$
\begin{aligned}
a_{11}x_1&=b_1,\\
a_{22}x_2&=b_2,\\
&\ \vdots\\
a_{nn}x_n&=b_n.
\end{aligned}
$$

Este sistema corresponde a
$A=\operatorname{diag}(a_{11},\ldots,a_{nn})$. Si todas las entradas
diagonales son no nulas, la solución es

$$
x_i=\frac{b_i}{a_{ii}},
\qquad i=1,\ldots,n.
$$

Si algún $a_{ii}=0$, debemos examinar la ecuación correspondiente:

- $0x_i=b_i\ne0$ hace que el sistema sea incompatible;
- $0x_i=0$ deja $x_i$ libre y, por sí sola, no determina una solución única.

### Definición 5.2. Matrices triangulares y sistemas triangulares

Una matriz $U=[u_{ij}]$ es **triangular superior** si $u_{ij}=0$ cuando $i>j$;
es decir, todas las entradas situadas debajo de la diagonal principal son cero:

$$
U=
\begin{bmatrix}
u_{11}&u_{12}&\cdots&u_{1n}\\
0&u_{22}&\cdots&u_{2n}\\
\vdots&\ddots&\ddots&\vdots\\
0&\cdots&0&u_{nn}
\end{bmatrix}.
$$

El sistema $Ux=b$ se resuelve desde la última ecuación mediante
**sustitución hacia atrás**. Si $u_{ii}\ne0$ para todo $i$,

$$
x_n=\frac{b_n}{u_{nn}},
$$

y luego, para $j=n-1,n-2,\ldots,1$,

$$
x_j=\frac{b_j-\displaystyle\sum_{k=j+1}^n u_{jk}x_k}{u_{jj}}.
$$

Una matriz $L=[\ell_{ij}]$ es **triangular inferior** si $\ell_{ij}=0$ cuando
$i<j$; es decir, todas las entradas situadas encima de la diagonal principal
son cero:

$$
L=
\begin{bmatrix}
\ell_{11}&0&\cdots&0\\
\ell_{21}&\ell_{22}&\ddots&\vdots\\
\vdots&\ddots&\ddots&0\\
\ell_{n1}&\cdots&\ell_{n,n-1}&\ell_{nn}
\end{bmatrix}.
$$

El sistema $Lx=b$ se resuelve desde la primera ecuación mediante
**sustitución hacia adelante**. Si $\ell_{ii}\ne0$ para todo $i$,

$$
x_1=\frac{b_1}{\ell_{11}},
$$

y, para $j=2,3,\ldots,n$,

$$
x_j=\frac{b_j-\displaystyle\sum_{k=1}^{j-1}\ell_{jk}x_k}{\ell_{jj}}.
$$

Ambos algoritmos requieren del orden de $n^2$ operaciones. Este costo es mucho
menor que tratar cada ecuación de manera independiente o calcular una inversa.
La condición de ser triangular no exige que las entradas diagonales sean no
nulas; esa condición adicional es la que permite ejecutar estas fórmulas sin
dividir entre cero y obtener una solución única.

### Verificación mediante el residuo

Si $\widehat x$ es una solución calculada, definimos su residuo como

$$
r=b-A\widehat x.
$$

En aritmética exacta, una solución satisface $r=0$. En cálculos de punto
flotante esperamos que $\|r\|$ sea pequeño en relación con los datos.

Los sistemas generales requieren transformaciones que preserven exactamente su
conjunto solución. Ese problema se desarrolla, comenzando nuevamente en el
lenguaje de ecuaciones, en [Eliminación de Gauss–Jordan](02_eliminacion_gauss_jordan.md).

## 6. Preguntas de comprobación

1. ¿Por qué no se puede normalizar el vector cero?
2. ¿Qué indica el signo de $x^Ty$ sobre el ángulo entre $x$ e $y$?
3. ¿Cuándo se alcanza la igualdad en Cauchy-Schwarz?
4. Si $A$ es $3\times4$ y $B$ es $4\times2$, ¿qué dimensiones tiene $AB$?
5. ¿Está necesariamente definido $BA$?
6. ¿Qué representa cada columna de $A$ en la expresión $Ax$?
7. Si $A\in\mathbb R^{m\times n}$, ¿qué órdenes tienen las identidades que
   aparecen en $I_mA=A=AI_n$?
8. ¿Qué significa que dos particiones por bloques sean conformables?
9. ¿Por qué la fórmula de $(AB)^T$ invierte el orden de los factores?
10. ¿Qué entradas de $\operatorname{diag}(d_1,\ldots,d_n)$ pueden ser no
    nulas?

## 7. Fórmulas esenciales

$$
\|x\|=\sqrt{x^Tx},
\qquad
d(x,y)=\|x-y\|,
$$

$$
|x^Ty|\leq\|x\|\|y\|,
\qquad
\cos\theta=\frac{x^Ty}{\|x\|\|y\|},
$$

$$
A(B+C)=AB+AC,
\qquad
(A+B)C=AC+BC,
$$

$$
(AB)C=A(BC),
\qquad
(AB)^T=B^TA^T,
$$

$$
C_{ik}=\sum_{j=1}^{s}A_{ij}B_{jk}
\quad\text{(producto por bloques)},
$$

$$
I_n=[\delta_{ij}]_{i,j=1}^n,
\qquad
I_mA=A=AI_n
\quad(A\in\mathbb R^{m\times n}),
$$

$$
Ax=x_1a_1+\cdots+x_na_n.
$$

$$
x_j=\frac{b_j-\sum_{k=j+1}^n u_{jk}x_k}{u_{jj}}
\quad\text{(sustitución hacia atrás)},
$$

$$
x_j=\frac{b_j-\sum_{k=1}^{j-1}\ell_{jk}x_k}{\ell_{jj}}
\quad\text{(sustitución hacia adelante)},
$$
