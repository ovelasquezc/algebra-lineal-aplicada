# Eliminación de Gauss–Jordan

## Objetivos

Al finalizar este tema, el estudiante podrá:

1. definir el conjunto solución y reconocer sistemas equivalentes;
2. justificar por reversibilidad que las operaciones elementales conservan
   todas las soluciones;
3. traducir operaciones sobre ecuaciones a operaciones sobre filas de una
   matriz aumentada;
4. distinguir una matriz escalonada de una matriz escalonada reducida;
5. ejecutar eliminación gaussiana y eliminación de Gauss–Jordan;
6. describir todas las soluciones de un sistema, incluidas las variables libres;
7. clasificar un sistema mediante los rangos de $A$ y $[A\mid b]$;
8. calcular la inversa de una matriz por operaciones elementales.

## 1. Sistemas de ecuaciones y conjuntos solución

Consideremos primero un sistema escrito como ecuaciones, sin introducir aún
matrices. Por ejemplo,

$$
\mathcal S:
\begin{cases}
x+2y+z=1,\\
x-y+3z=0.
\end{cases}
$$

Una **solución** de $\mathcal S$ es una terna $(x,y,z)\in\mathbb R^3$ que
satisface simultáneamente las dos ecuaciones.

### Definición 1.1. Conjunto solución

El **conjunto solución** de un sistema $\mathcal S$ es

$$
\operatorname{Sol}(\mathcal S)
=\{x:\text{$x$ satisface todas las ecuaciones de $\mathcal S$}\}.
$$

Resolver un sistema no significa encontrar solamente un punto que funcione:
significa describir todo el conjunto $\operatorname{Sol}(\mathcal S)$.

### Definición 1.2. Sistemas equivalentes

Dos sistemas $\mathcal S$ y $\mathcal T$ son **equivalentes** si tienen
exactamente el mismo conjunto solución:

$$
\boxed{
\operatorname{Sol}(\mathcal S)=\operatorname{Sol}(\mathcal T).
}
$$

La eliminación transforma un sistema en otros sistemas más sencillos. Para
que el procedimiento sea correcto, cada transformación debe producir un
sistema equivalente, no simplemente uno cuyas ecuaciones parezcan más
convenientes.

## 2. Operaciones sobre ecuaciones

Denotemos las ecuaciones de un sistema por
$\mathcal E_1,\ldots,\mathcal E_m$. Al sumar ecuaciones se suman ambos miembros
de las igualdades; al multiplicar una ecuación por un escalar se multiplican
también ambos miembros.

### Ejemplo 2.1. Reemplazar una ecuación

En $\mathcal S$, restemos la primera ecuación de la segunda:

$$
\begin{aligned}
(x-y+3z)-(x+2y+z)&=0-1,\\
-3y+2z&=-1.
\end{aligned}
$$

Se obtiene el sistema

$$
\mathcal T:
\begin{cases}
x+2y+z=1,\\
-3y+2z=-1.
\end{cases}
$$

La operación puede escribirse como

$$
\mathcal E_2\leftarrow\mathcal E_2-\mathcal E_1.
$$

Comprobemos con detalle que no se perdió ni se agregó ninguna solución.

**Primera inclusión.** Si $(x,y,z)\in\operatorname{Sol}(\mathcal S)$,
satisface las dos ecuaciones originales. Al restarlas, satisface
$-3y+2z=-1$ y también conserva la primera ecuación. Por tanto,

$$
\operatorname{Sol}(\mathcal S)\subseteq\operatorname{Sol}(\mathcal T).
$$

**Inclusión recíproca.** Si
$(x,y,z)\in\operatorname{Sol}(\mathcal T)$, satisface

$$
x+2y+z=1,
\qquad
-3y+2z=-1.
$$

Al sumar estas igualdades se recupera

$$
x-y+3z=0.
$$

Así, el punto satisface las dos ecuaciones de $\mathcal S$, y

$$
\operatorname{Sol}(\mathcal T)\subseteq\operatorname{Sol}(\mathcal S).
$$

Concluimos que

