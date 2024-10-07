# Introducción.

Se realiza captura de fuentes de datos para realizar diferentes modelos de aprendizaje. 

Este proyecto captura y utiliza diversas fuentes de datos para desarrollar modelos de aprendizaje automático enfocados en la predicción de biomasa aérea (AGB) en áreas geográficas.

Se implementan técnicas como la Regresión Lineal, Random Forest y XGBoost, evaluando la precisión mediante métricas como el MSE y R². Adicionalmente, se visualizan predicciones de biomasa dentro de un polígono geoespacial, y se aplican técnicas de agrupamiento K-Means para calcular biomasa y carbono por parcela, brindando un enfoque integral en la gestión de biomasa forestal.

## Estructura del Proyecto

El repositorio contiene notebooks Jupyter desarrollados en Google Colab para el análisis y modelado de datos:

**Carpeta 1: Datos**

Notebooks para preprocesamiento de datos y generación de características.

**Carpeta 2: Machine Learning**

Notebooks para la implementación de modelos de machine learning (Regresión Lineal, Random Forest, XGBoost) y la predicción de biomasa.

Cada notebook puede ser ejecutado directamente en Google Colab, asegurando que las dependencias necesarias estén instaladas previamente.

### **Carpeta 1: Datos**

**Multidatos.ipynb**
  
Este notebook está diseñado para la captura y análisis de datos de dispositivos, con especial enfoque en parámetros como temperatura y humedad. Se manipulan datos de   diferentes dispositivos, almacenados en un DataFrame, y se realiza un análisis exploratorio.

El archivo **Multidatos.ipynb** realiza las siguientes acciones:

1. **Conexión a varias fuentes de datos:**
   - **Oracle**: Para obtener imágenes almacenadas en una base de datos.
   - **KoboToolbox**: Para consultar datos de ubicación (GPS) relacionados con encuestas o análisis de campo.
   - **IoT | AWS**: Para recuperar datos de dispositivos IoT almacenados en un bucket S3 en AWS, principalmente relacionados con la temperatura y la humedad.

2. **Instalación de dependencias**: Asegura que se instalen las librerías necesarias para el procesamiento y la visualización de los datos, como `rasterio`, `SQLAlchemy`, `geopandas`, `folium`, y `boto3`.

3. **Consulta y visualización de datos**:
   - **Base de datos Oracle**: Consulta imágenes anteriores y posteriores almacenadas en la base de datos.
   - **KoboToolbox**: Recupera datos de GPS y los filtra, mostrando ubicaciones precisas y realizando una consulta a una API para obtener datos catastrales y polígonos asociados a cada coordenada.
   - **IoT | AWS**: Consulta dispositivos en AWS para recuperar valores de temperatura y humedad, transformando los datos y formateando fechas y horas para su análisis.

4. **Visualización**: 
   - Muestra un mapa interactivo con las coordenadas de ubicación y los polígonos asociados, marcando los puntos GPS obtenidos de KoboToolbox.
   - Muestra los tres DataFrames resultantes: Oracle, KoboToolbox, y AWS IoT.


**Ejecuta este notebook en Google Colab**:  
<a href="https://colab.research.google.com/github/fabianhuertas1992/DatosML/blob/main/Datos/Multidatos.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

----------

2. **Query_DB.ipynb**  
   Este notebook realiza consultas a múltiples bases de datos (Oracle, KoboToolbox, IoT a través de AWS) y procesa las respuestas para generar datasets y visualizaciones. También se aplican modelos de aprendizaje para realizar análisis y simulaciones de los datos obtenidos. 

   **Funcionalidades principales:**
   - **Oracle**: Consulta datos de imágenes y NDVI a través de un sistema de base de datos, procesando los resultados para crear visualizaciones y estadísticas sobre vegetación y análisis geoespacial.
   - **KoboToolbox**: Recupera datos de geolocalización para su análisis y visualización en un mapa con datos catastrales de parcelas.
   - **IoT | AWS**: Consulta dispositivos IoT que registran valores de temperatura y humedad, almacena los datos en S3 y los procesa para obtener estadísticas y gráficos de estos valores por dispositivo.

   **Visualizaciones**:
   - Mapa interactivo con datos catastrales y ubicaciones GPS.
   - Gráficos de barras y de calor para mostrar la distribución de temperatura y humedad de los dispositivos.
   - Gráfico 3D interactivo que visualiza los datos de temperatura y humedad por dispositivo.
   - Simulación de temperaturas a lo largo del tiempo con gráficos de tendencias.

   **Ejecuta este notebook en Google Colab**:  
   <a href="https://colab.research.google.com/github/fabianhuertas1992/DatosML/blob/main/Datos/Query_DB.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

