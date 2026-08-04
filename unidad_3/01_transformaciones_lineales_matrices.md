# Transformaciones lineales y representación matricial

## Objetivos

Al finalizar este bloque, podrás:

1. decidir si una aplicación entre espacios vectoriales es lineal;
2. calcular e interpretar su núcleo y su imagen;
3. relacionar inyectividad, sobreyectividad, rango y nulidad;
4. construir la matriz de una transformación respecto de bases dadas;
5. representar composiciones e inversas mediante productos e inversas de
   matrices;
6. distinguir una transformación de cualquiera de sus representaciones
   matriciales.

## 1. De una regla a una transformación lineal

Sean $V$ y $W$ espacios vectoriales sobre el mismo cuerpo $\mathbb K$.

### Definición 1.1. Transformación lineal

Una aplicación $T:V\to W$ es **lineal** si, para todos $u,v\in V$ y
$\alpha,\beta\in\mathbb K$,

$$
\boxed{T(\alpha u+\beta v)=\alpha T(u)+\beta T(v).}
$$

Esta única condición equivale a exigir por separado

$$
T(u+v)=T(u)+T(v),
\qquad
T(\alpha u)=\alpha T(u).
$$

```{admonition} Qué debe preservarse
:class: important
La linealidad no significa que la gráfica sea una recta. Significa que la
aplicación preserva todas las combinaciones lineales.
```

### Proposición 1.2. Consecuencias inmediatas

**Enunciado.** Si $T:V\to W$ es lineal, entonces:

1. $T(0_V)=0_W$;
2. $T(-u)=-T(u)$;
3. $T(u-v)=T(u)-T(v)$;
4. $T(\sum_{j=1}^r\alpha_jv_j)=\sum_{j=1}^r\alpha_jT(v_j)$.

**Prueba.** Como $0_V=0_V+0_V$,
$T(0_V)=T(0_V)+T(0_V)$ y, al sumar el opuesto, $T(0_V)=0_W$.
Luego

$$
0_W=T(0_V)=T(u-u)=T(u)+T(-u),
$$

de donde $T(-u)=-T(u)$. Las otras propiedades se obtienen por linealidad e
inducción en el número de sumandos. $\square$

### Ejemplo 1.3. Aplicaciones lineales

Son lineales:

1. $T:\mathbb R^2\to\mathbb R^2$, $T(x,y)=(2x,3y)$;
2. la rotación $R_\theta:\mathbb R^2\to\mathbb R^2$;
3. la proyección $P(x,y)=(x,0)$;
4. la derivación $D:\mathcal P_2\to\mathcal P_1$, $D(p)=p'$;
5. la multiplicación por una matriz fija, $T_A(x)=Ax$.

### Ejemplo 1.4. Cómo detectar que no es lineal

La aplicación

$$
F(x,y)=(x^2,y)
$$

no es lineal porque, por ejemplo,

$$
F(2(1,0))=(4,0)\neq(2,0)=2F(1,0).
$$

También es no lineal toda aplicación afín $F(x)=Ax+b$ con $b\neq0$, pues
$F(0)=b\neq0$.

## 2. Una transformación queda determinada por una base

### Teorema 2.1. Extensión lineal desde una base

**Enunciado.** Sea $\mathcal B=(v_1,\ldots,v_n)$ una base de $V$. Dados
vectores arbitrarios $w_1,\ldots,w_n\in W$, existe una única transformación
lineal $T:V\to W$ tal que

$$
T(v_j)=w_j,
\qquad j=1,\ldots,n.
$$

**Prueba.** Cada $x\in V$ tiene coordenadas únicas
$x=\sum_j\alpha_jv_j$. Definimos

$$
T(x)=\sum_{j=1}^n\alpha_jw_j.
$$

La unicidad de coordenadas hace que la definición sea consistente y permite
verificar la linealidad. Cualquier transformación con las imágenes indicadas
debe satisfacer esa misma fórmula, por lo que es única. $\square$

### Consecuencia 2.2

Para calcular $T(x)$ no es necesario conocer una fórmula cerrada si se conocen
las imágenes de una base: se calculan las coordenadas de $x$ y se combinan las
imágenes con esos mismos coeficientes.

## 3. Núcleo e imagen

### Definición 3.1

