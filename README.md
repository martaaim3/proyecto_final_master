
# Análisis de Ventas y Desarrollo Mundial
## Proyecto Final Máster - Análisis de Datos

Este proyecto tiene como objetivo analizar y relacionar datos de ventas online con indicadores socioeconómicos globales (PIB per cápita y tasa de desempleo) para obtener insights de negocio y desarrollar un dashboard interactivo en Power BI.

## Objetivos
- Realizar una **limpieza y transformación exhaustiva** de dos datasets independientes:
  - **Ecommerce (Online Retail)**: transacciones de ventas.
  - **World Development Indicators (WDI)**: indicadores económicos por país.
- Unir ambos conjuntos de datos creando un dataset enriquecido.
- Cumplir requisitos mínimos: **>50.000 filas y 20 columnas**.
- Realizar un análisis descriptivo y estadístico.
- Diseñar un dashboard interactivo en **Power BI** que permita explorar las relaciones entre indicadores y ventas.

## Datos originales

Por limitaciones de GitHub (archivos >100MB), el dataset `Indicators.csv` necesario para reproducir el proyecto se encuentra disponible en una Release.

➡ Puedes descargarlo desde aquí:

[** Descargar Indicators.csv desde la Release**](https://github.com/martaaim3/proyecto_final_master/releases/tag/v1.0-datos)

## Estructura del proyecto
 proyecto_final_master
┣  dashboard
┃ ┗  dashboard.pbix
┣  datos
┃ ┣  ecommerce_original.csv
┃ ┣  indicators_original.csv
┃ ┣  ecommerce_limpio.csv
┃ ┣  indicators_limpio.csv
┃ ┗  ecommerce_indicators_final.csv
┣  informe final
┃ ┗  informe_proyecto_final.pdf
┣  python
┃ ┣  eda.ipynb
┃ ┗  pipeline_limpieza_merge.ipynb
┣  README.md
┣  .gitignore



## Proceso seguido

### Importación y exploración inicial
- Se cargaron ambos datasets en **Python (pandas)**.
- Se exploraron dimensiones, tipos de datos, nulos y valores extremos.

Limpieza y transformación individual

Dataset Ecommerce:
--Eliminación de filas con valores negativos y nulos.
--Creación de columnas derivadas:
--TotalSales = Quantity * UnitPrice
--Year, Month, Day, Weekday
--Indicadores como IsWeekend e IsHighValue
--DescriptionLength, Qty_x_Price, Qty_Squared, Log_UnitPrice, etc.

Dataset WDI:
--Selección de indicadores clave (GDP_per_capita y Unemployment_rate).
--Transformación con melt y pivot para tener una fila por país y año.

Unión de los dos datasets
--Se realizó un merge entre ecommerce e indicadores usando Country y Year.
--Resultado final: 401.604 filas y +20 columnas, garantizando los requisitos del máster.

Análisis descriptivo y estadístico
--Generación de describe() para métricas como TotalSales, GDP_per_capita o AvgTicket.

Cálculo de correlaciones:
GDP_per_capita vs TotalSales

Gráficos exploratorios con seaborn/matplotlib:
--Histogramas de distribución de TotalSales y GDP_per_capita.
--Boxplots por país.

Dashboard en Power BI
KPIs:
-- Ticket medio ≈ 373 €
-- Total ventas ≈ 8 millones €

Visualizaciones clave:
--Diagrama de dispersión: PIB per cápita vs ticket medio (tamaño según ventas).
--Gráfico lineal: evolución mensual de ventas totales por país.

Filtros interactivos:
--Slicers de Country, Year e TotalSales.

Autora: Marta Ibáñez Marco
