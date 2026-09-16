# Espacios vectoriales reales, conjuntos afines y suma directa

## Objetivos

Al finalizar este tema, el estudiante podrá:

1. reconocer espacios y subespacios vectoriales reales fuera de $\mathbb R^n$;
2. describir el espacio generado por un conjunto como una intersección de
   subespacios y como el conjunto de sus combinaciones lineales finitas;
3. estudiar generación, independencia lineal, bases y dimensión en espacios
   vectoriales abstractos;
4. distinguir un subespacio de una traslación afín;
5. calcular la suma y la intersección de dos subespacios;
6. decidir si una suma es directa;
7. relacionar suma directa, unicidad de descomposición y dimensión.

En las clases anteriores, las propiedades se estudiaron principalmente en
$\mathbb R^n$. Ahora se enuncian para un espacio vectorial real general. No se
introducen números complejos en esta unidad.

## 1. Espacio vectorial real

### Definición 1.1. Espacio vectorial

Un **espacio vectorial real** es un conjunto no vacío $V$ con una suma de
vectores y un producto por escalares reales que, para cualesquiera
$u,v,w\in V$ y $\lambda,\mu\in\mathbb R$, cumplen:

1. **Cierre aditivo:** $u+v\in V$.
2. **Conmutatividad:** $u+v=v+u$.
3. **Asociatividad aditiva:** $(u+v)+w=u+(v+w)$.
4. **Vector cero:** existe $0_V\in V$ tal que $v+0_V=v$.
5. **Inverso aditivo:** para cada $v$ existe $-v$ tal que $v+(-v)=0_V$.
6. **Cierre escalar:** $\lambda v\in V$.
7. **Compatibilidad escalar:** $(\lambda\mu)v=\lambda(\mu v)$ y $1v=v$.
8. **Distributividad:** $\lambda(u+v)=\lambda u+\lambda v$ y
   $(\lambda+\mu)v=\lambda v+\mu v$.

```{admonition} Los vectores no siempre son listas de números
:class: note
Una matriz, un polinomio o una función pueden ser vectores. Las operaciones y
los axiomas, no la apariencia de los objetos, determinan la estructura.
```

### Ejemplo 1.2. Espacios frecuentes

- $\mathbb R^n$, con las operaciones usuales.
- $M_{m\times n}(\mathbb R)$, el espacio de matrices reales de tamaño
  $m\times n$.
- $\mathcal P_n$, los polinomios reales de grado a lo sumo $n$.
- $\mathbb R[x]$, el espacio de todos los polinomios reales.
- $\mathcal F(X,\mathbb R)$, las funciones de un conjunto $X$ en $\mathbb R$.

En el espacio de matrices, las operaciones se realizan entrada a entrada. En
el espacio de funciones se definen puntualmente:

$$
(f+g)(x)=f(x)+g(x),
\qquad
(\lambda f)(x)=\lambda f(x).
$$

Así, si $X=[0,1]$, $f(x)=x^2$ y $g(x)=x+1$, entonces

$$
(f+g)(x)=x^2+x+1,
\qquad
(3f)(x)=3x^2.
$$

Los vectores de estos espacios son matrices, polinomios o funciones; no es
necesario identificarlos primero con una lista de coordenadas.

### Ejemplo 1.3. Polinomios y la cota del grado

El espacio

$$
\mathcal P_n
=\{a_0+a_1x+\cdots+a_nx^n:a_0,\ldots,a_n\in\mathbb R\}
$$

es cerrado bajo suma y producto por escalares. Aunque un polinomio pueda
escribirse con coeficientes finales iguales a cero, sus operaciones se definen
como operaciones entre polinomios, no como operaciones entre listas de una
longitud elegida de manera arbitraria.

Además,

$$
\mathcal P_0\subseteq\mathcal P_1\subseteq\cdots\subseteq\mathbb R[x].
$$

