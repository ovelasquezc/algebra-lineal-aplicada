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

1. [Aproximación de Fourier y compresión de imágenes](04_fourier_compresion.md)
2. [Laboratorio de Fourier y DCT](04_laboratorio_fourier_dct.ipynb)

Este bloque introduce solamente los números complejos necesarios para Fourier.
Las series y la transformada discreta se presentan como coordenadas y
proyecciones en bases ortonormales. La DCT bidimensional permite interpretar
la compresión de imágenes como selección de componentes de frecuencia.

## Convenciones

- En los tres primeros bloques trabajamos exclusivamente sobre los números
  reales; los complejos aparecen recién en C13 para Fourier.
- Los productos internos se denotan por $\langle u,v\rangle$.
- En espacios complejos usamos la convención lineal en la primera entrada.
- Los cálculos simbólicos se mantienen exactos siempre que sea posible.
