# Unidad 4. Componentes principales y otras aplicaciones

## Logro de aprendizaje

Al finalizar la unidad, el estudiante podrá formular y resolver problemas de
aproximación, reducción de dimensionalidad y optimización mediante SVD,
pseudoinversa, PCA, gradientes, Hessianas y multiplicadores de Lagrange,
interpretando las posibilidades y limitaciones de cada método.

## Organización prevista

El sílabo contiene más temas que sesiones disponibles. Por ello algunos
recursos se desarrollan durante dos clases y las aplicaciones se agrupan
alrededor de una misma herramienta matemática.

| Sesiones | Tema | Recursos previstos |
|---|---|---|
| C21 | Cálculo de la SVD y pseudoinversa | Hoja de teoría y laboratorio |
| C22 | Aproximación de subespacios y de rango bajo | Hoja de teoría y laboratorio |
| C23 | PCA, reducción de dimensionalidad y aplicaciones | Hoja de teoría y laboratorio |
| C24 | Gradiente y Hessiana | Hoja de teoría y laboratorio |
| C25 | Optimización con y sin restricciones | Hoja de teoría y laboratorio |
| Con el avance hasta C22 | Preparación para el EF | Repaso teórico, problemas y laboratorio |

## Primer bloque: C21

1. [Descomposición en valores singulares y pseudoinversa](01_svd_pseudoinversa.md)
2. [Laboratorio de SVD y pseudoinversa](01_laboratorio_svd_pseudoinversa.ipynb)

Esta sesión construye y calcula la SVD desde el teorema espectral aplicado a
$A^TA$, y deduce la pseudoinversa de Moore-Penrose. La interpretación por
subespacios se usa para comprender $A^+b$ y preparar C22, pero el teorema de
mejor aproximación de rango bajo y sus aplicaciones se reservan para esa
sesión.

## Segundo bloque: C22

1. [Subespacios de mejor aproximación y rango bajo](02_subespacios_rango_bajo.md)
2. [Laboratorio de aproximación de rango bajo](02_laboratorio_rango_bajo.ipynb)

Esta sesión formula el mejor ajuste por subespacios, obtiene la solución con
los vectores singulares derechos y presenta el teorema de
Eckart-Young-Mirsky. La compresión de imágenes funciona como aplicación
visual y cuantitativa. PCA, centrado de datos y filtrado colaborativo se
reservan para C23.

## Preparación para el examen final con el avance actual

1. [Repaso teórico para el examen final](03_repaso_teorico_ef.md)
2. [Guía de preparación y simulacro](03_preparacion_ef.md)
3. [Laboratorio de preparación](03_laboratorio_preparacion_ef.ipynb)

Este bloque es acumulativo, pero da prioridad a teoría espectral, formas
cuadráticas, SVD, pseudoinversa y aproximación de rango bajo. PCA, gradiente,
Hessiana y optimización quedan fuera de esta versión y se incorporarán cuando
se desarrollen esos temas.

## Convenciones

- Para $A\in\mathbb R^{m\times n}$, se escribe
  $A=U\Sigma V^T$.
- Los valores singulares se ordenan
  $\sigma_1\geq\cdots\geq\sigma_r>0$.
- $A^+$ denota la pseudoinversa de Moore-Penrose.
- Los cálculos exactos se realizan con SymPy y las verificaciones numéricas
  con NumPy cuando corresponde.