$$
\boxed{
\operatorname{Sol}(\mathcal S)=\operatorname{Sol}(\mathcal T).
}
$$

La segunda inclusión fue posible porque la operación se puede deshacer:

$$
\mathcal E_2\leftarrow\mathcal E_2+\mathcal E_1.
$$

### Principio 2.2. La idea esencial: reversibilidad

Una transformación segura debe poder recorrerse en ambos sentidos. Por
ejemplo,

$$
x=1
\quad\Longleftrightarrow\quad
2x=2,
$$

porque multiplicar por $2$ se revierte dividiendo entre $2$.

En cambio, aunque

$$
x=1\quad\Longrightarrow\quad x^2=1,
$$

la implicación recíproca es falsa: $x^2=1$ admite $x=1$ y $x=-1$. Elevar al
cuadrado introdujo una solución y, por tanto, no es una operación apropiada
para la eliminación.

```{admonition} Una implicación no basta
:class: warning
Para conservar el conjunto solución hay que justificar las dos inclusiones.
Que toda solución del sistema original satisfaga el sistema nuevo no impide que
el sistema nuevo tenga soluciones adicionales. La reversibilidad proporciona
automáticamente la inclusión recíproca.
```

### Definición 2.3. Operaciones elementales sobre ecuaciones

Sean $i\neq j$. Las tres operaciones elementales son:

1. **Intercambio de ecuaciones:**

   $$
   \mathcal E_i\leftrightarrow\mathcal E_j.
   $$

2. **Reemplazo de una ecuación:**

   $$
   \mathcal E_i\leftarrow\mathcal E_i+\lambda\mathcal E_j,
   \qquad \lambda\in\mathbb R.
   $$

   La ecuación $\mathcal E_j$ no se modifica.

3. **Escalamiento por un número no nulo:**

   $$
   \mathcal E_i\leftarrow\lambda\mathcal E_i,
   \qquad \lambda\neq0.
   $$

Sus operaciones inversas son, respectivamente,

$$
\mathcal E_i\leftrightarrow\mathcal E_j,
\qquad
\mathcal E_i\leftarrow\mathcal E_i-\lambda\mathcal E_j,
\qquad
\mathcal E_i\leftarrow\frac1\lambda\mathcal E_i.
$$

La condición $\lambda\neq0$ en el tercer caso es indispensable. Multiplicar
una ecuación por cero la convierte en $0=0$, destruye su información y no puede
revertirse.

### Teorema 2.4. Conservación del conjunto solución

**Enunciado.** Si un sistema $\mathcal T$ se obtiene de $\mathcal S$ mediante
una operación elemental sobre ecuaciones, entonces

$$
\boxed{
\operatorname{Sol}(\mathcal S)=\operatorname{Sol}(\mathcal T).
}
$$

**Prueba.** Toda solución de $\mathcal S$ satisface la ecuación transformada:
el orden de las ecuaciones no afecta que se cumplan simultáneamente; una
igualdad válida sigue siendo válida al multiplicarla por un escalar; y la suma
de igualdades válidas es válida. Esto prueba
$\operatorname{Sol}(\mathcal S)\subseteq\operatorname{Sol}(\mathcal T)$.

Cada operación tiene la operación elemental inversa indicada arriba. Aplicando
el mismo argumento a la inversa se obtiene
$\operatorname{Sol}(\mathcal T)\subseteq\operatorname{Sol}(\mathcal S)$.
Por tanto, los conjuntos son iguales. $\square$

Una sucesión de operaciones elementales también conserva el conjunto solución,
porque conserva las soluciones en cada paso.

## 3. De las ecuaciones a los arreglos matriciales

Consideremos ahora un sistema de $m$ ecuaciones y $n$ incógnitas:

$$
\begin{aligned}
\mathcal E_1:&\quad
a_{11}x_1+\cdots+a_{1n}x_n=b_1,\\
\mathcal E_2:&\quad
a_{21}x_1+\cdots+a_{2n}x_n=b_2,\\
&\ \vdots\\
\mathcal E_m:&\quad
a_{m1}x_1+\cdots+a_{mn}x_n=b_m.
\end{aligned}
$$

