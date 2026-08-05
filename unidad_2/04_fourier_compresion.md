# Aproximación de Fourier y compresión de imágenes

## Objetivos

Al finalizar este tema, el estudiante podrá:

1. interpretar los coeficientes de Fourier como coordenadas en una familia
   ortonormal;
2. demostrar que las sumas parciales de Fourier son las mejores
   aproximaciones dentro de los polinomios trigonométricos;
3. formular la transformada discreta de Fourier en una base ortonormal;
4. interpretar la DCT bidimensional y la compresión como selección de
   componentes de frecuencia.

```{admonition} Prerrequisito
:class: note
Antes de continuar, revise
[Números complejos y espacios con producto interno complejo](04_numeros_complejos_espacios.md).
Allí se fijan la forma polar, la fórmula de Euler, los espacios vectoriales
complejos y la convención del producto interno que se usa en este tema.
```

## 1. Fourier como proyección

Consideremos el espacio de Hilbert $L^2([-\pi,\pi],\mathbb C)$, formado por
funciones de cuadrado integrable, con producto interno

$$
\langle f,g\rangle
=\frac1{2\pi}\int_{-\pi}^{\pi}
f(t)\overline{g(t)}\,dt.
$$

Para los ejemplos del curso basta pensar en funciones continuas por tramos. La
formulación en $L^2$ permite aplicar el teorema de proyección; no
desarrollaremos aquí los detalles analíticos de este espacio.

### Teorema 1.1. Ortogonalidad de las exponenciales

**Enunciado.** Las funciones

$$
e_k(t)=e^{ikt},
\qquad k\in\mathbb Z,
$$

forman una familia ortonormal:

$$
\langle e_k,e_m\rangle=\delta_{km}.
$$

**Prueba.** Como $\overline{e^{imt}}=e^{-imt}$,

$$
\langle e_k,e_m\rangle
=\frac1{2\pi}\int_{-\pi}^{\pi}e^{i(k-m)t}\,dt.
$$

Si $k=m$, la integral vale $2\pi$. Si $k\neq m$, una primitiva muestra que
los valores en ambos extremos se cancelan. $\square$

### Definición 1.2. Polinomios trigonométricos

El espacio de polinomios trigonométricos de orden $N$ es

$$
\mathcal T_N
=\operatorname{span}\{e_{-N},\ldots,e_{-1},e_0,e_1,\ldots,e_N\}.
$$

Tiene dimensión $2N+1$.

### Teorema 1.3. Suma parcial de Fourier

**Enunciado.** La proyección de $f$ sobre $\mathcal T_N$ es

$$
\boxed{
S_Nf(t)=\sum_{k=-N}^{N}c_ke^{ikt},
}
$$

donde

$$
\boxed{
c_k=\langle f,e_k\rangle
=\frac1{2\pi}\int_{-\pi}^{\pi}f(t)e^{-ikt}\,dt.
}
$$

Además,

$$
\boxed{
\|f-S_Nf\|^2
=\|f\|^2-\sum_{k=-N}^{N}|c_k|^2.
}
$$

**Prueba.** El Teorema 1.1 permite aplicar la fórmula de proyección compleja
del tema anterior. La identidad del error se obtiene por Pitágoras. $\square$

Los coeficientes $c_k$ son coordenadas de $f$ en direcciones de frecuencia.
El valor $|c_k|^2$ mide la contribución cuadrática de la frecuencia $k$.

### Teorema 1.4. Mejor aproximación por polinomios trigonométricos

**Enunciado.** Para todo $p\in\mathcal T_N$,

$$
\boxed{
\|f-p\|^2
=\|f-S_Nf\|^2+\|S_Nf-p\|^2.
}
$$

En consecuencia,

$$
\boxed{
\|f-S_Nf\|
=\min_{p\in\mathcal T_N}\|f-p\|,
}
$$

y la igualdad $\|f-p\|=\|f-S_Nf\|$ ocurre solamente cuando $p=S_Nf$.

**Prueba.** Como $S_Nf$ es la proyección de $f$ sobre $\mathcal T_N$,

$$
f-S_Nf\perp\mathcal T_N.
$$

Para $p\in\mathcal T_N$, el vector $S_Nf-p$ también pertenece a
$\mathcal T_N$. Por tanto, en la descomposición

$$
f-p=(f-S_Nf)+(S_Nf-p)
$$

