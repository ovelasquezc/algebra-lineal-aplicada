# Preparación para el examen final

```{admonition} Orden de trabajo
:class: note
Estudia primero el [repaso teórico](03_repaso_teorico_ef.md). Resuelve esta
guía por escrito y sin software. Después usa el
[laboratorio](03_laboratorio_preparacion_ef.ipynb) para comprobar resultados.
```

## Propósito, alcance y procedencia

Esta versión cubre el curso hasta aproximación de rango bajo. No incluye PCA,
gradiente, Hessiana ni optimización. Los temas previos continúan siendo
prerrequisitos, pero la mayor carga está en la Unidad 3 y en los dos primeros
bloques de la Unidad 4.

La procedencia aparece en cada encabezado. **Adaptado** indica que se conserva
la habilidad evaluada, pero se ajustan el enunciado o los datos al alcance
actual. Los ejercicios de **elaboración para esta guía** completan conexiones
que no estaban representadas en los exámenes históricos.

| Prioridad | Bloque | Debes poder hacer |
|---|---|---|
| Prerrequisito | Sistemas, subespacios y ortogonalidad | hallar espacios fundamentales, proyectar y resolver mínimos cuadrados |
| Central | Espectro y formas cuadráticas | diagonalizar, aplicar el teorema espectral y clasificar formas |
| Central | SVD | construirla, leer los cuatro espacios y calcular normas |
| Central | Pseudoinversa | verificar Moore--Penrose y resolver con norma mínima |
| Central | Rango bajo | truncar, cuantificar el error e interpretar energía |

## 1. Preguntas conceptuales

### Ejercicio 1. Verdadero o falso (Examen Final 2026-I y Lista EF 2026-I, adaptados)

Decide si cada afirmación es verdadera o falsa. Justifica con una prueba
breve o un contraejemplo.

1. Si todos los valores singulares de una matriz cuadrada $A$ son uno,
   entonces $A=A^T$.
2. Dos matrices con los mismos valores propios son iguales.
3. Una matriz real simétrica tiene una base ortonormal de vectores propios.
4. Si $A$ es semidefinida positiva, entonces $A$ es invertible.
5. $A$ y $A^T$ tienen los mismos valores singulares no nulos.
6. Los valores singulares de $-3A$ son $-3\sigma_i$.
7. Si $A$ es invertible y $A=U\Sigma V^T$, entonces
   $A^{-1}=V\Sigma^{-1}U^T$.
8. Si $A$ es cuadrada, $\det(A)=\prod_i\sigma_i$.
9. $AA^+$ y $A^+A$ son siempre matrices simétricas.
10. Si $A$ es invertible, entonces $A^+=A^{-1}$.
11. Para todo $b$, el vector $A^+b$ satisface $Ax=b$.
12. $A^+b$ es la solución de norma mínima del problema de mínimos cuadrados.
13. La mejor aproximación de rango uno se obtiene conservando el término
    asociado al menor valor singular.
14. $\|A-A_k\|_F^2=\sum_{i>k}\sigma_i^2$.
15. Si $\sigma_k=\sigma_{k+1}$, la mejor aproximación de rango $k$ es
    necesariamente única.
16. Los vectores singulares derechos asociados a valores singulares nulos
    pertenecen a $\ker(A)$.

## 2. Resultados y demostraciones

### Ejercicio 2. Transformaciones de la SVD (Lista EF 2026-I)

Sea $A\in\mathbb R^{m\times n}$ con valores singulares no nulos
$\sigma_1\geq\cdots\geq\sigma_r>0$.

1. Determina los valores singulares no nulos de $A^T$.
2. Determina los de $tA$, para $t\in\mathbb R$.
3. Si $A$ es cuadrada e invertible, determina los de $A^{-1}$ y cuida su
   orden.
4. Si $A$ es cuadrada, demuestra que
   $|\det A|=\prod_i\sigma_i$ y explica por qué aparece el valor absoluto.