-----------------------------------------------------------------------------------------------------------

### **Carpeta 2: Machine Learning**

Esta carpeta contiene notebooks que implementan y comparan diferentes modelos de machine learning para predecir la biomasa aérea (AGB) en Mg/ha. Los modelos evaluados incluyen **Regresión Lineal**, **Random Forest** y **XGBoost**. A continuación, se detallan los contenidos de cada archivo en esta carpeta:

1. **Modelo_ML.ipynb**  
   Este notebook se enfoca en la **extracción, transformación y carga de datos (ETL)** desde diversas fuentes, incluyendo **KoboToolbox**. Después de procesar los datos, se entrenan diferentes modelos de machine learning para predecir la biomasa en función de variables como el NDVI, el diámetro a la altura del pecho (DAP) y la altura de los árboles.  
   **Principales características**:
   - Procesamiento de datos desde KoboToolbox.
   - Comparación inicial de modelos de aprendizaje automático.
   
   **Ejecuta este notebook en Google Colab**:  
   <a href="https://colab.research.google.com/github/fabianhuertas1992/DatosML/blob/main/Machine%20Learning/Modelo_ML.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

2. **ML_comparativos.ipynb**  
   Este notebook implementa una **comparación detallada de tres modelos de machine learning** (Regresión Lineal, Random Forest y XGBoost) para predecir la biomasa en Mg/ha.  
   **Características del notebook**:
   - **Carga y preprocesamiento** de datos: Se eliminan valores nulos y se generan nuevas características como NDVI_DAP y HT_NDVI.
   - **Selección de características clave**: NDVI, DAP, altura, NDVI_DAP y HT_NDVI.
   - **Comparación de modelos**: Se evalúan los modelos utilizando **MSE** y **R²**, con visualizaciones gráficas que muestran las diferencias entre las predicciones y los valores reales de biomasa.
   - **Conclusiones**: Se visualiza cómo cada modelo captura la relación entre las características y la biomasa.

   **Ejecuta este notebook en Google Colab**:  
   <a href="https://colab.research.google.com/github/fabianhuertas1992/DatosML/blob/main/Machine%20Learning/ML_comparativos.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

3. **ML_Parcelas.ipynb**  
   Este notebook realiza el entrenamiento de modelos agrupando los datos por parcelas, lo que permite observar la **variabilidad espacial** en las predicciones de biomasa.  
   **Aspectos clave**:
   - **Agrupación de datos por parcelas**: Permite que los modelos enfoquen el análisis en áreas específicas.
   - **Modelos utilizados**: Se implementan **Regresión Lineal**, **Random Forest** y **XGBoost**.
   - **Evaluación de rendimiento**: Se evalúan los modelos con métricas como **R²** y **MSE**.
   - **Visualización de resultados**: Los valores predichos por cada modelo se comparan gráficamente con los valores reales de biomasa.

   **Ejecuta este notebook en Google Colab**:  
   <a href="https://colab.research.google.com/github/fabianhuertas1992/DatosML/blob/main/Machine%20Learning/ML_Parcelas.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

4. **ML_Parcelas(entrenamiento).ipynb**  
   Similar al notebook **ML_Parcelas.ipynb**, este archivo entrena modelos de machine learning para predecir la biomasa en función de características como NDVI, DAP y altura de los árboles, pero se enfoca más en el proceso de entrenamiento.  
   **Aspectos clave**:
   - **Problemas en los datos**: Se concluye que los datos actuales no son suficientes para obtener predicciones precisas, lo que sugiere la necesidad de más datos o mejores técnicas de preprocesamiento.
   - **Comparación entre modelos**: Al igual que en otros notebooks, se utilizan **XGBoost**, **Random Forest** y **Regresión Lineal**.

   **Ejecuta este notebook en Google Colab**:  
   <a href="https://colab.research.google.com/github/fabianhuertas1992/DatosML/blob/main/Machine%20Learning/ML_Parcelas(entrenamiento).ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

---




