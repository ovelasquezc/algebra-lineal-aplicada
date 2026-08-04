# Repaso teórico para el Examen Parcial

## Cómo usar esta hoja

El Examen Parcial integra las Unidades 1 y 2. Esta síntesis no sustituye las
hojas de teoría: organiza los resultados que debes poder **enunciar**,
**aplicar** y **justificar**. Conviene estudiar cada resultado separando:

1. hipótesis;
2. conclusión;
3. interpretación geométrica o algebraica;
4. prueba o idea de prueba;
5. procedimiento asociado.

Para repasar con mayor detalle los fundamentos, consulta el
[repaso teórico de la PC1](../unidad_1/09_repaso_teorico_pc1.md). Después de
esta hoja, resuelve la [guía de preparación](05_preparacion_ep.md) sin
software. El [laboratorio](05_laboratorio_preparacion_ep.ipynb) sirve para
comprobar cálculos y explorar ejemplos.

```{admonition} Alcance
:class: important
El EP comprende las Unidades 1 y 2. Las transformaciones lineales, los valores
propios y la diagonalización pertenecen a la Unidad 3 y no forman parte de
esta preparación.
```

## 1. Herramientas de la Unidad 1 que se siguen usando

### 1.1. Sistemas y espacios fundamentales

Para $A\in\mathbb R^{m\times n}$,

$$
A:\mathbb R^n\longrightarrow\mathbb R^m,
\qquad
\ker(A)\subseteq\mathbb R^n,
\qquad
\operatorname{Im}(A)=\operatorname{Col}(A)\subseteq\mathbb R^m.
$$

Resolver $Ax=b$ equivale a decidir si $b\in\operatorname{Col}(A)$.

### Teorema 1.1. Rango-nulidad

**Enunciado.** Si $A$ tiene $n$ columnas, entonces

$$
\boxed{\operatorname{rango}(A)+\operatorname{nulidad}(A)=n.}
$$

**Idea de prueba.** En la forma escalonada, cada variable es pivote o libre.
Las variables pivote cuentan el rango y las libres parametrizan una base del
núcleo.

### Proposición 1.2. Soluciones de un sistema compatible

**Enunciado.** Si $x_p$ es una solución particular de $Ax=b$, entonces

$$
\boxed{\{x:Ax=b\}=x_p+\ker(A).}
$$

**Prueba.** $Ax=b=Ax_p$ si y solo si $A(x-x_p)=0$, es decir,
$x-x_p\in\ker(A)$. $\square$

### 1.2. Bases y coordenadas

Si $\mathcal B=(v_1,\ldots,v_n)$ es una base y
$M_{\mathcal B}=[v_1\ \cdots\ v_n]$, entonces

$$
x=M_{\mathcal B}[x]_{\mathcal B}.
$$

Para bases $\mathcal B$ y $\mathcal C$ del mismo espacio,

$$
\boxed{
P_{\mathcal B\to\mathcal C}
=M_{\mathcal C}^{-1}M_{\mathcal B},
\qquad
[x]_{\mathcal C}=P_{\mathcal B\to\mathcal C}[x]_{\mathcal B}.
}
$$

La columna $j$ de $P_{\mathcal B\to\mathcal C}$ es
$[v_j]_{\mathcal C}$, donde $v_j$ es el vector $j$-ésimo de $\mathcal B$.

## 2. Producto interno, norma y ortogonalidad

### Definición 2.1. Producto interno real

Un producto interno en un espacio vectorial real $V$ es una función
$\langle\cdot,\cdot\rangle:V\times V\to\mathbb R$ que es simétrica,
lineal y definida positiva. La norma inducida es

$$
\|x\|=\sqrt{\langle x,x\rangle}.
$$

Dos vectores son ortogonales cuando $\langle x,y\rangle=0$.

### Teorema 2.2. Pitágoras

**Enunciado.** Si $x\perp y$, entonces

$$
\boxed{\|x+y\|^2=\|x\|^2+\|y\|^2.}
$$

