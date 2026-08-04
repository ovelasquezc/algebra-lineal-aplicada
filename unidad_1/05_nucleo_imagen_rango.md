# Núcleo, imagen y rango

## Objetivos

Al finalizar este tema, el estudiante podrá:

1. determinar el núcleo y la imagen de una matriz;
2. calcular bases para los espacios fila y columna;
3. interpretar el rango mediante pivotes, filas e imagen;
4. aplicar el teorema rango–nulidad;
5. describir el conjunto solución de $Ax=b$ como un conjunto afín.

## 1. Una matriz como aplicación

Sea

$$
A\in\mathbb R^{m\times n}.
$$

La multiplicación por $A$ define una aplicación

$$
\begin{aligned}
T_A:\mathbb R^n&\longrightarrow\mathbb R^m,\\
x&\longmapsto Ax.
\end{aligned}
$$

Las dimensiones son importantes: $A$ recibe vectores con $n$ componentes y
produce vectores con $m$ componentes.

## 2. Núcleo

### Definición 2.1. Núcleo y nulidad

El **núcleo** de $A$ es

$$
\ker(A)=\{x\in\mathbb R^n:Ax=0\}.
$$

Su dimensión se llama **nulidad**:

$$
\operatorname{nul}(A)=\dim\ker(A).
$$

Por tanto, $\ker(A)$ es un subconjunto del dominio $\mathbb R^n$.

### Teorema 2.2. El núcleo es un subespacio

**Enunciado.** $\ker(A)$ es un subespacio de $\mathbb R^n$.

**Prueba.** $A0=0$, por lo que el núcleo no es vacío. Si $u,v\in\ker(A)$ y
$\alpha,\beta\in\mathbb R$, entonces

$$
A(\alpha u+\beta v)=\alpha Au+\beta Av=0.
$$

Así, $\alpha u+\beta v\in\ker(A)$. $\square$

### Cálculo de una base del núcleo

1. Reduzca $A$ por filas.
2. Resuelva $Ax=0$ en función de las variables libres.
3. Escriba la solución en forma paramétrica vectorial.
4. Tome como base los vectores que acompañan a los parámetros.

Si no hay variables libres, $\ker(A)=\{0\}$ y su base es la familia vacía;
su dimensión es cero. El vector cero por sí solo **no** es una base.

## 3. Imagen y espacio columna

### Definición 3.1. Imagen

La **imagen** de $A$ es

$$
\operatorname{Im}(A)
=\{Ax:x\in\mathbb R^n\}
\subseteq\mathbb R^m.
$$

Si

$$
A=\begin{bmatrix}A_1&\cdots&A_n\end{bmatrix},
$$

entonces

$$
Ax=x_1A_1+\cdots+x_nA_n,
$$

y por ello

$$
\operatorname{Im}(A)
=\operatorname{span}\{A_1,\ldots,A_n\}.
$$

La imagen coincide con el **espacio columna** de $A$.

### Teorema 3.2. La imagen es un subespacio

**Enunciado.** $\operatorname{Im}(A)$ es un subespacio de $\mathbb R^m$.

**Prueba.** $0=A0$ pertenece a la imagen. Si $y_1=Ax_1$ y $y_2=Ax_2$, entonces

$$
\alpha y_1+\beta y_2
=A(\alpha x_1+\beta x_2),
$$

que también pertenece a la imagen. $\square$

### Cálculo de una base de la imagen

1. Calcule $\operatorname{rref}(A)$.
2. Identifique los índices de las columnas pivote.
3. Seleccione las columnas con esos índices en la matriz **original**.

Estas columnas forman una base de $\operatorname{Im}(A)$.

## 4. Espacio fila

Si las filas de $A$ son $f_1,\ldots,f_m\in\mathbb R^n$, el **espacio fila** es

$$
\mathcal F(A)=\operatorname{span}\{f_1,\ldots,f_m\}.
$$

Las operaciones elementales reemplazan filas por combinaciones reversibles de
las filas anteriores; por tanto, preservan el espacio fila. Las filas no nulas
de $\operatorname{rref}(A)$ forman una base de $\mathcal F(A)$.

## 5. Tres interpretaciones del rango

### Teorema 5.1. Igualdad de rangos

**Enunciado.** Para toda matriz $A$, coinciden:

1. el número de pivotes de $A$;
2. la dimensión del espacio columna;
3. la dimensión del espacio fila.

Este valor común es el **rango** de $A$:

$$
\operatorname{rango}(A)
=\dim\operatorname{Im}(A)
=\dim\mathcal F(A).
$$

**Idea de prueba.** Las columnas pivote originales forman una base de la imagen,
por lo que su cantidad es la dimensión del espacio columna. Las filas no nulas
de la forma reducida forman una base del espacio fila, y hay exactamente una
por pivote. Así, las tres cantidades coinciden.

### Corolario 5.2. Rango y transpuesta

