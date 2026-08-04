# Mínimos cuadrados y ajuste de datos

## Objetivos

Al finalizar este tema, el estudiante podrá:

1. interpretar un problema de mínimos cuadrados como una proyección ortogonal;
2. derivar y resolver las ecuaciones normales;
3. distinguir la unicidad del vector ajustado de la unicidad de los
   coeficientes;
4. construir matrices de diseño para ajustes lineales, polinomiales y con
   funciones base generales;
5. interpretar el residuo y el coeficiente de determinación $R^2$.

## 1. Cuando un sistema no tiene solución exacta

Sea $A\in\mathbb R^{m\times n}$ y $b\in\mathbb R^m$. Si
$b\notin\operatorname{Col}(A)$, el sistema $Ax=b$ es incompatible. En lugar
de exigir igualdad, buscamos un vector $x$ para el cual $Ax$ esté lo más cerca
posible de $b$.

### Definición 1.1. Solución de mínimos cuadrados

Un vector $x^*\in\mathbb R^n$ es una **solución de mínimos cuadrados** de
$Ax=b$ si

$$
\|Ax^*-b\|
=\min_{x\in\mathbb R^n}\|Ax-b\|.
$$

Minimizar la norma o su cuadrado produce las mismas soluciones. El vector

$$
r^*=b-Ax^*
$$

se llama **residuo**. Sus componentes miden las discrepancias entre los datos
observados y los valores ajustados.

## 2. Interpretación geométrica

Todos los vectores de la forma $Ax$ pertenecen a
$\operatorname{Col}(A)$. Por tanto, minimizar $\|Ax-b\|$ equivale a buscar el
punto de $\operatorname{Col}(A)$ más cercano a $b$.

### Teorema 2.1. Caracterización por proyección

**Enunciado.** Para $x^*\in\mathbb R^n$ son equivalentes:

1. $x^*$ es una solución de mínimos cuadrados de $Ax=b$.
2. $Ax^*=P_{\operatorname{Col}(A)}(b)$.
3. $b-Ax^*\in\operatorname{Col}(A)^\perp$.

**Prueba.** Al variar $x$, el vector $Ax$ recorre exactamente
$\operatorname{Col}(A)$. Por el teorema de proyección, el vector de ese
subespacio que minimiza la distancia a $b$ es
$P_{\operatorname{Col}(A)}(b)$, y se caracteriza porque el residuo es
ortogonal a todo el subespacio. $\square$

```{admonition} Dos objetos distintos
:class: important
El vector ajustado $\widehat b=Ax^*$ es único, porque una proyección ortogonal
es única. Los coeficientes $x^*$ podrían no ser únicos si columnas distintas
de $A$ describen las mismas direcciones.
```

## 3. Ecuaciones normales

### Teorema 3.1. Ecuaciones normales

**Enunciado.** Un vector $x^*$ resuelve el problema de mínimos cuadrados si y
solo si

$$
\boxed{A^TAx^*=A^Tb.}
$$

**Prueba.** Por el Teorema 2.1, $x^*$ es solución si y solo si
$r^*=b-Ax^*$ es ortogonal a cada columna de $A$. Los productos internos con
todas las columnas se reúnen en el vector $A^Tr^*$. Así,

$$
A^T(b-Ax^*)=0
\quad\Longleftrightarrow\quad
A^TAx^*=A^Tb.
$$

$\square$

Estas se llaman **ecuaciones normales** porque expresan que el residuo es
normal, es decir, perpendicular, al espacio de columnas.

### Proposición 3.2. Identidad de optimalidad

**Enunciado.** Si $x^*$ satisface las ecuaciones normales, entonces para todo
$x\in\mathbb R^n$,

$$
\boxed{
\|Ax-b\|^2
=\|Ax^*-b\|^2+\|A(x-x^*)\|^2.
}
$$

Equivalentemente, para $F(x)=\frac12\|Ax-b\|^2$,

$$
F(x)-F(x^*)=\frac12\|A(x-x^*)\|^2\geq0.
$$

**Prueba.** Escribimos

