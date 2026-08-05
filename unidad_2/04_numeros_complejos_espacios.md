# Números complejos y espacios con producto interno complejo

## Objetivos

Al finalizar este tema, el estudiante podrá:

1. operar con números complejos en forma rectangular y polar;
2. calcular potencias y raíces complejas;
3. explicar por qué $\mathbb C$ es un cuerpo y por qué se necesita al
   estudiar polinomios;
4. usar el teorema fundamental del álgebra y la propiedad de las raíces
   conjugadas de polinomios reales;
5. reconocer espacios vectoriales y productos internos complejos;
6. preparar la estructura que se usará en Fourier y, más adelante, en valores
   propios.

## 1. Construcción y forma rectangular

El conjunto de los números complejos puede construirse como $\mathbb R^2$ con
las operaciones

$$
(a,b)+(c,d)=(a+c,b+d),
$$

$$
(a,b)(c,d)=(ac-bd,ad+bc).
$$

Identificamos $(a,0)$ con el número real $a$ y escribimos
$i=(0,1)$. Entonces

$$
i^2=(-1,0)=-1
$$

y todo número complejo tiene una única **forma rectangular**

$$
\boxed{z=a+bi},
\qquad a,b\in\mathbb R.
$$

Se definen

$$
\operatorname{Re}(z)=a,
\qquad
\operatorname{Im}(z)=b.
$$

Si $z=a+bi$ y $w=c+di$, entonces

$$
z+w=(a+c)+(b+d)i,
$$

$$
zw=(ac-bd)+(ad+bc)i.
$$

### Ejemplo 1.1. Operaciones en forma rectangular

Para $z=2-3i$ y $w=1+2i$,

$$
z+w=3-i,
$$

$$
zw=(2-3i)(1+2i)=8+i.
$$

## 2. $\mathbb C$ como cuerpo

Un **cuerpo** es un conjunto de escalares con suma y producto que satisfacen
las propiedades usuales: asociatividad y conmutatividad de ambas operaciones,
existencia de $0$ y $1$, existencia de opuestos e inversos multiplicativos
para los elementos no nulos, y distributividad del producto respecto de la
suma.

### Proposición 2.1. Estructura de cuerpo de $\mathbb C$

**Enunciado.** Con las operaciones anteriores, $\mathbb C$ es un cuerpo. En
particular:

1. el cero es $0+0i$;
2. el opuesto de $z=a+bi$ es $-a-bi$;
3. el uno es $1+0i$;
4. si $z=a+bi\neq0$, entonces

   $$
   \boxed{
   z^{-1}=\frac{a}{a^2+b^2}-\frac{b}{a^2+b^2}i.
   }
   $$

**Idea de prueba.** Las propiedades algebraicas se verifican usando las de los
números reales. Para el inverso se multiplica $a+bi$ por $a-bi$ y se usa que
$(a+bi)(a-bi)=a^2+b^2>0$. $\square$

La palabra cuerpo importa: significa que $\mathbb C$ puede usarse como
conjunto de escalares de un espacio vectorial, del mismo modo que
$\mathbb R$.

## 3. Conjugado, módulo y división

### Definición 3.1. Conjugado y módulo

Para $z=a+bi$ se definen

$$
\overline z=a-bi,
\qquad
|z|=\sqrt{a^2+b^2}.
$$

### Proposición 3.2. Propiedades básicas

**Enunciado.** Para $z,w\in\mathbb C$:

1. $\overline{z+w}=\overline z+\overline w$;
2. $\overline{zw}=\overline z\,\overline w$;
3. $z\overline z=|z|^2$;
4. $|zw|=|z|\,|w|$;
5. si $w\neq0$, entonces

   $$
   \frac zw=\frac{z\overline w}{|w|^2}.
   $$

**Prueba.** Las tres primeras identidades se obtienen al escribir los números
en forma rectangular. Para la cuarta,

$$
|zw|^2=(zw)\overline{zw}
=z\overline z\,w\overline w
=|z|^2|w|^2,
$$

