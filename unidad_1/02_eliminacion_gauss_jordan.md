# Eliminación de Gauss–Jordan

## Objetivos

Al finalizar este tema, el estudiante podrá:

1. distinguir una matriz escalonada de una matriz escalonada reducida;
2. ejecutar eliminación gaussiana y eliminación de Gauss–Jordan;
3. describir todas las soluciones de un sistema, incluidas las variables libres;
4. clasificar un sistema mediante los rangos de $A$ y $[A\mid b]$;
5. calcular la inversa de una matriz por operaciones elementales.

## 1. Del sistema a la matriz aumentada

Un sistema de $m$ ecuaciones y $n$ incógnitas se escribe como

$$
Ax=b,
\qquad
A\in\mathbb R^{m\times n},\quad
x\in\mathbb R^n,\quad
b\in\mathbb R^m.
$$

La **matriz aumentada** del sistema es

$$
[A\mid b].
$$

Cada fila de $[A\mid b]$ representa una ecuación. Por ello, una operación
aplicada a una ecuación debe aplicarse a toda la fila, incluido el término
independiente.

### Definición 1.1. Operaciones elementales por filas

Las operaciones elementales son:

1. **Intercambio:** $F_i\leftrightarrow F_j$.
2. **Escalamiento:** $F_i\leftarrow \lambda F_i$, con $\lambda\neq 0$.
3. **Reemplazo:** $F_j\leftarrow F_j+\lambda F_i$, con $i\neq j$.

La restricción $\lambda\neq0$ en el escalamiento es indispensable: multiplicar
una ecuación por cero destruye información y no es reversible.

### Teorema 1.2. Conservación del conjunto solución

**Enunciado.** Si $[\widetilde A\mid\widetilde b]$ se obtiene de
$[A\mid b]$ mediante una operación elemental por filas, entonces

$$
Ax=b
\quad\text{y}\quad
\widetilde A x=\widetilde b
$$

tienen exactamente el mismo conjunto solución.

**Prueba.** Cada operación elemental es reversible:

- el intercambio se revierte intercambiando nuevamente las mismas filas;
- $F_i\leftarrow\lambda F_i$ se revierte con
  $F_i\leftarrow\lambda^{-1}F_i$;
- $F_j\leftarrow F_j+\lambda F_i$ se revierte con
  $F_j\leftarrow F_j-\lambda F_i$.

Una igualdad válida se transforma en otra igualdad válida al multiplicarla por
un escalar no nulo, sumarle un múltiplo de otra igualdad o cambiar el orden de
las ecuaciones. Por reversibilidad, toda solución del sistema inicial es
solución del transformado y recíprocamente. $\square$

## 2. Matrices elementales

### Definición 2.1. Matriz elemental

Una **matriz elemental** es la matriz obtenida al aplicar una sola operación
elemental a la identidad $I_m$.

### Proposición 2.2. Una operación por filas es una multiplicación

**Enunciado.** Sea $A\in\mathbb R^{m\times n}$. Si $E$ se obtiene aplicando a
$I_m$ una operación elemental, entonces $EA$ es el resultado de aplicar esa
misma operación a $A$.

**Idea de prueba.** La fila $i$ de $EA$ es una combinación lineal de las filas
de $A$, cuyos coeficientes son los elementos de la fila $i$ de $E$. Como $E$
registra exactamente la operación aplicada a $I_m$, reproduce la misma
combinación en las filas de $A$.

Toda matriz elemental es invertible y su inversa corresponde a la operación
inversa.

## 3. Forma escalonada y forma escalonada reducida

### Definición 3.1. Pivote

El primer elemento no nulo de una fila no nula se llama **pivote** o
**entrada principal** de esa fila. La columna que contiene un pivote es una
**columna pivote**.

### Definición 3.2. Matriz escalonada

Una matriz está en **forma escalonada por filas** si cumple:

1. todas las filas nulas están debajo de las filas no nulas;
2. el pivote de cada fila no nula está estrictamente a la derecha del pivote de
   la fila anterior;
3. todos los elementos debajo de cada pivote son cero.

Por ejemplo,

$$
\begin{bmatrix}
2&3&2&3&2\\
0&1&0&0&-2\\
0&0&1&1&-1\\
0&0&0&0&0
\end{bmatrix}
$$

es escalonada.

### Definición 3.3. Matriz escalonada reducida

Una matriz está en **forma escalonada reducida por filas** si:

1. está en forma escalonada;
2. cada pivote es igual a $1$;
3. cada pivote es el único elemento no nulo de su columna.