$$
Ax-b=A(x-x^*)+(Ax^*-b).
$$

El primer sumando pertenece a $\operatorname{Col}(A)$ y el segundo es
ortogonal a ese espacio porque $x^*$ satisface las ecuaciones normales. La
identidad se obtiene por Pitágoras. $\square$

Esta fórmula prueba directamente que toda solución de las ecuaciones normales
minimiza el error. También muestra que dos minimizadores $x_1,x_2$ satisfacen
$A(x_1-x_2)=0$ y, por tanto, producen el mismo vector ajustado.

### Proposición 3.3. Núcleo de la matriz normal

**Enunciado.** Para toda matriz real $A$,

$$
\boxed{\operatorname{Nul}(A^TA)=\operatorname{Nul}(A).}
$$

En consecuencia,
$\operatorname{rango}(A^TA)=\operatorname{rango}(A)$.

**Prueba.** Si $Ax=0$, entonces $A^TAx=0$. Recíprocamente, si
$A^TAx=0$, entonces

$$
0=x^TA^TAx=\|Ax\|^2,
$$

y por tanto $Ax=0$. La igualdad de rangos se obtiene con rango-nulidad.
$\square$

### Teorema 3.4. Propiedades generales de las soluciones

**Enunciado.** Para todo $A\in\mathbb R^{m\times n}$ y
$b\in\mathbb R^m$, sea

$$
L=\{x\in\mathbb R^n:A^TAx=A^Tb\}.
$$

Entonces:

1. $L$ es no vacío y es un conjunto afín;
2. para cualesquiera $x_1,x_2\in L$ se cumple
   $Ax_1=Ax_2=P_{\operatorname{Col}(A)}(b)$;
3. si $x_0\in L$, entonces

   $$
   \boxed{L=x_0+\operatorname{Nul}(A)};
   $$

4. la solución es única si y solo si las columnas de $A$ son linealmente
   independientes, es decir, si y solo si
   $\operatorname{rango}(A)=n$;
5. entre todas las soluciones existe exactamente una de norma euclídea
   mínima. Es la única solución que pertenece a
   $\operatorname{Nul}(A)^\perp$.

**Prueba.** La proyección de $b$ sobre $\operatorname{Col}(A)$ existe. Como
todo vector de ese espacio tiene la forma $Ax$, existe $x_0$ que produce la
proyección; por el Teorema 3.1, $x_0\in L$. La linealidad de las ecuaciones
normales muestra que $L$ es afín.

La Proposición 3.2 aplicada a dos elementos de $L$ da
$A(x_1-x_2)=0$. Por tanto, todos producen el mismo ajuste y
$L=x_0+\operatorname{Nul}(A)$. Este conjunto contiene un solo punto si y solo
si $\operatorname{Nul}(A)=\{0\}$, condición equivalente a
$\operatorname{rango}(A)=n$.

Para la última afirmación, descomponemos ortogonalmente una solución como
$x_0=u+v$, donde
$u\in\operatorname{Nul}(A)^\perp$ y $v\in\operatorname{Nul}(A)$. Como
$Au=Ax_0$, también $u\in L$. Toda solución tiene entonces la forma $u+w$ con
$w\in\operatorname{Nul}(A)$, y

$$
\|u+w\|^2=\|u\|^2+\|w\|^2.
$$

La norma es mínima únicamente cuando $w=0$. $\square$

### Corolario 3.5. Fórmula en rango columna completo

**Enunciado.** Si las columnas de $A$ son linealmente independientes,
$A^TA$ es invertible y la solución única es

$$
\boxed{x^*=(A^TA)^{-1}A^Tb.}
$$

**Prueba.** Por la Proposición 3.3, $A^TA$ tiene núcleo trivial. Al ser
cuadrada, es invertible, y se despeja $x^*$ de las ecuaciones normales.
$\square$

```{admonition} Fórmula teórica y cálculo numérico
:class: warning
La fórmula explica la geometría, pero en un programa no conviene formar
$(A^TA)^{-1}$. Para datos numéricos se usa `numpy.linalg.lstsq` o una
factorización QR. Formar $A^TA$ puede amplificar problemas de
condicionamiento.
```

