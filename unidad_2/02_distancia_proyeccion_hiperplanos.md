# Distancia, proyección ortogonal e hiperplanos

## Objetivos

Al finalizar este tema, el estudiante podrá:

1. formular la distancia de un punto a un conjunto;
2. caracterizar la proyección sobre un conjunto convexo cerrado;
3. calcular proyecciones sobre subespacios y conjuntos afines;
4. construir e interpretar matrices de proyección ortogonal;
5. obtener la proyección y la distancia a un hiperplano.

```{admonition} Estructura que se usa en este tema
:class: note
La definición general de **espacio vectorial real con producto interno** está
en [Ortogonalidad y proceso de Gram–Schmidt](01_ortogonalidad_gram_schmidt.md).
En esta hoja se especializan sus resultados a la distancia y la proyección.
```

## 1. Distancia de un punto a un conjunto

### Definición 1.1. Distancia a un conjunto

Sea $C\subseteq\mathbb R^n$ no vacío. La **distancia** de $x$ a $C$ es

$$
\operatorname{dist}(x,C)=\inf_{y\in C}\|x-y\|.
$$

Se usa un ínfimo porque un conjunto arbitrario podría no contener un punto que
alcance la menor distancia.

### Definición 1.2. Punto más cercano y proyección

Un punto $p\in C$ es un **punto más cercano** a $x$ si

$$
\|x-p\|=\operatorname{dist}(x,C).
$$

Cuando ese punto existe y es único, se llama **proyección de $x$ sobre $C$** y
se denota $P_C(x)$ o $\operatorname{proj}_C(x)$.

```{admonition} Existencia y unicidad son preguntas diferentes
:class: warning
El conjunto abierto $C=(0,1)$ no contiene un punto más cercano a $x=2$. Un
conjunto no convexo puede contener varios puntos igualmente cercanos. Las
hipótesis de cerrado y convexo resolverán ambos problemas en $\mathbb R^n$.
```

## 2. Proyección sobre un conjunto convexo

### Definición 2.1. Conjunto convexo

Un conjunto $C\subseteq\mathbb R^n$ es **convexo** si

$$
\lambda y+(1-\lambda)z\in C
$$

para todo $y,z\in C$ y todo $\lambda\in[0,1]$. Geométricamente, el segmento
entre dos puntos del conjunto permanece dentro del conjunto.

### Teorema 2.2. Existencia y unicidad

**Enunciado.** Si $C\subseteq\mathbb R^n$ es no vacío, cerrado y convexo,
entonces para cada $x\in\mathbb R^n$ existe un único punto $P_C(x)\in C$ que
minimiza $\|x-y\|$ sobre $y\in C$.

**Idea de prueba.** Para la existencia, se elige una sucesión de puntos de $C$
cuyas distancias a $x$ se aproximan al ínfimo. Puede restringirse a una bola
cerrada y acotada; allí existe una subsucesión convergente, y el límite
pertenece a $C$ por ser cerrado. Para la unicidad, si $p$ y $q$ fueran dos
minimizadores distintos, su punto medio pertenecería a $C$. La identidad del
paralelogramo mostraría que ese punto medio está estrictamente más cerca de
$x$, una contradicción.

### Teorema 2.3. Caracterización por producto interno

**Enunciado.** Sea $C\subseteq\mathbb R^n$ no vacío, cerrado y convexo. Para
$p\in C$ son equivalentes:

1. $p=P_C(x)$.
2. Para todo $y\in C$,

   $$
   \boxed{\langle x-p,y-p\rangle\leq0.}
   $$

**Prueba.** Supongamos primero que $p=P_C(x)$. Para $y\in C$ y
$0<t\leq1$, la convexidad garantiza que $p+t(y-p)\in C$. Por minimalidad,

$$
\|x-p\|^2
\leq \|x-p-t(y-p)\|^2.
$$

Al expandir, dividir entre $t>0$ y hacer $t\to0^+$ se obtiene
$\langle x-p,y-p\rangle\leq0$.

Recíprocamente, si se cumple la desigualdad, entonces para todo $y\in C$,