Si se fija el orden de las variables $(x_1,\ldots,x_n)$, toda la información
numérica puede guardarse en el arreglo

$$
\left[
\begin{array}{cccc|c}
a_{11}&a_{12}&\cdots&a_{1n}&b_1\\
a_{21}&a_{22}&\cdots&a_{2n}&b_2\\
\vdots&\vdots&&\vdots&\vdots\\
a_{m1}&a_{m2}&\cdots&a_{mn}&b_m
\end{array}
\right].
$$

La parte izquierda es la **matriz de coeficientes** $A$, la última columna es
$b$, y el arreglo completo es la **matriz aumentada** $[A\mid b]$. Con
$x=(x_1,\ldots,x_n)^T$, el sistema se abrevia como

$$
Ax=b.
$$

```{admonition} La matriz es una representación del sistema
:class: note
La fila $i$ almacena los coeficientes y el término independiente de
$\mathcal E_i$. Para interpretar correctamente el arreglo debe mantenerse fijo
el orden de las variables. Una operación sobre una ecuación debe aplicarse a
toda su fila, incluida la entrada situada después de la barra.
```

### Traducción de las operaciones elementales

Las operaciones sobre ecuaciones se convierten en operaciones sobre filas:

1. $\mathcal E_i\leftrightarrow\mathcal E_j$ se escribe
   $F_i\leftrightarrow F_j$.
2. $\mathcal E_i\leftarrow\mathcal E_i+\lambda\mathcal E_j$ se escribe
   $F_i\leftarrow F_i+\lambda F_j$.
3. $\mathcal E_i\leftarrow\lambda\mathcal E_i$, con $\lambda\neq0$, se
   escribe $F_i\leftarrow\lambda F_i$.

### Ejemplo 3.1. El mismo reemplazo en lenguaje matricial

Para el sistema $\mathcal S$, la matriz aumentada es

$$
\left[
\begin{array}{ccc|c}
1&2&1&1\\
1&-1&3&0
\end{array}
\right].
$$

La operación
$\mathcal E_2\leftarrow\mathcal E_2-\mathcal E_1$ se traduce en
$F_2\leftarrow F_2-F_1$:

$$
\left[
\begin{array}{ccc|c}
1&2&1&1\\
1&-1&3&0
\end{array}
\right]
\xrightarrow{F_2\leftarrow F_2-F_1}
\left[
\begin{array}{ccc|c}
1&2&1&1\\
0&-3&2&-1
\end{array}
\right].
$$

El segundo arreglo representa precisamente el sistema $\mathcal T$.

### Ejemplo 3.2. Intercambiar ecuaciones e intercambiar filas

Escribir primero la segunda ecuación de $\mathcal T$ no cambia en absoluto la
condición de satisfacer ambas:

$$
\begin{cases}
x+2y+z=1,\\
-3y+2z=-1
\end{cases}
\quad\text{y}\quad
\begin{cases}
-3y+2z=-1,\\
x+2y+z=1
\end{cases}
$$

son literalmente la misma conjunción de dos afirmaciones, escrita en distinto
orden. En el lenguaje de ecuaciones, el intercambio es conceptualmente
trivial.

Sin embargo, una matriz es un arreglo ordenado de números. Cambiar el orden de
las ecuaciones exige mover dos filas completas:

$$
\left[
\begin{array}{ccc|c}
1&2&1&1\\
0&-3&2&-1
\end{array}
\right]
\xrightarrow{F_1\leftrightarrow F_2}
\left[
\begin{array}{ccc|c}
0&-3&2&-1\\
1&2&1&1
\end{array}
\right].
$$

El intercambio de filas es, por tanto, una transformación no trivial del
arreglo matricial, aunque no altera el significado lógico del sistema ni su
conjunto solución.

### Teorema 3.3. Conservación de soluciones en lenguaje matricial

**Enunciado.** Si $[\widetilde A\mid\widetilde b]$ se obtiene de
$[A\mid b]$ mediante una operación elemental por filas, entonces

$$
Ax=b
\quad\text{y}\quad
\widetilde A x=\widetilde b
$$