**Prueba.** Al expandir $\langle x+y,x+y\rangle$, los dos términos cruzados
son cero. $\square$

### Teorema 2.3. Cauchy-Schwarz

**Enunciado.** Para $x,y\in V$,

$$
|\langle x,y\rangle|\leq\|x\|\|y\|.
$$

Hay igualdad si y solo si $x$ e $y$ son linealmente dependientes.

**Idea de prueba.** Si $y\neq0$, se usa la no negatividad de

$$
\left\|x-\frac{\langle x,y\rangle}{\|y\|^2}y\right\|^2.
$$

### Proposición 2.4. Familia ortogonal

**Enunciado.** Toda familia ortogonal de vectores no nulos es linealmente
independiente.

**Prueba.** Si $\sum_j\alpha_jv_j=0$, se toma producto interno con $v_k$.
La ortogonalidad elimina todos los términos salvo
$\alpha_k\|v_k\|^2$, por lo que $\alpha_k=0$. Esto vale para todo $k$.
$\square$

### Teorema 2.5. Coordenadas en una base ortonormal

**Enunciado.** Si $(u_1,\ldots,u_n)$ es una base ortonormal de $V$, entonces

$$
\boxed{x=\sum_{j=1}^n\langle x,u_j\rangle u_j,}
\qquad
\boxed{\|x\|^2=\sum_{j=1}^n|\langle x,u_j\rangle|^2.}
$$

La segunda igualdad es la identidad de Parseval.

## 3. Proceso de Gram-Schmidt

### Teorema 3.1. Gram-Schmidt

**Enunciado.** A partir de una familia linealmente independiente
$(v_1,\ldots,v_r)$ se construye una familia ortogonal
$(w_1,\ldots,w_r)$ mediante

$$
w_1=v_1,
$$

$$
\boxed{
w_k=v_k-\sum_{j=1}^{k-1}
\frac{\langle v_k,w_j\rangle}{\langle w_j,w_j\rangle}w_j.
}
$$

Luego $u_k=w_k/\|w_k\|$ produce una familia ortonormal con el mismo espacio
generado.

**Idea de prueba.** Cada $w_k$ se obtiene restando de $v_k$ sus componentes
en las direcciones ya construidas. Por ello es ortogonal a
$w_1,\ldots,w_{k-1}$. Además, la transformación entre las familias es
triangular con diagonal no nula, así que preserva los espacios generados
parcialmente.

```{admonition} Señal de alerta
:class: warning
Si durante Gram-Schmidt aparece $w_k=0$, la familia inicial era linealmente
dependiente o se cometió un error de cálculo.
```

## 4. Proyección ortogonal y mínima distancia

### Teorema 4.1. Proyección sobre un subespacio

**Enunciado.** Sea $W$ un subespacio de dimensión finita. Para cada $x$ existe
un único $p\in W$ tal que

$$
x-p\in W^\perp.
$$

Este vector $p=P_W(x)$ es la única mejor aproximación de $x$ en $W$:

$$
\boxed{\|x-P_W(x)\|=\min_{w\in W}\|x-w\|.}
$$

**Prueba.** Para $w\in W$,

$$
x-w=(x-p)+(p-w),
$$

y los dos sumandos son ortogonales. Por Pitágoras,

$$
\|x-w\|^2=\|x-p\|^2+\|p-w\|^2\geq\|x-p\|^2.
$$

La igualdad solo ocurre cuando $w=p$. $\square$

### Corolario 4.2. Fórmula con base ortonormal

Si $(u_1,\ldots,u_r)$ es una base ortonormal de $W$, entonces

$$
\boxed{P_W(x)=\sum_{j=1}^r\langle x,u_j\rangle u_j.}
$$

Si $U=[u_1\ \cdots\ u_r]$, la matriz de proyección es

$$
\boxed{P=UU^T.}
$$

Cumple

$$
P^T=P,
\qquad
P^2=P,
\qquad
\operatorname{Im}(P)=W,
\qquad
\ker(P)=W^\perp.
$$

### Proposición 4.3. Fórmula con una base cualquiera

