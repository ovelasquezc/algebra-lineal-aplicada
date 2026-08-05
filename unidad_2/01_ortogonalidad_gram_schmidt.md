# Ortogonalidad y proceso de Gram–Schmidt

## Objetivos

Al finalizar este tema, el estudiante podrá:

1. reconocer y verificar productos internos reales;
2. distinguir conjuntos ortogonales de conjuntos ortonormales;
3. obtener coordenadas en una base ortogonal;
4. determinar propiedades básicas de un complemento ortogonal;
5. construir bases ortogonales y ortonormales mediante Gram–Schmidt;
6. distinguir, a nivel introductorio, un espacio con producto interno de un
   espacio de Hilbert.

## 1. Producto interno

En $\mathbb R^n$ ya utilizamos el producto punto para medir longitudes y
ángulos. La misma estructura puede definirse en otros espacios vectoriales.

### Definición 1.1. Producto interno real

Sea $V$ un espacio vectorial real. Un **producto interno** es una función

$$
\langle\cdot,\cdot\rangle:V\times V\longrightarrow\mathbb R
$$

que satisface, para $u,v,w\in V$ y $\alpha\in\mathbb R$:

1. **Simetría:** $\langle u,v\rangle=\langle v,u\rangle$.
2. **Aditividad:** $\langle u+v,w\rangle=\langle u,w\rangle+\langle v,w\rangle$.
3. **Homogeneidad:** $\langle\alpha u,v\rangle=\alpha\langle u,v\rangle$.
4. **Positividad definida:** $\langle u,u\rangle\geq0$, y
   $\langle u,u\rangle=0$ si y solo si $u=0$.

Por simetría, la linealidad también se cumple en el segundo argumento.

### Ejemplo 1.2. Producto interno usual

En $\mathbb R^n$,

$$
\langle x,y\rangle=x^Ty=\sum_{i=1}^n x_i y_i.
$$

### Ejemplo 1.3. Producto interno ponderado

Si $A$ es una matriz simétrica definida positiva, entonces

$$
\langle x,y\rangle_A=x^TAy
$$

es un producto interno en $\mathbb R^n$. Por ejemplo, con
$A=\operatorname{diag}(2,1)$ se obtiene

$$
\langle x,y\rangle_A=2x_1y_1+x_2y_2.
$$

Dos vectores pueden ser ortogonales para un producto interno y no serlo para
otro.

### Ejemplo 1.4. Producto interno en polinomios

En $\mathcal P_2$, el espacio de polinomios reales de grado a lo más $2$,

$$
\langle p,q\rangle=\int_{-1}^{1}p(t)q(t)\,dt
$$

es un producto interno. Así, $1$ y $t$ son ortogonales porque
$\int_{-1}^{1}t\,dt=0$.

## 2. Norma y ortogonalidad

Todo producto interno induce una norma:

$$
\|u\|=\sqrt{\langle u,u\rangle}.
$$

Las propiedades de esta norma —incluidas Cauchy–Schwarz y la desigualdad
triangular— se establecieron en la Unidad 1. Aquí las usaremos en un espacio
con producto interno general.

### Definición 2.1. Espacio real con producto interno

Un **espacio real con producto interno** es un espacio vectorial real $V$
provisto de un producto interno. La norma y la distancia asociadas son

$$
\|u\|=\sqrt{\langle u,u\rangle},
\qquad
d(u,v)=\|u-v\|.
$$

Esta es la estructura en la que se definen ortogonalidad, ángulos y
proyecciones. No se trata solamente de trabajar en $\mathbb R^n$: también son
ejemplos los espacios de polinomios con productos internos integrales.

```{admonition} Mención: espacios de Hilbert
:class: note
Una sucesión $(x_n)$ es **de Cauchy** si sus términos terminan siendo tan
cercanos entre sí como se quiera. Un espacio con producto interno es un
**espacio de Hilbert** si es completo para la norma inducida: toda sucesión de
Cauchy converge a un elemento del propio espacio.

Todo espacio con producto interno de dimensión finita es automáticamente de
Hilbert. La completitud cobra importancia en dimensión infinita. Por ejemplo,
$L^2([-\pi,\pi])$ es el espacio de Hilbert natural para formular Fourier con
plena generalidad. En el curso usaremos las ideas geométricas de esta teoría,
sin desarrollar sus aspectos analíticos.
```

### Definición 2.2. Vectores ortogonales

Dos vectores $u,v\in V$ son **ortogonales**, y escribimos $u\perp v$, si

$$
\langle u,v\rangle=0.
$$

### Definición 2.3. Conjuntos ortogonales y ortonormales

Un conjunto de vectores no nulos $\{v_1,\ldots,v_r\}$ es:

1. **ortogonal** si $\langle v_i,v_j\rangle=0$ para $i\neq j$;
2. **ortonormal** si es ortogonal y $\|v_i\|=1$ para todo $i$.

### Teorema 2.4. Pitágoras