El polinomio $x^{800}+x$ pertenece a $\mathbb R[x]$ y a $\mathcal P_{800}$,
pero no a $\mathcal P_2$.

### Ejemplo 1.4. Subespacios de un espacio de funciones

En $\mathcal F(\mathbb R,\mathbb R)$, las funciones continuas forman un
subespacio y las funciones derivables forman otro. La función cero es la
función $0(x)=0$ para todo $x$, y el opuesto de $f$ es la función
$(-f)(x)=-f(x)$.

## 2. Criterio de subespacio

### Teorema 2.1. Criterio de combinación lineal

Sea $W$ un subconjunto no vacío de un espacio vectorial real
$V$. Entonces $W$ es subespacio de $V$ si y solo si

$$
\alpha u+\beta v\in W
\qquad
\text{para todos }u,v\in W\text{ y }\alpha,\beta\in\mathbb R.
$$

**Prueba.** Si $W$ es subespacio, la condición se obtiene de sus cerraduras.
Recíprocamente, tomando $\alpha=\beta=0$ se obtiene $0_V\in W$; con
$(\alpha,\beta)=(1,1)$ se obtiene cierre bajo suma, y con $\beta=0$ se obtiene
cierre bajo producto escalar. Los demás axiomas se heredan de $V$. $\square$

### Proposición 2.2. Intersecciones

La intersección de cualquier familia no vacía de subespacios de
$V$ es un subespacio de $V$.

**Prueba.** El vector cero pertenece a todos los subespacios. Si $u$ y $v$
pertenecen a la intersección, cada combinación $\alpha u+\beta v$ pertenece a
cada subespacio y, por tanto, a la intersección. $\square$

### Definición 2.3. Espacio generado

Sea $S\subseteq V$ y considere la familia de todos los subespacios que
contienen a $S$:

$$
\mathscr F_S
=\{W\subseteq V:W\text{ es subespacio de }V\text{ y }S\subseteq W\}.
$$

Esta familia no es vacía porque $V\in\mathscr F_S$. El **espacio generado**
por $S$ se define por

$$
\operatorname{span}(S)
=\bigcap_{W\in\mathscr F_S}W.
$$

Por la Proposición 2.2, $\operatorname{span}(S)$ es un subespacio. Además,
contiene a $S$ y está contenido en todo subespacio que contenga a $S$; por
ello es el **menor subespacio de $V$ que contiene a $S$**.

### Teorema 2.4. Descripción mediante combinaciones lineales

Si $S\neq\varnothing$, entonces

$$
\operatorname{span}(S)
=\left\{
\alpha_1v_1+\cdots+\alpha_rv_r:
r\in\mathbb N,\ v_1,\ldots,v_r\in S,\
\alpha_1,\ldots,\alpha_r\in\mathbb R
\right\}.
$$

Es importante que las combinaciones sean **finitas**, incluso cuando $S$ sea
infinito.

**Prueba.** El conjunto del lado derecho contiene a $S$ y es cerrado bajo
combinaciones lineales; por tanto, es un subespacio que contiene a $S$. A la
vez, cualquier subespacio que contenga a $S$ debe contener todas las
combinaciones lineales finitas de sus elementos. Las dos inclusiones dan la
igualdad. $\square$

En particular,

$$
\operatorname{span}(\varnothing)
=\bigcap_{W\in\mathscr F_{\varnothing}}W
=\{0_V\}.
$$

En efecto, todo subespacio contiene a $0_V$ y $\{0_V\}$ es uno de los
subespacios que aparecen en la intersección. Por tanto, la igualdad se sigue
directamente de la definición de espacio generado, sin adoptar un convenio
adicional. Asimismo, $\operatorname{span}(V)=V$, pues el único subespacio de
$V$ que contiene a $V$ es el propio $V$.

Esta conclusión es compatible con la descripción del Teorema 2.4 si se llama
**suma vacía** a la combinación sin sumandos, cuyo valor es $0_V$.

