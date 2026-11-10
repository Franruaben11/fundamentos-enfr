# Fundamentos ENFR 2018

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
No se imputan masivamente IMC, glucemia, presión sistólica ni perímetro de
cintura: esas mediciones pertenecen a submuestras y se analizan con casos
completos para cada hipótesis. El IMC utilizado es el valor `imc_bima` provisto
por la base; el cálculo desde peso y talla se usa únicamente como control de
consistencia.

Los análisis son no ponderados. Aunque la base incluye factores de expansión,
los resultados se interpretan como resultados de la muestra analizada y no como
estimaciones poblacionales oficiales. Por tratarse de datos observacionales y
transversales, las asociaciones no deben interpretarse como relaciones causales.

La fuente de definiciones de variables es el
[manual de usuario ENFR 2018 de INDEC](https://www.indec.gob.ar/ftp/cuadros/menusuperior/enfr/manual_base_usuario_enfr2018.pdf).
