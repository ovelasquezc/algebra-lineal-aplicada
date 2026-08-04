# Preparación para la PC1

```{admonition} Tres recursos complementarios
:class: note
Comienza por el [repaso teórico](09_repaso_teorico_pc1.md). Después resuelve
esta guía y el simulacro por escrito. Utiliza el
[laboratorio computacional](09_laboratorio_preparacion_pc1.ipynb) solamente
para comprobar resultados.
```

## Propósito

Este material de práctica escrita sirve para integrar la Unidad 1 antes de la
primera práctica calificada. Los ejercicios son nuevos o han sido
reformulados; no anticipan las preguntas de la evaluación.

La preparación tiene tres niveles:

1. **Reconocer:** identificar definiciones, hipótesis y conclusiones.
2. **Calcular:** ejecutar un procedimiento y comprobar el resultado.
3. **Justificar:** explicar por qué el procedimiento es válido y qué significa
   la respuesta.

## 1. Cobertura

| Bloque | Debes poder hacer |
|---|---|
| Geometría de $\mathbb R^n$ | Calcular producto interno, norma y ángulo; usar Cauchy–Schwarz y desigualdad triangular |
| Sistemas lineales | Reducir por Gauss–Jordan; identificar pivotes; clasificar y parametrizar soluciones |
| Generación e independencia | Traducir combinaciones a sistemas; decidir generación e independencia mediante rango |
| Subespacios, bases y dimensión | Aplicar el criterio de subespacio; extraer bases; usar rango–nulidad |
| Núcleo e imagen | Respetar los espacios ambiente; calcular bases e interpretar compatibilidad |
| Determinante e invertibilidad | Calcular determinantes; controlar operaciones elementales; usar las equivalencias de invertibilidad |
| Espacios reales y conjuntos afines | Reconocer ejemplos fuera de $\mathbb R^n$; escribir $x_p+W$ |
| Suma directa | Calcular suma e intersección; justificar unicidad; usar la fórmula de dimensión |
| Coordenadas y cambio de base | Distinguir $x$ de $[x]_{\mathcal B}$; construir matrices de transición y matrices relativas |

Los números complejos no forman parte de esta evaluación.

## 2. Antes de comenzar un problema

### 2.1. Registra tamaños y espacios

Si $A\in\mathbb R^{m\times n}$, entonces

$$
A:\mathbb R^n\longrightarrow\mathbb R^m,
\qquad
\ker(A)\subseteq\mathbb R^n,
\qquad
\operatorname{Im}(A)\subseteq\mathbb R^m.
$$

Además,

$$
\operatorname{rango}(A)+\operatorname{nulidad}(A)=n.
$$

### 2.2. Decide qué matriz reducir

- Para resolver $Ax=b$, reduzca $[A\mid b]$.
- Para una base de $\operatorname{Im}(A)$, encuentre pivotes en la RREF pero
  seleccione las columnas correspondientes de la **matriz original**.
- Para $\ker(A)$, resuelva $Ax=0$.
- Para una intersección $U\cap W$, resuelva $B_Ua=B_Wb$.
- Para coordenadas, resuelva $M_{\mathcal B}c=x$.

### 2.3. Comprueba

Una respuesta no termina al obtener números:

- sustituya una solución en el sistema;
- compruebe que una base propuesta genera y es independiente;
- verifique que las dimensiones satisfacen las fórmulas correspondientes;
- confirme la dirección de una matriz de cambio de base;
- use $AA^{-1}=I$ si calculó una inversa.

## 3. Preguntas conceptuales

Indique si cada afirmación es verdadera o falsa. Justifique con un argumento o
un contraejemplo; escribir solamente V o F no es suficiente.

1. Todo sistema homogéneo tiene al menos una solución.
2. Las operaciones elementales por filas preservan el espacio columna de una
   matriz.
3. Si $A\in\mathbb R^{m\times n}$ y $\ker(A)=\{0\}$, entonces $Ax=b$ tiene
   solución única para todo $b\in\mathbb R^m$.
4. Si $A$ es cuadrada y $\det(A)\neq0$, sus columnas forman una base del
   espacio ambiente.