Si $S=\{v_1,\ldots,v_r\}$, se recupera la notación estudiada antes:

$$
\operatorname{span}\{v_1,\ldots,v_r\}
=\{\alpha_1v_1+\cdots+\alpha_rv_r:\alpha_i\in\mathbb R\}.
$$

### Ejemplo 2.5. Un conjunto generador infinito

En $\mathbb R[x]$,

$$
\operatorname{span}\{1,x,x^2,x^3,\ldots\}=\mathbb R[x].
$$

El conjunto generador es infinito, pero cada polinomio usa solamente un número
finito de monomios. En cambio,

$$
\operatorname{span}\{1,x,\ldots,x^n\}=\mathcal P_n.
$$

## 3. Independencia lineal, bases y dimensión

### Definición 3.1. Familia linealmente independiente

Los vectores $v_1,\ldots,v_r\in V$ son **linealmente independientes** si

$$
\alpha_1v_1+\cdots+\alpha_rv_r=0_V
$$

implica necesariamente
$\alpha_1=\cdots=\alpha_r=0$. Si existe una relación con algún coeficiente no
nulo, la familia es **linealmente dependiente**.

Un subconjunto $S\subseteq V$ es linealmente independiente si toda subfamilia
finita de elementos distintos de $S$ es linealmente independiente. Esta
formulación permite hablar, por ejemplo, de la independencia del conjunto
infinito $\{1,x,x^2,\ldots\}$.

### Definición 3.2. Base

Un subconjunto $\mathcal B\subseteq V$ es una **base** de $V$ si:

1. $\mathcal B$ es linealmente independiente;
2. $\operatorname{span}(\mathcal B)=V$.

La generación garantiza que todo vector se puede escribir usando elementos de
la base, y la independencia garantiza que esa escritura es única.

### Definición 3.3. Dimensión

Si $V$ posee una base finita, todas sus bases tienen la misma cantidad de
elementos. Esa cantidad se llama **dimensión** de $V$ y se denota $\dim V$.
Si no existe una base finita, se dice que $V$ es de dimensión infinita.

### Ejemplo 3.4. Bases en tres espacios abstractos

1. La familia $(1,x,\ldots,x^n)$ es una base de $\mathcal P_n$; por tanto,
   $\dim\mathcal P_n=n+1$.
2. Si $E_{ij}$ es la matriz que tiene un $1$ en la posición $(i,j)$ y ceros
   en las demás entradas, entonces
   $\{E_{ij}:1\leq i\leq m,\ 1\leq j\leq n\}$ es una base de
   $M_{m\times n}(\mathbb R)$ y su dimensión es $mn$.
3. El conjunto $\{1,x,x^2,\ldots\}$ es una base infinita de $\mathbb R[x]$.
   Los monomios generan todos los polinomios y son independientes porque un
   polinomio es cero exactamente cuando todos sus coeficientes son cero.

### Ejemplo 3.5. Independencia de funciones exponenciales

En el espacio de funciones derivables de $\mathbb R$ en $\mathbb R$, sean

$$
f_0(x)=1,
\qquad
f_1(x)=e^x,
\qquad
f_2(x)=e^{2x}.
$$

Suponga que, para todo $x\in\mathbb R$,

$$
\alpha_0+\alpha_1e^x+\alpha_2e^{2x}=0.
$$

Al derivar se obtiene

$$
\alpha_1e^x+2\alpha_2e^{2x}=0,
$$

y al derivar otra vez,

$$
\alpha_1e^x+4\alpha_2e^{2x}=0.
$$

La diferencia de las dos últimas identidades da
$2\alpha_2e^{2x}=0$, luego $\alpha_2=0$. Después se deduce
$\alpha_1=0$ y finalmente $\alpha_0=0$. Por tanto,
$\{f_0,f_1,f_2\}$ es linealmente independiente.