Para $T:V\to W$ lineal,

$$
\ker(T)=\{v\in V:T(v)=0_W\},
$$

$$
\operatorname{Im}(T)=T(V)=\{T(v):v\in V\}.
$$

El núcleo es un subconjunto del **dominio** y la imagen es un subconjunto del
**codominio**.

### Proposición 3.2. Son subespacios

**Enunciado.** $\ker(T)$ es subespacio de $V$ e
$\operatorname{Im}(T)$ es subespacio de $W$.

**Prueba.** Si $u,v\in\ker(T)$, entonces

$$
T(\alpha u+\beta v)=\alpha T(u)+\beta T(v)=0,
$$

por lo que el núcleo es cerrado bajo combinaciones lineales. Si
$y_1=T(u)$ e $y_2=T(v)$ pertenecen a la imagen, entonces

$$
\alpha y_1+\beta y_2=T(\alpha u+\beta v)
$$

también pertenece a ella. $\square$

### Ejemplo 3.3. Núcleo e imagen en $\mathbb R^n$

Sea

$$
T:\mathbb R^3\to\mathbb R^2,
\qquad
T(x,y,z)=(x+y,y+z).
$$

Para el núcleo resolvemos

$$
x+y=0,
\qquad
y+z=0.
$$

Así,

$$
\ker(T)=\operatorname{span}\{(-1,1,-1)\}.
$$

Las imágenes de la base canónica son

$$
T(e_1)=(1,0),
\qquad
T(e_2)=(1,1),
\qquad
T(e_3)=(0,1).
$$

Como $(1,0)$ y $(0,1)$ pertenecen a la imagen,

$$
\operatorname{Im}(T)=\mathbb R^2.
$$

### Ejemplo 3.4. Derivación

Para $D:\mathcal P_2\to\mathcal P_1$, $D(p)=p'$,

$$
\ker(D)=\operatorname{span}\{1\},
\qquad
\operatorname{Im}(D)=\mathcal P_1.
$$

El ejemplo muestra que los elementos del dominio y el codominio no tienen que
ser columnas.

## 4. Inyectividad, sobreyectividad e isomorfismos

### Definición 4.1

Una transformación lineal $T:V\to W$ es:

- **inyectiva** si $T(u)=T(v)$ implica $u=v$;
- **sobreyectiva** si $\operatorname{Im}(T)=W$;
- un **isomorfismo** si es inyectiva y sobreyectiva.

Dos espacios son isomorfos cuando existe un isomorfismo entre ellos. Esto
significa que poseen la misma estructura lineal, aunque sus elementos se
presenten de manera distinta.

### Teorema 4.2. Criterio del núcleo

**Enunciado.** $T$ es inyectiva si y solo si

$$
\boxed{\ker(T)=\{0_V\}.}
$$

**Prueba.** Si $T$ es inyectiva y $T(v)=0_W=T(0_V)$, entonces $v=0_V$.
Recíprocamente, si $T(u)=T(v)$, entonces $T(u-v)=0_W$. Un núcleo trivial
implica $u-v=0_V$, es decir, $u=v$. $\square$

### Teorema 4.3. Rango-nulidad

**Enunciado.** Si $V$ tiene dimensión finita, entonces

$$
\boxed{
\dim V=\dim\ker(T)+\dim\operatorname{Im}(T).
}
$$

**Idea de prueba.** Se toma una base del núcleo y se completa a una base de
$V$. Las imágenes de los vectores añadidos forman una base de
$\operatorname{Im}(T)$.

### Corolario 4.4. Igual dimensión

Si $\dim V=\dim W<\infty$, entonces son equivalentes:

1. $T$ es inyectiva;
2. $T$ es sobreyectiva;
3. $T$ es un isomorfismo.

**Prueba.** Un núcleo trivial equivale a rango $\dim V=\dim W$, que equivale
a que la imagen sea todo $W$. $\square$

### Corolario 4.5. Dimensión e isomorfismo

Dos espacios vectoriales de dimensión finita sobre el mismo cuerpo son
isomorfos si y solo si tienen la misma dimensión.

## 5. Representación matricial en bases canónicas

Sea $T:\mathbb R^n\to\mathbb R^m$ lineal y
$\mathcal E=(e_1,\ldots,e_n)$ la base canónica del dominio.