$$
\begin{aligned}
\|x-y\|^2
&=\|x-p-(y-p)\|^2\\
&=\|x-p\|^2+\|y-p\|^2
  -2\langle x-p,y-p\rangle\\
&\geq\|x-p\|^2.
\end{aligned}
$$

Por tanto, $p$ es el punto más cercano. $\square$

La desigualdad expresa que el ángulo entre $x-p$ y cualquier dirección
$y-p$ que entra en $C$ desde $p$ es obtuso o recto.

```{figure} figuras/proyeccion_convexa.svg
:name: fig-proyeccion-convexa
:width: 90%

Caracterización de la proyección sobre un conjunto convexo cerrado. En el
punto más cercano, todas las direcciones hacia el conjunto forman con el
residuo un ángulo mayor o igual que $90^\circ$.
```

## 3. Caso particular: subespacios

Todo subespacio de $\mathbb R^n$ es cerrado y convexo. En este caso, la
desigualdad del teorema anterior se convierte en una igualdad.

### Teorema 3.1. Caracterización de la proyección ortogonal

**Enunciado.** Sea $W\subseteq\mathbb R^n$ un subespacio y $p\in W$. Entonces

$$
p=P_W(x)
\quad\Longleftrightarrow\quad
x-p\in W^\perp.
$$

Equivalentemente,

$$
\langle x-p,w\rangle=0
\qquad\text{para todo }w\in W.
$$

**Prueba.** Si $p=P_W(x)$, en el Teorema 2.3 podemos tomar
$y=p+tw$ para cualquier $w\in W$ y cualquier $t\in\mathbb R$. Así,

$$
t\langle x-p,w\rangle\leq0
$$

para valores positivos y negativos de $t$; por tanto el producto interno es
cero. La implicación inversa se sigue del Teorema 2.3. $\square$

```{figure} figuras/proyeccion_subespacio.svg
:name: fig-proyeccion-subespacio
:width: 86%

En un subespacio se puede avanzar desde $p$ en ambas direcciones. Por eso la
desigualdad del caso convexo se convierte en la igualdad
$\langle x-p,w\rangle=0$ para todo $w\in W$: el residuo es ortogonal a todo
el subespacio.
```

### Corolario 3.2. Mejor aproximación y Pitágoras

**Enunciado.** Si $p=P_W(x)$, entonces para todo $w\in W$,

$$
\boxed{\|x-w\|^2=\|x-p\|^2+\|p-w\|^2.}
$$

En particular, $p$ es el único punto de $W$ que minimiza la distancia a $x$.

**Prueba.** Se escribe $x-w=(x-p)+(p-w)$. El primer sumando pertenece a
$W^\perp$ y el segundo a $W$, así que son ortogonales. Se aplica Pitágoras.
$\square$

### Teorema 3.3. Descomposición ortogonal

**Enunciado.** Para todo subespacio $W\subseteq\mathbb R^n$,

$$
\mathbb R^n=W\oplus W^\perp.
$$

Cada $x\in\mathbb R^n$ se escribe de manera única como

$$
x=P_W(x)+P_{W^\perp}(x).
$$

**Prueba.** Sea $p=P_W(x)$. Entonces $p\in W$ y $x-p\in W^\perp$, de modo que
$x=p+(x-p)$. La unicidad se obtiene de
$W\cap W^\perp=\{0\}$. $\square$

```{admonition} Alcance y versión en espacios de Hilbert
:class: note
En dimensión finita todo subespacio es cerrado, por lo que el teorema anterior
se aplica sin hipótesis adicionales. En un espacio de Hilbert $H$, la versión
general afirma que, para todo **subespacio cerrado** $W$,

$$
H=W\oplus W^\perp.
$$

La condición de cerrado es esencial. Este teorema de proyección es el puente
conceptual hacia la aproximación por polinomios trigonométricos en Fourier.
```

## 4. Cómo calcular la proyección

### Teorema 4.1. Fórmula con una base ortogonal

**Enunciado.** Si $(v_1,\ldots,v_r)$ es una base ortogonal de $W$, entonces

