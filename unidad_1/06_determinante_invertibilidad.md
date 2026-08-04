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

## 2. Definición mediante propiedades

### Definición 2.1. Determinante

El determinante es la única función

$$
\det:(\mathbb R^n)^n\longrightarrow\mathbb R
$$

que cumple:

1. **Multilinealidad:** es lineal en cada columna cuando las demás se mantienen
   fijas.
2. **Alternancia:** intercambiar dos columnas cambia el signo.
3. **Normalización:** $\det(I_n)=1$.

La multilinealidad en la columna $i$ significa, por ejemplo,

$$
\begin{aligned}
&\det(A_1,\ldots,\alpha u+\beta v,\ldots,A_n)\\
&\qquad=\alpha\det(A_1,\ldots,u,\ldots,A_n)
+\beta\det(A_1,\ldots,v,\ldots,A_n).
\end{aligned}
$$

## 3. Consecuencias inmediatas

### Proposición 3.1. Columnas repetidas

**Enunciado.** Si dos columnas de $A$ son iguales, entonces $\det(A)=0$.

**Prueba.** Intercambiar esas columnas no cambia la matriz, pero por alternancia
cambia el signo del determinante. Así,
$\det(A)=-\det(A)$ y, por tanto, $\det(A)=0$. $\square$

### Corolario 3.2. Columnas dependientes

**Enunciado.** Si las columnas de $A$ son linealmente dependientes, entonces
$\det(A)=0$.

**Idea de prueba.** Despeje una columna como combinación de las demás y use la
multilinealidad. Cada término resultante tiene dos columnas proporcionales y,
por alternancia, determinante cero.

## 4. Determinantes pequeños

Para una matriz $1\times1$,

$$
\det([a])=a.
$$

Para una matriz $2\times2$,

$$
\det\begin{bmatrix}a&b\\c&d\end{bmatrix}=ad-bc.
$$

Geométricamente, el valor absoluto es el área del paralelogramo generado por
las columnas.

Para una matriz triangular,

$$
\det(A)=a_{11}a_{22}\cdots a_{nn}.
$$

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

### Ejemplo 5.3

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

2. Encuentre un contraejemplo para
   $\det(A+B)=\det(A)+\det(B)$.
3. Demuestre que si $A$ es triangular e invertible, todos sus elementos
   diagonales son no nulos.
4. Use determinantes para decidir para qué valores de $a$ es invertible

   $$
   A(a)=\begin{bmatrix}
   1&a&1&3\\
   a&1&3&1\\
   1&3&1&a\\
   3&1&a&1
   \end{bmatrix}.
   $$

5. Pruebe que

   $$
   \begin{bmatrix}
   2&-2&-4\\
   -1&3&4\\
   1&-2&-3
   \end{bmatrix}
   $$

   es idempotente. ¿Puede ser invertible una matriz idempotente distinta de
   $I$? Justifique.
