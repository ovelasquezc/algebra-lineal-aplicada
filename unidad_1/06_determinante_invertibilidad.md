# Determinante e invertibilidad

## Objetivos

Al finalizar este tema, el estudiante podrá:

1. calcular determinantes por expansión y por eliminación;
2. anticipar cómo cambia el determinante bajo operaciones elementales;
3. relacionar determinante, rango, independencia e invertibilidad;
4. usar el determinante para detectar matrices singulares;
5. interpretar el valor absoluto del determinante como factor de escala.

## 1. Qué mide el determinante

Para una matriz cuadrada

$$
A=\begin{bmatrix}A_1&\cdots&A_n\end{bmatrix}
\in\mathbb R^{n\times n},
$$

el determinante asigna un escalar a sus columnas. Este escalar registra dos
aspectos:

- $\det(A)=0$ cuando las columnas pierden una dimensión y son dependientes;
- $|\det(A)|$ es el factor por el cual $A$ escala volúmenes $n$-dimensionales.

El signo registra la orientación.

## 2. Recordatorio: determinantes de orden $1$, $2$ y $3$

Antes de formular el determinante en orden general, recordemos las expresiones
que ya se conocen para matrices pequeñas.

### Orden $1$

Para una matriz $1\times1$,

$$
\det([a])=a.
$$

Por ejemplo, $\det([-5])=-5$.

### Orden $2$

Para una matriz $2\times2$,

$$
\det\begin{bmatrix}a&b\\c&d\end{bmatrix}=ad-bc.
$$

Geométricamente, el valor absoluto es el área del paralelogramo generado por
las columnas.

#### Ejemplo 2.1

$$
\det\begin{bmatrix}2&-1\\3&4\end{bmatrix}
=2(4)-(-1)(3)=11.
$$

### Orden $3$

Para una matriz $3\times3$, puede usarse la expresión conocida obtenida al
desarrollar por la primera fila:

$$
\det\begin{bmatrix}
a&b&c\\d&e&f\\g&h&i
\end{bmatrix}
=a(ei-fh)-b(di-fg)+c(dh-eg).
$$

#### Ejemplo 2.2

$$
\begin{aligned}
\det\begin{bmatrix}
1&2&0\\
-1&3&1\\
2&0&4
\end{bmatrix}
&=1(12)-2(-6)+0\\
&=24.
\end{aligned}
$$

En particular, para una matriz triangular de orden $1$, $2$ o $3$, el
determinante es el producto de los elementos diagonales. Más adelante veremos
que esto vale en cualquier orden.

```{admonition} Propósito de este recordatorio
:class: note
Estas fórmulas permiten calcular determinantes pequeños. La definición que
sigue no parte de una regla especial para cada tamaño: caracteriza una sola
función determinante válida para todo orden $n$.
```

## 3. Definición general mediante propiedades

### Definición 3.1. Determinante

El determinante es la única función

$$
\det:(\mathbb R^n)^n\longrightarrow\mathbb R
$$

que cumple:

1. **Multilinealidad.** El determinante es lineal en **una columna a la vez**
   cuando todas las demás permanecen fijas. Para cada posición $j$,
   cualesquiera columnas $u,v\in\mathbb R^n$ y escalares
   $\alpha,\beta\in\mathbb R$,

   $$
   \begin{aligned}
   &\det(A_1,\ldots,A_{j-1},\alpha u+\beta v,A_{j+1},\ldots,A_n)\\
   &\quad=
   \alpha\det(A_1,\ldots,A_{j-1},u,A_{j+1},\ldots,A_n)\\
   &\qquad+
   \beta\det(A_1,\ldots,A_{j-1},v,A_{j+1},\ldots,A_n).
   \end{aligned}
   $$

   En particular, multiplicar **una sola columna** por $\lambda$ multiplica
   el determinante por $\lambda$.

2. **Alternancia.** Si se intercambian dos columnas cualesquiera $A_j$ y
   $A_k$, con $j\neq k$, el determinante cambia de signo:

   $$
   \det(A_1,\ldots,A_j,\ldots,A_k,\ldots,A_n)
   =-\det(A_1,\ldots,A_k,\ldots,A_j,\ldots,A_n).
   $$

   Como consecuencia, si dos columnas son iguales, el determinante es cero.

