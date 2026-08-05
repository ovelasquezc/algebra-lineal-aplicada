# Análisis de componentes principales y aplicaciones

## Objetivos

Al finalizar esta sesión, podrás:

1. distinguir una aproximación SVD de un subespacio afín obtenido mediante PCA;
2. centrar un conjunto de datos y construir su matriz de covarianza;
3. probar la equivalencia entre minimizar distancias y maximizar varianza;
4. calcular componentes, coordenadas principales y reconstrucciones;
5. proyectar datos de $\mathbb R^3$ sobre un plano principal;
6. interpretar una aproximación de rango bajo mediante factores latentes;
7. usar esos factores para formular una predicción sencilla de calificaciones.

## 1. SVD sin centrar frente a PCA

Consideremos una nube de puntos de $\mathbb R^2$ alargada y situada
principalmente en un cuadrante, lejos del origen. Hay dos problemas distintos.

### 1.1. SVD de rango uno: una recta que pasa por el origen

Si las observaciones son las filas de $X$, la aproximación de rango uno sin
centrar resuelve

$$
\min_{\dim V=1}\sum_{i=1}^N\operatorname{dist}(x_i,V)^2,
$$

donde $V=\operatorname{span}\{v\}$ es un **subespacio lineal**. Toda recta
admisible debe pasar por el origen. La solución es

$$
V=\operatorname{span}\{v_1\},
$$

con $v_1$ el primer vector singular derecho de $X$. Cuando la nube está lejos
del origen, su posición puede influir fuertemente en esta dirección.

### 1.2. PCA: una recta afín que pasa por la media

Primero buscamos el punto que minimiza la suma de distancias cuadradas a las
observaciones:

$$
\boxed{
\bar x=\arg\min_{a\in\mathbb R^d}\sum_{i=1}^N\|x_i-a\|^2.
}
$$

**Prueba.** Para cualquier $a$,

$$
\sum_i\|x_i-a\|^2
=\sum_i\|x_i-\bar x\|^2+N\|a-\bar x\|^2.
$$

El segundo término es no negativo y solo se anula cuando $a=\bar x$.
$\square$

Después centramos $z_i=x_i-\bar x$ y calculamos la mejor dirección $v_1$ para
la matriz centrada $Z$. Al regresar a las coordenadas originales obtenemos

$$
\boxed{A_1=\bar x+\operatorname{span}\{v_1\}.}
$$

$A_1$ es un **subespacio afín**: pasa por la media y, salvo que la media esté
alineada de manera especial, no pasa por el origen.

```{figure} figuras/svd_vs_pca_afin.svg
---
name: svd-frente-pca-afin
width: 100%
---
La SVD aplicada directamente a los datos busca una recta lineal obligada a
pasar por el origen. PCA centra la nube y produce una recta afín que pasa por
la media. El laboratorio calcula y compara ambas rectas para los mismos datos.
```

```{admonition} La diferencia esencial
:class: important
SVD no es sinónimo de PCA. PCA puede calcularse mediante la SVD de la matriz
centrada, pero incluye una traslación: primero resta la media y finalmente la
vuelve a sumar. Así transforma un problema de subespacios lineales para $Z$
en un problema de subespacios afines para $X$.
```

## 2. Centrado de los datos

Sean $x_1,\ldots,x_N\in\mathbb R^d$ observaciones y

$$
\bar x=\frac1N\sum_{i=1}^N x_i
$$

su media. Definimos los datos centrados

$$
z_i=x_i-\bar x
$$

y la matriz

$$
Z=\begin{pmatrix}z_1^T\\ \vdots\\z_N^T\end{pmatrix}.
$$

Sus columnas tienen media cero. Con las observaciones dispuestas en filas, la
normalización de la matriz de productos cruzados da la matriz de covarianza:

$$
\boxed{C=\frac1N Z^TZ.}
$$

Si se usa la convención muestral, se reemplaza $N$ por $N-1$. Este cambio
modifica los valores propios por un factor común, pero no las direcciones
principales.

La orientación de la matriz importa:

- si las observaciones son filas, $Z\in\mathbb R^{N\times d}$ y la covarianza
  entre variables es $Z^TZ/N\in\mathbb R^{d\times d}$;
- si las observaciones se colocan como columnas,
  $Z\in\mathbb R^{d\times N}$ y la misma covarianza se escribe $ZZ^T/N$.

Con observaciones en filas, $ZZ^T/N$ es en cambio una matriz de Gram entre
observaciones. Comparte los valores propios no nulos, salvo la normalización,
con $Z^TZ/N$, pero sus vectores propios viven en $\mathbb R^N$ y no son las
direcciones principales del espacio de variables $\mathbb R^d$.

```{admonition} El centrado es esencial
:class: important
Sin centrar, $\|Xv\|^2/N$ mide un segundo momento respecto del origen. Después
de centrar, $\|Zv\|^2/N$ es la varianza de las coordenadas proyectadas.
```

