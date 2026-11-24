# Fundamentos ENFR 2018

**Informe:** https://docs.google.com/document/d/1ELUgr4DkXi67-vZ29fEjLcLC8v2O2YSWFIo8HmbdViI/edit?usp=sharing

Análisis de la Encuesta Nacional de Factores de Riesgo (ENFR) 2018 de Argentina,
coordinada por INDEC y la Secretaría de Gobierno de Salud.

## Archivos

- `analisis_enfr.ipynb`: notebook única del trabajo.
- `ENFR 2018 - Base usuario.txt`: base cruda original.
- `dataset_procesado.txt`: archivo generado por la notebook, no se usa como entrada.
- `requirements.txt`: dependencias de Python.

## Ejecución local

Se recomienda Python 3.10 o superior.

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
jupyter notebook
```

Abrir `analisis_enfr.ipynb` y ejecutar todas las celdas desde el comienzo.
La notebook lee la base cruda desde el mismo directorio y genera
`dataset_procesado.txt`.

## Decisiones metodológicas

Los códigos `99` de variables categóricas se tratan como valores faltantes.
Para los datos faltantes, creamos `imc_general` priorizando la medición física (`imc_bima`) y completando con el autorreporte (`imc`), imputamos `promedio_sistolica` con KNN ($k=5$), y rellenamos hábitos y categóricas con mediana o moda según el caso. La `glucosa` (~82% de nulos por ser de submuestra bioquímica) no se imputó y se analizó solo con casos completos.

Los análisis son no ponderados. Aunque la base incluye factores de expansión,
los resultados se interpretan como resultados de la muestra analizada y no como
estimaciones poblacionales oficiales. Por tratarse de datos observacionales y
transversales, las asociaciones no deben interpretarse como relaciones causales.

La fuente de definiciones de variables es el
[manual de usuario ENFR 2018 de INDEC](https://www.indec.gob.ar/ftp/cuadros/menusuperior/enfr/manual_base_usuario_enfr2018.pdf).