3. **Normalización.** La matriz identidad tiene determinante uno:

   $$
   \det(I_n)=\det(e_1,\ldots,e_n)=1.
   $$

Aunque la definición se ha escrito usando columnas, las propiedades análogas
se cumplen por filas: el determinante es lineal en una fila cuando las demás
se fijan, e intercambiar dos filas cambia su signo.

### Ejemplos 3.2. Las propiedades en matrices conocidas

Ahora podemos usar las fórmulas recordadas en la sección anterior para
comprobar concretamente las propiedades de la definición.

**Multilinealidad.** Fijemos la primera columna $A_1=(1,2)^T$ y escribamos
$(3,4)^T=(3,0)^T+(0,4)^T$. Entonces

$$
\begin{aligned}
\det\begin{bmatrix}1&3\\2&4\end{bmatrix}
&=\det\begin{bmatrix}1&3\\2&0\end{bmatrix}
  +\det\begin{bmatrix}1&0\\2&4\end{bmatrix}\\
&=-6+4=-2.
\end{aligned}
$$

**Alternancia.** Al intercambiar las dos columnas,

$$
\det\begin{bmatrix}1&3\\2&4\end{bmatrix}=-2,
\qquad
\det\begin{bmatrix}3&1\\4&2\end{bmatrix}=2.
$$

**Normalización.** En orden tres,

$$
\det\begin{bmatrix}
1&0&0\\
0&1&0\\
0&0&1
\end{bmatrix}=1.
$$

Combinando normalización y multilinealidad,

$$
\det\begin{bmatrix}
2&0&0\\
0&-3&0\\
0&0&4
\end{bmatrix}
=2(-3)(4)\det(I_3)=-24.
$$

## 4. Consecuencias inmediatas

### Proposición 4.1. Columnas repetidas

**Enunciado.** Si dos columnas de $A$ son iguales, entonces $\det(A)=0$.

**Prueba.** Intercambiar esas columnas no cambia la matriz, pero por alternancia
cambia el signo del determinante. Así,
$\det(A)=-\det(A)$ y, por tanto, $\det(A)=0$. $\square$

### Corolario 4.2. Columnas dependientes

**Enunciado.** Si las columnas de $A$ son linealmente dependientes, entonces
$\det(A)=0$.

**Idea de prueba.** Despeje una columna como combinación de las demás y use la
multilinealidad. Cada término resultante tiene dos columnas proporcionales y,
por alternancia, determinante cero.

## 5. Menores, cofactores y fórmula de Laplace

### Definición 5.1. Menor y cofactor

La matriz $A_{ij}$ se obtiene eliminando la fila $i$ y la columna $j$ de $A$.
El cofactor correspondiente es

$$
C_{ij}=(-1)^{i+j}\det(A_{ij}).
$$

### Teorema 5.2. Expansión de Laplace

**Enunciado.** El determinante puede expandirse por cualquier fila $i$:

$$
\det(A)=\sum_{j=1}^n a_{ij}C_{ij},
$$

o por cualquier columna $j$:

$$
\det(A)=\sum_{i=1}^n a_{ij}C_{ij}.
$$

```{admonition} Por qué aparecen determinantes de orden $n-1$
:class: note
Fijemos la columna $j$ para realizar el desarrollo y escribámosla en la base
canónica:

$$
A_j=\sum_{i=1}^n a_{ij}e_i.
$$

Por multilinealidad en esa columna,

$$
\det(A_1,\ldots,A_j,\ldots,A_n)
=\sum_{i=1}^n a_{ij}
\det(A_1,\ldots,e_i,\ldots,A_n).
$$

Una vez fijada $e_i$ en la posición $j$, el término restante es una función
multilineal y alternante de las otras $n-1$ columnas. Al eliminar la coordenada
$i$ de esas columnas, dicha función es, salvo el signo
$(-1)^{i+j}$, **el único determinante de orden $n-1$**. Por eso

$$
\det(A_1,\ldots,e_i,\ldots,A_n)
=(-1)^{i+j}\det(A_{ij}),
$$

y se obtiene la fórmula de Laplace

$$
\det(A)=\sum_{i=1}^n a_{ij}(-1)^{i+j}\det(A_{ij}).
$$

La expansión tiene así un sentido recursivo: el determinante de orden $n$ se
construye a partir del único determinante ya definido en orden $n-1$, hasta
llegar al caso inicial $\det([a])=a$.
```