## 4. Ajuste de una recta

Dados puntos $(t_i,y_i)$, buscamos una recta

$$
y=at+c
$$

que minimice la suma de cuadrados de los residuos verticales:

$$
\sum_{i=1}^m (y_i-at_i-c)^2.
$$

Definimos la matriz de diseño, el vector de parámetros y el vector de datos:

$$
X=
\begin{bmatrix}
t_1&1\\
t_2&1\\
\vdots&\vdots\\
t_m&1
\end{bmatrix},
\qquad
\beta=\begin{bmatrix}a\\c\end{bmatrix},
\qquad
y=\begin{bmatrix}y_1\\y_2\\\vdots\\y_m\end{bmatrix}.
$$

El problema es $\min_\beta\|X\beta-y\|^2$. Sus ecuaciones normales son

$$
\begin{bmatrix}
\sum t_i^2&\sum t_i\\
\sum t_i&m
\end{bmatrix}
\begin{bmatrix}a\\c\end{bmatrix}
=
\begin{bmatrix}
\sum t_iy_i\\
\sum y_i
\end{bmatrix}.
$$

### Ejemplo 4.1

Para los puntos $(1,2)$, $(2,2)$ y $(3,4)$,

$$
X=
\begin{bmatrix}
1&1\\2&1\\3&1
\end{bmatrix},
\qquad
y=\begin{bmatrix}2\\2\\4\end{bmatrix}.
$$

Entonces

$$
X^TX=\begin{bmatrix}14&6\\6&3\end{bmatrix},
\qquad
X^Ty=\begin{bmatrix}18\\8\end{bmatrix}.
$$

Al resolver se obtiene

$$
a=1,
\qquad
c=\frac23,
$$

de modo que la recta ajustada es $y=t+\frac23$. El residuo es

$$
r=y-X\beta=
\begin{bmatrix}\frac13\\-\frac23\\\frac13\end{bmatrix},
\qquad
X^Tr=0.
$$

La última igualdad verifica simultáneamente que la suma de residuos es cero y
que los residuos no tienen componente en la dirección de los valores $t_i$.

## 5. Matrices de diseño y funciones base

El modelo puede ser no lineal en la variable de entrada y seguir siendo
lineal en sus parámetros. Dadas funciones
$\varphi_1,\ldots,\varphi_p$, buscamos

$$
f(t)=\sum_{j=1}^p\beta_j\varphi_j(t).
$$

La matriz de diseño se define por

$$
X_{ij}=\varphi_j(t_i).
$$

Así, el vector $X\beta$ contiene los valores ajustados
$f(t_1),\ldots,f(t_m)$.

Ejemplos de bases:

1. recta: $1,t$;
2. polinomio cuadrático: $1,t,t^2$;
3. modelo trigonométrico real: $1,\sin t,\cos t$;
4. superficie afín en dos variables: $1,s,t$.

En todos los casos se resuelve el mismo problema geométrico:

$$
\min_\beta\|X\beta-y\|^2.
$$

### Ejemplo 5.1. Aproximación cuadrática en una variable

Para los datos

$$
(-2,5),\ (-1,2),\ (0,1),\ (1,2),\ (2,4),
$$

buscamos

$$
f(t)=a+bt+ct^2.
$$

Con las funciones base $1,t,t^2$,

$$
X=
\begin{bmatrix}
1&-2&4\\
1&-1&1\\
1&0&0\\
1&1&1\\
1&2&4
\end{bmatrix},
\qquad
z=\begin{bmatrix}5\\2\\1\\2\\4\end{bmatrix}.
$$

Las ecuaciones normales son

$$
\begin{bmatrix}
5&0&10\\
0&10&0\\
10&0&34
\end{bmatrix}
\begin{bmatrix}a\\b\\c\end{bmatrix}
=
\begin{bmatrix}14\\-2\\40\end{bmatrix}.
$$

Al resolver,