**Enunciado.** Si $u\perp v$, entonces

$$
\|u+v\|^2=\|u\|^2+\|v\|^2.
$$

**Prueba.** Al expandir con las propiedades del producto interno,

$$
\begin{aligned}
\|u+v\|^2
&=\langle u+v,u+v\rangle\\
&=\|u\|^2+2\langle u,v\rangle+\|v\|^2.
\end{aligned}
$$

El término cruzado es cero porque $u\perp v$. $\square$

### Teorema 2.5. Independencia de un conjunto ortogonal

**Enunciado.** Todo conjunto ortogonal de vectores no nulos es linealmente
independiente.

**Prueba.** Supongamos que
$c_1v_1+\cdots+c_rv_r=0$. Al tomar producto interno con $v_k$,

$$
0=\left\langle\sum_{i=1}^r c_iv_i,v_k\right\rangle
=c_k\|v_k\|^2.
$$

Como $v_k\neq0$, se tiene $\|v_k\|^2>0$ y por tanto $c_k=0$. Esto vale para
cada $k$. $\square$

## 3. Bases ortogonales y expansión

### Definición 3.1. Base ortogonal

Una base de $W$ es **ortogonal** si sus vectores son mutuamente ortogonales; es
**ortonormal** si, además, todos tienen norma $1$.

### Teorema 3.2. Coeficientes en una base ortogonal

**Enunciado.** Si $\mathcal B=(v_1,\ldots,v_r)$ es una base ortogonal de $W$,
entonces todo $x\in W$ se escribe como

$$
x=\sum_{i=1}^r
\frac{\langle x,v_i\rangle}{\|v_i\|^2}v_i.
$$

Si la base es ortonormal, la fórmula se reduce a

$$
x=\sum_{i=1}^r\langle x,v_i\rangle v_i.
$$

**Prueba.** Escriba $x=\sum_i c_iv_i$ y tome producto interno con $v_k$.
La ortogonalidad anula todos los términos salvo uno:

$$
\langle x,v_k\rangle=c_k\|v_k\|^2.
$$

Despejando se obtiene la fórmula. $\square$

### Ejemplo 3.3

En $\mathbb R^3$, sean

$$
v_1=(1,1,0),\qquad v_2=(1,-1,0),\qquad x=(2,0,0).
$$

Como $v_1\cdot v_2=0$,

$$
c_1=\frac{x\cdot v_1}{v_1\cdot v_1}=1,
\qquad
c_2=\frac{x\cdot v_2}{v_2\cdot v_2}=1,
$$

y por tanto $x=v_1+v_2$.

### Corolario 3.4. Identidad de Parseval

**Enunciado.** Si $(e_1,\ldots,e_r)$ es una base ortonormal de $W$, entonces,
para todo $x\in W$,

$$
\|x\|^2=\sum_{i=1}^r|\langle x,e_i\rangle|^2.
$$

**Prueba.** Sustituya la expansión ortonormal de $x$ en
$\langle x,x\rangle$ y use la ortonormalidad. $\square$

## 4. Complemento ortogonal

### Definición 4.1. Complemento ortogonal

Para un subconjunto $S\subseteq V$, se define

$$
S^\perp=\{x\in V:\langle x,s\rangle=0\text{ para todo }s\in S\}.
$$

No es necesario que $S$ sea un subespacio para que $S^\perp$ sí lo sea.

### Proposición 4.2. Propiedades del complemento ortogonal

**Enunciado.** Sean $S,T\subseteq V$ y sea $W$ un subespacio. Entonces:

1. $S^\perp$ es un subespacio de $V$.
2. Si $S\subseteq T$, entonces $T^\perp\subseteq S^\perp$.
3. $S^\perp=(\operatorname{span}S)^\perp$.
4. $W\cap W^\perp=\{0\}$.
5. Si $V$ es de dimensión finita, entonces
   $\dim W+\dim W^\perp=\dim V$.

**Idea de prueba.** Las tres primeras propiedades se deducen directamente de
la linealidad del producto interno. Si $x\in W\cap W^\perp$, entonces
$\langle x,x\rangle=0$ y $x=0$. Para la quinta propiedad, se toma una base
ortonormal de $W$, se extiende a una base ortonormal de $V$ y se identifica la
parte añadida como una base de $W^\perp$.

```{admonition} Conexión con matrices
:class: note
Para el producto interno usual y una matriz real $A$,
$(\operatorname{Col}A)^\perp=\operatorname{Nul}(A^T)$. Esta igualdad conecta
la ortogonalidad con los espacios fundamentales estudiados en la Unidad 1.
```

## 5. Proyección sobre una dirección

Sea $u\neq0$. La componente de $x$ en la dirección de $u$ es

$$
\operatorname{proj}_u(x)
=\frac{\langle x,u\rangle}{\langle u,u\rangle}u.
$$

### Proposición 5.1. Descomposición respecto de una dirección

**Enunciado.** Para $u\neq0$,

