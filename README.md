# Talleres PISCO · SENAMHI

Material de talleres para trabajar con productos grillados **PISCO** ([SENAMHI](https://www.senamhi.gob.pe/)): precipitación y variables meteorológicas del Perú (~0.1°), principalmente en **R**, con apoyo de **Python**, Jupyter y QGIS.

Cada carpeta es un módulo autónomo (proyecto RStudio, scripts y datos auxiliares).

## Requisitos

| Herramienta | Uso |
|---|---|
| R ≥ 4.x + RStudio | Flujo principal de extracción y análisis |
| QGIS | Preparación de shapefiles / centroides (módulo QGIS+R) |
| Python 3 + Jupyter | Notebook y script del producto diario |
| Panoply (opcional) | Inspección rápida de NetCDF |

**Paquetes R habituales:** `raster`, `ncdf4`, `sp`, `rgdal`, `sf`, `tidyverse` / `lubridate`, `dplyr`, `readxl`.

> Varios scripts usan APIs legacy (`rgdal`, `sp` + `raster`). Funcionan en el contexto del taller; en proyectos nuevos conviene migrar a `terra` / `sf`.

## Datos PISCO (no versionados)

Los NetCDF (`.nc`) **no están en el repositorio**. Descárgalos desde las fuentes oficiales e indícalos en cada módulo:

- PISCO (IRI / Columbia): <http://iridl.ldeo.columbia.edu/SOURCES/.SENAMHI/.HSR/.PISCO/>
- Precipitación mensual v2.1 (enlace en [`pisco/EnlacePisco.txt`](pisco/EnlacePisco.txt))
- Referencias adicionales en [`datos-pisco-qgis-r/Link.txt`](datos-pisco-qgis-r/Link.txt)

Shapefiles y Excel de ejemplo suelen venir empaquetados (`.rar`) dentro de cada carpeta.

## Módulos

| Carpeta | Qué cubre | Entrada típica |
|---|---|---|
| [`pisco/`](pisco/) | Intro: extracción puntual desde NetCDF mensual, series temporales y ajuste Gumbel | `PrecipMonthly.nc`, coordenadas Excel |
| [`piscop-daily/`](piscop-daily/) | Producto diario: extracción, series, tiempos de retorno; notebook + Python | `PrecipDialy.nc`, coordenadas |
| [`datos-pisco-qgis-r/`](datos-pisco-qgis-r/) | Flujo QGIS + R (ej. subcuencas Piura): extracción, Gumbel, tiempos de retorno | NetCDF diario, `SHP.rar`, `Excel.rar` |
| [`pisco-gemra/`](pisco-gemra/) | Precipitación media mensual a escala de cuenca (ej. Santa / GEMRA) | NetCDF mensual, `SHP.rar`, coordenadas |

### Orden sugerido

1. **`pisco/`** — pipeline base (brick NetCDF → puntos → CSV → serie → Gumbel).
2. **`piscop-daily/`** — misma lógica a resolución diaria + variantes Python/Jupyter.
3. **`datos-pisco-qgis-r/`** — integración con capas vectoriales preparadas en QGIS.
4. **`pisco-gemra/`** — agregación espacial (media areal por cuenca).

## Cómo ejecutar

1. Clona el repo y abre el `.Rproj` del módulo (o fija el directorio de trabajo a esa carpeta).
2. Descarga el NetCDF correspondiente y descomprime shapefiles/Excel si aplica.
3. Ajusta rutas: muchos scripts tienen `setwd("D:/...")` absolutas de la máquina original — **cámbialas** a tu ruta local o usa rutas relativas al proyecto.
4. Instala dependencias (`install.packages(...)` al inicio de varios scripts) y ejecuta en orden (extracción → series → Gumbel / retorno).

Estructura de trabajo habitual dentro de un módulo:

```text
ENTRADA/   # NetCDF, Excel de coordenadas, shapefiles
SALIDA/    # CSV de series extraídas y resultados
*.R        # Scripts del flujo
```

## Alcance y limitaciones

- Material de **taller / aprendizaje**, no un paquete de producción.
- Rutas absolutas y nombres de carpetas de entrada varían entre módulos; hay que alinearlas al entorno local.
- Artefactos de sesión (`.Rhistory`, `.RData`, checkpoints Jupyter, etc.) están cubiertos por el [`.gitignore`](.gitignore) de la raíz.

## Referencia

Aybar et al. (2019) — producto PISCO de precipitación:  
<https://www.tandfonline.com/doi/abs/10.1080/02626667.2019.1649411>
