# Preparación para el Examen Parcial

```{admonition} Orden de trabajo
:class: note
Estudia primero el [repaso teórico](05_repaso_teorico_ep.md). Resuelve esta
guía por escrito y sin software. Al terminar, utiliza el
[laboratorio](05_laboratorio_preparacion_ep.ipynb) para comprobar cálculos.
```

## Propósito

Esta guía integra los fundamentos de la Unidad 1 con las aplicaciones de
ortogonalidad de la Unidad 2. Los problemas son nuevos o han sido
reformulados; no anticipan las preguntas del examen.

La procedencia aparece en cada encabezado. **Adaptado** indica que se conserva
la habilidad evaluada, pero se modificaron datos, contexto o preguntas. Los
ejercicios marcados como **elaboración para esta guía** no proceden de una
evaluación anterior.

La preparación tiene cuatro niveles:

1. **Enunciar:** reconocer hipótesis y conclusiones.
2. **Modelar:** traducir el problema a vectores, matrices o funciones base.
3. **Calcular:** ejecutar el procedimiento con orden.
4. **Justificar:** explicar por qué el resultado es válido y qué significa.

## 1. Cobertura y prioridad

| Prioridad | Bloque | Debes poder hacer |
|---|---|---|
| Prerrequisito | Sistemas, bases, rango y cambio de base | reducir, parametrizar, extraer bases y manejar coordenadas |
| Central | Producto interno y Gram-Schmidt | comprobar productos internos, ortogonalizar y normalizar |
| Central | Proyecciones e hiperplanos | caracterizar la mejor aproximación y construir matrices de proyección |
| Central | Mínimos cuadrados | formular matrices de diseño, derivar ecuaciones normales e interpretar residuos |
| Central | Fourier y DCT | reconocer bases de frecuencia, usar Parseval e interpretar compresión |

Las transformaciones lineales y la teoría espectral pertenecen a la Unidad 3.

## 2. Lista de comprobación antes de resolver

1. Escribe los espacios ambiente y los tamaños de las matrices.
2. Identifica si la familia dada es una base, una base ortogonal o una base
   ortonormal.
3. Distingue el subespacio de su traslación afín.
4. En mínimos cuadrados, identifica las observaciones y las funciones base.
5. En Fourier o DCT, declara la normalización utilizada.
6. Comprueba ortogonalidad del residuo, dimensiones y reconstrucción.

## 3. Preguntas conceptuales

Indica si cada afirmación es verdadera o falsa. Justifica con una prueba breve
o un contraejemplo.

1. Toda familia ortogonal es linealmente independiente.
2. Si $U$ tiene columnas ortonormales, entonces $UU^T=I$.
3. Si $P=P^T=P^2$, entonces $P$ es la matriz de una proyección ortogonal.
4. Si $p=P_W(x)$, entonces $x-p$ es ortogonal únicamente a $p$.
5. La proyección sobre un subespacio es una transformación que preserva todas
   las normas.
6. Si $H=x_0+W$, entonces $P_H(x)=x_0+P_W(x)$.
7. Las ecuaciones normales siempre son compatibles.
8. Si $A^TA$ es singular, el problema de mínimos cuadrados no tiene solución.
9. Dos soluciones de mínimos cuadrados pueden tener coeficientes distintos y
   producir el mismo vector ajustado.
10. Si $A$ tiene columnas independientes, $A^TA$ es invertible.
11. Una suma parcial de Fourier es una proyección ortogonal.
12. Descartar coeficientes de una base ortonormal permite calcular el error a
    partir de la energía descartada.
13. En una imagen, los coeficientes DCT de mayor magnitud siempre están en el
    bloque superior izquierdo.
14. Si $z\in\mathbb C$, entonces $z^2=|z|^2$.
15. Cambiar la normalización de la DFT no afecta las fórmulas de reconstrucción
    ni de Parseval.

## 4. Ejercicios graduados

### A. Bases, coordenadas y ortogonalidad

#### Ejercicio 1. Producto interno no usual (elaboración para esta guía)

En $\mathbb R^2$ se define

$$
\langle x,y\rangle_M=x^TMy,
\qquad
M=\begin{bmatrix}2&1\\1&2\end{bmatrix}.
$$