## 3. Distancia y varianza: dos formulaciones equivalentes

Sea $V\subseteq\mathbb R^d$ un subespacio de dimensión $k$, con base
ortonormal $Q=[q_1\ \cdots\ q_k]$, y sea $P_V=QQ^T$.

### Teorema 3.1. Equivalencia distancia--varianza

**Enunciado.** Para datos centrados, minimizar

$$
E(V)=\sum_{i=1}^N\operatorname{dist}(z_i,V)^2
$$

entre todos los subespacios de dimensión $k$ equivale a maximizar la suma de
las varianzas de las $k$ coordenadas proyectadas:

$$
\boxed{
\sum_{j=1}^k\operatorname{Var}(Zq_j)
=\frac1N\sum_{j=1}^k\|Zq_j\|^2.
}
$$

**Prueba.** Como $P_Vz_i$ y $z_i-P_Vz_i$ son ortogonales,

$$
\|z_i\|^2=\|P_Vz_i\|^2+\|z_i-P_Vz_i\|^2.
$$

Al sumar sobre $i$,

$$
\sum_i\|z_i\|^2
=\sum_i\|P_Vz_i\|^2+E(V).
$$

El primer miembro es constante. Además,

$$
\sum_i\|P_Vz_i\|^2
=\|ZQ\|_F^2
=\sum_{j=1}^k\|Zq_j\|^2.
$$

Como cada vector $Zq_j$ tiene media cero,

$$
\frac1N\|Zq_j\|^2=\operatorname{Var}(Zq_j).
$$

Por tanto, disminuir la suma de distancias cuadradas equivale a aumentar la
varianza total de las coordenadas proyectadas. $\square$

## 4. Componentes principales

Sea

$$
Z=U\Sigma V^T,
\qquad
\sigma_1\geq\cdots\geq\sigma_r>0.
$$

Como

$$
C=\frac1N V\Sigma^T\Sigma V^T,
$$

los vectores singulares derechos $v_j$ son vectores propios de la covarianza
y

$$
\lambda_j=\frac{\sigma_j^2}{N}.
$$

### Definición 4.1. Direcciones y componentes principales

Las primeras $k$ **direcciones principales** son
$v_1,\ldots,v_k$. Las **coordenadas principales** de las observaciones son
las filas de

$$
\boxed{T_k=ZV_k=U_k\Sigma_k,}
$$

donde $V_k=[v_1\ \cdots\ v_k]$.

La reconstrucción en el espacio original es

$$
\boxed{\widehat X_k=\mathbf 1\bar x^T+T_kV_k^T.}
$$

Es necesario sumar nuevamente la media porque PCA se calculó a partir de los
datos centrados.

### Teorema 4.2. Caracterización variacional

**Enunciado.** La primera dirección principal resuelve

$$
v_1\in\arg\max_{\|v\|=1}v^TCv.
$$

Después, para $j=2,\ldots,k$,

$$
v_j\in\arg\max_{\substack{\|v\|=1\\v\perp v_1,\ldots,v_{j-1}}}v^TCv.
$$

**Idea de prueba.** Se aplica Courant--Fischer a la matriz simétrica $C$.
Cada paso maximiza la varianza que todavía puede representarse en una
dirección ortogonal a las anteriores. Esta es la interpretación del proceso
de optimización secuencial o *greedy*.

## 5. Varianza explicada y selección de dimensión

La varianza de la componente $j$ es $\lambda_j$. Por ello,

$$
\boxed{
\rho_k=\frac{\lambda_1+\cdots+\lambda_k}
{\lambda_1+\cdots+\lambda_d}
=\frac{\sigma_1^2+\cdots+\sigma_k^2}
{\sigma_1^2+\cdots+\sigma_r^2}
}
$$

es la proporción de varianza explicada por las primeras $k$ componentes. Un
criterio práctico consiste en elegir el menor $k$ que alcance un umbral
prefijado. El umbral depende del propósito del análisis.

## 6. Proyección de puntos de $\mathbb R^3$ sobre un plano

Para observaciones tridimensionales, las dos primeras direcciones principales
generan el plano

$$
V_2=\operatorname{span}\{v_1,v_2\}.
$$

La proyección y el residuo de una observación centrada son

$$
P_{V_2}z_i=V_2V_2^Tz_i,
\qquad
r_i=z_i-P_{V_2}z_i,
$$

y satisfacen

$$
r_i\perp v_1,\qquad r_i\perp v_2.
$$

El laboratorio representa simultáneamente los puntos originales, el plano,
las proyecciones y los segmentos residuales ortogonales. Las coordenadas
bidimensionales que se conservan son

$$
t_i=V_2^Tz_i\in\mathbb R^2.
$$

## 7. Películas y componentes latentes

