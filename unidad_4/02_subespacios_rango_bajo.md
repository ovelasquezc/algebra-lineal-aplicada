# Subespacios de mejor aproximación y rango bajo

## Objetivos

Al finalizar esta sesión, podrás:

1. formular el problema del subespacio de mejor ajuste;
2. probar la equivalencia entre minimizar distancias y maximizar la suma de
   cuadrados de las proyecciones;
3. construir sucesivamente las direcciones de mejor ajuste;
4. aplicar la fórmula de Courant--Fischer;
5. construir una aproximación SVD truncada y aplicar el teorema de
   Eckart--Young--Mirsky;
6. calcular exactamente el error de truncamiento;
7. interpretar el compromiso entre rango, almacenamiento y calidad.

```{admonition} Alcance de C22
:class: note
Esta sesión estudia subespacios que pasan por el origen y aproximaciones de
rango bajo. El centrado de datos, la varianza y la interpretación estadística
se desarrollan en C23 al introducir PCA.
```

## 1. El mejor subespacio para un conjunto de datos

Sean $x_1,\ldots,x_N\in\mathbb R^d$ y sea

$$
X=\begin{pmatrix}
x_1^T\\
\vdots\\
x_N^T
\end{pmatrix}\in\mathbb R^{N\times d}.
$$

### Definición 1.1. Subespacio de mejor ajuste

Un subespacio $V\subseteq\mathbb R^d$ de dimensión $k$ es un
**$k$-subespacio de mejor ajuste** para los datos si minimiza

$$
\boxed{
E(V)=\sum_{i=1}^N\operatorname{dist}(x_i,V)^2
}
$$

entre todos los subespacios de dimensión $k$.

Si $P_V$ es la proyección ortogonal sobre $V$, entonces

$$
\operatorname{dist}(x_i,V)=\|x_i-P_Vx_i\|.
$$

### Proposición 1.2. Distancia y proyección

**Enunciado.** Minimizar $E(V)$ equivale a maximizar

$$
S(V)=\sum_{i=1}^N\|P_Vx_i\|^2.
$$

**Prueba.** Por la descomposición ortogonal,

$$
\|x_i\|^2=\|P_Vx_i\|^2+\|x_i-P_Vx_i\|^2.
$$

Al sumar,

$$
\sum_i\|x_i\|^2=S(V)+E(V).
$$

El miembro izquierdo no depende de $V$; por tanto, disminuir un término
equivale a aumentar el otro. $\square$

## 2. Formulación matricial

Sea $Q=[q_1\ \cdots\ q_k]\in\mathbb R^{d\times k}$ una matriz con columnas
ortonormales que generan $V$. Entonces

$$
P_V=QQ^T.
$$

Las coordenadas proyectadas de todos los datos son las filas de $XQ$, y

$$
S(V)=\|XQ\|_F^2
=\sum_{j=1}^k\|Xq_j\|^2.
$$

Así, el problema equivale a

$$
\boxed{
\max_{Q^TQ=I_k}\|XQ\|_F^2.
}
$$

### Definición 2.1. Norma de Frobenius

Para $A=(a_{ij})\in\mathbb R^{m\times n}$,

$$
\boxed{
\|A\|_F
=\left(\sum_{i=1}^m\sum_{j=1}^na_{ij}^2\right)^{1/2}.
}
$$

Es la norma euclídea de la lista de todas las entradas. Además,

$$
\|A\|_F^2=\operatorname{tr}(A^TA)
=\sum_{j=1}^r\sigma_j^2.
$$

## 3. Construcción sucesiva de las direcciones

Para una sola dirección, buscamos

$$
v_1\in\arg\max_{\|v\|=1}\|Xv\|^2.
$$

Una vez hallado $v_1$, buscamos la mejor dirección nueva sin volver a usar
la información que ya representa $v_1$:

$$
v_2\in\arg\max_{\substack{\|v\|=1\\v\perp v_1}}\|Xv\|^2.
$$

El procedimiento continúa de manera **secuencial** o *greedy*.

### Teorema 3.1. Construcción secuencial del mejor subespacio

**Enunciado.** Para $j=1,\ldots,k$, sea

$$
\boxed{
v_j\in\arg\max_{\substack{\|v\|=1\\
v\perp v_1,\ldots,v_{j-1}}}\|Xv\|^2,
}
$$

donde la condición de ortogonalidad es vacía cuando $j=1$. Entonces

$$
V_k=\operatorname{span}\{v_1,\ldots,v_k\}
$$

es un subespacio de mejor ajuste de dimensión $k$.

La estrategia es *greedy* porque en cada paso elige la mejor dirección entre
las que siguen disponibles. Que esas decisiones sucesivas produzcan también
la solución global no es automático; se deduce de Courant--Fischer.

## 4. Fórmula de Courant--Fischer

