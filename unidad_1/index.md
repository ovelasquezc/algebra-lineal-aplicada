# Unidad 1. Fundamentos del álgebra lineal

## Logro de aprendizaje

Al finalizar la unidad, el estudiante podrá analizar la estructura de espacios
vectoriales reales y sus subespacios, representar vectores en distintas bases y
resolver sistemas de ecuaciones lineales mediante procedimientos algebraicos y
computacionales.

## Organización

Esta unidad no identifica un archivo con una clase. Cada tema puede ocupar una
parte de una sesión o extenderse durante varias sesiones.

| Sesiones | Tema | Recursos |
|---|---|---|
| C1-C2 | Vectores, geometría de $\mathbb R^n$, matrices y sistemas sencillos | Hoja de teoría, laboratorio y repaso opcional de trigonometría |
| C3 | Operaciones elementales y eliminación de Gauss-Jordan | Presentación y laboratorio |
| C4 | Combinación e independencia lineal | Presentación y ejercicios |
| C5 | Subespacios, bases y dimensión | Presentación y laboratorio |
| C6-C7 | Núcleo, imagen, rango, rango-nulidad, determinante e invertibilidad | Presentaciones y laboratorios |
| C8 | Espacios vectoriales reales, subespacios afines y suma directa | Presentación y ejercicios |
| C9 | Representación de vectores y cambio de base | Hoja de teoría y cuaderno simbólico |

## Primer bloque: C1-C2

1. [Vectores, geometría de $\mathbb R^n$, matrices y sistemas](01_vectores_geometria_matrices.md)
2. [Laboratorio de vectores y matrices](01_laboratorio_vectores_matrices.ipynb)
3. [Repaso opcional de trigonometría](01_repaso_trigonometria.ipynb)

El repaso de trigonometría sirve como apoyo para interpretar el ángulo entre
vectores. Se reutilizará en la Unidad 2 antes de introducir números complejos y
análisis de Fourier.

## Segundo bloque: C3-C4

1. [Eliminación de Gauss–Jordan](02_eliminacion_gauss_jordan.md)
2. [Laboratorio de eliminación de Gauss–Jordan](02_laboratorio_gauss_jordan.ipynb)
3. [Combinación e independencia lineal](03_combinacion_independencia.md)

El laboratorio usa aritmética exacta para distinguir ceros matemáticos de
errores de redondeo y desarrolla sistemas con solución única, infinitas
soluciones, incompatibilidad y parámetros.

## Tercer bloque: C5-C7

1. [Subespacios, bases y dimensión](04_subespacios_bases_dimension.md)
2. [Laboratorio de subespacios, núcleo e imagen](04_laboratorio_subespacios_nucleo_imagen.ipynb)
3. [Núcleo, imagen y rango](05_nucleo_imagen_rango.md)
4. [Determinante e invertibilidad](06_determinante_invertibilidad.md)
5. [Laboratorio de determinante e invertibilidad](06_laboratorio_determinante.ipynb)

Este bloque conecta los procedimientos de Gauss–Jordan con bases de los
espacios fundamentales de una matriz y culmina en las caracterizaciones de
invertibilidad. Los laboratorios incluyen ejercicios con el nivel y tamaño de
las matrices utilizadas en la PC1.

## Cuarto bloque: C8-C9

1. [Espacios vectoriales reales, conjuntos afines y suma directa](07_espacios_vectoriales_afines_suma_directa.md)
2. [Laboratorio de espacios afines y suma directa](07_laboratorio_espacios_suma_directa.ipynb)
3. [Coordenadas y cambio de base](08_coordenadas_cambio_base.md)
4. [Laboratorio simbólico de cambio de base](08_laboratorio_cambio_base.ipynb)

Este bloque generaliza a espacios vectoriales reales las propiedades ya
estudiadas en $\mathbb R^n$. La Unidad 1 cierra con coordenadas y cambio de
base. Los números complejos se reservan para la Unidad 2.

## Convenciones

- Los vectores se escriben como columnas cuando participan en productos
  matriciales.
- Trabajamos sobre los números reales durante toda la Unidad 1.
- Las celdas de código usan principalmente `numpy` y `matplotlib`.
- Los resultados numéricos deben interpretarse y no solamente calcularse.
