# README: PROYECTO TFM: CLUSTERIZACIÓN DE RUTAS DE TRANSPORTE

## 1) RESUMEN EXPLICATIVO DEL PROYECTO

- **Business Description:** optimizar recursos destinados al reparto de mercancías de última milla (urbanos). Problema del Vendedor Viajero

- **Objetivo:** que el usuario pueda interactuar con las rutas generadas tras el proceso de optimización y clusterización. DIcho proceso es llevado a cabo tras un proceso de estructuración de datos, llamadas a la API de Google (servicios de Google Maps) y aplicación de los algoritmos diseñados al efecto
      
- **Modelos presentados:** 2 modelos diferentes basados en diferentes formas de aplicar la clusterización en función de la llamada a la API de Google

- **Variables optimización:** las variables seleccionadas para optimizar las rutas de transporte consisten en:
       - Distancia de la ruta
       - Duración de la ruta 
       - Duración de la ruta con tráfico
 
- **Explicación:** en el transcurso de la visualización de los modelos expuestos en los notebooks, he puesto énfasis en la fácil comprensión mediante una documentación exhaustiva de las decisiones llevadas a cabo; los cuales son tomadas sobre las necesidades reales del objetivo a cumplir y el correcto desarrollo del TFM 

## 2) REQUERIMIENTOS BÁSICOS

- Python 3.0 
- Google Maps API key
- Tableau Desktop
- Microsoft Excel
- Jupyter Notebook

### API keys

Cada llamada a Google Maps Web Service requiere de una **API key** o cliente ID. Las API keys se consiguen con una cuenta de Google en el siguiente enlace *https://developers.google.com/console*

Con la cuenta de Google se generan **Proyectos** en los que visualizar desde la facturación de los servicios solicitados a google hasta las modificaciones necesarias para conseguir el modelo que se necesite. El mío se llama "Clustering Deliveries"

Para conseguir una API key: una vez logueados selecciona un proyecto abierto o crea uno nuevo y activa la API deseada. Esta API tiene la función de API server la cual incluye llamadas a diferentes serivicios (geocoding, distance matrix,elevation API...), las cuales son individuales y deberán ser activadas según se necesite

Es aconsejable seguir las recomendaciones de seguridad y restricciones que aconseja Google, relativas sobre todo a la guarda de esta API key. Asímismo prestar mucha atención a las tarifas para que no haya sorpresas en la facturación

### Tableau Desktop

Este conocido programa de Visualización presenta una versión **Tableau Public** sin coste alguno, en el cual se puede desarrollar proyectos con la condición de estar abiertos al público, así como de tener ciertas limitaciones técnicas.

En mi caso recominedo, si eres estudiante, solicitar la licencia de 1 año e instalar **Tableau Desktop** aunque sino lo eres existe la prueba gratuíta de 14 días 

## 3) LIBRERÍAS 

- numpy
- pandas
- matplotlib
- datetime 
- math
- googlemaps
- geopandas
- descartes

### Libreria Googlemaps para python

#### Instalación

$ pip install -U googlemaps
#### The Python Client for Google Maps Services accede a las siguientes APIs de Google (Las marcadas en negrita serán las de uso de este TFM):

- Directions API
- **Distance Matrix API**
- Elevation API
- **Geocoding API**
- Geolocation API
- Places API
- Roads API
- Time Zone API

Recuerda que solo se necesita una API key, pero hay que habilitar en el código todas los servicios (single key) que sean necesarias. Para más información mira la guí de API keys

### Librería Geopandas y Descartes

#### Instalación

GEOPANDAS
- ! pip install geopandas

DESCARTES: necesario para poder plotear un geopanda
- ! pip install descartes


**NOTA:** El algoritmo de clusterización no se basa en ninguna librería existente. Los modelos tienen los algoritmos creados al efecto siguiendo las necesidades reales del problema a tratar

## 4) MANIFIESTO DE ARCHIVOS

En este ejercicio se verán, como adelanté en el resumen explciativo, dos modelos con la misma finalidad y diferente metodología. Ambos requerirán las mismas librerías, con la diferencia de que el modelo escogido será el que requiera las librerías de visualización, descartando por ello el uso de dichas librerías para el otro modelo

#### 1) Modelo_1.ypinb
Modelos de Clusteres fragmentados a los que aplicar un linkage de 1º y 2º grado (explicado sobre el desarrollo del modelo)
#### 2) Modelo_2.ypinb
Modelo de Optimización sobre la bbdd  a la que se aplica el algoritmo de clusterización creado a tal efecto
#### 3) info_tfm.py
Archivo importado para la llamda de la API, creado por motivos de seguridad en el uso de la API. Este archivo se pasa al examinador por correo para mayor seguridad
#### 4) final_document.xls
Archivo que contiene la base de datos final, necesaria para aplicar la visualización. Contempla los datos necesarios para el usuario
#### 5) tableau_final_document.twb
Archivo de Tableau con la visualiación interactiva por la cual el usuario podrá guiarse 
#### 6) tableau_final_document.twbx
Archivo empaquetado de tableau. Sirve para visulizar el contenido sin tener acceso a la base de datos. En este caso nuestro archivo excel