$$
x=\operatorname{proj}_u(x)
+\bigl(x-\operatorname{proj}_u(x)\bigr),
$$

donde la segunda componente es ortogonal a $u$.

**Prueba.** La suma es inmediata. Además,

$$
\begin{aligned}
\left\langle x-\operatorname{proj}_u(x),u\right\rangle
&=\langle x,u\rangle
-\frac{\langle x,u\rangle}{\langle u,u\rangle}\langle u,u\rangle\\
&=0.
\end{aligned}
$$

$\square$

En este bloque usamos esta fórmula para retirar componentes en direcciones ya
construidas. La interpretación como vector más cercano se probará al estudiar
minimización de distancias y proyección sobre subespacios.

## 6. Proceso de Gram–Schmidt

### Teorema 6.1. Ortogonalización de Gram–Schmidt

**Enunciado.** Sean $v_1,\ldots,v_r$ vectores linealmente independientes. Se
definen

$$
u_1=v_1,
$$

y, para $k=2,\ldots,r$,

$$
u_k=v_k-\sum_{i=1}^{k-1}
\frac{\langle v_k,u_i\rangle}{\langle u_i,u_i\rangle}u_i.
$$

Entonces:

1. $u_1,\ldots,u_r$ son no nulos y mutuamente ortogonales;
2. para cada $k$,
   $\operatorname{span}(u_1,\ldots,u_k)
    =\operatorname{span}(v_1,\ldots,v_k)$.

Por tanto, ambos conjuntos son bases del mismo subespacio. Al definir

$$
e_i=\frac{u_i}{\|u_i\|},
$$

se obtiene una base ortonormal.

**Idea de prueba.** Por inducción, al calcular
$\langle u_k,u_j\rangle$ con $j<k$, todos los términos de la suma se anulan
excepto el correspondiente a $i=j$, que cancela $\langle v_k,u_j\rangle$.
Así, $u_k$ es ortogonal a los vectores anteriores. La fórmula muestra que
$u_k$ pertenece al espacio generado por $v_1,\ldots,v_k$ y, despejando $v_k$,
se obtiene la inclusión inversa. Si algún $u_k$ fuera cero, $v_k$ pertenecería
al espacio generado por sus predecesores, en contradicción con la independencia
lineal.

### Ejemplo 6.2. Cálculo exacto

Partimos de

$$
v_1=(1,1,0),\quad v_2=(1,0,1),\quad v_3=(0,1,1).
$$

El proceso produce

$$
u_1=(1,1,0),
$$

$$
u_2=v_2-\frac{v_2\cdot u_1}{u_1\cdot u_1}u_1
=\left(\frac12,-\frac12,1\right),
$$

y

$$
\begin{aligned}
u_3
&=v_3-\frac{v_3\cdot u_1}{u_1\cdot u_1}u_1
       -\frac{v_3\cdot u_2}{u_2\cdot u_2}u_2\\
&=\left(-\frac23,\frac23,\frac23\right).
\end{aligned}
$$

Se verifica que $u_i\cdot u_j=0$ para $i\neq j$. Al normalizar:

$$
e_1=\frac1{\sqrt2}(1,1,0),\qquad
e_2=\frac1{\sqrt6}(1,-1,2),\qquad
e_3=\frac1{\sqrt3}(-1,1,1).
$$

## 7. Forma matricial y cálculo numérico

Si los vectores iniciales son las columnas de una matriz $A$, Gram–Schmidt
construye una matriz $Q$ con columnas ortonormales y una matriz triangular
superior $R$ tales que

$$
A=QR,
\qquad Q^TQ=I.
$$

En cálculo exacto, las fórmulas anteriores son suficientes. En punto flotante,
la versión clásica puede acumular errores cuando las columnas de $A$ son casi
dependientes. Las bibliotecas numéricas usan algoritmos más estables para
calcular una factorización QR.

## 8. Comprobación conceptual

1. ¿Por qué se exige que los vectores de entrada de Gram–Schmidt sean
   linealmente independientes?
2. ¿Qué cambia al reemplazar un producto interno por otro?
3. Si $S\subseteq T$, explique geométricamente por qué
   $T^\perp\subseteq S^\perp$.
4. Para una base ortonormal, ¿por qué no es necesario resolver un sistema para
   hallar las coordenadas de un vector?

## 9. Ejercicios

1. Compruebe que $(1,1,0)$, $(1,-1,2)$ y $(-1,1,1)$ forman una base
   ortogonal de $\mathbb R^3$ y conviértala en una base ortonormal.
2. Aplique Gram–Schmidt a
   $(1,0,1)$, $(1,1,0)$ y $(0,1,1)$.
3. En $\mathcal P_2$ con
   $\langle p,q\rangle=\int_{-1}^{1}p(t)q(t)\,dt$, ortogonalice
   $(1,t,t^2)$.
4. Si las columnas de $A$ generan $W$, explique cómo encontrar $W^\perp$
   resolviendo un sistema homogéneo.
