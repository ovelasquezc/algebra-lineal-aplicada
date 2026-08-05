# Repaso teórico para el examen final

## Cómo usar esta hoja

El examen final es acumulativo. Esta hoja reúne los resultados que conectan
las unidades y desarrolla con mayor detalle los temas posteriores a la PC2.
Para revisar los prerrequisitos, consulta también:

- [repaso para la PC1](../unidad_1/09_repaso_teorico_pc1.md);
- [repaso para el examen parcial](../unidad_2/05_repaso_teorico_ep.md);
- [repaso para la PC2](../unidad_3/07_repaso_teorico_pc2.md).

Después resuelve la [guía de preparación](03_preparacion_ef.md) sin software y
usa el [laboratorio](03_laboratorio_preparacion_ef.ipynb) para verificar los
cálculos.

```{admonition} Alcance de esta versión
:class: important
Este repaso fue preparado con el avance hasta SVD, pseudoinversa y
aproximación de rango bajo. Para PCA y sus aplicaciones debe complementarse
con C23. Gradiente, Hessiana y optimización se incorporarán más adelante.
```

## 1. Herramientas acumulativas

### Resultado 1.1. Rango-nulidad

**Enunciado.** Para $A\in\mathbb R^{m\times n}$,

$$
\boxed{\dim\ker(A)+\operatorname{rango}(A)=n.}
$$

**Idea de prueba.** Se extiende una base de $\ker(A)$ a una base de
$\mathbb R^n$. Las imágenes de los vectores añadidos forman una base de
$\operatorname{Im}(A)$.

### Resultado 1.2. Descomposiciones ortogonales

**Enunciado.** Para todo subespacio $S\subseteq\mathbb R^n$,

$$
\mathbb R^n=S\oplus S^\perp.
$$

Si las columnas de $Q$ forman una base ortonormal de $S$, entonces

$$
\boxed{P_S=QQ^T},\qquad
x=P_Sx+(I-P_S)x.
$$

Las matrices $P_S$ satisfacen $P_S^T=P_S$ y $P_S^2=P_S$.

### Resultado 1.3. Espacios fundamentales

**Enunciado.**

$$
\boxed{\operatorname{Im}(A)^\perp=\ker(A^T)},
\qquad
\boxed{\operatorname{Im}(A^T)^\perp=\ker(A)}.
$$

**Prueba de la primera igualdad.** Un vector $y$ pertenece a
$\operatorname{Im}(A)^\perp$ si y solo si $y^TAx=0$ para todo $x$, lo que
equivale a $A^Ty=0$. La segunda se obtiene aplicando la primera a $A^T$.
$\square$

### Resultado 1.4. Mínimos cuadrados y ecuaciones normales

**Enunciado.** Un vector $x_*$ minimiza $\|Ax-b\|_2$ si y solo si

$$
\boxed{A^TAx_*=A^Tb.}
$$

Equivalentemente, el residuo es ortogonal a la imagen:
$b-Ax_*\in\ker(A^T)$. El vector ajustado $Ax_*$ es único, aunque $x_*$ puede
no serlo.

**Idea de prueba.** Se descompone $b$ en su proyección sobre
$\operatorname{Im}(A)$ y su componente ortogonal. El término ortogonal no
puede reducirse eligiendo otro $x$.

## 2. Teoría espectral y formas cuadráticas

### Teorema 2.1. Teorema espectral real

**Enunciado.** Si $A=A^T\in\mathbb R^{n\times n}$, existe una matriz ortogonal
$Q$ y una matriz diagonal real $\Lambda$ tales que

$$
\boxed{A=Q\Lambda Q^T.}
$$

Por tanto, $\mathbb R^n$ admite una base ortonormal de vectores propios de
$A$.

**Idea de prueba.** Se obtiene un vector propio unitario real mediante un
extremo del cociente de Rayleigh. Su complemento ortogonal es invariante y
se aplica inducción a la restricción de $A$.

### Resultado 2.2. Cociente de Rayleigh

**Enunciado.** Si $A=A^T$ y sus valores propios satisfacen
$\lambda_1\geq\cdots\geq\lambda_n$, entonces