Si las columnas de $A$ forman una base de $W$, entonces

$$
\boxed{P_W=A(A^TA)^{-1}A^T.}
$$

No debe usarse esta fórmula si las columnas de $A$ son dependientes.

## 5. Conjuntos afines e hiperplanos

Un conjunto afín es una traslación $H=x_0+W$ de un subespacio. Si
$p=P_H(x)$, entonces

$$
p\in H,
\qquad
x-p\in W^\perp.
$$

### Teorema 5.1. Hiperplano

**Enunciado.** Sea

$$
H=\{z\in\mathbb R^n:a^Tz=b\},
\qquad a\neq0.
$$

Entonces

$$
\boxed{P_H(x)=x-\frac{a^Tx-b}{\|a\|^2}a,}
$$

y

$$
\boxed{d(x,H)=\frac{|a^Tx-b|}{\|a\|}.}
$$

**Prueba.** El desplazamiento entre $x$ y su proyección debe ser paralelo al
normal $a$. Se escribe $p=x-ta$ y se impone $a^Tp=b$. Esto determina
$t=(a^Tx-b)/\|a\|^2$. La distancia es $\|ta\|$. $\square$

## 6. Mínimos cuadrados y ecuaciones normales

Consideremos

$$
\min_{x\in\mathbb R^n}\|Ax-b\|_2.
$$

### Teorema 6.1. Ecuaciones normales

**Enunciado.** Un vector $x^*$ minimiza $\|Ax-b\|_2$ si y solo si

$$
\boxed{A^TAx^*=A^Tb.}
$$

Equivalentemente, el residuo $r=b-Ax^*$ satisface

$$
\boxed{A^Tr=0,}
$$

es decir, $r\perp\operatorname{Col}(A)$.

**Prueba.** El vector ajustado $Ax^*$ debe ser la proyección de $b$ sobre
$\operatorname{Col}(A)$. La caracterización ortogonal de la proyección exige
que $b-Ax^*$ sea ortogonal a cada columna de $A$, lo que equivale a
$A^T(b-Ax^*)=0$. $\square$

### Proposición 6.2. Existencia y unicidad

**Enunciado.** Las ecuaciones normales siempre tienen al menos una solución.
El vector ajustado $Ax^*$ es único. Los coeficientes $x^*$ son únicos si y
solo si las columnas de $A$ son linealmente independientes.

En ese caso,

$$
x^*=(A^TA)^{-1}A^Tb.
$$

Si $A$ tiene rango deficiente, el conjunto de minimizadores es afín y dos
minimizadores cualesquiera producen el mismo vector ajustado.

### Proposición 6.3. Identidad de optimalidad

Si $x^*$ satisface las ecuaciones normales, entonces para todo $x$,

$$
\boxed{
\|Ax-b\|^2
=\|Ax^*-b\|^2+\|A(x-x^*)\|^2.
}
$$

**Prueba.** Se descompone
$Ax-b=(Ax^*-b)+A(x-x^*)$. El primer sumando es ortogonal a la imagen de $A$ y
el segundo pertenece a ella; se aplica Pitágoras. $\square$

### 6.4. Matriz de diseño

Para aproximar datos $(t_i,y_i)$ por

$$
f(t)=c_1\phi_1(t)+\cdots+c_p\phi_p(t),
$$

se construye

$$
X_{ij}=\phi_j(t_i),
\qquad
y=(y_1,\ldots,y_m)^T,
$$

y se resuelve $\min_c\|Xc-y\|_2$. El modelamiento correcto exige identificar
una columna por cada función base.

## 7. Fourier como proyección

### 7.1. Complejos mínimos

Para $z=a+bi$,

$$
\overline z=a-bi,
\qquad
|z|^2=z\overline z,
\qquad
e^{it}=\cos t+i\sin t.
$$

En $\mathbb C^n$ usamos la convención lineal en la primera entrada:

$$
\langle x,y\rangle=\sum_jx_j\overline{y_j}=y^*x.
$$

### Teorema 7.1. Serie parcial de Fourier

