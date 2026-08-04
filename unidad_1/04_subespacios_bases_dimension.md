# Subespacios, bases y dimensión

## Objetivos

Al finalizar este tema, el estudiante podrá:

1. verificar si un subconjunto de $\mathbb R^n$ es un subespacio;
2. distinguir un subespacio vectorial de un conjunto afín;
3. determinar bases a partir de generadores o ecuaciones homogéneas;
4. calcular la dimensión de un subespacio;
5. interpretar las coordenadas de un vector respecto de una base.

## 1. Subespacios de $\mathbb R^n$

### Definición 1.1. Subespacio vectorial

Un subconjunto **no vacío** $W\subseteq\mathbb R^n$ es un subespacio vectorial
si cumple:

1. **Cerradura para la suma:** si $u,v\in W$, entonces $u+v\in W$.
2. **Cerradura para el producto por escalares:** si $v\in W$ y
   $\lambda\in\mathbb R$, entonces $\lambda v\in W$.

La condición “no vacío” es necesaria: de otro modo, el conjunto vacío
satisfaría las dos implicaciones de manera vacía, pero no contiene al vector
cero.

### Proposición 1.2. Criterio de combinaciones lineales

**Enunciado.** Para un conjunto no vacío $W\subseteq\mathbb R^n$, son
equivalentes:

1. $W$ es un subespacio;
2. para todos $u,v\in W$ y $\alpha,\beta\in\mathbb R$,
   $\alpha u+\beta v\in W$.

**Prueba.** Si $W$ es subespacio, entonces $\alpha u,\beta v\in W$ por
cerradura para escalares y su suma pertenece a $W$. Recíprocamente, tomando
$(\alpha,\beta)=(1,1)$ se obtiene cerradura para la suma; tomando
$(\alpha,\beta)=(\lambda,0)$ se obtiene cerradura para escalares. $\square$

### Corolario 1.3. El vector cero pertenece a todo subespacio

**Prueba.** Como $W$ es no vacío, existe $v\in W$. Por cerradura para
escalares, $0v=0\in W$. $\square$

Por ello, una forma rápida de demostrar que un conjunto **no** es subespacio es
comprobar que no contiene al vector cero.

## 2. Ejemplos y contraejemplos

### Ejemplo 2.1. Subespacios básicos

Son subespacios de $\mathbb R^n$:

1. $\{0\}$;
2. $\mathbb R^n$;
3. toda recta que pasa por el origen;
4. todo plano que pasa por el origen;
5. $\operatorname{span}\{v_1,\ldots,v_r\}$;
6. el conjunto solución de un sistema homogéneo $Ax=0$.

Para probar 5, sean

$$
u=\sum_{j=1}^r a_jv_j,
\qquad
w=\sum_{j=1}^r b_jv_j.
$$

Entonces

$$
\alpha u+\beta w
=\sum_{j=1}^r(\alpha a_j+\beta b_j)v_j,
$$

que sigue siendo una combinación lineal de los generadores.

### Ejemplo 2.2. Ecuaciones homogéneas

El conjunto

$$
W=\{(x,y,z)\in\mathbb R^3:x+2y-z=0\}
$$

es un subespacio. Si $u,w\in W$, entonces

$$
[1\ 2\ {-1}](\alpha u+\beta w)
=\alpha[1\ 2\ {-1}]u+\beta[1\ 2\ {-1}]w=0.
$$

### Ejemplo 2.3. Una ecuación no homogénea

El conjunto

$$
H=\{(x,y,z)\in\mathbb R^3:x+2y-z=1\}
$$

no es un subespacio porque $0\notin H$.

## 3. Subespacios afines

### Definición 3.1. Conjunto afín

Un subconjunto $S\subseteq\mathbb R^n$ es **afín** si existen un punto
$x_0\in\mathbb R^n$ y un subespacio $W$ tales que

$$
S=x_0+W=\{x_0+w:w\in W\}.
$$