$$
P_W(x)=\sum_{i=1}^r
\frac{\langle x,v_i\rangle}{\langle v_i,v_i\rangle}v_i.
$$

Si $(u_1,\ldots,u_r)$ es ortonormal,

$$
\boxed{P_W(x)=\sum_{i=1}^r\langle x,u_i\rangle u_i.}
$$

**Prueba.** La expresión pertenece a $W$. Al tomar producto interno de la
diferencia con cada vector de la base, se obtiene cero. El Teorema 3.1 concluye
que es la proyección. $\square$

### Teorema 4.2. Matriz de proyección con columnas ortonormales

**Enunciado.** Sea $U=[u_1\ \cdots\ u_r]\in\mathbb R^{n\times r}$, donde las
columnas forman una base ortonormal de $W$. Entonces

$$
P_W(x)=UU^Tx,
\qquad
\boxed{P_W=UU^T}.
$$

**Prueba.** La columna $U^Tx$ contiene los coeficientes
$\langle x,u_i\rangle$. Multiplicar por $U$ forma la combinación lineal del
Teorema 4.1. $\square$

### Proposición 4.3. Propiedades de la matriz de proyección

**Enunciado.** La matriz $P=UU^T$ satisface:

1. $P^T=P$.
2. $P^2=P$.
3. $\operatorname{Col}(P)=W$.
4. $\operatorname{Nul}(P)=W^\perp$.
5. $I-P$ es la matriz de proyección sobre $W^\perp$.

**Prueba.** La simetría es inmediata. Como $U^TU=I$,

$$
P^2=UU^TUU^T=UU^T=P.
$$

La fórmula $Px\in\operatorname{Col}(U)$ prueba una inclusión en la propiedad
3; para $w\in W$, se tiene $Pw=w$. Además, $Px=0$ equivale a $U^Tx=0$, es
decir, a que $x$ sea ortogonal a todas las columnas de $U$. Finalmente,
$x-Px\in W^\perp$, lo que prueba la última propiedad. $\square$

### Proposición 4.4. Fórmula desde una base no ortonormal

**Enunciado.** Si $B\in\mathbb R^{n\times r}$ tiene columnas linealmente
independientes y $W=\operatorname{Col}(B)$, entonces

$$
\boxed{P_W=B(B^TB)^{-1}B^T.}
$$

**Idea de prueba.** Escribimos $p=Bc$ y exigimos que
$x-Bc$ sea ortogonal a cada columna de $B$. Esto produce
$B^T(x-Bc)=0$. Como las columnas son independientes, $B^TB$ es invertible y
se despeja $c$. Si primero se calcula una factorización $B=QR$ con columnas
ortonormales en $Q$, la misma proyección es $QQ^T$.

## 5. Proyección sobre conjuntos afines

### Definición 5.1. Conjunto afín

Un conjunto no vacío $A\subseteq\mathbb R^n$ es **afín** si contiene toda
combinación afín de sus puntos. Equivalentemente, existen $a\in\mathbb R^n$ y
un subespacio $W$ tales que

$$
A=a+W=\{a+w:w\in W\}.
$$

El subespacio $W$ contiene las direcciones de $A$.

### Teorema 5.2. Proyección sobre una traslación

**Enunciado.** Si $A=a+W$, entonces

$$
\boxed{P_A(x)=a+P_W(x-a)}
$$

y

$$
\operatorname{dist}(x,A)=\|P_{W^\perp}(x-a)\|.
$$

**Prueba.** Todo punto de $A$ tiene la forma $a+w$. Por tanto,

$$
\|x-(a+w)\|=\|(x-a)-w\|.
$$

Minimizar sobre $A$ equivale a proyectar $x-a$ sobre $W$. $\square$

## 6. Hiperplanos

### Definición 6.1. Hiperplano

Sea $u\in\mathbb R^n$, $u\neq0$, y $c\in\mathbb R$. El conjunto

$$
H(u,c)=\{y\in\mathbb R^n:\langle y,u\rangle=c\}
$$

es un **hiperplano**. Es un conjunto afín cuya dirección es $u^\perp$; el
vector $u$ es normal al hiperplano.

