# Preparación para la PC2

```{admonition} Orden de trabajo
:class: note
Estudia primero el [repaso teórico](07_repaso_teorico_pc2.md). Resuelve esta
guía por escrito y sin software. Después usa el
[laboratorio](07_laboratorio_preparacion_pc2.ipynb) para comprobar resultados
y explorar casos cercanos.
```

## Propósito y procedencia

La guía combina teoría, demostración, cálculo e interpretación. La
procedencia se indica en cada encabezado. **Adaptado** significa que se
conserva la habilidad de una evaluación o lista histórica, pero se modifican
datos o preguntas. Los ejercicios de **elaboración para esta guía** completan
contenidos de la Unidad 3 que no estaban representados suficientemente en
esas evaluaciones.

La guía no anticipa las preguntas de la PC2. Su objetivo es que puedas:

1. **enunciar** definiciones y teoremas con sus hipótesis;
2. **modelar** transformaciones, recurrencias y formas cuadráticas;
3. **calcular** matrices, espacios propios y descomposiciones;
4. **justificar** diagonalización, ortogonalidad y clasificación por signo;
5. **interpretar** geométricamente los resultados.

## 1. Cobertura y prioridad

| Prioridad | Bloque | Debes poder hacer |
|---|---|---|
| Fundamental | Transformaciones lineales | probar linealidad, construir matrices, hallar núcleo e imagen |
| Fundamental | Operadores y adjuntos | reconocer invariancia, calcular adjuntos y usar relaciones ortogonales |
| Central | Valores propios | hallar polinomio característico, espacios propios y multiplicidades |
| Central | Diagonalización | decidir si existe, construirla y aplicarla a potencias o recurrencias |
| Central | Teorema espectral | diagonalizar ortogonalmente matrices simétricas y usar Rayleigh |
| Central | Formas cuadráticas | construir la matriz, reducir, clasificar y estudiar parámetros |

## 2. Preguntas conceptuales (PC2 2026-I y Lista PC2 2026-I, adaptadas)

Indica si cada afirmación es verdadera o falsa. Justifica mediante una prueba
breve o un contraejemplo.

1. Si $T(0)=0$, entonces $T$ es lineal.
2. Una transformación lineal queda determinada por sus valores en una base.
3. Si $\ker(T)=\{0\}$, entonces $T$ es sobreyectiva, sin importar las
   dimensiones del dominio y codominio.
4. La matriz de $S\circ T$ es el producto de las matrices en el mismo orden
   en que se nombran las transformaciones.
5. Todo espacio propio es un subespacio invariante.
6. Si $U$ es $T$-invariante, entonces $U^\perp$ también lo es.
7. En bases cualesquiera, la matriz del adjunto siempre es la transpuesta.
8. $\ker(T^*)=\operatorname{Im}(T)^\perp$.
9. Todo número real es valor propio de alguna matriz real.
10. Toda matriz real tiene al menos un valor propio real.
11. Si $0$ es valor propio de $A$, entonces $A$ no es invertible.
12. Vectores propios asociados a valores propios distintos son linealmente
    independientes.
13. Si el polinomio característico se descompone en factores lineales, la
    matriz es diagonalizable.
14. Si todos los valores propios son distintos, la matriz es diagonalizable.
15. Si $A=PDP^{-1}$, entonces necesariamente $P^{-1}=P^T$.
16. Toda matriz simétrica real es diagonalizable ortogonalmente.
17. Una matriz diagonalizable con valores propios reales es simétrica.
18. Matrices semejantes tienen el mismo polinomio característico.
19. Matrices congruentes tienen los mismos valores propios.
20. Una forma cuadrática definida positiva no tiene términos cruzados.
21. Una matriz semidefinida positiva puede ser singular.
22. El máximo de $x^TAx$ sobre $\|x\|=1$, para $A=A^T$, es el mayor valor
    propio de $A$.

## 3. Transformaciones, matrices y adjuntos

### Ejercicio 1. Linealidad y representación (elaboración para esta guía)

Sea $T:\mathcal P_2\to\mathbb R^2$ dada por

