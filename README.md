# Data Science I – Casos de dengue en CABA (2024–2025)

Análisis exploratorio de los casos confirmados de dengue en la Ciudad Autónoma de Buenos Aires durante la temporada 2024–2025, con datos abiertos del Gobierno de la Ciudad.

## Preguntas

1. ¿Cómo evolucionaron los casos a lo largo del tiempo? ¿Hay estacionalidad?
2. ¿Qué comunas fueron las más afectadas?
3. ¿Cómo se distribuyen los casos por grupo de edad?

## Datos

`casos_dengue` (CSV separado por `;`): un registro por semana epidemiológica, grupo etario y comuna.

| Columna | Descripción |
|---|---|
| `ano`, `semana_epidemiologica` | Año y semana epidemiológica |
| `fecha_inicio_semana_epidemiologica` | Fecha de inicio de la semana (d/m/aaaa) |
| `grupo_etario` | Rango de edad (`20 a 29`, …) |
| `departamento_residencia` | Comuna de residencia |
| `n_confirmados` | Casos confirmados |

Hay valores `SIN DATO` en grupo etario y comuna; se excluyen en los gráficos que usan esas columnas.

## Qué se hizo

- **Limpieza:** conteo de valores faltantes (`SIN DATO`) y conversión de tipos.
- **Visualizaciones** (Matplotlib y Seaborn):
  - evolución semanal de casos confirmados,
  - casos por comuna,
  - casos por grupo de edad.
- **Modelo exploratorio:** regresión lineal (scikit-learn) para estimar casos por semana, con selección de variables por *SequentialFeatureSelector* y codificación one-hot.

## Resultados

- El brote empezó en la **semana 41 de 2024** (octubre) y tuvo su **pico en la semana 14 de 2025** (fines de marzo), lo que confirma la estacionalidad del dengue hacia el final del verano.
- La **Comuna 11** concentró la mayor cantidad de casos, muy por encima del resto.
- La mayor carga de casos está en adultos jóvenes y de mediana edad.
- La regresión lineal **no logró predecir** los casos (R² ≈ 0): con un solo brote y pocas filas con casos no alcanza. Para un modelo predictivo harían falta varias temporadas y variables climáticas (temperatura, lluvias).

## Archivos

- `ProyectoDS_ParteI_Siciliano.ipynb`: primera entrega (análisis exploratorio).
- `ProyectoDS_ParteIII_Siciliano.ipynb`: entrega final (análisis exploratorio + modelo).
- `casos_dengue`: datos.

## Cómo ejecutarlo

1. Abrí el notebook en Google Colab (botón *Open in Colab* al inicio).
2. Subí `casos_dengue` a tu Google Drive como `Colab Notebooks/casos_dengue.csv`, o cambiá la ruta del `read_csv`.
3. Ejecutá las celdas en orden.

**Herramientas:** Python, Pandas, Matplotlib, Seaborn, scikit-learn, Google Colab.
