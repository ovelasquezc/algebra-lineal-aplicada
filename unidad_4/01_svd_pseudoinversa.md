# Cálculo de la SVD y pseudoinversa

## Objetivos

Al finalizar este bloque, podrás:

1. explicar por qué la SVD existe para toda matriz real;
2. construir una SVD completa y una SVD reducida;
3. relacionar valores singulares con $A^TA$, rango y espacios fundamentales;
4. interpretar geométricamente la factorización $A=U\Sigma V^T$;
5. construir la pseudoinversa y verificar las ecuaciones de Moore-Penrose;
6. resolver sistemas compatibles e incompatibles con una condición adicional
   de norma mínima.

## 1. El problema que resuelve la SVD

La diagonalización espectral de la Unidad 3 exige una matriz cuadrada y, para
obtener una base ortonormal, una matriz simétrica. Una matriz general

$$
A\in\mathbb R^{m\times n}
$$

puede ser rectangular, singular o no simétrica. Sin embargo,

$$
A^TA\in\mathbb R^{n\times n}
$$

siempre es simétrica y semidefinida positiva.

### Proposición 1.1. Propiedades de la matriz asociada

**Enunciado.** Para toda matriz real $A$:

1. $A^TA$ es simétrica;
2. $A^TA$ es semidefinida positiva;
3. $\ker(A^TA)=\ker(A)$;
4. $\operatorname{rango}(A^TA)=\operatorname{rango}(A)$.

**Prueba.** La simetría se obtiene de

$$
(A^TA)^T=A^TA.
$$

Además,

$$
x^TA^TAx=\|Ax\|^2\geq0.
$$

Si $Ax=0$, entonces $A^TAx=0$. Recíprocamente, si $A^TAx=0$,

$$
0=x^TA^TAx=\|Ax\|^2,
$$

por lo que $Ax=0$. Así, los núcleos coinciden. La igualdad de rangos se
deduce de rango-nulidad porque ambas matrices actúan sobre $\mathbb R^n$.
$\square$

## 2. Valores y vectores singulares

Por el teorema espectral existe una base ortonormal
$(v_1,\ldots,v_n)$ de vectores propios de $A^TA$. Sus valores propios son no
negativos. Los ordenamos como

$$
\lambda_1\geq\cdots\geq\lambda_r>0,
\qquad
\lambda_{r+1}=\cdots=\lambda_n=0,
$$

donde $r=\operatorname{rango}(A)$.

### Definición 2.1. Valores singulares

Los **valores singulares** de $A$ son

$$
\boxed{\sigma_i=\sqrt{\lambda_i}},
\qquad i=1,\ldots,\min(m,n).
$$

Los $v_i$ son vectores singulares derechos. Para cada valor singular no nulo,
se define

$$
\boxed{u_i=\frac{Av_i}{\sigma_i}}.
$$

Entonces

$$
Av_i=\sigma_i u_i,
\qquad
A^Tu_i=\sigma_i v_i.
$$

### Proposición 2.2. Ortonormalidad de los vectores izquierdos

**Enunciado.** Los vectores $u_1,\ldots,u_r$ construidos arriba son
ortonormales.

**Prueba.** Para $1\leq i,j\leq r$,

$$
u_i^Tu_j
=\frac{v_i^TA^TAv_j}{\sigma_i\sigma_j}
=\frac{\sigma_j^2}{\sigma_i\sigma_j}v_i^Tv_j
=\delta_{ij}.
$$

En el último paso, si $i=j$ el cociente es uno; si $i\neq j$, el producto
$v_i^Tv_j$ es cero. $\square$

```{admonition} No se divide entre cero
:class: warning
La fórmula $u_i=Av_i/\sigma_i$ se usa solo para $i\leq r$. Los vectores
izquierdos restantes se eligen completando una base ortonormal de
$\mathbb R^m$.
```

## 3. Teorema de descomposición en valores singulares

### Teorema 3.1. SVD completa

**Enunciado.** Para toda $A\in\mathbb R^{m\times n}$ de rango $r$ existen
matrices ortogonales

$$
U\in\mathbb R^{m\times m},
\qquad
V\in\mathbb R^{n\times n},
$$

y una matriz diagonal rectangular
$\Sigma\in\mathbb R^{m\times n}$ tales que

$$
\boxed{A=U\Sigma V^T.}
$$

Las entradas diagonales no nulas de $\Sigma$ son

$$
\sigma_1\geq\cdots\geq\sigma_r>0.
$$

**Idea de prueba.** Se diagonaliza ortogonalmente $A^TA$ y se toman sus
vectores propios como columnas de $V$. Para los valores propios positivos se
construyen $u_i=Av_i/\sigma_i$; estos vectores son ortonormales y se completan
a una base de $\mathbb R^m$. Las relaciones $Av_i=\sigma_i u_i$ se reúnen en