5. Todo conjunto afín contiene al vector cero.
6. Si $U\cap W=\{0\}$, entonces $U+W$ es una suma directa.
7. Si $U+W=V$, entonces necesariamente $V=U\oplus W$.
8. La columna $j$ de $P_{\mathcal B\to\mathcal C}$ contiene las coordenadas en
   $\mathcal C$ del vector $j$-ésimo de $\mathcal B$.
9. Dos matrices de igual rango tienen el mismo espacio columna.
10. La igualdad en Cauchy–Schwarz ocurre exactamente cuando los dos vectores
    son linealmente dependientes.
11. Si $(a+b)\perp(a-b)$, entonces $a\perp b$.
12. Una base de $\mathcal P_3$ debe tener cuatro polinomios.

```{admonition} Error frecuente con sumas y diferencias
:class: warning
De
$(a+b)\cdot(a-b)=0$ se obtiene $\|a\|^2-\|b\|^2=0$. La conclusión es
$\|a\|=\|b\|$, no $a\perp b$.
```

## 4. Ejercicios graduados

### A. Geometría y norma

#### Ejercicio 1

Sean $u=(1,-2,2)$ y $v=(2,1,0)$.

1. Calcule $u\cdot v$, $\|u\|$ y $\|v\|$.
2. Determine el ángulo entre ellos.
3. Obtenga un vector unitario en la dirección de $u$.
4. Verifique Cauchy–Schwarz y la desigualdad triangular para este par.

#### Ejercicio 2

Sean $a=(1,-1)$ y $b=(3,3)$. Describa el conjunto

$$
H=\{x\in\mathbb R^2:\|x-a\|=\|x-b\|\}.
$$

Obtenga una ecuación cartesiana, identifique un punto de $H$ y explique su
geometría.

#### Ejercicio 3

Demuestre la desigualdad triangular a partir de Cauchy–Schwarz. Separe con
claridad el **enunciado**, la **prueba** y el caso de igualdad.

### B. Sistemas y operaciones elementales

#### Ejercicio 4. Sistema con parámetro

Clasifique, según $\lambda\in\mathbb R$, el sistema

$$
\begin{cases}
x+y+z=2,\\
(\lambda-1)y+z=\tfrac12,\\
(\lambda+1)z=1.
\end{cases}
$$

Indique cuándo hay solución única, infinitas soluciones o ninguna solución.

#### Ejercicio 5. Problema integrado de rango

Sea

$$
A=\begin{bmatrix}
1&2&0&1&-1&3\\
2&4&1&3&0&7\\
1&2&1&2&1&4\\
3&6&1&4&-1&10
\end{bmatrix}.
$$

1. Calcule la RREF, el rango y la nulidad.
2. Halle bases de $\operatorname{Im}(A)$ y $\ker(A)$.
3. Decida si $Ax=b$ es compatible para
   $b=(1,3,2,4)^T$ y describa todas las soluciones.
4. Repita solamente la prueba de compatibilidad para
   $b'=(1,3,2,5)^T$.

#### Ejercicio 6. Inversa por Gauss–Jordan

Calcule, si existe, la inversa de

$$
G=\begin{bmatrix}1&2&0\\0&1&1\\2&3&1\end{bmatrix}
$$

reduciendo $[G\mid I_3]$. Compruebe el resultado por multiplicación.

### C. Generación, bases y espacios fundamentales

#### Ejercicio 7

Considere en $\mathbb R^4$ las columnas

$$
v_1=(1,2,0,1),\quad v_2=(0,1,1,1),\quad
v_3=(1,3,1,2),\quad v_4=(2,1,-1,1).
$$

1. Determine todas las relaciones de dependencia.
2. Extraiga una base del subespacio generado.
3. Exprese cada columna no pivote mediante la base elegida.

#### Ejercicio 8

En $\mathcal P_3$, estudie

$$
W=\{p:p(1)=0\}.
$$

Pruebe que es subespacio, halle una base y determine su dimensión.

#### Ejercicio 9

Sea $T:\mathcal P_3\to\mathcal P_2$ dada por $T(p)=p'$. Determine núcleo,
imagen, rango y nulidad. Verifique rango–nulidad.

### D. Determinante e invertibilidad

#### Ejercicio 10

Calcule el determinante de

$$
E=\begin{bmatrix}2&-1&0\\1&3&2\\0&4&1\end{bmatrix}
$$