tienen exactamente el mismo conjunto solución.

**Prueba.** Cada fila representa una ecuación, y cada operación elemental por
filas representa la correspondiente operación elemental sobre ecuaciones. El
resultado se sigue del Teorema 2.4. $\square$

### Definición 3.4. Equivalencia por filas

Dos matrices del mismo tamaño son **equivalentes por filas** si una puede
obtenerse de la otra mediante una sucesión finita de operaciones elementales
por filas. Escribimos

$$
A\sim B.
$$

La reversibilidad muestra que esta relación es reflexiva, simétrica y
transitiva.

## 4. Matrices elementales

### Definición 4.1. Matriz elemental

Una **matriz elemental** es la matriz obtenida al aplicar una sola operación
elemental a la identidad $I_m$.

### Proposición 4.2. Una operación por filas es una multiplicación

**Enunciado.** Sea $A\in\mathbb R^{m\times n}$. Si $E$ se obtiene aplicando a
$I_m$ una operación elemental, entonces $EA$ es el resultado de aplicar esa
misma operación a $A$.

**Idea de prueba.** La fila $i$ de $EA$ es una combinación lineal de las filas
de $A$, cuyos coeficientes son los elementos de la fila $i$ de $E$. Como $E$
registra exactamente la operación aplicada a $I_m$, reproduce la misma
combinación en las filas de $A$.

Toda matriz elemental es invertible y su inversa corresponde a la operación
inversa.

## 5. Forma escalonada y forma escalonada reducida

### Definición 5.1. Pivote

El primer elemento no nulo de una fila no nula se llama **pivote** o
**entrada principal** de esa fila. La columna que contiene un pivote es una
**columna pivote**.

### Definición 5.2. Matriz escalonada

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

### Definición 5.3. Matriz escalonada reducida

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

### Teorema 5.4. Existencia y unicidad de la forma reducida

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

## 6. Algoritmo de Gauss–Jordan

El objetivo no es cambiar arbitrariamente los números de una matriz, sino
reemplazar el sistema por otro equivalente en el que las ecuaciones puedan
leerse con facilidad. Cada flecha del algoritmo representa una operación
reversible y, por tanto, conserva **todo** el conjunto solución.

Para reducir una matriz aumentada:

1. localice la primera columna que tenga una entrada no nula en las filas aún
   no procesadas;
2. intercambie filas si es necesario para colocar esa entrada como pivote;
3. divida la fila pivote para convertir el pivote en $1$;
4. sume múltiplos de la fila pivote a las demás filas para producir ceros en
   toda la columna pivote;
5. avance una fila y una columna, y repita.

La **eliminación gaussiana** realiza la fase hacia adelante: ubica pivotes y
anula las entradas situadas debajo de ellos hasta obtener una forma
escalonada. Luego puede usarse sustitución hacia atrás. La eliminación de
**Gauss–Jordan** continúa: normaliza los pivotes y anula también las entradas
situadas encima de ellos, hasta obtener la forma escalonada reducida.

### Ejemplo 6.1. Solución única

Considere

$$
\begin{aligned}
x+y&=3,\\
2x-y&=0.
\end{aligned}
$$

Trabajemos primero con ecuaciones. Reemplazamos la segunda por ella misma
menos dos veces la primera:

$$
\mathcal E_2\leftarrow\mathcal E_2-2\mathcal E_1,
$$

$$
\begin{cases}
x+y=3,\\
-3y=-6.
\end{cases}
$$

Dividimos la segunda ecuación entre $-3$:

$$
\mathcal E_2\leftarrow-\frac13\mathcal E_2,
\qquad
\begin{cases}
x+y=3,\\
y=2.
\end{cases}
$$

Finalmente retiramos de la primera ecuación la variable que ya aparece como
pivote en la segunda:

$$
\mathcal E_1\leftarrow\mathcal E_1-\mathcal E_2,
\qquad
\begin{cases}
x=1,\\
y=2.
\end{cases}
$$

Cada sistema es equivalente al anterior porque cada paso es reversible. Ahora
escribimos exactamente los mismos pasos sobre la matriz aumentada:

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