### Teorema 6.2. Proyección y distancia a un hiperplano

**Enunciado.** Para $x\in\mathbb R^n$,

$$
\boxed{
P_H(x)=x-
\frac{\langle x,u\rangle-c}{\|u\|^2}u
}
$$

y

$$
\boxed{
\operatorname{dist}(x,H)=
\frac{|\langle x,u\rangle-c|}{\|u\|}.
}
$$

**Prueba.** Buscamos $p=x-\lambda u$ porque el error $x-p$ debe ser paralelo
al vector normal. La condición $p\in H$ da

$$
c=\langle x-\lambda u,u\rangle
=\langle x,u\rangle-\lambda\|u\|^2,
$$

de donde se obtiene $\lambda$. La distancia es
$\|x-p\|=|\lambda|\|u\|$. $\square$

```{figure} figuras/proyeccion_hiperplano.svg
:name: fig-proyeccion-hiperplano
:width: 90%

La corrección que lleva $x$ al hiperplano sigue su dirección normal. El
segmento entre $x$ y $P_H(x)$ es perpendicular a todas las direcciones del
hiperplano.
```

Si el hiperplano se escribe como
$\langle y,u\rangle+b=0$, basta tomar $c=-b$.

### Ejemplo 6.3

Considere

$$
H=\{y\in\mathbb R^3:y_1-2y_2+2y_3=3\}
$$

y $x=(4,0,-1)$. Aquí $u=(1,-2,2)$,
$\langle x,u\rangle=2$ y $\|u\|^2=9$. Por tanto,

$$
P_H(x)=x-\frac{2-3}{9}u
=\left(\frac{37}{9},-\frac{2}{9},-\frac{7}{9}\right),
$$

y

$$
\operatorname{dist}(x,H)=\frac{|2-3|}{3}=\frac13.
$$

## 7. Un ejemplo matricial

Sean

$$
u_1=\frac1{\sqrt2}(1,1,0),
\qquad
u_2=\frac1{\sqrt2}(1,-1,0),
$$

y $W=\operatorname{span}\{u_1,u_2\}$. Las columnas son ortonormales y

$$
P=UU^T=
\begin{bmatrix}
1&0&0\\
0&1&0\\
0&0&0
\end{bmatrix}.
$$

Para $x=(2,1,3)$,

$$
P_W(x)=(2,1,0),
\qquad
x-P_W(x)=(0,0,3)\in W^\perp.
$$

## 8. Errores frecuentes

1. Proyectar sobre cada vector de una base y sumar solo funciona directamente
   cuando la base es ortogonal.
2. $P_W(x)$ pertenece a $W$; el residuo $x-P_W(x)$ pertenece a $W^\perp$.
3. Una matriz idempotente no representa necesariamente una proyección
   **ortogonal**; para ello también debe ser simétrica.
4. En un hiperplano, el signo se controla sustituyendo el punto proyectado en
   la ecuación de $H$.
5. La distancia es una longitud y, por tanto, nunca es negativa.

## 9. Ejercicios

1. Para el segmento
   $C=\{(t,0):0\leq t\leq2\}$, determine $P_C(3,1)$ y verifique la
   desigualdad del Teorema 2.3.
2. Proyecte $x=(2,0,3)$ sobre el subespacio generado por
   $(1,1,0)$ y $(0,1,1)$. Verifique que el residuo es ortogonal a ambos
   generadores.
3. Si $P$ es una matriz simétrica e idempotente, demuestre que
   $\operatorname{Nul}(P)=\operatorname{Col}(P)^\perp$.
4. Sea $A=a+W$. Demuestre que $x-P_A(x)$ es ortogonal a todas las
   direcciones de $A$.
5. Halle la proyección de $(3,2)$ sobre la recta $2y_1+y_2=3$ y calcule la
   distancia.
6. Si $A\in\mathbb R^{m\times n}$, explique cómo proyectar un vector sobre
   $\operatorname{Nul}(A)$ usando una base, Gram–Schmidt y una matriz $UU^T$.
