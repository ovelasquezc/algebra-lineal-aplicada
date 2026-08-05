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
| C20 | Formas cuadráticas y cierre de la unidad | Hoja de teoría y laboratorio |
| Después de C20 | Preparación integral para la PC2 | Repaso teórico, problemas y laboratorio |

## Primer bloque: C14-C15

1. [Transformaciones lineales y representación matricial](01_transformaciones_lineales_matrices.md)
2. [Laboratorio de transformaciones lineales](01_laboratorio_transformaciones.ipynb)

Este bloque separa la transformación, que es una función entre espacios
vectoriales, de la matriz que la representa después de elegir bases. Retoma
núcleo, imagen, rango y cambio de base de la Unidad 1 y los organiza alrededor
de las propiedades de linealidad, composición e invertibilidad.

## Segundo bloque: C16

1. [Operadores, adjunto y subespacios invariantes](02_operadores_adjuntos_invariantes.md)
2. [Laboratorio de operadores, adjunto e invariancia](02_laboratorio_adjuntos_invariantes.ipynb)

Este bloque estudia las partes de un espacio que se conservan bajo un
operador, la forma matricial por bloques que resulta de esa invariancia y el
operador adjunto como vínculo entre transformaciones, producto interno y
ortogonalidad. Las propiedades espectrales de los operadores autoadjuntos se
desarrollarán después de introducir valores y vectores propios.

## Tercer bloque: C17

1. [Valores y vectores propios](03_valores_vectores_propios.md)
2. [Laboratorio de valores y vectores propios](03_laboratorio_valores_propios.ipynb)

Este bloque interpreta los vectores propios como direcciones invariantes y
desarrolla el cálculo del polinomio característico, los espacios propios y sus
multiplicidades. También distingue el espectro real del complejo y prepara el
criterio de diagonalización del bloque siguiente.

## Cuarto bloque: C18

1. [Diagonalización y descomposición espectral](04_diagonalizacion_descomposicion_espectral.md)
2. [Laboratorio de diagonalización](04_laboratorio_diagonalizacion.ipynb)

Este bloque caracteriza la diagonalización por semejanza, construye
$A=PDP^{-1}$ y aplica la descomposición en espacios propios al cálculo de
potencias, funciones matriciales y sistemas dinámicos. Los proyectores
espectrales se presentan en general; su carácter ortogonal para operadores
autoadjuntos se reserva para C19.

## Quinto bloque: C19

1. [Operadores autoadjuntos y teorema espectral](05_autoadjuntos_teorema_espectral.md)
2. [Laboratorio del teorema espectral](05_laboratorio_teorema_espectral.ipynb)

Este bloque demuestra que los operadores autoadjuntos tienen valores propios
reales y espacios propios distintos ortogonales. El teorema espectral conduce
a la diagonalización ortogonal o unitaria, a proyectores espectrales
ortogonales y a las cotas del cociente de Rayleigh.

## Sexto bloque: C20

1. [Formas cuadráticas y clasificación por signo](06_formas_cuadraticas.md)
2. [Laboratorio de formas cuadráticas](06_laboratorio_formas_cuadraticas.ipynb)

Este bloque cierra la unidad construyendo la matriz simétrica de una forma
cuadrática, reduciéndola a suma y diferencia de cuadrados y clasificándola
mediante espectro, inercia y criterios de Sylvester. También conecta la
positividad con matrices de Gram y optimización convexa.

## Cierre de la unidad: preparación para la PC2

1. [Repaso teórico para la PC2](07_repaso_teorico_pc2.md)
2. [Guía de preparación para la PC2](07_preparacion_pc2.md)
3. [Laboratorio de preparación para la PC2](07_laboratorio_preparacion_pc2.ipynb)

El cierre tiene alcance acumulativo sobre toda la Unidad 3. La hoja teórica
separa enunciados, pruebas e ideas de prueba; la guía combina conceptos,
cálculo, demostraciones y un simulacro; el laboratorio permite verificar los
cálculos después de resolverlos por escrito. La SVD se reserva para la Unidad
4.

## Convenciones

- La matriz relativa a bases $\mathcal B$ del dominio y $\mathcal C$ del
  codominio se denota $[T]_{\mathcal C\leftarrow\mathcal B}$.
- Las columnas de esa matriz son $[T(b_j)]_{\mathcal C}$.
- La composición $S\circ T$ significa aplicar primero $T$ y luego $S$.
- Los cálculos exactos se mantienen con SymPy y las verificaciones numéricas
  usan NumPy cuando corresponde.