```{admonition} La igualdad entre funciones es puntual
:class: note
Una relación $\alpha_0f_0+\alpha_1f_1+\alpha_2f_2=0$ significa que la
igualdad se cumple para todo valor del argumento. Esta información permite
evaluar en puntos convenientes o derivar la identidad.
```

### Proposición 3.6. Caracterización de una base finita

Una familia $(v_1,\ldots,v_r)$ es una base de $V$ si y solo si cada
$v\in V$ posee una expresión única

$$
v=\alpha_1v_1+\cdots+\alpha_rv_r.
$$

**Prueba.** La existencia equivale a que la familia genere $V$. Si dos
expresiones representan al mismo vector, al restarlas se obtiene una relación
lineal; la independencia obliga a que los coeficientes correspondientes sean
iguales. Recíprocamente, la existencia da generación y la unicidad aplicada a
$0_V$ da independencia. $\square$

## 4. Subconjuntos afines

### Definición 4.1. Conjunto afín

Un subconjunto no vacío $A\subseteq V$ es **afín** si, para $x,y\in A$ y
$t\in\mathbb R$,

$$
(1-t)x+ty\in A.
$$

La suma de los coeficientes es $1$. Esto distingue una combinación afín de una
combinación lineal.

### Teorema 4.2. Caracterización por traslación

Un conjunto no vacío $A$ es afín si y solo si existen
$x_0\in V$ y un subespacio $W\subseteq V$ tales que

$$
A=x_0+W=\{x_0+w:w\in W\}.
$$

En ese caso, para cualquier $x_0\in A$, el espacio de direcciones es
$W=A-x_0$.

**Prueba.** Si $A$ es afín y $x_0\in A$, las combinaciones afines permiten
verificar que $A-x_0$ contiene al cero y es cerrado bajo combinaciones
lineales. Luego $A=x_0+(A-x_0)$. Recíprocamente, si $x=x_0+u$ e $y=x_0+v$,
entonces

$$
(1-t)x+ty=x_0+((1-t)u+tv)\in x_0+W.
$$

$\square$

Un conjunto afín es subespacio exactamente cuando contiene al vector cero.
Así, una recta que no pasa por el origen es afín, pero no es subespacio.

### Proposición 4.3. Conjunto de soluciones de $Ax=b$

Si $Ax=b$ es compatible y $x_p$ es una solución particular,
entonces

$$
\{x:Ax=b\}=x_p+\ker(A).
$$

**Prueba.** Si $Ax=b$, entonces $A(x-x_p)=0$, de modo que
$x-x_p\in\ker(A)$. La implicación inversa se obtiene de
$A(x_p+z)=b$ para $z\in\ker(A)$. $\square$

Por eso un sistema compatible indeterminado tiene un conjunto solución afín;
su espacio de direcciones es el núcleo.

## 5. Suma de subespacios

### Definición 5.1. Suma

Para subespacios $U,W\subseteq V$,

$$
U+W=\{u+w:u\in U,\ w\in W\}.
$$

### Proposición 5.2. La suma es subespacio

$U+W$ es el menor subespacio de $V$ que contiene a $U\cup W$.

**Prueba.** Es no vacío. Si $u_i\in U$ y $w_i\in W$, entonces

$$
\alpha(u_1+w_1)+\beta(u_2+w_2)
=(\alpha u_1+\beta u_2)+(\alpha w_1+\beta w_2)\in U+W.
$$

Todo subespacio que contenga a $U$ y a $W$ contiene además cada suma $u+w$.
$\square$

Si las columnas de $B_U$ y $B_W$ son bases de $U$ y $W$, respectivamente,
entonces

$$
U+W=\operatorname{Col}\!\begin{bmatrix}B_U&B_W\end{bmatrix}.
$$

## 6. Suma directa

### Definición 6.1. Suma directa

La suma $U+W$ es **directa**, y se escribe $U\oplus W$, si cada vector de la
suma posee una única descomposición $v=u+w$ con $u\in U$ y $w\in W$.

### Teorema 6.2. Criterio de intersección

