# TP-Labo-ElNiño-2C2026

Trabajo práctico grupal de **Laboratorio de Métodos Cuantitativos** (FCE-UBA, 2.º cuatrimestre de 2026).

El trabajo estudia la asociación entre las fases de El Niño–Oscilación del Sur (ENOS), medidas con el índice RONI de la NOAA, y la frecuencia y simultaneidad de las precipitaciones mensuales excepcionalmente altas en 20 estaciones meteorológicas del Litoral argentino (Formosa, Chaco, Misiones, Corrientes, Entre Ríos y Santa Fe) durante 1991–2025.

## Integrantes

| Nombre y apellido | N.º de registro | Usuario de GitHub |
|---|---|---|
| Abril Palavecino | 921633 | @Abrilpalavecino28 |
| Alejandro Puglisi | 921413 | @afpuglisi |
| Florencia Larrinaga | 921742 | @Florlarrinaga22 |
| Jorge Delgado | 921415 | @enrique20delgado-create |
| Marco Rojas | 921753 | @MarcoRojas96 |

## Entregables

| Parte | Archivo o link |
|---|---|
| 1. Análisis en Python (Colab) | [`Notebook/Ds_Enso.ipynb`](Notebook/Ds_Enso.ipynb) (ejecutado) |
| 2. Informe académico (LaTeX) | [`Informe/informe_enso_litoral.pdf`](Informe/informe_enso_litoral.pdf) · [Proyecto en Overleaf](https://www.overleaf.com/project/6ae93083856526b7c6483d93/share#c4e52e0b6e3651fc3ee54d3b1bd0317de332fbd7173a5312) |
| 3. Presentación | [`presentacion/presentacion_enso.html`](Presentacion/presentacion_enso.html) · [Ver en línea](https://enrique20delgado-create.github.io/TP-Labo-ElNino-2C2026/Presentacion/presentacion_enso.html) |

## Preguntas de investigación

- **Principal:** ¿Qué relación existe entre las fases del ENOS y la frecuencia y simultaneidad de precipitaciones mensuales excepcionalmente altas en el Litoral argentino durante 1991–2025?
- **Secundaria:** ¿Existe variación de esa asociación según la estación del año y el período analizado?
- **Aplicada:** ¿La información previa del ENOS permite mejorar la predicción de meses con precipitaciones excepcionales respecto de una referencia climatológica?

## Principales resultados

- Una precipitación mensual se considera **excepcional** cuando supera el percentil 90 (P90) de su estación y mes calendario.
- Con El Niño, el 16,4 % de las observaciones superó el P90, contra el 10,9 % en Neutral y el 8,5 % en La Niña. El Niño se diferencia significativamente de las otras dos fases, mientras que Neutral y La Niña no difieren entre sí (regresión con errores HAC).
- Con El Niño también es más común que los extremos ocurran en muchas estaciones a la vez: el 28,2 % de los meses tuvo al menos un cuarto de las estaciones sobre su P90, contra el 11,4 % en La Niña.
- No hay evidencia significativa de que la asociación cambie según la estación del año o el quinquenio.
- Usar la fase ENOS de dos meses antes reduce apenas un 2,8 % el error de estimación (Brier score) respecto de la climatología, y la mejora desaparece con otros rezagos.

## Estructura del repositorio

```
├── README.md
├── Notebook/
│   └── Ds_Enso.ipynb                  # análisis completo, ejecutado
├── DF/
│   ├── smn_datos_meteorologicos_1991_2020.xlsx   # versionado con Git LFS
│   ├── smn_datos_meteorologicos_desde_2021_con_nasa.csv
│   ├── smn_estaciones_meteorologicas21-26.xlsx
│   ├── indices_enso_noaa_pacifico.csv
│   └── INDEC_precipitaciones_2010_2024_colab.xlsx
├── Graficos/                          # PNG exportados con plt.savefig()
├── Informe/
│   └── informe_enso_litoral.pdf
└── Presentacion/
    └── presentacion_enso.html
```

## Datos y fuentes

| Archivo | Contenido | Fuente |
|---|---|---|
| `smn_datos_meteorologicos_1991_2020.xlsx` | Precipitación diaria por estación, 1991–2020 | Servicio Meteorológico Nacional (SMN) |
| `smn_datos_meteorologicos_desde_2021_con_nasa.csv` | Precipitación diaria por estación, 2021–2026 | SMN |
| `smn_estaciones_meteorologicas21-26.xlsx` | Catálogo de estaciones (provincia, ubicación) | SMN |
| `indices_enso_noaa_pacifico.csv` | Índices ENOS mensuales (RONI y ONI) | NOAA Climate Prediction Center |
| `INDEC_precipitaciones_2010_2024_colab.xlsx` | Precipitación mensual por estación, usada para validar | INDEC |

**Archivo grande:** `smn_datos_meteorologicos_1991_2020.xlsx` (72 MB) está versionado con [Git LFS](https://git-lfs.com/) (ver `.gitattributes`). El notebook lo lee por URL sin pasos adicionales, y también se descarga normalmente desde la web de GitHub. Si se clona el repositorio, hay que tener Git LFS instalado (`git lfs install`) para bajar el archivo real y no solo el puntero.

## Cómo reproducir el análisis

1. Abrir `Notebook/Ds_Enso.ipynb` en Google Colab.
2. Ir a **Entorno de ejecución → Reiniciar sesión y ejecutar todo**. No hace falta subir archivos: el notebook lee los datasets directamente desde la carpeta `DF/` de este repositorio por URL:
   ```python
   URL = "https://github.com/enrique20delgado-create/TP-Labo-ElNino-2C2026/raw/refs/heads/main/DF/"
   ```
   Por eso el repositorio tiene que ser público y los archivos tienen que mantener su nombre y ubicación en `DF/`.
3. Los gráficos se exportan como PNG en el entorno de Colab.

Librerías utilizadas: pandas, NumPy, Matplotlib, seaborn, SciPy, statsmodels y scikit-learn.

## Uso de inteligencia artificial

Se usaron asistentes de IA (Claude y ChatGPT) en proyectos con contexto enriquecido para proponer gráficos, desarrollar y depurar código, sugerir pruebas estadísticas y redactar el informe y la presentación. Los prompts utilizados están documentados en el notebook, antes de cada bloque de código. Todos los resultados se validaron volviendo a ejecutar el notebook.
