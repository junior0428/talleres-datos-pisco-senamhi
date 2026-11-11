# talleres-datos-pisco-senamhi

Material de talleres para trabajar con productos **PISCO** (SENAMHI): precipitación y variables meteorológicas grilladas del Perú (resolución espacial ~0.1°), usando principalmente **R**, con apoyo de **Python**, notebooks y QGIS.

Cada carpeta es un ejercicio o módulo autónomo (proyecto RStudio / scripts / datos de ejemplo).

## Contenido

| Carpeta | Enfoque |
|---|---|
| [`Pisco/`](Pisco/) | Introducción: extracción de precipitación desde NetCDF, series temporales y ajuste Gumbel. |
| [`PISCOp_Daily/`](PISCOp_Daily/) | Producto diario PISCOp: extracción, series, tiempos de retorno, notebook y script Python. |
| [`Datos-PISCO-Qgis-R/`](Datos-PISCO-Qgis-R/) | Flujo QGIS + R: extracción puntual, Gumbel y tiempos de retorno; shapefiles/Excel empaquetados. |
| [`PPmCuencaPISCO_GEMRA/`](PPmCuencaPISCO_GEMRA/) | Precipitación media mensual a escala de cuenca (ej. Santa / GEMRA): extracción y promedios. |

## Stack

- **R**: `raster` / `ncdf4`, `sp`, `tidyverse` / `lubridate`, `readxl`
- **Python** / Jupyter (módulo diario)
- Archivos auxiliares: `.nc`, CSV, Excel, shapefiles (a menudo en `.rar`)

## Notas

- Los datos grillados PISCO no suelen versionarse aquí; se descargan desde las fuentes oficiales SENAMHI / enlaces indicados en cada carpeta (`EnlacePisco.txt`, `Link.txt`, etc.).
- Rutas absolutas en algunos scripts (`setwd(...)`) hay que adaptarlas al entorno local.
- Artefactos de sesión R, checkpoints de Jupyter y archivos temporales están ignorados vía el `.gitignore` de la raíz.