Si $Ax=b$ es compatible y $x_0$ es una solución particular, entonces

$$
\{x:Ax=b\}=x_0+\ker(A).
$$

**Prueba.** Si $Ax=b$, entonces
$A(x-x_0)=b-b=0$, de modo que $x-x_0\in\ker(A)$. Recíprocamente, si
$z\in\ker(A)$, entonces $A(x_0+z)=b$. $\square$

Un conjunto afín es subespacio vectorial si, y solo si, contiene al origen. En
el caso $Ax=b$, esto ocurre si, y solo si, $b=0$.

## 4. Operaciones con subespacios

### Proposición 4.1. Intersección

**Enunciado.** Si $U$ y $W$ son subespacios de $\mathbb R^n$, entonces
$U\cap W$ es un subespacio.

**Prueba.** El vector cero pertenece a ambos conjuntos. Si $u,v\in U\cap W$,
entonces $\alpha u+\beta v$ pertenece a $U$ y a $W$ por cerradura; por tanto,
pertenece a su intersección. $\square$

### Advertencia 4.2. La unión no suele ser subespacio

Los ejes coordenados

$$
U=\operatorname{span}\{(1,0)\},
\qquad
W=\operatorname{span}\{(0,1)\}
$$

son subespacios, pero $U\cup W$ no lo es: $(1,0),(0,1)\in U\cup W$ y
$(1,1)\notin U\cup W$.

### Definición 4.3. Suma de subespacios

La suma de $U$ y $W$ es

$$
U+W=\{u+w:u\in U,\ w\in W\}.
$$

La suma sí es siempre un subespacio. La suma directa se estudiará con mayor
detalle al final de la Unidad 1.

## 5. Bases

### Definición 5.1. Base

Sea $W$ un subespacio de $\mathbb R^n$. Una familia
$\mathcal B=(v_1,\ldots,v_r)$ es una **base** de $W$ si:

1. $v_1,\ldots,v_r$ son linealmente independientes;
2. $W=\operatorname{span}\{v_1,\ldots,v_r\}$.

Una base combina dos requisitos: no contiene direcciones redundantes y genera
todo el subespacio.

### Teorema 5.2. Unicidad de coordenadas

**Enunciado.** Si $\mathcal B=(v_1,\ldots,v_r)$ es una base de $W$, todo
$w\in W$ se expresa de manera única como

$$
w=c_1v_1+\cdots+c_rv_r.
$$

**Prueba.** La existencia se sigue de que $\mathcal B$ genera $W$. Si hubiera
dos expresiones,

$$
\sum_{j=1}^r c_jv_j=\sum_{j=1}^r d_jv_j,
$$

entonces

$$
\sum_{j=1}^r(c_j-d_j)v_j=0.
$$

La independencia implica $c_j-d_j=0$ para cada $j$. $\square$

El vector

$$
[w]_{\mathcal B}=\begin{bmatrix}c_1&\cdots&c_r\end{bmatrix}^T
$$

es el **vector de coordenadas** de $w$ en la base $\mathcal B$. El cambio entre
bases se desarrollará en C9.

## 6. Dimensión

### Teorema 6.1. Teorema de la dimensión

**Enunciado.** Todas las bases de un subespacio finito-dimensional tienen la
misma cantidad de vectores.

La prueba general usa el lema de intercambio: una familia linealmente
independiente no puede tener más elementos que una familia generadora del mismo
espacio.

### Definición 6.2. Dimensión

La **dimensión** de $W$, denotada $\dim(W)$, es el número de vectores de
cualquiera de sus bases.

Ejemplos:

$$
\dim\{0\}=0,
\qquad
\dim\mathbb R^n=n.
$$

Una recta vectorial tiene dimensión $1$ y un plano vectorial tiene dimensión
$2$.

### Teorema 6.3. Reducción y extensión de familias

Sea $W$ un subespacio finito-dimensional.