$$
T(p)=\bigl(p(1),p'(0)\bigr).
$$

1. Demuestra que $T$ es lineal.
2. Halla $[T]_{\mathcal C\leftarrow\mathcal B}$ para
   $\mathcal B=(1,t,t^2)$ y $\mathcal C=(e_1,e_2)$.
3. Calcula una base del núcleo y una base de la imagen.
4. Comprueba rango-nulidad.
5. Decide si $T$ es inyectiva o sobreyectiva.

### Ejercicio 2. Cambio de bases y composición (elaboración para esta guía)

Considera $T:\mathbb R^2\to\mathbb R^2$,

$$
T(x,y)=(2x-y,x+y),
$$

y las bases

$$
\mathcal B=((1,1),(1,-1)),
\qquad
\mathcal C=((1,0),(1,1)).
$$

1. Construye $[T]_{\mathcal C\leftarrow\mathcal B}$ a partir de las imágenes
   de los vectores de $\mathcal B$.
2. Verifica el resultado usando matrices de cambio de base.
3. Si $S(u,v)=(u+v,2v)$, calcula la matriz de $S\circ T$ en bases estándar.
4. Explica por qué invertir el orden del producto cambia la composición.

### Ejercicio 3. Invariancia y bloques (elaboración para esta guía)

Sea

$$
A=\begin{pmatrix}
1&2&0\\
0&1&0\\
3&-1&4
\end{pmatrix}.
$$

1. Decide si $U=\operatorname{span}\{e_1,e_3\}$ es $A$-invariante.
2. Decide si $W=\operatorname{span}\{e_1,e_2\}$ es $A$-invariante.
3. Para cada subespacio invariante, reordena una base y exhibe la estructura
   por bloques de la matriz.
4. Determina si el complemento ortogonal del subespacio también es
   invariante y justifica la respuesta.

### Ejercicio 4. Adjunto con producto interno ponderado (elaboración para esta guía)

En $\mathbb R^2$ usa

$$
\langle x,y\rangle_G=x^TGy,
\qquad
G=\begin{pmatrix}2&1\\1&3\end{pmatrix},
$$

y sea

$$
A=\begin{pmatrix}1&2\\0&-1\end{pmatrix}.
$$

1. Halla la matriz $A^*=G^{-1}A^TG$.
2. Verifica directamente la identidad
   $\langle Ax,y\rangle_G=\langle x,A^*y\rangle_G$ para vectores genéricos.
3. Decide si $A$ es autoadjunto respecto de este producto interno.
4. Calcula $\ker(A^*)$ y $\operatorname{Im}(A)^\perp$ y comprueba que
   coinciden.

## 4. Valores propios y diagonalización

### Ejercicio 5. Definición y rotaciones (PC2 2025-I, adaptado)

1. Enuncia qué significa que $\lambda$ sea valor propio de $A$.
2. Para

   $$
   R_\theta=\begin{pmatrix}
   \cos\theta&-\sin\theta\\
   \sin\theta&\cos\theta
   \end{pmatrix},
   \qquad 0<|\theta|<\pi,
   $$

   explica geométricamente por qué no hay direcciones propias reales salvo
   en los casos especiales y confirma la conclusión con el polinomio
   característico.
3. Indica los valores propios complejos de $R_\theta$.

### Ejercicio 6. Dos diagnósticos (Lista PC2 2026-I)

Para cada matriz, calcula el polinomio característico, los espacios propios,
las multiplicidades algebraicas y geométricas, y decide si es diagonalizable:

$$
A=\begin{pmatrix}2&1\\1&2\end{pmatrix},
\qquad
B=\begin{pmatrix}0&1&0\\0&0&1\\0&0&0\end{pmatrix}.
$$

Cuando sea posible, construye $PDP^{-1}$. Si la matriz es simétrica, exige
además que $P$ sea ortogonal.

### Ejercicio 7. Una matriz defectuosa y sus potencias (Lista PC2 2026-I)

Sea

$$
C=\begin{pmatrix}4&1&0\\0&4&0\\0&0&2\end{pmatrix}.
$$

1. Compara las multiplicidades algebraica y geométrica de cada valor propio.
2. Explica exactamente por qué $C$ no es diagonalizable.
3. Calcula $C^n$ sin diagonalizarla, usando la estructura del bloque
   superior izquierdo.
4. Escribe explícitamente $C^5$.

### Ejercicio 8. Semejanza y trazabilidad de vectores propios (PC2 2025-I, adaptado)

Sean $A=PBP^{-1}$, con $P$ invertible.

1. Demuestra que $A$ y $B$ tienen el mismo polinomio característico.
2. Si $Av=\lambda v$, encuentra un vector propio de $B$ para $\lambda$.
3. Demuestra que $\operatorname{tr}(A)=\operatorname{tr}(B)$ usando
   $\operatorname{tr}(XY)=\operatorname{tr}(YX)$.
4. Explica qué propiedades sí y cuáles no se conservan por semejanza.

### Ejercicio 9. Qué se puede inferir del espectro (Lista PC2 2026-I)

Una matriz real $B$ de tamaño $3\times3$ tiene valores propios $0,1,2$.
Determina, justificando si la información es suficiente:

1. $\det(B)$ y $\operatorname{tr}(B)$;
2. el rango de $B$;
3. $\det(B^TB)$;
4. los valores propios de $B^TB$;
5. los valores propios de $(B^2+I)^{-1}$.

```{admonition} Atención
:class: warning
Los valores propios de $B^TB$ son los cuadrados de los valores singulares de
$B$, no en general los cuadrados de los valores propios de $B$.
```

### Ejercicio 10. Recurrencia matricial (PC2 2026-I)

Sea

$$
x_0=1,\qquad x_1=4,\qquad
x_{n+1}=3x_n-2x_{n-1}.
$$

1. Escribe la recurrencia como $X_{n+1}=BX_n$ con
   $X_n=(x_n,x_{n-1})^T$.
2. Diagonaliza $B$.
3. Usa $B^n$ para deducir una fórmula cerrada para $x_n$.
4. Verifica la fórmula con la recurrencia y las condiciones iniciales.

## 5. Teorema espectral y formas cuadráticas

### Ejercicio 11. Descomposición espectral completa (PC2 2025-I)

Sea

$$
A=\begin{pmatrix}
6&2&2\\
2&3&1\\
2&1&3
\end{pmatrix}.
$$

1. Explica por qué $A$ es diagonalizable ortogonalmente antes de calcular.
2. Halla sus valores propios y una base ortonormal de cada espacio propio.
3. Construye $A=PDP^T$ y los proyectores espectrales.
4. Calcula $A^6$.
5. Construye una matriz real $C$ tal que $C^3=A$.
6. Interpreta la acción de $A$ en sus direcciones propias.

### Ejercicio 12. Forma cuadrática con un parámetro (PC2 2025-II)

Sea

$$
Q(x,y,z)=x^2+y^2+z^2+2axz,
\qquad a\neq0.
$$

1. Construye la matriz simétrica asociada.
2. Determina sus valores y vectores propios.
3. Reduce $Q$ a forma diagonal mediante un cambio ortogonal.
4. Determina para qué valores de $a$ es definida positiva, semidefinida
   positiva o indefinida.
5. Para $a=2$, escribe $Q$ como suma y diferencia de cuadrados y exhibe
   vectores donde tome signos opuestos.

### Ejercicio 13. Dos parámetros (PC2 2026-I)

Considera

$$
Q(x_1,x_2,x_3)
=\alpha x_1^2+x_2^2+x_3^2+2\beta x_2x_3,
\qquad \alpha\neq0.
$$

1. Escribe la matriz simétrica $M$.
2. Obtén sus valores propios sin calcular un determinante cúbico general.
3. Reduce la forma mediante un cambio ortogonal independiente de los
   parámetros.
4. Clasifica $Q$ en todas las regiones del plano $(\alpha,\beta)$.
5. Describe con cuidado los casos frontera $|\beta|=1$.

### Ejercicio 14. Extremos sobre el círculo (Lista PC2 2026-I)

Sea

$$
F(\theta)=a\cos^2\theta
+b\cos\theta\sin\theta
+c\sin^2\theta.
$$

Se sabe que $\max F=5$, $\min F=-2$ y que $\theta=\pi/3$ es un punto
de máximo.

1. Interpreta $F$ como una forma cuadrática sobre el círculo unitario.
2. Reconstruye la matriz simétrica usando sus valores y direcciones propias.
3. Determina $a,b,c$.
4. Verifica directamente los extremos obtenidos.

### Ejercicio 15. Demostraciones de positividad (Lista PC2 2026-I)

Demuestra cada enunciado indicando el resultado teórico que utilizas.

1. Si $A$ y $B$ son simétricas definidas positivas, entonces $A+B$ es
   definida positiva.
2. Si $A$ es simétrica definida positiva y $C$ es invertible, entonces
   $C^TAC$ es definida positiva.
3. Si $A$ es simétrica semidefinida positiva, existe $R$ tal que $A=RR^T$.
4. Si $A$ es simétrica definida negativa, todos sus valores propios son
   negativos, y recíprocamente.

### Ejercicio 16. Clasificación y extremos (PC2 2025-II, adaptado)

Para cada forma, construye su matriz simétrica, redúcela ortogonalmente,
clasifícala y determina sus extremos sobre la esfera unitaria:

$$
Q_1(x,y)=x^2-3xy+y^2,
$$

$$
Q_2(x,y,z)=2(xy+yz+zx).
$$

Exhibe, cuando existan, vectores no nulos $u,v,w$ tales que
$Q(u)>0$, $Q(v)<0$ y $Q(w)=0$.

## 6. Simulacro integrador

Resuélvelo en 100 minutos, sin software y justificando cada afirmación.

### Problema 1. Transformación y adjunto — 4 puntos (elaboración para esta guía)

Sea $T:\mathbb R^3\to\mathbb R^2$,

$$
T(x,y,z)=(x+y,y+z).
$$

1. Halla la matriz estándar, el núcleo y la imagen de $T$.
2. Comprueba rango-nulidad y decide si $T$ es inyectiva o sobreyectiva.
3. Calcula $T^*$ para los productos internos estándar.
4. Verifica $\ker(T^*)=\operatorname{Im}(T)^\perp$.

### Problema 2. Diagnóstico espectral — 5 puntos (Lista PC2 2026-I, adaptado)

Sea

$$
A=\begin{pmatrix}3&1&0\\0&3&0\\0&0&-1\end{pmatrix}.
$$

1. Calcula el polinomio característico y los espacios propios.
2. Compara multiplicidades y decide si $A$ es diagonalizable.
3. Calcula $A^n$ mediante su estructura por bloques.

### Problema 3. Teorema espectral — 6 puntos (PC2 2025-I, adaptado)

Sea

$$
S=\begin{pmatrix}2&1&1\\1&2&1\\1&1&2\end{pmatrix}.
$$

1. Construye una diagonalización ortogonal $S=PDP^T$.
2. Escribe los proyectores espectrales.
3. Obtén una fórmula para $S^n$.
4. Determina el máximo y mínimo de $x^TSx$ cuando $\|x\|=1$ y los puntos
   donde se alcanzan.

### Problema 4. Forma con parámetros — 5 puntos (PC2 2026-I, adaptado)

Sea

$$
Q(x,y,z)=\gamma x^2+2y^2+2z^2+2\delta yz,
\qquad \gamma\neq0.
$$

1. Construye su matriz simétrica.
2. Reduce ortogonalmente la forma.
3. Clasifícala para todos los valores de $\gamma$ y $\delta$.
4. Describe qué ocurre en los casos frontera.

## 7. Pistas y comprobaciones breves

Consulta esta sección solo después de intentar los problemas.

- **Ejercicio 1:** la matriz es
  $\begin{pmatrix}1&1&1\\0&1&0\end{pmatrix}$; la nulidad es $1$.
- **Ejercicio 4:** la transpuesta usual no es el adjunto pedido; incorpora
  $G$ a ambos lados.
- **Ejercicio 6:** $A$ tiene valores propios $3$ y $1$; $B$ solo tiene el
  valor propio $0$, con multiplicidad geométrica $1$.
- **Ejercicio 7:** para el bloque $4I+N$, se usa
  $(4I+N)^n=4^nI+n4^{n-1}N$ porque $N^2=0$.
- **Ejercicio 9:** el rango es $2$ porque los tres valores propios son
  distintos y, por ello, $B$ es diagonalizable; el espectro de $B^TB$ no
  queda determinado.
- **Ejercicio 10:** los valores propios de la matriz de recurrencia son $1$ y
  $2$; la fórmula es $x_n=3\cdot2^n-2$.
- **Ejercicio 11:** el espectro es $\{8,2,2\}$.
- **Ejercicio 12:** el espectro es $\{1,1+a,1-a\}$.
- **Ejercicio 13:** el espectro es
  $\{\alpha,1+\beta,1-\beta\}$.
- **Ejercicio 14:** usa una base ortonormal formada por
  $(\cos(\pi/3),\sin(\pi/3))$ y su perpendicular.
- **Problema 3:** $S=I+J$, donde $J$ es la matriz de unos.

## 8. Lista final de control

Antes de dar por terminada tu preparación, comprueba que puedes:

1. escribir una definición sin omitir el cuantificador $v\neq0$;
2. distinguir una prueba de un procedimiento de cálculo;
3. verificar $AP=PD$ y no solo presentar $P$ y $D$;
4. justificar cuándo una diagonalización puede ser ortogonal;
5. separar multiplicidad algebraica de geométrica;
6. construir correctamente la matriz de una forma con términos cruzados;
7. tratar por separado los casos frontera de un parámetro;
8. interpretar los valores propios extremos mediante Rayleigh;
9. detectar cuándo los datos no determinan lo solicitado;
10. resolver el simulacro dentro del tiempo previsto.
