# Álgebra Lineal Aplicada

Jupyter Book del curso de Álgebra Lineal Aplicada de la Universidad del
Pacífico.

## Construcción local

```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
jupyter-book build .
```

El sitio generado queda en `_build/html/`. Los cuadernos fuente se mantienen
sin resultados guardados; Jupyter Book los ejecuta durante la construcción.