### Ejemplo 5.3. Expansión simbólica

Para

$$
A=\begin{bmatrix}a&b&c\\d&e&f\\g&h&i\end{bmatrix},
$$

la expansión por la primera fila es

$$
\det(A)
=a\begin{vmatrix}e&f\\h&i\end{vmatrix}
-b\begin{vmatrix}d&f\\g&i\end{vmatrix}
+c\begin{vmatrix}d&e\\g&h\end{vmatrix}.
$$

Conviene expandir por una fila o columna con muchos ceros. Para matrices
grandes, la eliminación es mucho más eficiente.

### Proposición 5.4. Determinante de una matriz triangular

**Enunciado.** Si $A\in\mathbb R^{n\times n}$ es triangular superior o
triangular inferior, entonces

$$
\boxed{
\det(A)=a_{11}a_{22}\cdots a_{nn}.
}
$$

**Idea de prueba.** Se aplica repetidamente la expansión de Laplace por una
fila o columna extrema. En cada paso, los ceros eliminan todos los términos
salvo el que contiene el elemento diagonal correspondiente. $\square$

## 6. Efecto de las operaciones elementales

### Teorema 6.1. Operaciones por filas

Si $B$ se obtiene de $A$ mediante una operación elemental:

1. $F_i\leftrightarrow F_j$ implica $\det(B)=-\det(A)$.
2. $F_i\leftarrow\lambda F_i$ implica
   $\det(B)=\lambda\det(A)$.
3. $F_j\leftarrow F_j+\lambda F_i$ implica
   $\det(B)=\det(A)$.

**Prueba de 3.** Por linealidad en la fila modificada,

$$
\det(\ldots,F_j+\lambda F_i,\ldots)
=\det(\ldots,F_j,\ldots)
+\lambda\det(\ldots,F_i,\ldots).
$$

El segundo término tiene dos filas iguales y es cero. Las propiedades por filas
se deducen de las propiedades por columnas, o de
$\det(A^T)=\det(A)$. $\square$

### Algoritmo 6.2. Determinante por eliminación

1. Lleve $A$ a una matriz triangular superior usando reemplazos de filas e
   intercambios.
2. Registre cada intercambio de filas y cada escalamiento.
3. Multiplique los elementos de la diagonal.
4. Corrija el signo y los factores acumulados.

Si se evita normalizar los pivotes, los reemplazos no cambian el determinante y
solo es necesario registrar intercambios.

## 7. Propiedades fundamentales

### Teorema 7.1. Producto

**Enunciado.** Para matrices cuadradas del mismo orden,

$$
\det(AB)=\det(A)\det(B).
$$

### Corolario 7.2. Transpuesta, potencias e inversa

1. $\det(A^T)=\det(A)$.
2. $\det(A^k)=\det(A)^k$ para $k\in\mathbb N$.
3. Si $A$ es invertible,

   $$
   \det(A^{-1})=\frac{1}{\det(A)}.
   $$

**Prueba de 3.** Como $AA^{-1}=I$,

$$
1=\det(I)=\det(A)\det(A^{-1}).
$$

Además, para $A\in\mathbb R^{n\times n}$,

$$
\det(\lambda A)=\lambda^n\det(A),
$$

porque el factor $\lambda$ aparece en cada una de las $n$ columnas.

```{admonition} Multiplicar una fila no es multiplicar toda la matriz
:class: warning
Si se multiplica **una sola fila o columna** de $A$ por $\lambda$, el
determinante queda multiplicado por $\lambda$. En cambio, $\lambda A$
multiplica todas las entradas por $\lambda$: puede verse como multiplicar cada
una de las $n$ filas por $\lambda$ o, equivalentemente, cada una de las $n$
columnas. Son dos descripciones de la misma operación, no $2n$ escalamientos.
Por eso

$$
\boxed{\det(\lambda A)=\lambda^n\det(A),}
$$

no $\lambda\det(A)$.

Por ejemplo, si

$$
A=\begin{bmatrix}1&2\\3&4\end{bmatrix},
\qquad \det(A)=-2,
$$

entonces

$$
\det(3A)
=\det\begin{bmatrix}3&6\\9&12\end{bmatrix}
=-18
=3^2\det(A),
$$

mientras que $3\det(A)=-6$. Para una matriz $3\times3$, el factor sería
$\lambda^3$.

Dos consecuencias útiles son

$$
\det(\lambda I_n)=\lambda^n,
\qquad
\det(-A)=(-1)^n\det(A).
$$

Así, cambiar el signo de **toda** una matriz de orden par no cambia su
determinante; para orden impar sí cambia el signo.
```