Para subespacios $U,W\subseteq V$, son equivalentes:

1. $U+W=U\oplus W$.
2. $U\cap W=\{0_V\}$.
3. $u_1+w_1=u_2+w_2$ implica $u_1=u_2$ y $w_1=w_2$.

**Prueba.** Si la suma es directa y $z\in U\cap W$, entonces
$z+0=0+z$ son dos descomposiciones, luego $z=0$. Si la intersección es trivial
y $u_1+w_1=u_2+w_2$, entonces $u_1-u_2=w_2-w_1$ pertenece a la intersección;
por tanto, ambas diferencias son cero. La tercera afirmación es precisamente
la unicidad exigida en la definición. $\square$

### Teorema 6.3. Fórmula de dimensión

Si $U$ y $W$ son de dimensión finita,

$$
\dim(U+W)=\dim U+\dim W-\dim(U\cap W).
$$

**Idea de prueba.** Parta de una base de $U\cap W$, extiéndala a una base de
$U$ y a una base de $W$, y reúna los vectores añadidos una sola vez. El
conjunto resultante es una base de $U+W$.

### Corolario 6.4. Dimensión de una suma directa

Si $U\cap W=\{0\}$, entonces

$$
\dim(U\oplus W)=\dim U+\dim W.
$$

En particular, si además $\dim U+\dim W=\dim V$, entonces $V=U\oplus W$.

## 7. Criterios matriciales

Suponga que $B_U$ y $B_W$ tienen como columnas bases de $U,W\subseteq
\mathbb R^n$, y sea $B=[B_U\ B_W]$.

1. $\dim(U+W)=\operatorname{rango}(B)$.
2. La suma es directa si y solo si
   $\operatorname{rango}(B)=\dim U+\dim W$.
3. $\dim(U\cap W)=\dim U+\dim W-\operatorname{rango}(B)$.
4. $\mathbb R^n=U\oplus W$ si y solo si $B$ es cuadrada e invertible.

La ecuación $B_Ua=B_Wb$ equivale a

$$
\begin{bmatrix}B_U&-B_W\end{bmatrix}
\begin{bmatrix}a\\b\end{bmatrix}=0.
$$

Sus soluciones describen los vectores de $U\cap W$. Si $B_U$ y $B_W$ son
bases y la única solución es $a=b=0$, la suma es directa.

## 8. Ejemplo integrado

Sean

$$
U=\operatorname{span}\{(1,0,0),(0,1,0)\},\qquad
W=\operatorname{span}\{(0,0,1)\}.
$$

La matriz reunida es $I_3$, de rango $3$. Por ello
$U\cap W=\{0\}$ y $\mathbb R^3=U\oplus W$. Cada vector satisface

$$
(x,y,z)=(x,y,0)+(0,0,z),
$$

y esta descomposición es única.

En cambio, si $W'=\operatorname{span}\{(1,1,0)\}$, entonces $W'\subset U$.
Por tanto, $U+W'=U$ y la suma no es directa.

## 9. Comprobación conceptual

1. ¿Por qué $\{p\in\mathcal P_3:p(0)=0\}$ es subespacio?
2. ¿Por qué $\{p\in\mathcal P_3:p(0)=1\}$ es afín pero no subespacio?
3. Si $\dim U=3$, $\dim W=4$ y $\dim(U+W)=6$, ¿cuánto vale
   $\dim(U\cap W)$? ¿La suma es directa?
4. Si $V=U\oplus W$, explique por qué las bases de $U$ y $W$, reunidas,
   forman una base de $V$.
5. Pruebe directamente desde la definición como intersección que
   $S\subseteq T$ implica
   $\operatorname{span}(S)\subseteq\operatorname{span}(T)$.
6. Determine una base y la dimensión de $M_{2\times3}(\mathbb R)$.
7. Decida si $\{1+x,x+x^2,1-x^2\}$ es una base de $\mathcal P_2$.