Con

$$
\langle f,g\rangle
=\frac1{2\pi}\int_{-\pi}^{\pi}f(t)\overline{g(t)}\,dt,
$$

las funciones $e_k(t)=e^{ikt}$ son ortonormales. La proyección de $f$ sobre
$\mathcal T_N=\operatorname{span}\{e_{-N},\ldots,e_N\}$ es

$$
\boxed{S_Nf(t)=\sum_{k=-N}^{N}c_ke^{ikt},}
$$

donde

$$
\boxed{c_k=\frac1{2\pi}\int_{-\pi}^{\pi}f(t)e^{-ikt}\,dt.}
$$

Además,

$$
\boxed{
\|f-S_Nf\|^2
=\|f\|^2-\sum_{k=-N}^{N}|c_k|^2.
}
$$

**Idea de prueba.** Es la fórmula de proyección sobre una familia ortonormal,
aplicada a un espacio de funciones.

### Teorema 7.2. DFT e identidad de Parseval

Para muestras $x_0,\ldots,x_{M-1}$ definimos

$$
\widehat x_k
=\frac1M\sum_{n=0}^{M-1}x_ne^{-2\pi ikn/M}.
$$

Entonces

$$
x_n=\sum_{k=0}^{M-1}\widehat x_ke^{2\pi ikn/M},
$$

y

$$
\boxed{
\frac1M\sum_{n=0}^{M-1}|x_n|^2
=\sum_{k=0}^{M-1}|\widehat x_k|^2.
}
$$

## 8. DCT y compresión de imágenes

Para una imagen $A\in\mathbb R^{N\times N}$ y una matriz DCT ortogonal $C$,

$$
\boxed{B=CAC^T,}
\qquad
\boxed{A=C^TBC.}
$$

La ortogonalidad preserva la norma de Frobenius:

$$
\|A\|_F^2=\sum_{j,k}|A_{jk}|^2=\|B\|_F^2.
$$

Si $B_K$ conserva ciertos coeficientes y anula los demás, entonces

$$
\boxed{
\|A-C^TB_KC\|_F^2
=\sum_{(j,k)\text{ descartado}}|B_{jk}|^2.
}
$$

Seleccionar coeficientes es una proyección sobre un subespacio generado por
patrones DCT. Cuantizar los coeficientes es un paso adicional y no lineal.

## 9. Conexiones que debes reconocer

| Situación | Subespacio | Proyección o residuo |
|---|---|---|
| Aproximar un vector por columnas de $A$ | $\operatorname{Col}(A)$ | $Ax^*=P_{\operatorname{Col}(A)}b$ |
| Proyectar sobre $\ker(A)$ | $\ker(A)$ | primero base, luego Gram-Schmidt |
| Ajustar datos con funciones $\phi_j$ | columnas de la matriz de diseño | el residuo es ortogonal a cada columna |
| Suma parcial de Fourier | $\mathcal T_N$ | conserva frecuencias seleccionadas |
| Compresión DCT | patrones DCT conservados | el error es la energía descartada |

En todos los casos aparece la misma estructura:

$$
\boxed{
\text{dato}=\text{mejor aproximación}+\text{residuo ortogonal}.
}
$$

## 10. Errores frecuentes

1. Elegir columnas pivote de la RREF en vez de la matriz original para una
   base de la imagen.
2. Aplicar Gram-Schmidt a una familia dependiente sin detectarlo.
3. Usar $UU^T$ cuando las columnas de $U$ no son ortonormales.
4. Confundir la proyección sobre un hiperplano afín con la proyección sobre
   su subespacio paralelo.
5. Afirmar que los coeficientes de mínimos cuadrados siempre son únicos.
6. Construir una matriz de diseño sin una columna por cada función base.
7. Mezclar normalizaciones distintas de la DFT.
8. Confundir selección de frecuencias con cuantización JPEG.
9. Usar números complejos en Fourier sin conjugación en el producto interno.
10. Dar un resultado numérico sin identificar el espacio, las hipótesis o la
    interpretación solicitada.