### Teorema 5.1. Matriz canónica

**Enunciado.** Existe una única matriz $A\in\mathbb R^{m\times n}$ tal que

$$
\boxed{T(x)=Ax.}
$$

Sus columnas son las imágenes de los vectores canónicos:

$$
\boxed{A=[\,T(e_1)\ \cdots\ T(e_n)\,].}
$$

**Prueba.** Si $x=\sum_jx_je_j$, la linealidad da

$$
T(x)=\sum_jx_jT(e_j),
$$

que es precisamente el producto de la matriz indicada por $x$. La unicidad se
obtiene evaluando cualquier matriz representante en cada $e_j$. $\square$

Para el Ejemplo 3.3,

$$
[T]_{\mathcal E_2\leftarrow\mathcal E_3}
=\begin{bmatrix}1&1&0\\0&1&1\end{bmatrix}.
$$

Además,

$$
\ker(T)=\ker(A),
\qquad
\operatorname{Im}(T)=\operatorname{Col}(A).
$$

## 6. Matriz relativa a bases cualesquiera

Sean $\mathcal B=(b_1,\ldots,b_n)$ una base de $V$ y
$\mathcal C=(c_1,\ldots,c_m)$ una base de $W$.

### Definición 6.1. Matriz relativa

La matriz de $T:V\to W$ respecto de $\mathcal B$ y $\mathcal C$ es

$$
\boxed{
[T]_{\mathcal C\leftarrow\mathcal B}
=\begin{bmatrix}
[T(b_1)]_{\mathcal C}&\cdots&[T(b_n)]_{\mathcal C}
\end{bmatrix}.
}
$$

Su propiedad fundamental es

$$
\boxed{
[T(x)]_{\mathcal C}
=[T]_{\mathcal C\leftarrow\mathcal B}[x]_{\mathcal B}.
}
$$

```{admonition} Lectura de la flecha
:class: note
La matriz recibe coordenadas en $\mathcal B$ y devuelve coordenadas en
$\mathcal C$. Por eso escribimos $\mathcal C\leftarrow\mathcal B$.
```

### Proposición 6.2. Fórmula mediante matrices de bases

En espacios de columnas, sea $A$ la matriz canónica de $T$, y sean
$M_{\mathcal B}$ y $M_{\mathcal C}$ las matrices que contienen las bases como
columnas. Entonces

$$
\boxed{
[T]_{\mathcal C\leftarrow\mathcal B}
=M_{\mathcal C}^{-1}AM_{\mathcal B}.
}
$$

**Prueba.** Partimos de
$x=M_{\mathcal B}[x]_{\mathcal B}$. Luego

$$
T(x)=AM_{\mathcal B}[x]_{\mathcal B}.
$$

Para expresar la salida en $\mathcal C$, multiplicamos por
$M_{\mathcal C}^{-1}$. $\square$

### Caso especial 6.3. Operador

Si $T:V\to V$ y se usa una misma base $\mathcal B$ en dominio y codominio,

$$
[T]_{\mathcal B}=M_{\mathcal B}^{-1}AM_{\mathcal B}.
$$

Las matrices $A$ y $[T]_{\mathcal B}$ son **similares**. Representan el mismo
operador en bases diferentes. Esta observación será central al estudiar
diagonalización.

## 7. Composición e inversa

### Teorema 7.1. Matriz de una composición

**Enunciado.** Sean $T:U\to V$ y $S:V\to W$ lineales, con bases compatibles
$\mathcal B$, $\mathcal C$ y $\mathcal D$. Entonces

$$
\boxed{
[S\circ T]_{\mathcal D\leftarrow\mathcal B}
=[S]_{\mathcal D\leftarrow\mathcal C}
[T]_{\mathcal C\leftarrow\mathcal B}.
}
$$

**Prueba.** Para todo $x\in U$,

$$
\begin{aligned}
[(S\circ T)(x)]_{\mathcal D}
&=[S]_{\mathcal D\leftarrow\mathcal C}[T(x)]_{\mathcal C}\\
&=[S]_{\mathcal D\leftarrow\mathcal C}
[T]_{\mathcal C\leftarrow\mathcal B}[x]_{\mathcal B}.
\end{aligned}
$$