```{admonition} El determinante no es lineal en la matriz completa
:class: warning
En general,
$\det(A+B)\neq\det(A)+\det(B)$. La multilinealidad se refiere a variar una
sola fila o columna mientras las demás permanecen fijas.
```

## 8. Determinante e invertibilidad

### Teorema 8.1. Teorema de la matriz invertible

Para $A\in\mathbb R^{n\times n}$, son equivalentes:

1. $A$ es invertible.
2. $\det(A)\neq0$.
3. $\operatorname{rango}(A)=n$.
4. $\operatorname{rref}(A)=I_n$.
5. Las columnas de $A$ son linealmente independientes.
6. Las columnas de $A$ generan $\mathbb R^n$.
7. Las filas de $A$ son linealmente independientes.
8. $\ker(A)=\{0\}$.
9. Para todo $b\in\mathbb R^n$, $Ax=b$ tiene solución única.

**Idea de prueba.** Durante la eliminación, una matriz cuadrada tiene rango
completo exactamente cuando aparece un pivote en cada columna, es decir, cuando
se reduce a $I_n$. En ese caso es un producto de matrices elementales
invertibles. Si falta un pivote, la forma escalonada tiene una fila nula y su
determinante es cero. Las equivalencias con independencia, generación y núcleo
se obtuvieron mediante rango y rango–nulidad.

Una matriz con determinante cero se llama **singular**; una matriz con
determinante no nulo se llama **no singular**.

## 9. Propiedades de la inversa

Si $A$ y $B$ son invertibles:

1. $(A^{-1})^{-1}=A$.
2. $(A^T)^{-1}=(A^{-1})^T$.
3. $(AB)^{-1}=B^{-1}A^{-1}$.

**Prueba de 3.**

$$
(AB)(B^{-1}A^{-1})
=A(BB^{-1})A^{-1}=I,
$$

y el producto en el orden inverso también es $I$. $\square$

## 10. Tipos de matrices relacionados

Una matriz cuadrada $A$ puede ser:

- **diagonal:** $a_{ij}=0$ para $i\neq j$;
- **triangular superior:** $a_{ij}=0$ para $i>j$;
- **triangular inferior:** $a_{ij}=0$ para $i<j$;
- **simétrica:** $A=A^T$;
- **antisimétrica:** $A=-A^T$;
- **idempotente:** $A^2=A$;
- **nilpotente:** $A^k=0$ para algún $k\geq1$;
- **ortogonal:** $A^TA=AA^T=I$.

Para una matriz ortogonal, $A^{-1}=A^T$ y

$$
\det(A)^2=1,
$$

por lo que $\det(A)=\pm1$.

## 11. Ejercicios

1. Calcule por Laplace y por eliminación:

   $$
   \det\begin{bmatrix}
   2&-1&0\\
   3&4&1\\
   0&5&2
   \end{bmatrix}.
   $$

2. Si $A\in\mathbb R^{3\times3}$ y $\det(A)=-5$, calcule, sin conocer las
   entradas de $A$,

   $$
   \det(2A),\qquad
   \det(-A),\qquad
   \det\left(\frac12A\right).
   $$

   Explique por qué ninguno de estos cálculos requiere expandir un
   determinante.
3. Encuentre un contraejemplo para
   $\det(A+B)=\det(A)+\det(B)$.
4. Demuestre que si $A$ es triangular e invertible, todos sus elementos
   diagonales son no nulos.
5. Use determinantes para decidir para qué valores de $a$ es invertible

   $$
   A(a)=\begin{bmatrix}
   1&a&1&3\\
   a&1&3&1\\
   1&3&1&a\\
   3&1&a&1
   \end{bmatrix}.
   $$

6. Pruebe que

   $$
   \begin{bmatrix}
   2&-2&-4\\
   -1&3&4\\
   1&-2&-3
   \end{bmatrix}
   $$

   es idempotente. ¿Puede ser invertible una matriz idempotente distinta de
   $I$? Justifique.