**Enunciado.**

$$
\operatorname{rango}(A)=\operatorname{rango}(A^T).
$$

**Prueba.** El espacio fila de $A$ es el espacio columna de $A^T$. Como rango
fila y rango columna coinciden, ambos rangos son iguales. $\square$

## 6. Teorema rango–nulidad

### Teorema 6.1. Rango–nulidad

**Enunciado.** Si $A\in\mathbb R^{m\times n}$, entonces

$$
\boxed{\dim\ker(A)+\operatorname{rango}(A)=n.}
$$

**Prueba.** Sea $r=\operatorname{rango}(A)$. En la forma reducida hay $r$
columnas pivote y, por tanto, $n-r$ columnas no pivote. En el sistema homogéneo
$Ax=0$, cada columna no pivote corresponde a una variable libre.

Al asignar sucesivamente el valor $1$ a una variable libre y $0$ a las demás,
se obtienen $n-r$ vectores solución que generan todo el núcleo y son
linealmente independientes. Por ello,

$$
\dim\ker(A)=n-r,
$$

y el resultado se sigue al reorganizar. $\square$

```{admonition} Qué cuenta el teorema
:class: note
El número total de columnas se reparte entre variables pivote y variables
libres. El rango cuenta las primeras; la nulidad cuenta las segundas.
```

## 7. Sistemas compatibles y soluciones afines

### Teorema 7.1. Compatibilidad mediante la imagen

**Enunciado.**

$$
Ax=b\text{ es compatible}
\quad\Longleftrightarrow\quad
b\in\operatorname{Im}(A).
$$

**Prueba.** Por definición, $b\in\operatorname{Im}(A)$ si existe un vector
$x$ tal que $Ax=b$. $\square$

### Teorema 7.2. Estructura del conjunto solución

**Enunciado.** Si $x_p$ es una solución particular de $Ax=b$, entonces todas
las soluciones son

$$
x=x_p+z,
\qquad z\in\ker(A).
$$

**Prueba.** Ya se demostró que $Ax=b$ implica $A(x-x_p)=0$. Recíprocamente,
$A(x_p+z)=b$ para todo $z\in\ker(A)$. $\square$

Por tanto:

- si $\ker(A)=\{0\}$, una solución compatible es única;
- si $\dim\ker(A)>0$, una solución compatible produce infinitas soluciones.

## 8. Ejemplo completo

Sea

$$
C=\begin{bmatrix}
1&1&0&2\\
0&1&1&1\\
2&3&1&5
\end{bmatrix}.
$$

La tercera fila es la suma de dos veces la primera y la segunda. Por ello, el
rango es a lo sumo $2$; las dos primeras filas son independientes, de modo que
$\operatorname{rango}(C)=2$. Como $C$ tiene cuatro columnas,

$$
\dim\ker(C)=4-2=2.
$$

La reducción permite obtener explícitamente dos vectores que formen una base
del núcleo y seleccionar dos columnas originales que formen una base de la
imagen.

## 9. Matrices cuadradas e inyectividad

Para $A\in\mathbb R^{n\times n}$, son equivalentes:

1. $\ker(A)=\{0\}$;
2. $Ax=0$ tiene solamente la solución nula;
3. $\operatorname{rango}(A)=n$;
4. las columnas de $A$ son linealmente independientes;
5. las columnas de $A$ generan $\mathbb R^n$;
6. $A$ es invertible.

La equivalencia con $\det(A)\neq0$ se añadirá en el tema siguiente.

## 10. Errores frecuentes

1. Escribir $\ker(A)\subseteq\mathbb R^m$ cuando $A$ tiene $n$ columnas.
2. Usar columnas de la matriz reducida como base de la imagen original.
3. Incluir el vector cero como elemento de una base.
4. Confundir rango con número de filas o columnas sin revisar dependencias.
5. Verificar rango–nulidad usando el número de filas: el lado derecho es el
   número de **columnas**.

## 11. Ejercicios

1. Halle bases de $\ker(A)$, $\operatorname{Im}(A)$ y $\mathcal F(A)$ para

   $$
   A=\begin{bmatrix}
   1&2&3&4\\
   2&4&6&8\\
   1&1&1&1
   \end{bmatrix}.
   $$

2. Verifique rango–nulidad para la matriz anterior.
3. Determine el núcleo de

   $$
   \begin{bmatrix}
   2&2&2&1\\0&2&0&2\\2&0&2&1\\0&2&0&2
   \end{bmatrix}
   $$

   y compárelo con el de la segunda matriz propuesta en las notas de clase.
4. Pruebe que si $P$ y $Q$ son invertibles, entonces
   $\operatorname{rango}(PAQ)=\operatorname{rango}(A)$.
5. Sea $b\in\mathbb R^m$. Explique geométricamente por qué
   $Ax=b$ no puede tener exactamente dos soluciones.
