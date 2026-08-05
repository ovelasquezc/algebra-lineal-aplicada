# Ejercicios: Fourier y compresión

Esta hoja contiene los ejercicios escritos del tema. Las comprobaciones
numéricas y las visualizaciones se trabajan en el laboratorio separado.

## 1. Fourier continuo y mejor aproximación

1. Calcule $c_{-1},c_0,c_1$ para
   $f(t)=\cos t+2\sin t$.

2. Demuestre que, si $f$ toma valores reales, entonces
   $c_{-k}=\overline{c_k}$.

3. Calcule la suma parcial $S_2f$ para

   $$
   f(t)=3-2\cos t+4\sin(2t).
   $$

   ¿El error $\|f-S_2f\|$ es cero? Justifique sin integrar.

4. Sea $p\in\mathcal T_N$. Demuestre directamente que

   $$
   \|f-p\|^2
   =\|f-S_Nf\|^2+\|S_Nf-p\|^2.
   $$

   Identifique en qué paso se usa la ortogonalidad.

5. Si $q\in\mathcal T_N$ y $q\neq S_Nf$, explique por qué no puede producir
   el mismo error cuadrático que $S_Nf$.

6. Calcule los coeficientes reales de Fourier de $f(t)=|t|$ en
   $[-\pi,\pi]$. Use la paridad antes de integrar.

## 2. Fourier discreto

7. Construya la matriz discreta de Fourier para $M=4$ y verifique la
   ortonormalidad de sus columnas con el producto interno promedio.

8. Calcule a mano la DFT de $x=(1,0,-1,0)$ con la normalización del texto y
   reconstruya $x$ mediante la transformada inversa.

9. Explique por qué conservar juntas las frecuencias $k$ y $M-k$ permite
   obtener una reconstrucción real.

10. Pruebe Parseval discreto interpretando la DFT como coordenadas en una base
    ortonormal.

## 3. DCT y compresión

11. Construya la matriz DCT-II ortonormal para $N=4$ y verifique que
    $C^TC=I$.

12. Sea $A\in\mathbb R^{8\times8}$. Compare conceptualmente:

    a. conservar un bloque $3\times3$ de bajas frecuencias;
    b. conservar los nueve coeficientes DCT de mayor magnitud.

    ¿Qué criterio minimiza el error de Frobenius si se permiten nueve
    posiciones arbitrarias?

13. Demuestre que $\|A\|_F=\|CAC^T\|_F$ cuando $C$ es ortogonal.

14. Explique por qué anular coeficientes DCT es una proyección ortogonal,
    mientras que cuantizarlos mediante redondeo no lo es.