### Teorema 4.1. Courant--Fischer, forma secuencial

**Enunciado.** Sea $M\in\mathbb R^{d\times d}$ simétrica, con valores propios

$$
\lambda_1\geq\lambda_2\geq\cdots\geq\lambda_d
$$

y una base ortonormal de vectores propios $q_1,\ldots,q_d$. Entonces, para
$j=1,\ldots,d$,

$$
\boxed{
\lambda_j=
\max_{\substack{x\neq0\\x\perp q_1,\ldots,q_{j-1}}}
\frac{x^TMx}{x^Tx}.
}
$$

El máximo se alcanza, en particular, en $x=q_j$.

**Prueba.** Si $x\perp q_1,\ldots,q_{j-1}$, entonces

$$
x=\sum_{i=j}^d\alpha_iq_i.
$$

Como los $q_i$ son ortonormales,

$$
\frac{x^TMx}{x^Tx}
=\frac{\sum_{i=j}^d\lambda_i\alpha_i^2}
       {\sum_{i=j}^d\alpha_i^2}
\leq\lambda_j.
$$

La igualdad se obtiene al tomar $x=q_j$. $\square$

### Consecuencia para el problema de ajuste

Tomamos $M=X^TX$. Entonces

$$
\|Xv\|^2=v^TX^TXv,
$$

y los valores propios de $X^TX$ son
$\sigma_1^2\geq\cdots\geq\sigma_r^2>0$, seguidos eventualmente por ceros.
Courant--Fischer muestra, paso a paso, que puede elegirse

$$
v_j\in\arg\max_{\substack{\|v\|=1\\v\perp v_1,\ldots,v_{j-1}}}
\|Xv\|^2
$$

como el $j$-ésimo vector singular derecho. Por ello la construcción
secuencial y la optimización global conducen al mismo subespacio.

## 5. Solución mediante la SVD

Sea

$$
X=U\Sigma V^T
=\sum_{j=1}^r\sigma_ju_jv_j^T,
\qquad
\sigma_1\geq\cdots\geq\sigma_r>0.
$$

### Teorema 5.1. Mejor subespacio

**Enunciado.** Un $k$-subespacio de mejor ajuste para las filas de $X$ es

$$
\boxed{V_k=\operatorname{span}\{v_1,\ldots,v_k\}.}
$$

La máxima suma de cuadrados de las proyecciones y el error mínimo son

$$
\boxed{S(V_k)=\sum_{j=1}^k\sigma_j^2,}
$$

$$
\boxed{E(V_k)=\sum_{j=k+1}^r\sigma_j^2.}
$$

**Prueba.** Para una base ortonormal $Q=[q_1\ \cdots\ q_k]$,

$$
\|XQ\|_F^2
=\operatorname{tr}(Q^TX^TXQ).
$$

La construcción sucesiva y Courant--Fischer muestran que el máximo se obtiene
con $q_j=v_j$ y vale $\sum_{j=1}^k\sigma_j^2$. La Proposición 1.2 da entonces
el error mínimo. $\square$

```{admonition} Posible falta de unicidad
:class: important
Si $\sigma_k>\sigma_{k+1}$, el subespacio óptimo de dimensión $k$ es único.
Si $\sigma_k=\sigma_{k+1}$, distintas elecciones dentro del subespacio
singular repetido pueden producir soluciones óptimas diferentes.
```

## 6. Proyectar todas las filas a la vez

Sea $V_k=[v_1\ \cdots\ v_k]$. La matriz cuyas filas son las proyecciones de
las filas de $X$ sobre el mejor subespacio es

$$
\boxed{X_k=XV_kV_k^T.}
$$

Usando la SVD,

$$
XV_k=U_k\Sigma_k,
$$

por lo que

$$
\boxed{
X_k=U_k\Sigma_kV_k^T
=\sum_{j=1}^k\sigma_ju_jv_j^T.
}
$$

También

$$
X_k=U_kU_k^TX,
$$

que proyecta las columnas de $X$ sobre
$\operatorname{span}\{u_1,\ldots,u_k\}$.

## 7. Mejor aproximación matricial de rango bajo

### Teorema 7.1. Eckart--Young--Mirsky

**Enunciado.** Sea $A\in\mathbb R^{m\times n}$ con valores singulares
$\sigma_1\geq\cdots\geq\sigma_r>0$. Para $0\leq k<r$, la SVD truncada

$$
A_k=\sum_{j=1}^k\sigma_ju_jv_j^T
$$

resuelve

$$
\boxed{
A_k\in\arg\min_{\operatorname{rango}(B)\leq k}\|A-B\|_F.
}
$$

Además,

$$
\boxed{
\|A-A_k\|_F
=\left(\sum_{j=k+1}^r\sigma_j^2\right)^{1/2}.
}
$$

