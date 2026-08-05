# Ejercicios: números complejos y espacios complejos

Los ejercicios de esta hoja se resuelven a mano. El laboratorio que sigue se
reserva para comprobar operaciones, visualizar raíces y explorar ejemplos.

## 1. Forma rectangular y estructura de cuerpo

1. Sean $z=3-2i$ y $w=-1+4i$. Calcule:

   a. $z+w$;
   b. $zw$;
   c. $\overline z$ y $|z|$;
   d. $z/w$.

2. Encuentre las partes real e imaginaria de

   $$
   \frac{2+i}{3-2i}.
   $$

3. Verifique directamente que el inverso propuesto en la Proposición 2.1
   satisface $zz^{-1}=1$.

4. Demuestre que $z+\overline z=2\operatorname{Re}(z)$ y
   $z-\overline z=2i\operatorname{Im}(z)$. Deduzca fórmulas para recuperar
   las partes real e imaginaria usando $z$ y $\overline z$.

5. Pruebe que $|z+w|\leq|z|+|w|$ interpretando $z$ y $w$ como vectores de
   $\mathbb R^2$.

## 2. Forma polar, potencias y raíces

6. Escriba en forma polar:

   a. $1+i$;
   b. $-\sqrt3+i$;
   c. $-2i$;
   d. $-1-\sqrt3i$.

7. Escriba $z=1-\sqrt3i$ en forma polar y calcule $z^4$.

8. Use De Moivre para calcular $(1+i)^{12}$ sin expandir binomios.

9. Determine y represente en el plano complejo:

   a. las cuatro raíces de $z^4=16$;
   b. las tres raíces de $z^3=-8$;
   c. las seis raíces de $z^6=1$.

10. Explique por qué las raíces $n$-ésimas de un complejo no nulo forman
    los vértices de un polígono regular.

## 3. Polinomios y conjugación

11. Factorice completamente en $\mathbb C[t]$:

    a. $t^2+9$;
    b. $t^4-16$;
    c. $t^4+5t^2+4$.

12. Un polinomio real de grado $4$ tiene las raíces $2+i$ y $-3i$.
    Determine las otras dos raíces, contando multiplicidad, y construya un
    polinomio mónico que tenga exactamente esas cuatro raíces.

13. Demuestre que todo polinomio real de grado impar tiene al menos una raíz
    real. Use el teorema fundamental del álgebra y el hecho de que las raíces
    no reales aparecen en pares conjugados.

14. Si $p\in\mathbb R[t]$ y $z_0\notin\mathbb R$ es una raíz de multiplicidad
    $m$, justifique que $\overline{z_0}$ también tiene multiplicidad $m$.

## 4. Espacios vectoriales y productos internos complejos

15. Explique por qué $\{1,i\}$ es una base de $\mathbb C$ sobre $\mathbb R$,
    pero no es linealmente independiente sobre $\mathbb C$.

16. Determine si los vectores $(1,i)$ y $(i,-1)$ son linealmente
    independientes:

    a. sobre $\mathbb C$;
    b. sobre $\mathbb R$.

17. Verifique directamente que

    $$
    \langle x,y\rangle=\sum_{j=1}^n x_j\overline{y_j}
    $$

    es conjugado-lineal en la segunda entrada.

18. Con la convención del curso, verifique que

    $$
    \frac1{\sqrt2}(1,i),
    \qquad
    \frac1{\sqrt2}(i,1)
    $$

    forman una base ortonormal de $\mathbb C^2$.

19. Sea $W=\operatorname{span}_{\mathbb C}\{(1,i,0),(0,1,i)\}$. Aplique
    Gram–Schmidt con el producto interno canónico complejo y proyecte
    $x=(1,1,1)$ sobre $W$.

20. Para $f(t)=1+ie^{it}$ y $g(t)=e^{it}$, calcule

    $$
    \langle f,g\rangle
    =\frac1{2\pi}\int_{-\pi}^{\pi}f(t)\overline{g(t)}\,dt.
    $$

    Interprete el resultado como una coordenada en la dirección $e^{it}$.