1. Verifica que $M$ es simétrica y definida positiva.
2. Calcula $\langle(1,0),(0,1)\rangle_M$ y las normas de ambos vectores.
3. Determina el ángulo inducido por este producto interno.
4. Encuentra todos los vectores $(a,b)$ ortogonales a $(1,0)$.

#### Ejercicio 2. Gram-Schmidt exacto (Repaso EP 2026-I, adaptado)

Ortonormaliza, en el orden indicado,

$$
v_1=(1,1,0),qquad
v_2=(1,0,1),qquad
v_3=(0,1,1).
$$

En cada paso:

1. escribe las proyecciones que restas;
2. comprueba la ortogonalidad antes de normalizar;
3. verifica que los espacios generados parcialmente no cambian.

#### Ejercicio 3. Polinomios (Parcial 2025-II, adaptado)

En $\mathcal P_2$ usa

$$
\langle p,q\rangle=\int_{-1}^{1}p(t)q(t)\,dt.
$$

1. Aplica Gram-Schmidt a $(1,t,t^2)$.
2. Normaliza la familia.
3. Calcula las coordenadas de $f(t)=1+2t+3t^2$ en la base ortonormal.
4. Comprueba Parseval.

### B. Proyecciones, complementos e hiperplanos

#### Ejercicio 4. Proyección sobre un núcleo (Parcial 2025-I, adaptado)

Sea

$$
A=\begin{bmatrix}
1&1&0&1\\
0&1&1&1
\end{bmatrix},
\qquad
x=\begin{bmatrix}2\\-1\\3\\1\end{bmatrix}.
$$

1. Halla una base de $W=\ker(A)$.
2. Ortonormaliza la base.
3. Calcula $P_W(x)$ y la matriz $P_W$.
4. Verifica $P_W^T=P_W$, $P_W^2=P_W$ y $A P_W=0$.
5. Descompón $x$ como $p+q$, con $p\in W$ y $q\in W^\perp$.

#### Ejercicio 5. Base no ortonormal (Repaso EP 2026-I, adaptado)

Sea

$$
B=\begin{bmatrix}1&1\\1&0\\0&1\end{bmatrix},
\qquad W=\operatorname{Col}(B).
$$

1. Calcula $P_W$ usando $B(B^TB)^{-1}B^T$.
2. Calcula otra vez la proyección después de ortonormalizar las columnas.
3. Explica por qué ambas matrices coinciden.
4. Proyecta $x=(2,-1,3)^T$ y comprueba la ortogonalidad del residuo.

#### Ejercicio 6. Hiperplano afín (Lista histórica del EP, adaptado)

Para

$$
H=\{z\in\mathbb R^4: z_1-2z_2+2z_3-z_4=5\}
$$

y $x=(2,1,0,-1)^T$:

1. identifica un vector normal y el subespacio paralelo;
2. calcula $P_H(x)$;
3. calcula $d(x,H)$;
4. verifica que la proyección pertenece a $H$;
5. explica la diferencia entre $P_H(x)$ y la proyección sobre el hiperplano
   paralelo que pasa por el origen.

### C. Mínimos cuadrados y modelamiento

#### Ejercicio 7. Sistema incompatible (Parcial 2025-I, adaptado)

Considera

$$
A=\begin{bmatrix}
1&0\\
1&1\\
1&2\\
1&3
\end{bmatrix},
\qquad
b=\begin{bmatrix}1\\2\\2\\5\end{bmatrix}.
$$

1. Demuestra que $Ax=b$ es incompatible.
2. Deriva y resuelve las ecuaciones normales.
3. Calcula el vector ajustado y el residuo.
4. Verifica $A^Tr=0$.
5. Comprueba la identidad de optimalidad con $x=(0,1)^T$.

#### Ejercicio 8. Ajuste cuadrático completo (material de C12)

Para los datos

$$
(-2,5),\ (-1,2),\ (0,1),\ (1,2),\ (2,6),
$$

aproxima $y$ mediante $f(t)=a+bt+ct^2$.

1. Construye la matriz de diseño fila por fila.
2. Escribe y resuelve las ecuaciones normales.
3. Calcula los valores ajustados, residuos y SSE.
4. Justifica la unicidad de los coeficientes.

#### Ejercicio 9. Plano de ajuste (Parcial 2026-I, adaptado)

Los datos son