$$
AV=U\Sigma.
$$

Multiplicando por $V^T$ se obtiene $A=U\Sigma V^T$.

### SVD reducida

Si se conservan solo las columnas asociadas a valores singulares positivos,

$$
U_r=[u_1\ \cdots\ u_r],
\qquad
V_r=[v_1\ \cdots\ v_r],
\qquad
\Sigma_r=\operatorname{diag}(\sigma_1,\ldots,\sigma_r),
$$

entonces

$$
\boxed{A=U_r\Sigma_rV_r^T.}
$$

Esta es la SVD reducida o compacta. Sus tamaños son

$$
U_r:m\times r,
\qquad
\Sigma_r:r\times r,
\qquad
V_r:n\times r.
$$

## 4. Lectura geométrica breve

La transformación $x\mapsto Ax$ se descompone en tres pasos:

$$
x
\xmapsto{V^T}
V^Tx
\xmapsto{\Sigma}
\Sigma V^Tx
\xmapsto{U}
U\Sigma V^Tx.
$$

1. $V^T$ expresa la entrada en una base ortonormal de direcciones singulares.
2. $\Sigma$ estira cada dirección $v_i$ por el factor $\sigma_i$ y anula las
   direcciones del núcleo.
3. $U$ orienta las direcciones resultantes en el codominio.

La esfera unitaria se transforma en un elipsoide. Sus semiejes tienen
longitudes $\sigma_i$ y direcciones $u_i$. La selección de los primeros
términos para aproximar datos o subespacios se estudiará en C22.

### Consecuencia 4.1. Norma espectral

**Enunciado.**

$$
\boxed{\|A\|_2=\max_{\|x\|=1}\|Ax\|=\sigma_1.}
$$

**Prueba.** Si $x=Vz$ y $\|z\|=1$, entonces

$$
\|Ax\|^2=\|\Sigma z\|^2
=\sum_i\sigma_i^2z_i^2
\leq\sigma_1^2.
$$

La igualdad se alcanza con $x=v_1$. $\square$

## 5. Espacios fundamentales en la SVD

La SVD reducida identifica bases ortonormales de los cuatro espacios
fundamentales:

$$
\operatorname{Col}(A)=\operatorname{span}\{u_1,\ldots,u_r\},
$$

$$
\operatorname{Col}(A^T)=\operatorname{span}\{v_1,\ldots,v_r\},
$$

$$
\ker(A)=\operatorname{span}\{v_{r+1},\ldots,v_n\},
$$

$$
\ker(A^T)=\operatorname{span}\{u_{r+1},\ldots,u_m\}.
$$

También produce la expansión en matrices de rango uno:

$$
\boxed{A=\sum_{i=1}^r\sigma_i u_iv_i^T.}
$$

Cada término toma la componente de la entrada en la dirección $v_i$, la
multiplica por $\sigma_i$ y la coloca en la dirección $u_i$.

## 6. No unicidad y datos que sí son invariantes

Los valores singulares están determinados por $A$, contando multiplicidades,
pero los vectores singulares no siempre son únicos:

- para un valor singular simple, pueden cambiarse simultáneamente los signos
  de $u_i$ y $v_i$;
- para un valor singular repetido, puede elegirse otra base ortonormal del
  subespacio singular correspondiente;
- las bases de $\ker(A)$ y $\ker(A^T)$ pueden completarse de distintas formas.

En todos los casos se conservan $A$, los valores singulares y los subespacios
fundamentales.

## 7. Pseudoinversa de Moore-Penrose

### Definición 7.1. Construcción espectral

Si

$$
A=U\Sigma V^T,
$$

se construye $\Sigma^+$ transponiendo la forma rectangular de $\Sigma$ e
invirtiendo solo sus entradas no nulas:

$$
\sigma_i\longmapsto\frac1{\sigma_i},
\qquad
0\longmapsto0.
$$

La **pseudoinversa de Moore-Penrose** es

$$
\boxed{A^+=V\Sigma^+U^T.}
$$

Con la SVD reducida,

$$
\boxed{A^+=V_r\Sigma_r^{-1}U_r^T.}
$$

### Teorema 7.2. Ecuaciones de Moore-Penrose

**Enunciado.** $A^+$ es la única matriz que satisface

$$
\boxed{
AA^+A=A,
\qquad
A^+AA^+=A^+,
\qquad
(AA^+)^T=AA^+,
\qquad
(A^+A)^T=A^+A.}
$$

**Idea de prueba.** Se sustituyen $A=U\Sigma V^T$ y
$A^+=V\Sigma^+U^T$. La ortogonalidad cancela $U^TU$ y $V^TV$, y las
identidades se reducen a verificar las mismas ecuaciones para $\Sigma$ y
$\Sigma^+$, donde son inmediatas entrada por entrada.