y ambos lados son no negativos. La última identidad se obtiene multiplicando
numerador y denominador por $\overline w$. $\square$

### Ejemplo 3.3. Cociente

$$
\frac{2-3i}{1+2i}
=\frac{(2-3i)(1-2i)}{1^2+2^2}
=-\frac45-\frac75i.
$$

## 4. Forma polar y fórmula de Euler

Sea $z=a+bi\neq0$. En el plano complejo, $z$ corresponde al punto $(a,b)$.
Si

$$
r=|z|,
$$

podemos escoger un ángulo $\theta$ tal que

$$
a=r\cos\theta,
\qquad
b=r\sin\theta.
$$

El ángulo $\theta$ es un **argumento** de $z$. No es único: todos los
argumentos son $\theta+2k\pi$, con $k\in\mathbb Z$.

### Teorema 4.1. Fórmula de Euler

**Enunciado.** Para $\theta\in\mathbb R$,

$$
e^{i\theta}=\cos\theta+i\sin\theta.
$$

Por tanto, la **forma polar** de $z$ es

$$
\boxed{z=r(\cos\theta+i\sin\theta)=re^{i\theta}.}
$$

**Idea de prueba.** En la serie de potencias de $e^{i\theta}$, los términos
pares forman la serie del coseno y los impares forman $i$ veces la serie del
seno. $\square$

```{admonition} Cuidado al calcular el argumento
:class: warning
La igualdad $\tan\theta=b/a$ no determina por sí sola el cuadrante. Conviene
usar el punto $(a,b)$ o una función de dos argumentos como `atan2(b,a)`.
```

### Ejemplo 4.2. Paso a forma polar

Para $z=1-\sqrt3 i$ se tiene $r=2$ y puede tomarse
$\theta=-\pi/3$. Por tanto,

$$
z=2e^{-i\pi/3}.
$$

## 5. Productos, potencias y raíces

Si $z=re^{i\theta}$ y $w=se^{i\varphi}$, entonces

$$
zw=rs\,e^{i(\theta+\varphi)},
\qquad
\frac zw=\frac rs e^{i(\theta-\varphi)}\quad(w\neq0).
$$

### Teorema 5.1. Fórmula de De Moivre

**Enunciado.** Para todo entero $n$,

$$
\boxed{
(\cos\theta+i\sin\theta)^n
=\cos(n\theta)+i\sin(n\theta).
}
$$

En particular, si $z=re^{i\theta}$ y $n\geq0$,

$$
z^n=r^ne^{in\theta}.
$$

**Prueba.** Se usa la fórmula de Euler y la propiedad
$(e^{i\theta})^n=e^{in\theta}$. $\square$

### Ejemplo 5.2. Potencia

Si $z=1-\sqrt3i=2e^{-i\pi/3}$, entonces

$$
z^4=16e^{-4i\pi/3}
=16e^{2i\pi/3}
=-8+8\sqrt3i.
$$

### Teorema 5.3. Raíces $n$-ésimas

**Enunciado.** Sea $z=re^{i\theta}\neq0$ y $n\geq1$. Las soluciones de
$w^n=z$ son exactamente

$$
\boxed{
w_k=r^{1/n}e^{i(\theta+2k\pi)/n},
\qquad k=0,1,\ldots,n-1.
}
$$

**Idea de prueba.** Si $w=\rho e^{i\varphi}$, la ecuación $w^n=z$ exige
$\rho^n=r$ y $n\varphi=\theta+2k\pi$. Los valores $k=0,\ldots,n-1$ producen
todas las soluciones distintas. $\square$

### Ejemplo 5.4. Raíces cúbicas

Las raíces cúbicas de $8=8e^{i0}$ son

$$
2,
\qquad
2e^{2\pi i/3}=-1+\sqrt3i,
\qquad
2e^{4\pi i/3}=-1-\sqrt3i.
$$

Geométricamente son tres puntos igualmente espaciados sobre el círculo de
radio $2$.

