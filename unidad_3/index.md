# Unidad 3. Teoría espectral y aplicaciones

## Logro de aprendizaje

Al finalizar la unidad, el estudiante podrá representar y analizar operadores
lineales mediante matrices, valores y vectores propios, descomposiciones
espectrales y formas cuadráticas, interpretando las condiciones que permiten
diagonalizar y simplificar un problema.

## Organización prevista

La correspondencia entre recursos y sesiones es flexible: algunos bloques
ocuparán más de una clase y una clase puede combinar teoría, ejercicios y
laboratorio.

| Sesiones | Tema | Recursos previstos |
|---|---|---|
| C14-C15 | Transformaciones lineales, núcleo, imagen, isomorfismos y representación matricial | Hoja de teoría y laboratorio simbólico-numérico |
| C16 | Operadores, adjunto y espacios invariantes | Hoja de teoría y laboratorio |
| C17 | Valores y vectores propios; polinomio característico y multiplicidades | Hoja de teoría y laboratorio |
| C18 | Diagonalización y descomposición espectral | Hoja de teoría y laboratorio |
| C19 | Operadores autoadjuntos y matrices simétricas | Hoja de teoría y laboratorio |
| C20 | Formas cuadráticas y cierre de la unidad | Hoja de teoría, laboratorio y preparación para la PC2 |

## Primer bloque: C14-C15

1. [Transformaciones lineales y representación matricial](01_transformaciones_lineales_matrices.md)
2. [Laboratorio de transformaciones lineales](01_laboratorio_transformaciones.ipynb)

Este bloque separa la transformación, que es una función entre espacios
vectoriales, de la matriz que la representa después de elegir bases. Retoma
núcleo, imagen, rango y cambio de base de la Unidad 1 y los organiza alrededor
de las propiedades de linealidad, composición e invertibilidad.

## Convenciones

- La matriz relativa a bases $\mathcal B$ del dominio y $\mathcal C$ del
  codominio se denota $[T]_{\mathcal C\leftarrow\mathcal B}$.
- Las columnas de esa matriz son $[T(b_j)]_{\mathcal C}$.
- La composición $S\circ T$ significa aplicar primero $T$ y luego $S$.
- Los cálculos exactos se mantienen con SymPy y las verificaciones numéricas
  usan NumPy cuando corresponde.