$$
(x_i,y_i,z_i)\in
\{(0,0,1),(1,0,3),(0,1,0),(1,1,2),(2,1,5)\}.
$$

Ajusta $z=a+bx+cy$.

1. Construye $X$ y $z$.
2. Deriva las ecuaciones normales desde la condición de ortogonalidad.
3. Resuelve para $(a,b,c)$.
4. Interpreta el significado de cada coeficiente.
5. Calcula el residuo y comprueba que es ortogonal a las tres columnas de
   $X$.

#### Ejercicio 10. Solo modelamiento (material de C12)

Se desea ajustar datos $(x_i,y_i,z_i)$ con

$$
z=a+bx+cy+dx^2+exy+fy^2.
$$

Sin hacer cálculos numéricos:

1. escribe una fila genérica de la matriz de diseño;
2. indica los tamaños de $X$, $\beta$ y $z$ para $m$ observaciones;
3. formula el problema de mínimos cuadrados y las ecuaciones normales;
4. enuncia una condición necesaria y suficiente para la unicidad de
   $\beta$;
5. describe geométricamente qué se proyecta y sobre qué subespacio.

#### Ejercicio 11. Rango deficiente (elaboración para esta guía)

Sea

$$
X=\begin{bmatrix}
1&0&0\\
1&1&2\\
1&2&4\\
1&3&6
\end{bmatrix}.
$$

1. Explica por qué los coeficientes no son únicos.
2. Determina el núcleo de $X$.
3. Si $\beta^*$ es una solución de mínimos cuadrados, describe todas las
   soluciones.
4. Prueba que todas producen el mismo vector ajustado.

### D. Fourier, energía y compresión

#### Ejercicio 12. Coeficientes complejos (material de C13)

Sea $f(t)=t$ en $[-\pi,\pi]$.

1. Calcula $c_0$.
2. Para $k\neq0$, calcula
   $c_k=(2\pi)^{-1}\int_{-\pi}^{\pi}te^{-ikt}\,dt$ por partes.
3. Escribe $S_2f$ en forma compleja.
4. Reúne los términos $k$ y $-k$ para obtener la forma real.
5. Explica por qué solo aparecen senos.

#### Ejercicio 13. DFT corta (elaboración para esta guía)

Para $x=(1,0,-1,0)$ usa

$$
\widehat x_k=\frac14\sum_{n=0}^3x_ne^{-2\pi ikn/4}.
$$

1. Calcula los cuatro coeficientes.
2. Reconstruye las cuatro muestras.
3. Comprueba Parseval con esta normalización.
4. Interpreta las frecuencias que contienen energía.

#### Ejercicio 14. Selección de coeficientes (elaboración para esta guía)

Un vector tiene coordenadas en una base ortonormal

$$
c=(4,-2,1,0,3).
$$

1. Aproxima conservando solo las coordenadas 1 y 5.
2. Calcula la norma cuadrada del dato, de la aproximación y del error.
3. Verifica la identidad de energía.
4. Si solo puedes conservar dos coeficientes, justifica por qué esa selección
   minimiza el error.

#### Ejercicio 15. DCT bidimensional (material de C13)

Sea $C$ una matriz DCT ortogonal y $B=CAC^T$.

1. Demuestra que $A=C^TBC$.
2. Demuestra que $\|A\|_F=\|B\|_F$.
3. Formula la reconstrucción después de conservar un conjunto $S$ de
   coeficientes.
4. Demuestra que el error cuadrático es la suma de cuadrados de los
   coeficientes descartados.
5. Explica por qué conservar un bloque de bajas frecuencias y conservar los
   coeficientes de mayor magnitud son criterios distintos.

## 5. Banco de pruebas breves

Practica escribir, sin consultar apuntes, pruebas de los siguientes
resultados:

1. una familia ortogonal de vectores no nulos es independiente;
2. Gram-Schmidt preserva el espacio generado;
3. la caracterización ortogonal de la proyección implica mínima distancia;
4. $P=UU^T$ es simétrica e idempotente cuando $U^TU=I$;
5. la fórmula de proyección sobre un hiperplano;
6. las ecuaciones normales a partir de la ortogonalidad del residuo;
7. la identidad de optimalidad de mínimos cuadrados;
8. la suma parcial de Fourier es la mejor aproximación en $\mathcal T_N$;
9. el error por descarte en una base ortonormal es la energía descartada.