Para la norma espectral,

$$
\boxed{
\min_{\operatorname{rango}(B)\leq k}\|A-B\|_2
=\|A-A_k\|_2
=\sigma_{k+1}.
}
$$

**Idea de prueba.** El error de $A_k$ se obtiene restando las expansiones SVD.
Para cualquier matriz $B$ de rango a lo sumo $k$, existe una dirección
unitaria en $\operatorname{span}\{v_1,\ldots,v_{k+1}\}$ que pertenece a
$\ker(B)$. Sobre esa dirección, $A-B$ no puede tener norma menor que
$\sigma_{k+1}$. La versión completa para la norma de Frobenius distribuye el
error inevitable entre todas las direcciones descartadas.

## 8. Selección del rango

No existe un único $k$ correcto para todas las aplicaciones. Dos medidas
útiles son:

### Error relativo

$$
\boxed{
\frac{\|A-A_k\|_F}{\|A\|_F}
=\sqrt{
\frac{\sum_{j=k+1}^r\sigma_j^2}
{\sum_{j=1}^r\sigma_j^2}
}.}
$$

### Proporción de la norma de Frobenius al cuadrado conservada

$$
\boxed{
\eta_k
=\frac{\sum_{j=1}^k\sigma_j^2}
{\sum_{j=1}^r\sigma_j^2}.
}
$$

Se puede elegir el menor $k$ tal que $\eta_k$ supere un umbral, por ejemplo
$0.90$ o $0.95$. El umbral es una decisión de modelamiento, no un teorema.

## 9. Almacenamiento y compresión

Una matriz densa $A\in\mathbb R^{m\times n}$ requiere $mn$ números. La forma
truncada almacena

$$
U_k:m\times k,
\qquad
\Sigma_k:k,
\qquad
V_k:n\times k,
$$

es decir,

$$
\boxed{k(m+n+1)}
$$

números. Hay reducción nominal cuando

$$
k(m+n+1)<mn.
$$

```{admonition} Conteo matemático y archivo real
:class: warning
Este conteo ignora encabezados, precisión, codificación y metadatos. Una SVD
truncada no es automáticamente un formato de archivo competitivo; aquí se
usa para comprender la aproximación de rango bajo.
```

## 10. Aplicación a imágenes

Una imagen en escala de grises puede verse como una matriz cuyos valores
representan intensidades. Una reconstrucción de rango $k$ es

$$
I_k=U_k\Sigma_kV_k^T.
$$

Al aumentar $k$:

- disminuye el error de Frobenius;
- aumenta el detalle visible;
- aumenta el almacenamiento de los factores.

Para imágenes RGB pueden aproximarse por separado las tres matrices de color.
Después de reconstruir, las intensidades deben limitarse al rango válido antes
de visualizar o guardar.

El laboratorio utiliza una fotografía suministrada por el docente. La copia
incluida en el libro se redujo a $640\times427$ píxeles, se convirtió a escala
de grises y se exportó sin metadatos de cámara.

## 11. Ejemplo pequeño

Supongamos que una matriz tiene SVD

$$
A=6u_1v_1^T+3u_2v_2^T+u_3v_3^T.
$$

La mejor aproximación de rango uno es

$$
A_1=6u_1v_1^T,
$$

con errores

$$
\|A-A_1\|_2=3,
\qquad
\|A-A_1\|_F=\sqrt{3^2+1^2}=\sqrt{10}.
$$

La mejor aproximación de rango dos es

$$
A_2=6u_1v_1^T+3u_2v_2^T,
$$

y ambos errores valen $1$.

## 12. Relación con PCA

Cuando las filas de $X$ son observaciones centradas, para cada vector unitario
$v$ las coordenadas proyectadas son $Xv$ y

$$
\operatorname{Var}(Xv)=\frac1N\|Xv\|^2
$$

si se usa la convención poblacional. Por tanto, en datos centrados, maximizar
$S(V)$ equivale a maximizar la varianza total de las coordenadas proyectadas.
Esta interpretación, las coordenadas principales y sus aplicaciones se
desarrollan en C23. Para datos no centrados, $\|Xv\|^2/N$ es un segundo
momento respecto del origen y no debe llamarse varianza.

## 13. Errores frecuentes

1. Truncar valores singulares sin conservar el mismo orden en $U$ y $V$.
2. Confundir el valor singular $\sigma_j$ con su contribución
   $\sigma_j^2$ a la norma de Frobenius al cuadrado.
3. Afirmar que $A_k$ tiene rango exactamente $k$ cuando se incluyeron valores
   singulares nulos.
4. Proyectar filas con $U_kU_k^T$ en lugar de $V_kV_k^T$.
5. Aplicar la interpretación de PCA a datos no centrados.
6. Comparar calidad solo por apariencia, sin medir error y almacenamiento.
