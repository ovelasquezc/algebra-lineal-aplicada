# Unidad 2. Ortogonalidad y ajuste de datos

## Logro de aprendizaje

Al finalizar la unidad, el estudiante podrá interpretar distancia y
ortogonalidad en espacios con producto interno, obtener aproximaciones mediante
proyecciones y aplicar estas ideas al ajuste de datos y a la representación
eficiente de información.

## Organización prevista

La numeración de los recursos no equivale necesariamente a una clase. Un tema
puede ocupar más de una sesión y una sesión puede combinar teoría, cálculo a
mano y trabajo computacional.

| Sesiones | Tema | Recursos |
|---|---|---|
| C10 | Producto interno real, ortogonalidad, bases ortogonales y Gram–Schmidt | Hoja de teoría y laboratorio exacto-numérico |
| C11 | Distancia, complemento ortogonal, hiperplanos y proyección sobre subespacios | Hoja de teoría y laboratorio |
| C12 | Mínimos cuadrados, ecuaciones normales y ajuste de datos | Hoja de teoría y laboratorio |
| C13 | Números complejos, espacios complejos, Fourier y compresión de imágenes | Hojas de teoría y ejercicios; laboratorios separados |

## Primer bloque: C10

1. [Ortogonalidad y proceso de Gram–Schmidt](01_ortogonalidad_gram_schmidt.md)
2. [Laboratorio de Gram–Schmidt](01_laboratorio_gram_schmidt.ipynb)

Este bloque generaliza el producto punto usual de $\mathbb R^n$ a espacios
vectoriales reales con producto interno. También distingue brevemente esta
estructura de la de un espacio de Hilbert. La proyección sobre una sola
dirección se utiliza como herramienta para ortogonalizar. La caracterización
de la proyección como solución de un problema de distancia se desarrollará en
el siguiente bloque.

## Segundo bloque: C11

1. [Distancia, proyección ortogonal e hiperplanos](02_distancia_proyeccion_hiperplanos.md)
2. [Laboratorio de proyecciones](02_laboratorio_proyecciones.ipynb)

Este bloque formula la proyección como un problema de mínima distancia. Primero
se estudia la caracterización sobre conjuntos convexos cerrados y luego se
especializa a subespacios, conjuntos afines e hiperplanos. Las ecuaciones
normales y el ajuste de datos se reservan para C12.

## Tercer bloque: C12

1. [Mínimos cuadrados y ajuste de datos](03_minimos_cuadrados_ajuste.md)
2. [Laboratorio de mínimos cuadrados](03_laboratorio_minimos_cuadrados.ipynb)

Este bloque interpreta los sistemas incompatibles mediante la proyección sobre
el espacio de columnas, deriva las ecuaciones normales y las aplica a matrices
de diseño para ajustes lineales y polinomiales. Se estudian también el residuo,
la unicidad de los coeficientes y el coeficiente de determinación $R^2$.

## Cuarto bloque: C13

### Números complejos y estructura previa

1. [Números complejos y espacios con producto interno complejo](04_numeros_complejos_espacios.md)
2. [Ejercicios de números complejos y espacios complejos](04_ejercicios_numeros_complejos.md)
3. [Laboratorio de números complejos](04_laboratorio_numeros_complejos.ipynb)

Esta sección desarrolla los números complejos en forma rectangular y polar,
sus operaciones, potencias y raíces. El teorema fundamental del álgebra y los
pares de raíces conjugadas preparan el estudio posterior de valores propios.
Antes de Fourier se introducen también los espacios vectoriales complejos y
los espacios con producto interno complejo.

### Fourier y compresión

1. [Aproximación de Fourier y compresión de imágenes](04_fourier_compresion.md)
2. [Ejercicios de Fourier y compresión](04_ejercicios_fourier.md)
3. [Laboratorio de Fourier y DCT](04_laboratorio_fourier_dct.ipynb)

Las series y la transformada discreta se presentan como coordenadas y
proyecciones en familias ortonormales. El teorema de mejor aproximación explica
por qué la suma parcial de Fourier es óptima entre los polinomios
trigonométricos del orden fijado. La DCT bidimensional permite interpretar la
compresión de imágenes como selección de componentes de frecuencia.

## Preparación para el Examen Parcial

1. [Repaso teórico para el EP](05_repaso_teorico_ep.md)
2. [Guía de preparación y simulacro](05_preparacion_ep.md)
3. [Laboratorio de comprobación](05_laboratorio_preparacion_ep.ipynb)

La preparación integra las Unidades 1 y 2. La síntesis organiza definiciones,
teoremas y pruebas; la guía reúne ejercicios escritos y un simulacro; el
laboratorio se reserva para verificar cálculos después de resolverlos a mano.
Las transformaciones lineales y la teoría espectral permanecen fuera del EP
porque corresponden a la Unidad 3.

## Convenciones

- En los tres primeros bloques trabajamos sobre espacios vectoriales reales
  con producto interno. En C13 se desarrolla primero $\mathbb C$ y luego se
  pasa a espacios vectoriales y productos internos complejos antes de Fourier.
- Los productos internos se denotan por $\langle u,v\rangle$.
- En espacios complejos usamos la convención lineal en la primera entrada.
- Los cálculos simbólicos se mantienen exactos siempre que sea posible.