$$
\boxed{\lambda_n\leq \frac{x^TAx}{x^Tx}\leq\lambda_1}
\quad(x\neq0).
$$

Los extremos se alcanzan en vectores propios de los valores propios extremos.

### Resultado 2.3. Clasificación de una forma cuadrática

Sea $q(x)=x^TAx$ con $A=A^T$. Entonces:

1. $q$ es definida positiva si todos los valores propios son positivos;
2. es semidefinida positiva si todos son no negativos;
3. es definida negativa si todos son negativos;
4. es indefinida si hay valores propios de signos opuestos.

**Justificación.** Si $A=Q\Lambda Q^T$ y $z=Q^Tx$, entonces

$$
q(x)=\sum_{i=1}^n\lambda_i z_i^2.
$$

## 3. Descomposición en valores singulares

### Teorema 3.1. SVD completa y reducida

**Enunciado.** Toda $A\in\mathbb R^{m\times n}$ de rango $r$ admite

$$
\boxed{A=U\Sigma V^T},
$$

donde $U$ y $V$ son ortogonales y las entradas diagonales no nulas de
$\Sigma$ son

$$
\sigma_1\geq\cdots\geq\sigma_r>0.
$$

La SVD reducida es

$$
\boxed{A=U_r\Sigma_rV_r^T}
$$

con tamaños $U_r:m\times r$, $\Sigma_r:r\times r$ y $V_r:n\times r$.

**Idea de prueba.** Se diagonaliza ortogonalmente $A^TA$. Para cada vector
propio unitario $v_i$ asociado a $\sigma_i^2>0$, se define
$u_i=Av_i/\sigma_i$. Estos vectores son ortonormales y satisfacen
$Av_i=\sigma_i u_i$.

### Resultado 3.2. Espacios fundamentales leídos en la SVD

**Enunciado.** Si $A=U_r\Sigma_rV_r^T$, entonces

$$
\boxed{\operatorname{Im}(A)=\operatorname{span}\{u_1,\ldots,u_r\}},
$$

$$
\boxed{\operatorname{Im}(A^T)=\operatorname{span}\{v_1,\ldots,v_r\}}.
$$

En una SVD completa, los vectores derechos restantes forman una base de
$\ker(A)$ y los izquierdos restantes forman una base de $\ker(A^T)$.

### Resultado 3.3. Transformaciones de los valores singulares

**Enunciado.** Los valores singulares no nulos cumplen:

1. $A$ y $A^T$ tienen los mismos valores singulares;
2. los de $tA$ son $|t|\sigma_i$;
3. si $A$ es invertible, los de $A^{-1}$ son los recíprocos, ordenados en
   sentido inverso;
4. si $A$ es cuadrada, $|\det A|=\prod_i\sigma_i$.

**Prueba de 4.** De $A=U\Sigma V^T$,

$$
|\det A|=|\det U|\det(\Sigma)|\det V^T|
=\prod_i\sigma_i,
$$

pues los determinantes de las matrices ortogonales tienen valor absoluto
uno. $\square$

### Resultado 3.4. Normas inducidas por la SVD

**Enunciado.**

$$
\boxed{\|A\|_2=\sigma_1},
\qquad
\boxed{\|A\|_F^2=\sum_{i=1}^r\sigma_i^2}.
$$

La primera mide la máxima amplificación sobre vectores unitarios; la segunda
es la suma de los cuadrados de todas las entradas.

## 4. Pseudoinversa

### Definición 4.1. Pseudoinversa de Moore--Penrose

Si $A=U_r\Sigma_rV_r^T$, se define

$$
\boxed{A^+=V_r\Sigma_r^{-1}U_r^T.}
$$

### Teorema 4.2. Caracterización de Moore--Penrose

**Enunciado.** $A^+$ es la única matriz que satisface

$$
AA^+A=A,qquad A^+AA^+=A^+,
$$

$$
(AA^+)^T=AA^+,qquad (A^+A)^T=A^+A.
$$

**Idea de prueba.** Al sustituir la SVD, las identidades se reducen a las
correspondientes para la diagonal $\Sigma$ y su inversa sobre las entradas
no nulas. La unicidad se obtiene separando dominio y codominio en los cuatro
espacios fundamentales.

### Resultado 4.3. Proyecciones y solución canónica

