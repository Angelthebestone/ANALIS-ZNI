# ANALISIS ZNI — Instrucciones para Claude

## Descripción del Proyecto

Proyecto de grado universitario que analiza el estado del servicio de energía eléctrica en las **Zonas No Interconectadas (ZNI)** de Colombia. Combina datos de cobertura, localidades y prestación del servicio para análisis exploratorio.

## Estructura del Repositorio

```
ANALISIS ZNI/
├── NOTEBOOKS/
│   └── ANALISIS ZNI.ipynb      # Notebook principal de análisis
├── DATASETS/
│   ├── DIVIPOLA_-_Códigos_cabeceras_-_Centros_poblados_20260126.csv
│   ├── Estado_de_la_prestación_del_servicio_de_energía_en_Zonas_No_Interconectadas_20260122.csv
│   ├── Anexo_ICEE_2023_dpto_mpio.xlsx
│   ├── Anexos_PIEC.xlsx
│   ├── Proyectos generación de energía.csv
│   ├── comunidades_energeticas_postuladas.csv
│   ├── proyectos_6GW.csv
│   └── Índice de Cobertura de Energía Eléctrica Nacional Histórico.csv
├── entornoZNI/                 # Entorno virtual Python
└── README.md
```

## Entorno de Desarrollo

- **Plataforma:** Windows 11
- **Lenguaje:** Python 3 (Jupyter Notebook / ipykernel)
- **Entorno virtual:** `entornoZNI/` (activar con `entornoZNI\Scripts\activate`)
- **Librerías principales:** pandas, numpy, matplotlib, datetime, unicodedata

## Notebook Principal — Estructura

| Sección | Descripción |
|---------|-------------|
| 1. Configuración | Imports, rutas (URLs), funciones auxiliares |
| 2. Carga de datos | Lectura de los 3 datasets principales |
| 3. Limpieza | DIVIPOLA, ZNI, ICEE Municipal por separado |
| 4. Integración | Merge ZNI-DIVIPOLA y filtrado de ICEE |
| 5. Análisis Exploratorio | Gráficas y estadísticas |
| 6. Exportación | Guardado de resultados |

## DataFrames Clave

| Variable | Fuente | Descripción |
|----------|--------|-------------|
| `df_localidades` | DIVIPOLA CSV | Códigos de cabeceras y centros poblados |
| `df_ZNI` | ZNI CSV | Estado de prestación del servicio en ZNI |
| `df_ICEE_municipios` | ICEE xlsx | Índice de Cobertura Eléctrica municipal 2023 |
| `df_ZNI_limpio` | (derivado) | ZNI después del proceso de limpieza |

## Convenciones

- **Idioma:** Todo el código, comentarios y commits están en **español**
- **Rutas:** Los `URL1`, `URL2`, `URL3` están definidos en la celda 5 del notebook con rutas absolutas de Windows
- **Encoding:** Los archivos CSV usan caracteres especiales (tildes, ñ); tener cuidado con el encoding al leer
- **Commits:** Mensajes descriptivos en español, sin `--no-verify`

## Notas Importantes

- La celda de carga de DIVIPOLA hace `.drop(2)` porque la fila 2 tiene doble coma
- El CSV de ZNI usa `decimal=','` y `thousands='.'` (formato europeo/colombiano)
- Las rutas están hardcodeadas para `C:/Users/Lenovo/Desktop/ANALISIS ZNI/` — no mover la carpeta
- El proyecto usa Git LFS para archivos pesados (xlsx)
- No hay tests automatizados; la validación es visual dentro del notebook
