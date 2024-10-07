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

### **Datos**

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

---

  