La unicidad de la matriz representante da el resultado. $\square$

El orden importa: aplicar primero $T$ y luego $S$ produce el producto
$[S][T]$.

### Teorema 7.2. Inversa

**Enunciado.** Si $T:V\to W$ es un isomorfismo, entonces $T^{-1}:W\to V$ es
lineal y

$$
\boxed{
[T^{-1}]_{\mathcal B\leftarrow\mathcal C}
=([T]_{\mathcal C\leftarrow\mathcal B})^{-1}.
}
$$

**Idea de prueba.** La linealidad de la inversa se obtiene aplicando $T$ a
$T^{-1}(\alpha y_1+\beta y_2)$ y usando la unicidad de la preimagen. La
identidad matricial sigue de representar $T^{-1}\circ T=I_V$.

## 8. Ejemplo integrado

Sea

$$
T:\mathbb R^3\to\mathbb R^2,
\qquad
T(x,y,z)=(x+2y,y+z),
$$

con

$$
\mathcal B=((1,0,0),(1,1,0),(0,1,1)),
$$

$$
\mathcal C=((1,1),(1,0)).
$$

La matriz canónica y las matrices de bases son

$$
A=\begin{bmatrix}1&2&0\\0&1&1\end{bmatrix},
\quad
M_{\mathcal B}=\begin{bmatrix}1&1&0\\0&1&1\\0&0&1\end{bmatrix},
\quad
M_{\mathcal C}=\begin{bmatrix}1&1\\1&0\end{bmatrix}.
$$

Por tanto,

$$
\boxed{
[T]_{\mathcal C\leftarrow\mathcal B}
=M_{\mathcal C}^{-1}AM_{\mathcal B}
=\begin{bmatrix}0&1&2\\1&2&0\end{bmatrix}.
}
$$

La primera columna es $[T(1,0,0)]_{\mathcal C}$, la segunda es
$[T(1,1,0)]_{\mathcal C}$ y la tercera es
$[T(0,1,1)]_{\mathcal C}$.

## 9. Errores frecuentes

1. Confundir $\operatorname{Im}(T)$ con el codominio completo.
2. Colocar el núcleo en el codominio o la imagen en el dominio.
3. Probar linealidad solamente con algunos vectores.
4. Construir la matriz con las imágenes como filas en vez de columnas.
5. Usar coordenadas canónicas cuando la salida se pide en otra base.
6. Invertir el orden en la matriz de una composición.
7. Concluir que una transformación es invertible solo porque dominio y
   codominio tienen igual dimensión.
8. Confundir la transformación con una matriz particular que la representa.
9. Aplicar la fórmula de similitud a una transformación entre espacios de
   dimensiones distintas.

## 10. Ejercicios

### Ejercicio 1 (presentación C14-C15, adaptado)

Para $T:\mathbb R^3\to\mathbb R^2$,
$T(x,y,z)=(x+y,y+z)$, calcula núcleo, imagen, rango y nulidad. Decide si es
inyectiva o sobreyectiva.

### Ejercicio 2 (elaboración para esta hoja)

Decide cuáles aplicaciones son lineales y justifica:

1. $T(x,y)=(x-2y,3x+y)$;
2. $F(x,y)=(x-2y+1,3x+y)$;
3. $D:\mathcal P_3\to\mathcal P_2$, $D(p)=p'$;
4. $E:\mathcal P_3\to\mathbb R$, $E(p)=p(1)$.

### Ejercicio 3 (material de cambio de base, adaptado)

Construye $[T]_{\mathcal C\leftarrow\mathcal B}$ para el ejemplo integrado
calculando directamente cada una de sus columnas. Verifica después la fórmula
$M_{\mathcal C}^{-1}AM_{\mathcal B}$.

### Ejercicio 4 (elaboración para esta hoja)

Sean $T:\mathbb R^2\to\mathbb R^3$ y $S:\mathbb R^3\to\mathbb R^2$ dadas
por

$$
T(x,y)=(x,y,x+y),
\qquad
S(a,b,c)=(a+c,b-c).
$$

Calcula las matrices de $S\circ T$ y $T\circ S$. Compara tamaños, núcleos e
imágenes y explica por qué las composiciones no cumplen el mismo papel.