Si $A$ es cuadrada e invertible, todos sus valores singulares son positivos y
$A^+=A^{-1}$.

## 8. Proyecciones producidas por la pseudoinversa

Usando la SVD reducida,

$$
AA^+=U_rU_r^T,
\qquad
A^+A=V_rV_r^T.
$$

Por tanto:

$$
\boxed{AA^+=P_{\operatorname{Col}(A)}},
\qquad
\boxed{A^+A=P_{\operatorname{Col}(A^T)}}.
$$

Ambas matrices son simétricas e idempotentes. La primera actúa en el
codominio; la segunda, en el dominio.

## 9. Sistemas y mínimos cuadrados

### Teorema 9.1. Solución canónica

**Enunciado.** Para todo $b\in\mathbb R^m$,

$$
\boxed{x^+=A^+b}
$$

es la única solución de norma mínima entre todas las soluciones del problema

$$
\min_x\|Ax-b\|_2.
$$

Además,

$$
Ax^+=AA^+b=P_{\operatorname{Col}(A)}b.
$$

**Prueba.** La segunda identidad muestra que $Ax^+$ es la proyección de $b$
sobre la imagen de $A$, por lo que minimiza el residuo. Toda solución de
mínimos cuadrados tiene la forma

$$
x=x^++z,
\qquad z\in\ker(A).
$$

Como $x^+\in\operatorname{Col}(A^T)=\ker(A)^\perp$, se tiene

$$
\|x\|^2=\|x^+\|^2+\|z\|^2\geq\|x^+\|^2,
$$

con igualdad solo si $z=0$. $\square$

### Casos importantes

1. Si $Ax=b$ es compatible, $A^+b$ es su solución de norma mínima.
2. Si es incompatible, $A^+b$ es la solución de mínimos cuadrados de norma
   mínima.
3. Si $A$ tiene columnas linealmente independientes,
   $$A^+=(A^TA)^{-1}A^T.$$
4. Si $A$ tiene filas linealmente independientes,
   $$A^+=A^T(AA^T)^{-1}.$$

## 10. Ejemplo exacto

Sea

$$
A=\begin{pmatrix}
3&0\\
4&0\\
0&5
\end{pmatrix}.
$$

Entonces $A^TA=25I_2$, de modo que $\sigma_1=\sigma_2=5$. Una elección es

$$
v_1=e_1,
\qquad
v_2=e_2,
$$

$$
u_1=\frac15(3,4,0)^T,
\qquad
u_2=(0,0,1)^T.
$$

La SVD reducida es

$$
A=
\begin{pmatrix}
3/5&0\\
4/5&0\\
0&1
\end{pmatrix}
\begin{pmatrix}5&0\\0&5\end{pmatrix}I_2,
$$

y

$$
A^+=\frac15
\begin{pmatrix}
3/5&4/5&0\\
0&0&1
\end{pmatrix}
=
\begin{pmatrix}
3/25&4/25&0\\
0&0&1/5
\end{pmatrix}.
$$

El valor singular repetido explica por qué pueden elegirse otras bases
ortonormales dentro del mismo subespacio singular.

## 11. Procedimiento de cálculo

Para construir una SVD a mano:

1. calcula $A^TA$;
2. encuentra sus valores propios y una base ortonormal de cada espacio propio;
3. ordena los valores propios de mayor a menor;
4. define $\sigma_i=\sqrt{\lambda_i}$;
5. para $\sigma_i>0$, calcula $u_i=Av_i/\sigma_i$;
6. completa las bases ortonormales si se pide la SVD completa;
7. forma $U$, $\Sigma$ y $V$;
8. verifica $U^TU=I$, $V^TV=I$ y $A=U\Sigma V^T$;
9. para la pseudoinversa, invierte solo los valores singulares positivos;
10. verifica las cuatro ecuaciones de Moore-Penrose.

## 12. Errores frecuentes

1. Confundir valores singulares con valores propios de $A$.
2. Usar $AA^T$ para obtener vectores derechos o $A^TA$ para obtener vectores
   izquierdos sin advertir el cambio de espacio.
3. Dividir entre un valor singular cero.
4. Escribir una matriz $\Sigma$ con dimensiones incompatibles.
5. Suponer que una salida computacional es única y comparar signos columna a
   columna.
6. Invertir los ceros al construir $\Sigma^+$.
7. Afirmar que $A^+b$ siempre resuelve exactamente $Ax=b$.
8. Confundir $AA^+$, que actúa en $\mathbb R^m$, con $A^+A$, que actúa en
   $\mathbb R^n$.