## 6. Por qué se necesitan los números complejos

El polinomio real $p(x)=x^2+1$ no tiene raíces reales, pero en $\mathbb C$
se factoriza como

$$
x^2+1=(x-i)(x+i).
$$

Esto no es un caso aislado.

### Teorema 6.1. Teorema fundamental del álgebra

**Enunciado.** Todo polinomio complejo no constante posee al menos una raíz
compleja. En consecuencia, si $p$ tiene grado $n\geq1$, existen raíces
distintas $z_1,\ldots,z_r$ y enteros positivos $m_1,\ldots,m_r$ tales que

$$
\boxed{
p(z)=a_n(z-z_1)^{m_1}\cdots(z-z_r)^{m_r},
\qquad
m_1+\cdots+m_r=n.
}
$$

Los números $m_j$ son las multiplicidades de las raíces. No probaremos este
teorema en el curso; lo usaremos como garantía de que en $\mathbb C$ un
polinomio se descompone por completo en factores lineales.

### Teorema 6.2. Raíces conjugadas de polinomios reales

**Enunciado.** Si $p\in\mathbb R[t]$ y $z\in\mathbb C$, entonces

$$
p(\overline z)=\overline{p(z)}.
$$

En particular, si $p(z)=0$, entonces $p(\overline z)=0$. Las raíces no reales
de un polinomio con coeficientes reales aparecen en pares conjugados, con la
misma multiplicidad.

**Prueba.** Si $p(t)=a_nt^n+\cdots+a_0$ y todos los $a_j$ son reales,

$$
\overline{p(z)}
=\sum_{j=0}^n\overline{a_jz^j}
=\sum_{j=0}^na_j\overline z^{,j}
=p(\overline z).
$$

Si $p(z)=0$, el lado izquierdo es cero. $\square$

Para justificar también la multiplicidad, si
$p(t)=(t-z)^m q(t)$ con $q(z)\neq0$, se conjugan los coeficientes de la
identidad. Como $p$ tiene coeficientes reales, se obtiene

$$
p(t)=(t-\overline z)^m\overline q(t),
$$

donde $\overline q(\overline z)=\overline{q(z)}\neq0$.

### Ejemplo 6.3. Par conjugado

Las raíces de $t^2-2t+5$ son $1+2i$ y $1-2i$, y

$$
t^2-2t+5=(t-(1+2i))(t-(1-2i)).
$$

```{admonition} Conexión posterior con valores propios
:class: note
El polinomio característico de una matriz real tiene coeficientes reales. Por
ello, sus valores propios no reales aparecerán en pares conjugados. Esta
consecuencia se retomará en
[Valores y vectores propios](../unidad_3/03_valores_vectores_propios.md).
```

## 7. Espacios vectoriales complejos

### Definición 7.1. Espacio vectorial sobre $\mathbb C$

Un **espacio vectorial complejo** es un espacio vectorial cuyos escalares
pertenecen al cuerpo $\mathbb C$. Los axiomas son los mismos que para un
espacio vectorial real; lo que cambia es el conjunto de escalares permitido.

Son ejemplos:

1. $\mathbb C^n$;
2. $\mathcal P_n(\mathbb C)$, los polinomios de grado a lo más $n$ con
   coeficientes complejos;
3. $C([-\pi,\pi],\mathbb C)$, las funciones continuas de valores complejos.

La distinción importa. Por ejemplo, $\mathbb C$ tiene dimensión $1$ como
espacio vectorial complejo, con base $\{1\}$, pero dimensión $2$ como espacio
vectorial real, con base $\{1,i\}$.

### Ejemplo 7.2. Combinaciones lineales complejas

En $\mathbb C^2$, los vectores

$$
u=(1,i),
\qquad
v=(i,-1)
$$

son linealmente dependientes sobre $\mathbb C$, pues $v=iu$. En cambio, si se
consideran solamente escalares reales, son linealmente independientes.

## 8. Espacios con producto interno complejo

En este curso adoptamos la convención de que el producto interno es lineal en
la primera entrada.

