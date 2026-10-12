# repo_ML_2026Q4_Grupo1

Proyecto de análisis y carga de datasets para ejercicios de Machine Learning y Data Science.

## Descripción

Este repositorio contiene una pequeña utilidad para cargar datasets de Hugging Face y generar reportes descriptivos de un DataFrame. Está pensado para actividades académicas o prototipos rápidos donde se necesita:

- Descargar un dataset desde Hugging Face.
- Convertirlo a un DataFrame de pandas.
- Opcionalmente guardarlo en disco en formatos CSV, JSON, Parquet o Excel.
- Generar un reporte resumido de columnas, tipos, nulos y estadísticas numéricas.

La lógica principal se encuentra en el paquete `src/clases_po` y el notebook de ejemplo en `src/actividades/actividad_1.ipynb`.

## Estructura del proyecto

```text
repo_ML_2026Q4_Grupo1/
├── requirements.txt
├── README.md
├── src/
│   ├── actividades/
│   │   └── actividad_1.ipynb
│   └── clases_po/
│       ├── __init__.py
│       ├── hf_loader.py
│       └── reportes.py
└── .venv/
```

## Componentes principales

### `HFDatasetLoader`

Clase ubicada en `src/clases_po/hf_loader.py` que permite cargar un dataset de Hugging Face con opciones como:

- nombre del dataset
- configuración específica del dataset
- split a utilizar
- token para datasets privados
- directorio de caché
- máximo de filas
- nombre de archivo de salida
- tipo de archivo de salida

### `Reportes`

Clase ubicada en `src/clases_po/reportes.py` para generar reportes legibles de un DataFrame. Permite:

- Mostrar el total de filas y columnas
- Identificar duplicados
- Revisar tipos de columnas
- Ver valores nulos por columna
- Obtener estadísticas numéricas
- Guardar el reporte en un archivo de texto

## Requisitos

- Python 3.11+
- pip
- Entorno virtual recomendado (`.venv` incluido en el repositorio)

## Instalación

1. Clona el repositorio:

```bash
git clone https://github.com/maycolvasquez-iud/repo_ML_2026Q4_Grupo1.git
cd repo_ML_2026Q4_Grupo1
```

2. Crea y activa un entorno virtual:

```bash
python -m venv .venv
source .venv/bin/activate
```

3. Instala dependencias:

```bash
pip install -r requirements.txt
```

## Uso rápido

### Cargar un dataset desde Hugging Face

```python
from clases_po import HFDatasetLoader

loader = HFDatasetLoader(
    dataset_name="ameya-akkalkotkar/VideoGamesList",
    split="train",
    filename="datos/videogames.csv",
)

df = loader.load()
print(df.head())
```

### Generar un reporte del DataFrame

```python
from clases_po import Reportes

reporte = Reportes()
print(reporte.generar_reporte(df))
reporte.guardar_reporte(df, "salidas/reporte.txt")
```

## Ejemplo incluido

El notebook `src/actividades/actividad_1.ipynb` muestra un flujo típico de trabajo:

1. Importar `HFDatasetLoader`
2. Definir el nombre del dataset
3. Cargar datos desde Hugging Face
4. Inspeccionar la estructura del DataFrame
5. Revisar información relevante del dataset

## Dependencias principales

El proyecto usa:

- `pandas`
- `numpy`
- `matplotlib`
- `datasets`
- `ipykernel`
- `nbconvert`

## Licencia

Este proyecto no especifica una licencia en el repositorio. Si vas a reutilizarlo o compartirlo, conviene revisar antes la política de uso del repositorio y de los datos descargados desde Hugging Face.

## Notas

- Los datasets descargados pueden almacenarse en caché automáticamente por la librería `datasets`.
- El flujo está preparado para experimentación, exploración y preparación de datos antes de aplicar modelos de Machine Learning.