### Ejemplo 6.2. Infinitas soluciones y forma paramétrica

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

### Ejemplo 6.3. Sistema incompatible

Una fila de la forma

$$
\begin{bmatrix}0&0&\cdots&0&\mid&c\end{bmatrix},
\qquad c\neq0,
$$

representa la contradicción $0=c$. En ese caso, el sistema no tiene solución.

## 7. Rango y clasificación de sistemas

### Definición 7.1. Rango

El **rango** de una matriz $A$, denotado $\operatorname{rango}(A)$, es el
número de pivotes de $\operatorname{rref}(A)$.

### Teorema 7.2. Criterio de Rouché–Capelli

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

### Proposición 7.3. Propiedades básicas del rango

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

## 8. Inversa mediante Gauss–Jordan

### Teorema 8.1. Prueba de invertibilidad y cálculo de la inversa

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

## 9. Errores frecuentes

1. Usar una transformación que solo garantiza una implicación y asumir que
   conserva el conjunto solución.
2. Multiplicar una ecuación o fila por cero.
3. Aplicar una operación a $A$ y no aplicarla a $b$.
4. Olvidar que intercambiar ecuaciones no cambia el sistema, pero en su
   representación matricial exige intercambiar las filas completas.
5. Confundir una columna sin pivote con una ecuación redundante: las columnas
   se relacionan con variables; las filas, con ecuaciones.
6. Detenerse en forma escalonada y leer la solución como si ya estuviera
   reducida.
7. Dar valores particulares a las variables libres y perder soluciones.
8. Usar aritmética decimal demasiado pronto y convertir ceros exactos en
   números pequeños distintos de cero.

## 10. Ejercicios

1. Considere

   $$
   \mathcal S:
   \begin{cases}
   x+2y-z=4,\\
   3x-y+2z=1
   \end{cases}
   $$

   y el sistema obtenido mediante
   $\mathcal E_2\leftarrow\mathcal E_2-3\mathcal E_1$.

   a. Escriba el sistema transformado.
   b. Pruebe directamente las dos inclusiones entre sus conjuntos solución.
   c. Indique la operación que recupera $\mathcal S$.

2. Determine cuáles de las siguientes transformaciones son reversibles y
   cuáles pueden alterar el conjunto solución:

   a. intercambiar dos ecuaciones;
   b. multiplicar una ecuación por $-5$;
   c. multiplicar una ecuación por $0$;
   d. elevar ambos miembros de una ecuación al cuadrado;
   e. reemplazar $\mathcal E_1$ por
      $\mathcal E_1+7\mathcal E_2$, dejando $\mathcal E_2$ sin cambio.

3. Escriba la matriz aumentada de

   $$
   \begin{cases}
   2x-y+z=3,\\
   x+3y-2z=0,\\
   -x+y+4z=5.
   \end{cases}
   $$

   Aplique, en este orden,
   $F_1\leftrightarrow F_3$,
   $F_2\leftarrow F_2+F_1$ y
   $F_1\leftarrow-F_1$. Después de cada paso, vuelva al lenguaje de ecuaciones
   y escriba el sistema representado.

4. Reduzca la matriz

   $$
   \begin{bmatrix}
   4&6&5&7&3\\
   4&7&4&6&2\\
   4&6&4&6&4\\
   2&3&2&3&2
   \end{bmatrix}
   $$

   y señale sus pivotes y su rango.

5. Clasifique y resuelva, si es posible,

   $$
   \begin{aligned}
   x+y+z&=2,\\
   2x+2y+2z&=4,\\
   x-y+z&=0.
   \end{aligned}
   $$

6. Construya matrices $A$ y $B$ para las cuales
   $\operatorname{rango}(AB)<
   \min\{\operatorname{rango}(A),\operatorname{rango}(B)\}$.

7. Calcule la inversa de

   $$
   A=\begin{bmatrix}2&1\\5&3\end{bmatrix}
   $$

   mediante $[A\mid I_2]$ y verifique ambos productos
   $AA^{-1}$ y $A^{-1}A$.