### Ejercicio 3. Productos espectrales (Examen Final 2025-I y Lista EF 2026-I)

Sea $A\in\mathbb R^{n\times n}$ y sea $A=U\Sigma V^T$ una SVD completa.

1. Calcula las diagonalizaciones espectrales de $A^TA$ y $AA^T$.
2. Demuestra que $A^TA$ y $AA^T$ son ortogonalmente similares.
3. Explica qué cambia si $A$ es rectangular.
4. Prueba que $\ker(A^TA)=\ker(A)$.

### Ejercicio 4. Identidad para la pseudoinversa (Lista EF 2026-I)

Usa una SVD reducida para demostrar que

$$
\boxed{(A^+)^T=(A^T)^+.}
$$

Indica claramente la SVD que utilizas para $A^T$ y verifica las dimensiones
de cada factor.

### Ejercicio 5. Proyecciones fundamentales (elaboración para esta guía)

Demuestra mediante la SVD que

$$
AA^+=P_{\operatorname{Im}(A)},
\qquad
A^+A=P_{\operatorname{Im}(A^T)}.
$$

Deduce de estas identidades:

1. un criterio para que $Ax=b$ sea compatible;
2. que $b-AA^+b\in\ker(A^T)$;
3. que todas las soluciones de mínimos cuadrados producen el mismo vector
   ajustado.

### Ejercicio 6. Error óptimo (Examen Final 2025-II, adaptado)

Enuncia el teorema de Eckart--Young--Mirsky y explica la diferencia entre sus
conclusiones en norma espectral y en norma de Frobenius. Da una idea de por
qué ninguna matriz de rango a lo más $k$ puede mejorar el error
$\sigma_{k+1}$ en norma espectral.

## 3. Cálculo de SVD y pseudoinversa

### Ejercicio 7. SVD rectangular completa (Lista EF 2026-I)

Para

$$
A=\begin{pmatrix}
1&-1\\
0&1\\
1&0
\end{pmatrix},
$$

1. calcula $A^TA$ y sus pares propios;
2. construye una SVD reducida;
3. completa $U$ para obtener una SVD completa;
4. reconstruye $A$ y comprueba las dimensiones;
5. identifica bases ortonormales de $\operatorname{Im}(A)$,
   $\operatorname{Im}(A^T)$, $\ker(A)$ y $\ker(A^T)$.

### Ejercicio 8. SVD de una matriz de rango uno (Examen Final 2026-I)

Sean $a,b\in\mathbb R$, con $ab\neq0$, y

$$
A=\begin{pmatrix}a&b\\-a&-b\end{pmatrix}.
$$

1. Determina sus valores singulares.
2. Calcula una SVD completa $A=U\Sigma V^T$.
3. Obtén $A^+$ a partir de la SVD.
4. Para $y=(c,d)^T$, determina la solución de norma mínima de
   $\min_x\|Ax-y\|_2$.
5. Indica para qué valores de $c,d$ el sistema $Ax=y$ es compatible.

### Ejercicio 9. Moore--Penrose en dos orientaciones (Lista EF 2026-I)

Calcula la pseudoinversa de cada matriz y verifica las cuatro ecuaciones de
Moore--Penrose:

$$
A=\begin{pmatrix}1&2\\-1&-2\end{pmatrix},
\qquad
B=\begin{pmatrix}1&-1\\0&0\\1&-1\end{pmatrix}.
$$

Después interpreta geométricamente $AA^+$, $A^+A$, $BB^+$ y $B^+B$.

### Ejercicio 10. Involución simétrica (Lista EF 2026-I)

Sea $A\in\mathbb R^{n\times n}$ tal que $A^{-1}=A=A^T$.

1. Demuestra que todos sus valores singulares son uno.
2. Dada cualquier matriz ortogonal $U$, encuentra una matriz ortogonal $V$
   tal que $A=UIV^T$ sea una SVD.