$$
\boxed{
a=\frac{38}{35},\qquad
b=-\frac15,\qquad
c=\frac67.
}
$$

Por tanto,

$$
\widehat f(t)=\frac{38}{35}-\frac15t+\frac67t^2.
$$

El vector de residuos, en el orden dado, es

$$
r=\frac1{35}
\begin{bmatrix}3\\-5\\-3\\9\\-4\end{bmatrix}.
$$

La igualdad $X^Tr=0$ significa aquí que

$$
\sum_i r_i=0,
\qquad
\sum_i t_ir_i=0,
\qquad
\sum_i t_i^2r_i=0.
$$

### Ejemplo 5.2. Aproximación afín en dos variables

Dados

$$
\begin{array}{c|cccc}
(x_i,y_i)&(0,0)&(1,0)&(0,1)&(1,1)\\ \hline
z_i&1&3&4&5
\end{array},
$$

buscamos el plano

$$
f(x,y)=a+bx+cy.
$$

La matriz de diseño y el vector de observaciones son

$$
X=
\begin{bmatrix}
1&0&0\\
1&1&0\\
1&0&1\\
1&1&1
\end{bmatrix},
\qquad
z=\begin{bmatrix}1\\3\\4\\5\end{bmatrix}.
$$

Las ecuaciones normales quedan

$$
\begin{bmatrix}
4&2&2\\
2&2&1\\
2&1&2
\end{bmatrix}
\begin{bmatrix}a\\b\\c\end{bmatrix}
=
\begin{bmatrix}13\\8\\9\end{bmatrix}.
$$

Su solución es

$$
\boxed{
a=\frac54,\qquad b=\frac32,\qquad c=\frac52,
}
$$

de modo que

$$
\widehat f(x,y)=\frac54+\frac32x+\frac52y.
$$

El residuo es

$$
r=z-X\beta
=\frac14\begin{bmatrix}-1\\1\\1\\-1\end{bmatrix},
\qquad X^Tr=0.
$$

### Modelamiento 5.3. Polinomio completo de grado dos en dos variables

Para observaciones $(x_i,y_i,z_i)$, modelamos

$$
f(x,y)=a+bx+cy+dx^2+exy+fy^2.
$$

La fila asociada a la observación $i$ es

$$
\phi_i^T=
\begin{bmatrix}
1&x_i&y_i&x_i^2&x_iy_i&y_i^2
\end{bmatrix},
$$

y la matriz de diseño se obtiene apilando esas filas:

$$
X=
\begin{bmatrix}
1&x_1&y_1&x_1^2&x_1y_1&y_1^2\\
\vdots&\vdots&\vdots&\vdots&\vdots&\vdots\\
1&x_m&y_m&x_m^2&x_my_m&y_m^2
\end{bmatrix},
\qquad
\beta=
\begin{bmatrix}a\\b\\c\\d\\e\\f\end{bmatrix},
\qquad
z=
\begin{bmatrix}z_1\\\vdots\\z_m\end{bmatrix}.
$$

El modelamiento termina en las ecuaciones normales

$$
\boxed{X^TX\beta=X^Tz.}
$$

Escritas por funciones base, son las seis ecuaciones

$$
\sum_{k=1}^6
\left(\sum_{i=1}^m\phi_j(x_i,y_i)\phi_k(x_i,y_i)\right)\beta_k
=
\sum_{i=1}^m\phi_j(x_i,y_i)z_i,
\qquad j=1,\ldots,6,
$$

donde

$$
(\phi_1,\ldots,\phi_6)=(1,x,y,x^2,xy,y^2).
$$

No cambia el método si se restringe el modelo. Por ejemplo:

1. sin interacción: $a+bx+cy+dx^2+ey^2$, con fila
   $[1,x_i,y_i,x_i^2,y_i^2]$;
2. modelo bilineal: $a+bx+cy+dxy$, con fila
   $[1,x_i,y_i,x_iy_i]$;
3. cuadrático solo en $x$: $a+bx+cy+dx^2$, con fila
   $[1,x_i,y_i,x_i^2]$.