Por ejemplo,

$$
\begin{bmatrix}
1&0&0&\tfrac12&5\\
0&1&0&0&-2\\
0&0&1&1&-1\\
0&0&0&0&0
\end{bmatrix}
$$

está en forma escalonada reducida.

```{admonition} Dos procedimientos relacionados
:class: note
La **eliminación gaussiana** termina en una forma escalonada y suele continuar
con sustitución hacia atrás. La **eliminación de Gauss–Jordan** elimina también
por encima de los pivotes y termina en la forma escalonada reducida.
```

### Teorema 3.4. Existencia y unicidad de la forma reducida

**Enunciado.** Para toda matriz $A$ existe una sucesión de operaciones
elementales que la transforma en una matriz escalonada reducida. Además, esa
matriz reducida es única y se denota por $\operatorname{rref}(A)$.

**Idea de prueba de la existencia.** Se busca de izquierda a derecha una
entrada no nula, se la lleva a la posición de pivote mediante un intercambio,
se normaliza y se anulan las demás entradas de su columna. Se repite el proceso
en la submatriz restante. El número finito de filas y columnas garantiza que el
procedimiento termina.

La unicidad es un resultado más delicado: aunque distintas sucesiones de
operaciones pueden producir matrices intermedias diferentes, las posiciones de
los pivotes y todos los elementos de la matriz reducida final quedan
determinados por $A$.

## 4. Algoritmo de Gauss–Jordan

Para reducir una matriz:

1. localice la primera columna que tenga una entrada no nula en las filas aún
   no procesadas;
2. intercambie filas si es necesario para colocar esa entrada como pivote;
3. divida la fila pivote para convertir el pivote en $1$;
4. sume múltiplos de la fila pivote a las demás filas para producir ceros en
   toda la columna pivote;
5. avance una fila y una columna, y repita.

### Ejemplo 4.1. Solución única

Considere

$$
\begin{aligned}
x+y&=3,\\
2x-y&=0.
\end{aligned}
$$

Entonces

$$
\left[
\begin{array}{cc|c}
1&1&3\\
2&-1&0
\end{array}
\right]
\xrightarrow{F_2\leftarrow F_2-2F_1}
\left[
\begin{array}{cc|c}
1&1&3\\
0&-3&-6
\end{array}
\right]
$$

$$
\xrightarrow{F_2\leftarrow-\frac13F_2}
\left[
\begin{array}{cc|c}
1&1&3\\
0&1&2
\end{array}
\right]
\xrightarrow{F_1\leftarrow F_1-F_2}
\left[
\begin{array}{cc|c}
1&0&1\\
0&1&2
\end{array}
\right].
$$

Por tanto, $(x,y)=(1,2)$.

### Ejemplo 4.2. Infinitas soluciones y forma paramétrica

Suponga que la reducción de un sistema en cuatro incógnitas produce

$$
\left[
\begin{array}{cccc|c}
1&0&2&-1&3\\
0&1&-1&4&2\\
0&0&0&0&0
\end{array}
\right].
$$

Las columnas $1$ y $2$ son pivote. Las variables $x_3$ y $x_4$ son libres.
Tomando $x_3=s$ y $x_4=t$,

$$
x_1=3-2s+t,
\qquad
x_2=2+s-4t.
$$

La solución completa es

$$
x=
\begin{bmatrix}3\\2\\0\\0\end{bmatrix}
+s\begin{bmatrix}-2\\1\\1\\0\end{bmatrix}
+t\begin{bmatrix}1\\-4\\0\\1\end{bmatrix},
\qquad s,t\in\mathbb R.
$$

No basta presentar un solo valor de $x$: deben declararse todas las variables
libres y describirse el conjunto solución completo.

### Ejemplo 4.3. Sistema incompatible

Una fila de la forma

$$
\begin{bmatrix}0&0&\cdots&0&\mid&c\end{bmatrix},
\qquad c\neq0,
$$

representa la contradicción $0=c$. En ese caso, el sistema no tiene solución.

## 5. Rango y clasificación de sistemas

### Definición 5.1. Rango

El **rango** de una matriz $A$, denotado $\operatorname{rango}(A)$, es el
número de pivotes de $\operatorname{rref}(A)$.

### Teorema 5.2. Criterio de Rouché–Capelli

**Enunciado.** Sea $A\in\mathbb R^{m\times n}$. El sistema $Ax=b$:

1. tiene solución si, y solo si,
   $\operatorname{rango}(A)=\operatorname{rango}([A\mid b])$;
2. tiene solución única si, además,
   $\operatorname{rango}(A)=n$;