de dos maneras: expansión de Laplace y eliminación. Indique el efecto de cada
operación elemental utilizada.

#### Ejercicio 11

Para

$$
D_\lambda=
\begin{bmatrix}
\lambda&1&0\\1&\lambda&0\\0&0&\lambda+2
\end{bmatrix},
$$

determine los valores de $\lambda$ para los cuales la matriz es singular.
Relacione la respuesta con rango, núcleo y unicidad de $D_\lambda x=b$.

### E. Espacios afines y suma directa

#### Ejercicio 12

Escriba el plano

$$
H=\{(x,y,z):x+2y-z=3\}
$$

como $x_0+W$. Dé un punto $x_0$, una base de $W$ y justifique por qué $H$ es
afín pero no es subespacio.

#### Ejercicio 13

En $\mathbb R^4$, sean

$$
\begin{aligned}
U&=\operatorname{span}\{(1,0,1,0),(0,1,0,1)\},\\
W&=\operatorname{span}\{(1,0,-1,0),(0,1,0,-1)\}.
\end{aligned}
$$

1. Pruebe que $\mathbb R^4=U\oplus W$.
2. Descomponga $(3,1,-1,5)$ como $u+w$.
3. Explique por qué la descomposición es única.

#### Ejercicio 14

Sean $U,W\leq V$, con $\dim U=4$, $\dim W=3$ y
$\dim(U+W)=6$. Calcule $\dim(U\cap W)$ y decida si la suma es directa.

### F. Coordenadas y cambio de base

#### Ejercicio 15

Sean

$$
\mathcal B=((1,1),(1,-1)),\qquad
\mathcal C=((2,0),(1,1)).
$$

1. Calcule $P_{\mathcal B\to\mathcal C}$ y su inversa.
2. Para $x=(5,1)$, calcule $[x]_{\mathcal B}$ y $[x]_{\mathcal C}$ por dos
   caminos.
3. Interprete las columnas de $P_{\mathcal B\to\mathcal C}$.

#### Ejercicio 16

Sea $T:\mathbb R^2\to\mathbb R^2$ cuya matriz canónica es

$$
A=\begin{bmatrix}2&1\\1&0\end{bmatrix}.
$$

Calcule $[T]_{\mathcal C\leftarrow\mathcal B}$ para las bases del ejercicio
anterior. Verifique la fórmula con un vector genérico de coordenadas
$(r,s)^T$ en $\mathcal B$.

#### Ejercicio 17

Pruebe que

$$
P_{\mathcal B\to\mathcal D}
=P_{\mathcal C\to\mathcal D}P_{\mathcal B\to\mathcal C}.
$$

No basta multiplicar un ejemplo: argumente qué ocurre al aplicar ambos lados a
$[x]_{\mathcal B}$.

## 5. Banco de demostraciones

Practique escribir pruebas breves y completas de los siguientes resultados:

1. El criterio de subespacio mediante $\alpha u+\beta v$.
2. Un conjunto ortogonal de vectores no nulos es linealmente independiente.
3. La representación respecto de una base es única.
4. Si $Ax=b$ es compatible, su conjunto solución es $x_p+\ker(A)$.
5. $U+W$ es directa si y solo si $U\cap W=\{0\}$.
6. Si $A$ es cuadrada, $\det(A)\neq0$ si y solo si $A$ es invertible.

En cada prueba identifique explícitamente las hipótesis que utiliza.

## 6. Simulacro integrador

Tiempo sugerido: **120 minutos**. Resuelva primero sin software. Use el
cuaderno de preparación solamente al terminar, para comprobar cálculos.

### Problema 1. Conceptos y geometría — 4 puntos

1. Justifique: si $A\in\mathbb R^{4\times6}$ tiene rango $4$, entonces
   $Ax=b$ es compatible para todo $b\in\mathbb R^4$, pero nunca tiene solución
   única.
2. Si $(a+b)\perp(a-b)$, determine la relación correcta entre $\|a\|$ y
   $\|b\|$.
3. Explique por qué una recta afín que no pasa por el origen no es subespacio.

### Problema 2. Sistema y espacios fundamentales — 6 puntos

Sea

$$
M=\begin{bmatrix}
1&2&-1&0&3\\
2&4&-2&0&6\\
0&1&1&2&0
\end{bmatrix},
\qquad
b=\begin{bmatrix}1\\2\\3\end{bmatrix}.
$$

