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
| C10 | Producto interno, ortogonalidad, bases ortogonales y Gram–Schmidt | Hoja de teoría y laboratorio exacto-numérico |
| C11 | Distancia, complemento ortogonal, hiperplanos y proyección sobre subespacios | Hoja de teoría y laboratorio |
| C12 | Mínimos cuadrados, ecuaciones normales y ajuste de datos | Hoja de teoría y laboratorio |
| C13 | Aproximación en bases ortogonales, Fourier y compresión de imágenes | Hoja de teoría y laboratorio |

## Primer bloque: C10

1. [Ortogonalidad y proceso de Gram–Schmidt](01_ortogonalidad_gram_schmidt.md)
2. [Laboratorio de Gram–Schmidt](01_laboratorio_gram_schmidt.ipynb)

Este bloque generaliza el producto punto usual de $\mathbb R^n$ a espacios
vectoriales reales con producto interno. La proyección sobre una sola dirección
se utiliza como herramienta para ortogonalizar. La caracterización de la
proyección como solución de un problema de distancia se desarrollará en el
siguiente bloque.

## Convenciones

- En los primeros bloques trabajamos exclusivamente sobre los números reales.
- Los productos internos se denotan por $\langle u,v\rangle$.
- Los cálculos simbólicos se mantienen exactos siempre que sea posible.
- Los números complejos se introducirán únicamente al llegar al análisis de
  Fourier.