## 6. Simulacro integrador

Tiempo sugerido: **120 minutos**. Puntaje total: **20 puntos**. Resuelve sin
software y usa el laboratorio únicamente al terminar.

### Problema 1. Conceptos y prueba (elaboración para este simulacro) — 3 puntos

1. Prueba que una familia ortogonal de vectores no nulos es linealmente
   independiente. (1 punto)
2. Decide y justifica: si las columnas de $A$ son dependientes, el problema
   $\min_x\|Ax-b\|$ puede carecer de solución. (1 punto)
3. Explica la diferencia entre proyección sobre un subespacio y sobre una
   traslación afín. (1 punto)

### Problema 2. Núcleo, Gram-Schmidt y proyección (Parcial 2025-I, adaptado) — 5 puntos

Sea

$$
A=\begin{bmatrix}1&1&0&1\\0&1&1&1\end{bmatrix},
\qquad x=(2,-1,3,1)^T.
$$

1. Halla una base de $\ker(A)$. (1 punto)
2. Obtén una base ortonormal mediante Gram-Schmidt. (2 puntos)
3. Calcula $P_{\ker(A)}(x)$ y comprueba que el residuo pertenece a
   $\operatorname{Im}(A^T)$. (2 puntos)

### Problema 3. Hiperplano (Lista histórica del EP, adaptado) — 3 puntos

Para

$$
H=\{z\in\mathbb R^3:2z_1-z_2+2z_3=4\},
\qquad x=(1,2,0)^T,
$$

calcula la proyección, la distancia y verifica las dos condiciones que
caracterizan la proyección. Justifica la fórmula utilizada.

### Problema 4. Ajuste de datos (Parcial 2025-I, adaptado) — 5 puntos

Con los datos

$$
(0,1),\ (1,2),\ (2,2),\ (3,5),
$$

ajusta $y=a+bt$.

1. Construye la matriz de diseño y deriva las ecuaciones normales. (2 puntos)
2. Calcula los coeficientes, el vector ajustado y el residuo. (2 puntos)
3. Verifica ortogonalidad y justifica la unicidad. (1 punto)

### Problema 5. Fourier y compresión (elaboración para este simulacro) — 4 puntos

1. Para $x=(1,0,-1,0)$ calcula su DFT con la normalización del Ejercicio 13 y
   comprueba Parseval. (2 puntos)
2. En una base ortonormal, un dato tiene coordenadas
   $(5,2,-1,0,2)$. Si solo pueden conservarse dos, selecciona las que
   minimizan el error y calcula el error cuadrático. Interpreta la respuesta
   en el contexto de compresión. (2 puntos)

## 7. Resultados para autocontrol

Consulta esta sección después de completar los ejercicios.

```{dropdown} Resultados breves

- Ejercicio 1: los autovalores de $M$ son $1$ y $3$;
  $\cos\theta=1/2$; los vectores ortogonales a $(1,0)$ satisfacen
  $2a+b=0$.
- Ejercicio 2: puede obtenerse
  $u_1=(1,1,0)/\sqrt2$,
  $u_2=(1,-1,2)/\sqrt6$ y
  $u_3=(-1,1,1)/\sqrt3$.
- Ejercicio 6: $a=(1,-2,2,-1)^T$, $a^Tx-b=-4$ y
  $d(x,H)=4/\sqrt{10}$.
- Ejercicio 7: la recta ajustada es
  $\widehat y=0.7+1.2t$.
- Ejercicio 9: el modelo exacto es $z=1+2x-y$; el residuo es cero.
- Ejercicio 11: $\ker(X)=\operatorname{span}\{(0,-2,1)^T\}$.
- Ejercicio 12: $c_0=0$ y $c_k=i(-1)^k/k$ para $k\neq0$.
- Ejercicio 13: $\widehat x=(0,1/2,0,1/2)$ y la energía media es $1/2$.
- Ejercicio 14: energía total $30$, energía conservada $25$ y error cuadrático
  $5$.
- Problema 4: $\widehat y=0.7+1.2t$ y
  $r=(0.3,0.1,-1.1,0.7)^T$.
- Problema 5.2: se conservan $5$ y cualquiera de los dos coeficientes de
  magnitud $2$; el error cuadrático es $5$.
```