**Enunciado.**

$$
\boxed{AA^+=P_{\operatorname{Im}(A)}},
\qquad
\boxed{A^+A=P_{\operatorname{Im}(A^T)}}.
$$

Además,

$$
\boxed{x_*=A^+b}
$$

es la única solución de norma mínima entre todas las soluciones de mínimos
cuadrados. Si $Ax=b$ es compatible, es su solución de norma mínima.

**Idea de prueba.** La SVD descompone $b$ en direcciones $u_i$. La
pseudoinversa invierte solo las direcciones con $\sigma_i>0$ y elimina la
componente de $\ker(A^T)$. Toda otra solución de mínimos cuadrados difiere
de $x_*$ en un vector de $\ker(A)$, ortogonal a $x_*$.

## 5. Aproximación de rango bajo

### Teorema 5.1. Eckart--Young--Mirsky

Sea

$$
A=\sum_{i=1}^r\sigma_i u_iv_i^T,
\qquad
A_k=\sum_{i=1}^k\sigma_i u_iv_i^T.
$$

**Enunciado.** Entre todas las matrices $B$ de rango a lo más $k$,
$A_k$ es una mejor aproximación de $A$ tanto en norma espectral como en
norma de Frobenius. Además,

$$
\boxed{\|A-A_k\|_2=\sigma_{k+1}},
$$

$$
\boxed{\|A-A_k\|_F^2=\sum_{i=k+1}^r\sigma_i^2.}
$$

**Idea de prueba.** La matriz truncada conserva las $k$ direcciones de mayor
amplificación. Ninguna matriz de rango $k$ puede reproducir todas las
$k+1$ primeras direcciones singulares; la ortogonalidad de los sumandos da
la fórmula exacta para el error de Frobenius.

### Resultado 5.2. Mejor subespacio para las filas

**Enunciado.** Si las filas de $X$ son datos en $\mathbb R^d$, un subespacio
de dimensión $k$ que minimiza la suma de distancias cuadradas es

$$
\boxed{S_k=\operatorname{span}\{v_1,\ldots,v_k\}.}
$$

La parte de $\|A\|_F^2$ conservada es $\sum_{i=1}^k\sigma_i^2$ y el error residual al cuadrado es
$\sum_{i=k+1}^r\sigma_i^2$.

## 6. Procedimientos que debes dominar

### Construir una SVD

1. Calcula $A^TA$ y sus valores propios no negativos.
2. Ordena $\sigma_i=\sqrt{\lambda_i}$ de mayor a menor.
3. Elige vectores propios derechos ortonormales $v_i$.
4. Para $\sigma_i>0$, calcula $u_i=Av_i/\sigma_i$.
5. Completa bases ortonormales si se pide la SVD completa.
6. Verifica dimensiones, ortogonalidad y $U\Sigma V^T=A$.

### Resolver con la pseudoinversa

1. Identifica el rango y usa solo valores singulares positivos.
2. Forma $A^+=V_r\Sigma_r^{-1}U_r^T$.
3. Calcula $x_*=A^+b$ y $\widehat b=AA^+b$.
4. Comprueba $A^T(b-Ax_*)=0$.
5. Decide compatibilidad verificando si $AA^+b=b$.

### Construir una aproximación de rango $k$

1. Conserva los primeros $k$ términos de la SVD.
2. Calcula el error a partir de los valores singulares descartados.
3. Distingue la proporción de $\|A\|_F^2$ conservada,
   $100\sum_{i\leq k}\sigma_i^2/\sum_i\sigma_i^2$, de reducción de
   almacenamiento.

## 7. Errores frecuentes

- Confundir valores propios con valores singulares.
- Usar $u_i=Av_i/\sigma_i$ cuando $\sigma_i=0$.
- Omitir los vectores que completan $U$ o $V$ en una SVD completa.
- Suponer que $A^+=(A^TA)^{-1}A^T$ sin verificar rango columna completo.
- Creer que $A^+b$ siempre resuelve exactamente $Ax=b$.
- Truncar según el tamaño de entradas y no según los valores singulares.
- Usar $\sum_i\sigma_i$ cuando se pide la norma de Frobenius al cuadrado o
  el error de Frobenius.