los dos sumandos son ortogonales. Pitágoras da la identidad y muestra que el
segundo término solo puede aumentar el error. $\square$

```{admonition} Por qué la aproximación de Fourier es tan buena
:class: important
Entre **todos** los polinomios trigonométricos de orden a lo más $N$, la suma
parcial $S_Nf$ es el único que produce el menor error en la norma cuadrática.
No se escogen los coeficientes por ensayo: son las coordenadas de una
proyección ortogonal.
```

### Ejemplo 1.5. La función $f(t)=t$

En $[-\pi,\pi]$, se tiene $c_0=0$ y, para $k\neq0$,

$$
c_k=\frac1{2\pi}\int_{-\pi}^{\pi}t e^{-ikt}\,dt
=i\frac{(-1)^k}{k}.
$$

Por tanto,

$$
S_Nf(t)
=2\sum_{k=1}^{N}\frac{(-1)^{k+1}}{k}\sin(kt).
$$

La forma real aparece al reunir los términos de frecuencias $k$ y $-k$.

## 2. Forma real de Fourier

Si $f$ toma valores reales, entonces

$$
c_{-k}=\overline{c_k}.
$$

Al usar la fórmula de Euler, la misma proyección puede escribirse como

$$
\boxed{
S_Nf(t)=\frac{a_0}{2}
+\sum_{k=1}^{N}
\bigl(a_k\cos(kt)+b_k\sin(kt)\bigr),
}
$$

con

$$
a_k=\frac1\pi\int_{-\pi}^{\pi}f(t)\cos(kt)\,dt,
\qquad k\geq0,
$$

$$
b_k=\frac1\pi\int_{-\pi}^{\pi}f(t)\sin(kt)\,dt,
\qquad k\geq1.
$$

Fourier complejo y Fourier real son la misma proyección escrita en dos
familias equivalentes: exponenciales complejas o senos y cosenos.

### Ejemplo 2.1. Onda cuadrada

Para la extensión periódica de

$$
f(t)=
\begin{cases}
-1,&-\pi<t<0,\\
1,&0<t<\pi,
\end{cases}
$$

la función es impar. Por tanto, $a_k=0$ y

$$
b_k=
\begin{cases}
\dfrac4{\pi k},&k\text{ impar},\\
0,&k\text{ par}.
\end{cases}
$$

Así,

$$
S_Nf(t)=\frac4\pi
\sum_{\substack{1\leq k\leq N\\k\text{ impar}}}
\frac{\sin(kt)}{k}.
$$

Cerca de los saltos aparece una sobreoscilación persistente conocida como
fenómeno de Gibbs.

## 3. Fourier discreto

Una señal digital con $M$ muestras es un vector
$x=(x_0,\ldots,x_{M-1})\in\mathbb C^M$. Usamos el producto interno promedio

$$
\langle x,y\rangle_M
=\frac1M\sum_{n=0}^{M-1}x_n\overline{y_n}.
$$

### Teorema 3.1. Base discreta de Fourier

**Enunciado.** Los vectores

$$
e_k[n]=e^{2\pi i kn/M},
\qquad k=0,\ldots,M-1,
$$

forman una base ortonormal de $\mathbb C^M$ para
$\langle\cdot,\cdot\rangle_M$.

**Idea de prueba.** El producto interno entre $e_k$ y $e_\ell$ es una suma
geométrica de potencias de una raíz $M$-ésima de la unidad. La suma vale uno
si $k=\ell$ y cero en caso contrario.

### Corolario 3.2. Transformada discreta e inversa

Los coeficientes y la reconstrucción son

$$
\boxed{
\widehat x_k
=\frac1M\sum_{n=0}^{M-1}x_ne^{-2\pi i kn/M},
}
$$

$$
\boxed{
x_n=\sum_{k=0}^{M-1}\widehat x_ke^{2\pi i kn/M}.
}
$$

La FFT es un algoritmo eficiente para calcular estos coeficientes; no es una
transformada diferente.

### Proposición 3.3. Parseval discreto

**Enunciado.** Con la normalización anterior,

$$
\frac1M\sum_{n=0}^{M-1}|x_n|^2
=\sum_{k=0}^{M-1}|\widehat x_k|^2.
$$

**Prueba.** Es la identidad de Parseval para las coordenadas de $x$ en una
base ortonormal. $\square$