En cada caso se forma la matriz con las columnas correspondientes y se plantea
$X^TX\beta=X^Tz$.

## 6. Medición del ajuste

### Definición 6.1. Sumas de cuadrados

Sea $\widehat y=X\beta^*$ y supongamos que la columna constante pertenece a
$\operatorname{Col}(X)$. Definimos

$$
\bar y=\frac1m\sum_{i=1}^m y_i,
\qquad
\overline y=(\bar y,\ldots,\bar y).
$$

La suma total de cuadrados y la suma de cuadrados del residuo son

$$
\mathrm{SST}=\|y-\overline y\|^2,
\qquad
\mathrm{SSE}=\|y-\widehat y\|^2.
$$

Si los datos no son todos iguales, el **coeficiente de determinación** es

$$
\boxed{R^2=1-\frac{\mathrm{SSE}}{\mathrm{SST}}.}
$$

### Teorema 6.2. Descomposición de la variabilidad

**Enunciado.** Si la columna constante está incluida en el modelo, entonces

$$
\|y-\overline y\|^2
=\|y-\widehat y\|^2+\|\widehat y-\overline y\|^2.
$$

En particular, si $\mathrm{SST}>0$,

$$
0\leq R^2\leq1.
$$

**Prueba.** Tanto $\widehat y$ como $\overline y$ pertenecen a
$\operatorname{Col}(X)$, mientras que $y-\widehat y$ es ortogonal a ese
subespacio. Por tanto,

$$
y-\overline y=(y-\widehat y)+(\widehat y-\overline y)
$$

es una suma ortogonal. Pitágoras da la identidad y las cotas. $\square$

Así, $R^2$ mide la fracción de la variabilidad respecto de la media explicada
por el subespacio del modelo. Un valor alto no prueba por sí solo que el
modelo sea apropiado; también deben examinarse los residuos y el contexto.

## 7. Extensión: regularización cuadrática

Cuando las columnas son dependientes o casi dependientes puede considerarse,
para $\alpha>0$,

$$
\min_x\bigl(\|Ax-b\|^2+\alpha\|x\|^2\bigr).
$$

Este problema equivale a mínimos cuadrados con

$$
\widetilde A=
\begin{bmatrix}A\\\sqrt\alpha I\end{bmatrix},
\qquad
\widetilde b=\begin{bmatrix}b\\0\end{bmatrix},
$$

y sus ecuaciones normales son

$$
\boxed{(A^TA+\alpha I)x=A^Tb.}
$$

La penalización favorece coeficientes pequeños y hace que la solución sea
única. El parámetro $\alpha$ introduce un compromiso entre ajuste y tamaño de
los coeficientes.

## 8. Errores frecuentes

1. Confundir los residuos verticales del ajuste de una función con las
   distancias euclídeas de los puntos a la curva.
2. Suponer que los coeficientes son únicos solo porque el vector ajustado lo
   es.
3. Calcular explícitamente $(A^TA)^{-1}$ en código numérico.
4. Interpretar $R^2$ sin verificar que el modelo contiene una constante.
5. Pensar que un modelo polinomial no es lineal: es lineal en sus
   coeficientes, que es lo relevante para mínimos cuadrados lineales.

## 9. Ejercicios

1. Halle la recta de mínimos cuadrados para $(0,1)$, $(1,2)$ y $(2,2)$.
   Verifique directamente que $X^Tr=0$.
2. Demuestre que si $b\in\operatorname{Col}(A)$, toda solución de mínimos
   cuadrados es una solución exacta de $Ax=b$.
3. Sea $A=[a_1\ a_2]$ con $a_2=2a_1$. Explique por qué el ajuste es único
   pero los coeficientes no lo son.
4. Construya la matriz de diseño para
   $f(t)=\beta_0+\beta_1t+\beta_2t^2+\beta_3t^3$.
5. Pruebe que, cuando el modelo contiene una constante, la suma de los
   residuos de mínimos cuadrados es cero.
6. Compare el ajuste lineal y cuadrático de un conjunto de datos mediante
   SSE y $R^2$. Examine además la gráfica de los residuos.