1. Toda familia generadora de $W$ puede reducirse a una base eliminando
   vectores redundantes.
2. Toda familia linealmente independiente contenida en $W$ puede extenderse a
   una base de $W$.

**Idea de prueba.** En el primer caso se elimina todo vector que sea combinación
de los demás; en el segundo se añaden vectores fuera del espacio ya generado.
El proceso termina porque no puede haber más de $\dim(W)$ vectores
independientes.

### Corolario 6.4. Tres condiciones relacionadas

Si $\dim(W)=d$ y $v_1,\ldots,v_r\in W$, cualquier par de las siguientes
afirmaciones implica la tercera:

1. $v_1,\ldots,v_r$ son linealmente independientes;
2. generan $W$;
3. $r=d$.

En particular:

- si $r<d$, no pueden generar todo $W$;
- si $r>d$, no pueden ser linealmente independientes.

## 7. Cómo calcular bases

### 7.1 A partir de generadores columna

Sea

$$
A=\begin{bmatrix}v_1&\cdots&v_r\end{bmatrix}.
$$

1. Calcule $\operatorname{rref}(A)$.
2. Identifique sus columnas pivote.
3. Seleccione las columnas con esos índices en la matriz **original** $A$.

Esas columnas forman una base de
$\operatorname{span}\{v_1,\ldots,v_r\}$.

### 7.2 A partir de generadores fila

Las operaciones elementales por filas no cambian el espacio generado por las
filas. Por tanto, las filas no nulas de $\operatorname{rref}(A)$ forman una
base del espacio fila de $A$.

```{admonition} Fila y columna se tratan de manera distinta
:class: warning
Para el espacio fila se usan las filas no nulas de la matriz reducida. Para el
espacio columna se recuperan las columnas pivote de la matriz original.
```

### 7.3 A partir de ecuaciones homogéneas

Si

$$
W=\{x\in\mathbb R^n:Ax=0\},
$$

se resuelve el sistema en función de las variables libres y se escribe

$$
x=t_1z_1+\cdots+t_kz_k.
$$

Los vectores $z_1,\ldots,z_k$ forman una base de $W$. La justificación y la
relación con el rango se desarrollan en el tema siguiente.

## 8. Ejemplo integrado

Considere

$$
W=\operatorname{span}\{(1,-1,1),(2,0,1),(-4,-2,-1),(3,1,2)\}.
$$

Al colocar los vectores como columnas y reducir, los índices pivote son
$1,2,4$. Por tanto,

$$
\{(1,-1,1),(2,0,1),(3,1,2)\}
$$

es una base de $W$ y $\dim(W)=3$. El tercer generador es redundante porque

$$
(-4,-2,-1)=2(1,-1,1)-3(2,0,1).
$$

Es indispensable verificar los índices mediante reducción: la cantidad
original de generadores no es la dimensión si existe redundancia.

## 9. Ejercicios

1. Determine cuáles conjuntos son subespacios de $\mathbb R^3$:

   - $\{(x,y,z):x-y+2z=0\}$;
   - $\{(x,y,z):x-y+2z=3\}$;
   - $\{(x,y,z):x\geq0\}$.

2. Pruebe que la intersección arbitraria de subespacios es un subespacio.
3. Halle una base y la dimensión de

   $$
   W=\left\{x\in\mathbb R^4:
   \begin{aligned}
   x_1+2x_2-4x_3+3x_4&=0,\\
   -x_1-2x_3+x_4&=0,\\
   x_1+x_2-x_3+2x_4&=0
   \end{aligned}\right\}.
   $$

4. Halle una base del espacio generado por
   $(1,2,3,4),(2,4,6,8),(0,1,1,1)$.
5. Sea $\mathcal B=((1,1),(1,-1))$. Calcule las coordenadas de $(5,1)$ en
   $\mathcal B$ y reconstruya el vector a partir de ellas.