3. tiene infinitas soluciones si
   $\operatorname{rango}(A)=\operatorname{rango}([A\mid b])<n$;
4. no tiene solución si
   $\operatorname{rango}(A)<\operatorname{rango}([A\mid b])$.

**Idea de prueba.** Una columna pivote adicional en la última columna de la
matriz aumentada equivale a una fila contradictoria. Si no hay contradicción,
cada columna no pivote de $A$ corresponde a una variable libre. Cero variables
libres produce una solución única; una o más variables libres producen
infinitas soluciones.

### Proposición 5.3. Propiedades básicas del rango

Para matrices de tamaños compatibles:

1. $0\leq\operatorname{rango}(A)\leq\min\{m,n\}$ si
   $A\in\mathbb R^{m\times n}$.
2. $\operatorname{rango}(A)=\operatorname{rango}(A^T)$.
3. $\operatorname{rango}(AB)\leq
   \min\{\operatorname{rango}(A),\operatorname{rango}(B)\}$.
4. Si $P$ y $Q$ son invertibles, entonces
   $\operatorname{rango}(PAQ)=\operatorname{rango}(A)$.
5. Sobre los números reales,
   $\operatorname{rango}(A^TA)=\operatorname{rango}(A)$.

**Ideas de prueba.**

- La propiedad 1 se sigue de que no puede haber más de un pivote por fila ni
  por columna.
- Multiplicar por una matriz invertible equivale a aplicar transformaciones
  reversibles; por eso no cambia el rango.
- Para la propiedad 3, las columnas de $AB$ son combinaciones lineales de las
  columnas de $A$; la cota por $\operatorname{rango}(B)$ se obtiene de forma
  análoga o usando transpuestas.
- Para la propiedad 5, $A^TAx=0$ implica
  $x^TA^TAx=\|Ax\|^2=0$, de donde $Ax=0$. Así,
  $A$ y $A^TA$ tienen el mismo núcleo y, por tanto, el mismo número de
  columnas pivote. La formulación general mediante núcleo y rango se retomará
  más adelante.

## 6. Inversa mediante Gauss–Jordan

### Teorema 6.1. Prueba de invertibilidad y cálculo de la inversa

**Enunciado.** Sea $A\in\mathbb R^{n\times n}$. Entonces $A$ es invertible si,
y solo si,

$$
\operatorname{rref}(A)=I_n.
$$

En ese caso, si las mismas operaciones se aplican a $[A\mid I_n]$, se obtiene

$$
[A\mid I_n]\longrightarrow[I_n\mid A^{-1}].
$$

**Prueba.** Si las operaciones están representadas por matrices elementales
$E_k,\ldots,E_1$, entonces

$$
E_k\cdots E_1A=I_n.
$$

Por tanto, $E_k\cdots E_1=A^{-1}$. Aplicar esas operaciones al bloque derecho
$I_n$ produce precisamente $A^{-1}$. Recíprocamente, una matriz invertible
tiene un pivote en cada columna, por lo que su forma reducida es $I_n$.
$\square$

## 7. Errores frecuentes

1. Aplicar una operación a $A$ y no aplicarla a $b$.
2. Multiplicar una fila por cero.
3. Confundir una columna sin pivote con una ecuación redundante: las columnas
   se relacionan con variables; las filas, con ecuaciones.
4. Detenerse en forma escalonada y leer la solución como si ya estuviera
   reducida.
5. Dar valores particulares a las variables libres y perder soluciones.
6. Usar aritmética decimal demasiado pronto y convertir ceros exactos en
   números pequeños distintos de cero.

## 8. Ejercicios

1. Reduzca la matriz

   $$
   \begin{bmatrix}
   4&6&5&7&3\\
   4&7&4&6&2\\
   4&6&4&6&4\\
   2&3&2&3&2
   \end{bmatrix}
   $$

   y señale sus pivotes y su rango.

2. Clasifique y resuelva, si es posible,

   $$
   \begin{aligned}
   x+y+z&=2,\\
   2x+2y+2z&=4,\\
   x-y+z&=0.
   \end{aligned}
   $$

3. Construya matrices $A$ y $B$ para las cuales
   $\operatorname{rango}(AB)<
   \min\{\operatorname{rango}(A),\operatorname{rango}(B)\}$.

4. Calcule la inversa de

   $$
   A=\begin{bmatrix}2&1\\5&3\end{bmatrix}
   $$

   mediante $[A\mid I_2]$ y verifique ambos productos
   $AA^{-1}$ y $A^{-1}A$.