1. Calcule RREF, rango y nulidad.
2. Halle bases de imagen y núcleo.
3. Resuelva $Mx=b$ y escriba el conjunto solución como $x_p+\ker(M)$.

### Problema 3. Suma directa — 4 puntos

Para los subespacios $U,W$ del Ejercicio 13:

1. verifique la intersección trivial mediante una ecuación matricial;
2. use dimensiones para concluir que $\mathbb R^4=U\oplus W$;
3. descomponga $x=(3,1,-1,5)$.

### Problema 4. Determinante — 3 puntos

Calcule $\det(E)$ para la matriz del Ejercicio 10 mediante eliminación y decida
si $Ex=c$ tiene solución única para todo $c\in\mathbb R^3$.

### Problema 5. Cambio de base — 3 puntos

Sean

$$
\mathcal B=((1,0),(1,1)),\qquad
\mathcal C=((1,1),(1,-1)),\qquad x=(4,2).
$$

Calcule $P_{\mathcal B\to\mathcal C}$, $[x]_{\mathcal B}$ y
$[x]_{\mathcal C}$. Verifique el cambio de coordenadas.

## 7. Respuestas de control

Las respuestas siguientes permiten detectar errores de cálculo. No sustituyen
la justificación ni muestran el desarrollo completo.

```{admonition} Clave conceptual
:class: dropdown
1 V; 2 F; 3 F; 4 V; 5 F; 6 V; 7 F; 8 V; 9 F; 10 V; 11 F;
12 V.
```

```{admonition} Resultados de los ejercicios graduados
:class: dropdown
- E1: $u\cdot v=0$, $\|u\|=3$, $\|v\|=\sqrt5$, ángulo $\pi/2$.
- E2: $H=\{(x,y):x+2y=4\}$; contiene al punto medio $(2,1)$.
- E4: única si $\lambda\neq\pm1$; infinitas si $\lambda=1$; ninguna si
  $\lambda=-1$.
- E5: rango $2$, nulidad $4$, columnas pivote 1 y 3; el primer sistema es
  compatible y el segundo es incompatible.
- E6: $\det(G)=2$ y
  $G^{-1}=\begin{bmatrix}-1&-1&1\\1&1/2&-1/2\\-1&1/2&1/2\end{bmatrix}$.
- E7: rango $3$, columnas pivote 1, 2 y 4; $v_3=v_1+v_2$.
- E8: $W=(t-1)\mathcal P_2$ y $\dim W=3$.
- E9: $\ker(T)=\operatorname{span}\{1\}$, $\operatorname{Im}(T)=\mathcal P_2$.
- E10: $\det(E)=-9$.
- E11: singular para $\lambda\in\{-2,-1,1\}$.
- E12: puede usarse $x_0=(3,0,0)$ y
  $W=\operatorname{span}\{(-2,1,0),(1,0,1)\}$.
- E13: $(3,1,-1,5)=(1,3,1,3)+(2,-2,-2,2)$.
- E14: $\dim(U\cap W)=1$; no es directa.
- E15:
  $P_{\mathcal B\to\mathcal C}=\begin{bmatrix}0&1\\1&-1\end{bmatrix}$,
  $[x]_{\mathcal B}=(3,2)^T$, $[x]_{\mathcal C}=(2,1)^T$.
- E16:
  $[T]_{\mathcal C\leftarrow\mathcal B}=\begin{bmatrix}1&0\\1&1\end{bmatrix}$.
```

```{admonition} Resultados numéricos del simulacro
:class: dropdown
- P2: rango $2$, nulidad $3$, columnas pivote 1 y 2; una base del núcleo es
  $(3,-1,1,0,0)^T$, $(4,-2,0,1,0)^T$, $(-3,0,0,0,1)^T$.
- P3: los coeficientes de la descomposición, en las bases dadas, son
  $(1,3,2,-2)^T$.
- P4: $\det(E)=-9$, luego existe solución única para todo $c$.
- P5:
  $P_{\mathcal B\to\mathcal C}=\begin{bmatrix}1/2&1\\1/2&0\end{bmatrix}$,
  $[x]_{\mathcal B}=(2,2)^T$ y $[x]_{\mathcal C}=(3,1)^T$.
```