3. Realiza la construcción para

   $$
   A=\begin{pmatrix}0&1\\1&0\end{pmatrix},
   \qquad
   U=\frac15\begin{pmatrix}3&-4\\4&3\end{pmatrix}.
   $$

Explica por qué una SVD no tiene que coincidir con una diagonalización
espectral, incluso para una matriz simétrica.

## 4. Conexiones acumulativas

### Ejercicio 11. Espectro, forma cuadrática y SVD (elaboración para esta guía)

Sea

$$
C=\begin{pmatrix}2&-1&0\\-1&2&0\\0&0&-3\end{pmatrix}.
$$

1. Diagonaliza ortogonalmente $C$.
2. Clasifica $q(x)=x^TCx$.
3. Halla los valores singulares de $C$.
4. Construye una SVD usando la información espectral.
5. Compara los signos de los valores propios con la información que
   conservan los valores singulares.

### Ejercicio 12. Ecuaciones normales y pseudoinversa (elaboración para esta guía)

Considera

$$
A=\begin{pmatrix}1&0\\1&1\\1&2\end{pmatrix},
\qquad
b=\begin{pmatrix}1\\2\\2\end{pmatrix}.
$$

1. Resuelve las ecuaciones normales.
2. Calcula $A^+$ y verifica que produce la misma solución.
3. Halla el vector ajustado y el residuo.
4. Comprueba la ortogonalidad del residuo con $\operatorname{Im}(A)$.
5. Explica por qué en este caso la solución es única.

### Ejercicio 13. Sistema compatible con infinitas soluciones (elaboración para esta guía)

Sea

$$
D=\begin{pmatrix}1&1&0\\0&1&1\end{pmatrix},
\qquad
b=\begin{pmatrix}2\\1\end{pmatrix}.
$$

1. Describe todas las soluciones de $Dx=b$.
2. Calcula $D^+b$.
3. Verifica que $D^+b$ es ortogonal a $\ker(D)$.
4. Demuestra directamente que es la solución de menor norma.

## 5. Aproximación de rango bajo

### Ejercicio 14. Truncamiento a partir de una SVD (Examen Final 2025-II, adaptado)

Una matriz $X\in\mathbb R^{6\times4}$ tiene SVD reducida

$$
X=10u_1v_1^T+4u_2v_2^T+2u_3v_3^T+u_4v_4^T.
$$

1. Calcula $\|X\|_2$ y $\|X\|_F$.
2. Escribe $X_2$, la mejor aproximación de rango dos.
3. Calcula $\|X-X_2\|_2$ y $\|X-X_2\|_F$.
4. Determina el porcentaje de energía capturada por $X_2$.
5. ¿Cuál es el menor rango que captura al menos el $95\%$ de la energía?
6. Explica qué subespacio aproxima mejor las filas de $X$ con dimensión dos.

### Ejercicio 15. Cálculo de una aproximación (elaboración para esta guía)

Sea

$$
M=\begin{pmatrix}3&0\\0&2\\0&0\end{pmatrix}.
$$

1. Escribe una SVD de $M$.
2. Calcula explícitamente la mejor aproximación de rango uno.
3. Verifica directamente los errores espectral y de Frobenius.
4. Propón otra matriz de rango uno y comprueba que no mejora ambos errores.

### Ejercicio 16. Compresión y almacenamiento (elaboración para esta guía)

Una imagen en escala de grises se representa mediante una matriz
$A\in\mathbb R^{m\times n}$. Se almacena su SVD truncada mediante $U_k$,
$\Sigma_k$ y $V_k$.

1. Compara los $mn$ números originales con los necesarios para los tres
   factores truncados.
2. Deduce una desigualdad para que el formato truncado use menos números.
3. Explica por qué aumentar $k$ reduce el error pero también reduce la tasa
   de compresión.
4. Si se conocen solo los valores singulares, explica qué errores y qué
   porcentajes sí pueden calcularse sin reconstruir la imagen.