El siguiente ejemplo está adaptado de
[Wegner (2024)](../referencias.md). Consideremos siete personas y cinco
películas. Las filas representan personas y las columnas, películas:

| | Alien | Casablanca | Star Wars | Titanic | The Matrix |
|---|---:|---:|---:|---:|---:|
| Abbie | 0 | 2 | 0 | 2 | 1 |
| Bailey | 1 | 0 | 1 | 0 | 1 |
| Catherine | 5 | 0 | 5 | 0 | 5 |
| Darlene | 0 | 4 | 0 | 4 | 2 |
| Elena | 3 | 0 | 3 | 0 | 3 |
| Fatima | 0 | 5 | 0 | 5 | 0 |
| Gladys | 4 | 0 | 4 | 0 | 4 |

Denotemos esta matriz por $A\in\mathbb R^{7\times5}$. Su SVD tiene tres
valores singulares no nulos, aproximadamente

$$
12.4,\qquad 9.5,\qquad 1.3.
$$

La aproximación de rango dos

$$
\check A=U_2\Sigma_2V_2^T
$$

cumple

$$
\|A-\check A\|_F\approx1.3.
$$

Para almacenarla mediante sus factores se requieren
$7(2)+2+5(2)=26$ números, frente a los $35$ de la matriz original.

```{figure} figuras/doscomponentes.png
---
name: dos-componentes-peliculas
width: 100%
---
Aproximación de rango dos de la matriz de calificaciones. Los dos factores
dominantes separan aproximadamente preferencias por ciencia ficción (SF) y
por romance (RM).
```

### 7.1. Espacios de personas y películas

Sea $R\cong\mathbb R^7$ el espacio de personas y
$M\cong\mathbb R^5$ el espacio de películas. La calificación se modela como
la aplicación bilineal

$$
\operatorname{rat}:R\times M\longrightarrow\mathbb R,
\qquad
\operatorname{rat}(r,m)=r^TAm.
$$

La SVD induce bases ortonormales $\{u_1,\ldots,u_7\}$ de $R$ y
$\{v_1,\ldots,v_5\}$ de $M$. En estas bases,

$$
\operatorname{rat}(r,m)=(r)_{\mathcal U}^T\Sigma(m)_{\mathcal V}.
$$

Al conservar solo dos términos, una persona se representa mediante dos
coordenadas y cada película mediante otras dos. Estos son perfiles
artificiales o **factores latentes**: no vienen etiquetados de antemano, pero
sus signos y magnitudes permiten reconocer patrones en los datos.

```{admonition} PCA y factorización de calificaciones
:class: note
El mecanismo algebraico es el mismo: SVD, proyección y coordenadas de baja
dimensión. En PCA estadístico se centra la matriz para estudiar variación
alrededor de la media. En este ejemplo se aproxima directamente la matriz de
calificaciones para conservar su escala y obtener factores de usuarios y
películas.
```

## 8. Filtrado colaborativo: una nueva persona

Hannah ha calificado *Alien* con $4$ y *Casablanca* con $1$. Si
$(x,y)$ son sus coordenadas en el modelo de dos factores, las columnas de
$V_2^T$ y los valores singulares aproximados dan

$$
7.018x-1.204y=4,
$$

$$
1.125x+6.612y=1.
$$

La solución es aproximadamente

$$
x=0.579,\qquad y=0.053.
$$

Para *The Matrix*, cuyas dos coordenadas después de incorporar los valores
singulares son aproximadamente $(7.399,0.274)$,

$$
\operatorname{rat}(\text{Hannah},\text{The Matrix})
\approx
\begin{bmatrix}0.579&0.053\end{bmatrix}
\begin{bmatrix}7.399\\0.274\end{bmatrix}
\approx4.30.
$$

El modelo predice una calificación cercana a $4$. Es una predicción fuera de
la muestra: se estimó usando coordenadas latentes obtenidas de otras personas.

## 9. Qué debe interpretarse con cautela

1. El signo de cada componente puede invertirse sin cambiar el modelo.
2. Componentes con valores propios repetidos no determinan direcciones únicas.
3. Una proporción alta de varianza explicada no garantiza que la proyección
   sea adecuada para toda tarea posterior.
4. En datos de calificaciones, un cero puede significar una calificación real
   o un dato faltante; ambas situaciones requieren modelos distintos.
5. Los factores latentes sugieren interpretaciones, pero la SVD no les asigna
   nombres ni significado causal.

## 10. Errores frecuentes

1. Calcular PCA sin restar la media y llamar varianza al segundo momento.
2. Confundir las direcciones $V_k$ con las coordenadas $ZV_k$.
3. Reconstruir con $ZV_kV_k^T$ y olvidar sumar la media.
4. Usar $\sigma_j$ en lugar de $\sigma_j^2$ para la varianza explicada.
5. Intercambiar el espacio de personas $\mathbb R^7$ con el de películas
   $\mathbb R^5$.