### Definición 8.1. Producto interno complejo

Sea $V$ un espacio vectorial complejo. Un **producto interno complejo** o
**hermitiano** es una función

$$
\langle\cdot,\cdot\rangle:V\times V\longrightarrow\mathbb C
$$

que satisface, para $u,v,w\in V$ y $\alpha\in\mathbb C$:

1. **simetría conjugada:**
   $\langle u,v\rangle=\overline{\langle v,u\rangle}$;
2. **aditividad en la primera entrada:**
   $\langle u+v,w\rangle=\langle u,w\rangle+\langle v,w\rangle$;
3. **homogeneidad en la primera entrada:**
   $\langle\alpha u,v\rangle=\alpha\langle u,v\rangle$;
4. **positividad definida:** $\langle u,u\rangle\geq0$, y
   $\langle u,u\rangle=0$ si y solo si $u=0$.

De estas propiedades se deduce la conjugada-linealidad en la segunda entrada:

$$
\langle u,\alpha v+w\rangle
=\overline\alpha\langle u,v\rangle+\langle u,w\rangle.
$$

### Ejemplo 8.2. Producto interno canónico en $\mathbb C^n$

Para $x,y\in\mathbb C^n$,

$$
\boxed{
\langle x,y\rangle
=\sum_{j=1}^n x_j\overline{y_j}
=y^*x,
}
$$

donde $y^*=\overline y^{,T}$ es la transpuesta conjugada. La norma inducida
es

$$
\|x\|^2=\langle x,x\rangle=\sum_{j=1}^n|x_j|^2.
$$

La conjugación no es decorativa: garantiza que $\langle x,x\rangle$ sea real
y no negativo.

### Ejemplo 8.3. Producto interno en funciones complejas

Para funciones continuas de valores complejos en $[-\pi,\pi]$, definimos

$$
\boxed{
\langle f,g\rangle
=\frac1{2\pi}\int_{-\pi}^{\pi}f(t)\overline{g(t)}\,dt.
}
$$

La norma asociada satisface

$$
\|f\|^2
=\frac1{2\pi}\int_{-\pi}^{\pi}|f(t)|^2\,dt.
$$

Este es el producto interno que permite interpretar los coeficientes de
Fourier como coordenadas y las sumas parciales como proyecciones.

```{admonition} Mención: Hilbert complejo
:class: note
La definición de espacio de Hilbert es la misma en el caso complejo: es un
espacio con producto interno que es completo para su norma inducida. El espacio
$L^2([-\pi,\pi],\mathbb C)$ es el marco completo natural de Fourier. Aquí
trabajaremos con las fórmulas y la geometría necesarias, sin desarrollar la
teoría de convergencia de $L^2$.
```

## 9. Ortogonalidad y proyección compleja

Las definiciones de ortogonalidad, conjunto ortonormal y complemento ortogonal
son las mismas:

$$
u\perp v
\quad\Longleftrightarrow\quad
\langle u,v\rangle=0.
$$

### Teorema 9.1. Proyección sobre una familia ortonormal compleja

**Enunciado.** Si $(u_1,\ldots,u_r)$ es una familia ortonormal y
$W=\operatorname{span}\{u_1,\ldots,u_r\}$, entonces

$$
\boxed{
P_W(x)=\sum_{j=1}^r\langle x,u_j\rangle u_j.
}
$$

Además,

$$
\|x-P_W(x)\|^2
=\|x\|^2-\sum_{j=1}^r|\langle x,u_j\rangle|^2.
$$

**Prueba.** La combinación pertenece a $W$. Por la convención elegida,

$$
\left\langle
x-\sum_{j=1}^r\langle x,u_j\rangle u_j,u_k
\right\rangle=0
$$

para cada $k$. El residuo pertenece a $W^\perp$ y la identidad se obtiene por
Pitágoras. $\square$

Esta fórmula es exactamente la que se usará en el siguiente tema: las
direcciones ortonormales serán las funciones $e^{ikt}$.