## 6. Simulacro de examen final

```{admonition} Condiciones sugeridas
:class: important
Tiempo: 100 minutos. Puntaje: 20 puntos. Trabaja sin software y justifica
cada respuesta. Revisa los resultados solo después de terminar.
```

### Pregunta 1. Conceptos con justificación — 4 puntos

Indica si cada afirmación es verdadera o falsa:

1. Si $A^TA=I$, entonces todos los valores singulares de $A$ son uno.
2. Si $A$ es simétrica, sus valores singulares son sus valores propios.
3. $AA^+b$ es el vector de $\operatorname{Im}(A)$ más cercano a $b$.
4. Si $\operatorname{rango}(A)=k$, entonces $A_k=A$.

### Pregunta 2. Teoría espectral y forma cuadrática — 5 puntos

Sea

$$
H=\begin{pmatrix}4&2\\2&1\end{pmatrix}.
$$

1. Diagonaliza ortogonalmente $H$.
2. Clasifica $q(x)=x^THx$.
3. Determina el máximo y el mínimo de $q(x)$ sobre $\|x\|=1$.
4. Halla una SVD de $H$ y explica su relación con la diagonalización.

### Pregunta 3. Pseudoinversa y mínimos cuadrados — 6 puntos

Sea

$$
A=\begin{pmatrix}1&1\\-1&-1\\1&1\end{pmatrix},
\qquad
b=\begin{pmatrix}2\\0\\1\end{pmatrix}.
$$

1. Construye una SVD reducida de $A$.
2. Calcula $A^+$.
3. Halla la solución de norma mínima de $\min_x\|Ax-b\|_2$.
4. Calcula el vector ajustado y el residuo.
5. Decide si $Ax=b$ es compatible y justifica geométricamente.

### Pregunta 4. Rango bajo — 5 puntos

Una matriz $X$ tiene valores singulares $8,4,2,1$.

1. Calcula $\|X\|_2$ y $\|X\|_F$.
2. Escribe la mejor aproximación de rango dos en términos de sus vectores
   singulares.
3. Calcula los errores espectral y de Frobenius.
4. Calcula el porcentaje de energía capturada.
5. Determina el rango mínimo que captura al menos el $95\%$ de la energía.

## 7. Pistas y resultados breves

Abre esta sección únicamente después de intentar los ejercicios.

```{dropdown} Ejercicio 1
1 F, 2 F, 3 V, 4 F, 5 V, 6 F, 7 V, 8 F, 9 V, 10 V, 11 F,
12 V, 13 F, 14 V, 15 F, 16 V.
```

```{dropdown} Ejercicio 8
Sea $r=\sqrt{a^2+b^2}$. El único valor singular no nulo es
$\sqrt2r$. La imagen está generada por $(1,-1)^T$ y la imagen de $A^T$ por
$(a,b)^T$. La compatibilidad exige $c+d=0$.
```

```{dropdown} Ejercicio 12
La solución es $(7/6,1/2)^T$ y el residuo es
$(-1/6,1/3,-1/6)^T$.
```

```{dropdown} Ejercicio 13
Las soluciones son $(1+t,1-t,t)^T$. La de norma mínima corresponde a
$t=0$, por lo que $D^+b=(1,1,0)^T$.
```

```{dropdown} Ejercicio 14
$\|X\|_2=10$, $\|X\|_F=11$, $\|X-X_2\|_2=2$ y
$\|X-X_2\|_F=\sqrt5$. La energía capturada por rango dos es
$116/121$. El rango mínimo para superar $95\%$ es dos.
```

```{dropdown} Simulacro
En la pregunta 1: V, F, V, V. En la pregunta 2, los valores propios de $H$
son $5$ y $0$. En la pregunta 4, la energía total es $85$, la capturada es
$80$ y el rango mínimo para al menos $95\%$ es tres.
```