Conservar un subconjunto de coeficientes y anular el resto es proyectar la
señal sobre el subespacio generado por las frecuencias seleccionadas.

## 4. Imágenes y transformadas bidimensionales

Una imagen en escala de grises puede representarse por una matriz
$A\in\mathbb R^{N\times M}$. Cada entrada es la intensidad de un píxel. El
producto interno natural para matrices es el de Frobenius:

$$
\langle A,B\rangle_F
=\sum_{r,s}A_{rs}B_{rs},
\qquad
\|A\|_F^2=\sum_{r,s}|A_{rs}|^2.
$$

La transformada bidimensional usa productos de funciones de una variable. En
Fourier, cada componente representa simultáneamente una frecuencia vertical y
una horizontal.

## 5. Transformada discreta del coseno

La DCT evita trabajar explícitamente con números complejos y suele concentrar
gran parte de la norma cuadrática de bloques de imagen en pocos coeficientes de
baja frecuencia.

### Definición 5.1. Matriz DCT-II ortonormal

Para $0\leq k,n<N$, definimos

$$
C_{kn}=\alpha_k
\cos\left(\frac{\pi(2n+1)k}{2N}\right),
$$

donde

$$
\alpha_0=\frac1{\sqrt N},
\qquad
\alpha_k=\sqrt{\frac2N}\quad(k\geq1).
$$

### Teorema 5.2. Ortogonalidad y DCT bidimensional

**Enunciado.** La matriz $C$ es ortogonal:

$$
CC^T=C^TC=I.
$$

Para una imagen cuadrada $A\in\mathbb R^{N\times N}$, sus coeficientes DCT y
su reconstrucción son

$$
\boxed{B=CAC^T,}
\qquad
\boxed{A=C^TBC.}
$$

Además,

$$
\|A\|_F=\|B\|_F.
$$

**Idea de prueba.** Las filas de $C$ son muestras normalizadas de cosenos y
forman una base ortonormal de $\mathbb R^N$. La DCT 2D aplica el cambio de base
por filas y columnas. La invariancia de la norma se sigue de la ortogonalidad.

### Proposición 5.3. Selección de coeficientes

**Enunciado.** Sea $K$ un conjunto de posiciones de frecuencia y sea $B_K$ la
matriz que conserva $B_{rs}$ para $(r,s)\in K$ y coloca cero en las demás
posiciones. Entonces

$$
A_K=C^TB_KC
$$

es la proyección ortogonal de $A$ sobre los patrones DCT seleccionados, y

$$
\boxed{
\|A-A_K\|_F^2
=\sum_{(r,s)\notin K}|B_{rs}|^2.
}
$$

**Prueba.** Los patrones bidimensionales obtenidos como productos de filas de
$C$ forman una base ortonormal para el producto de Frobenius. Anular
coordenadas es proyectar sobre el subespacio generado por las restantes.
$\square$

## 6. Lectura lineal de la compresión JPEG

En una descripción simplificada, JPEG:

1. divide la imagen en bloques de $8\times8$;
2. aplica una DCT a cada bloque;
3. cuantiza los coeficientes, con mayor pérdida usual en frecuencias altas;
4. codifica eficientemente los numerosos ceros resultantes.

```{admonition} Proyección y cuantización no son lo mismo
:class: warning
Conservar algunos coeficientes y anular los demás sí es una proyección
ortogonal. La cuantización de JPEG redondea coeficientes y añade otra fuente
de error. La interpretación por proyecciones explica la selección de
frecuencias, pero JPEG contiene pasos adicionales.
```

Las bajas frecuencias describen variaciones suaves y estructura global. Las
altas frecuencias describen detalles finos, bordes y parte del ruido. La
calidad depende de cuánta norma cuadrática se conserva, no solamente del
número de coeficientes.

## 7. Errores frecuentes

1. Omitir la conjugación en un producto interno complejo.
2. Confundir la FFT con una transformada distinta de la DFT.
3. Mezclar normalizaciones de la DFT y obtener factores incorrectos de $M$.
4. Eliminar frecuencias sin preservar la simetría conjugada cuando se desea
   reconstruir una señal real.
5. Afirmar que toda compresión es una proyección: la cuantización es un paso
   no lineal.
6. Confundir compresión DCT con compresión por SVD; esta última se estudiará
   después de introducir valores singulares.
