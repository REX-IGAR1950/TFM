{
 "cells": [
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# README:  PROYECTO TFM: CLUSTERIZACIÓN DE RUTAS DE TRANSPORTE"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## 1) RESUMEN EXPLICATIVO DEL PROYECTO\n",
    "\n",
    "- **Business Description:** optimizar recursos destinados al reparto de mercancías de última milla (urbanos). Problema del Vendedor Viajero\n",
    "\n",
    "- **Objetivo:** que el usuario pueda interactuar con las rutas generadas tras el proceso de optimización y clusterización. DIcho proceso es llevado a cabo tras un proceso de estructuración de datos, llamadas a la API de Google (servicios de Google Maps) y aplicación de los algoritmos diseñados al efecto\n",
    "      \n",
    "- **Modelos presentados:** 2 modelos diferentes basados en diferentes formas de aplicar la clusterización en función de la llamada a la API de Google\n",
    "\n",
    "- **Variables optimización:** las variables seleccionadas para optimizar las rutas de transporte consisten en:\n",
    "       - Distancia de la ruta\n",
    "       - Duración de la ruta \n",
    "       - Duración de la ruta con tráfico\n",
    " \n",
    "- **Explicación:** en el transcurso de la visualización de los modelos expuestos en los notebooks, he puesto énfasis en la fácil comprensión mediante una documentación exhaustiva de las decisiones llevadas a cabo; los cuales son tomadas sobre las necesidades reales del objetivo a cumplir y el correcto desarrollo del TFM "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## 2) REQUERIMIENTOS BÁSICOS\n",
    "\n",
    "- Python 3.0 \n",
    "- Google Maps API key\n",
    "- Tableau Desktop\n",
    "- Microsoft Excel\n",
    "- Jupyter Notebook\n",
    "\n",
    "### API keys\n",
    "\n",
    "Cada llamada a Google Maps Web Service requiere de una **API key** o cliente ID. Las API keys se consiguen con una cuenta de Google en el siguiente enlace *https://developers.google.com/console*\n",
    "\n",
    "Con la cuenta de Google se generan **Proyectos** en los que visualizar desde la facturación de los servicios solicitados a google hasta las modificaciones necesarias para conseguir el modelo que se necesite. El mío se llama \"Clustering Deliveries\"\n",
    "\n",
    "Para conseguir una API key: una vez logueados selecciona un proyecto abierto o crea uno nuevo y activa la API deseada. Esta API tiene la función de API server la cual incluye llamadas a diferentes serivicios (geocoding, distance matrix,elevation API...), las cuales son individuales y deberán ser activadas según se necesite\n",
    "\n",
    "Es aconsejable seguir las recomendaciones de seguridad y restricciones que aconseja Google, relativas sobre todo a la guarda de esta API key. Asímismo prestar mucha atención a las tarifas para que no haya sorpresas en la facturación\n",
    "\n",
    "### Tableau Desktop\n",
    "\n",
    "Este conocido programa de Visualización presenta una versión **Tableau Public** sin coste alguno, en el cual se puede desarrollar proyectos con la condición de estar abiertos al público, así como de tener ciertas limitaciones técnicas.\n",
    "\n",
    "En mi caso recominedo, si eres estudiante, solicitar la licencia de 1 año e instalar **Tableau Desktop** aunque sino lo eres existe la prueba gratuíta de 14 días "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## 3) LIBRERÍAS \n",
    "\n",
    "- numpy\n",
    "- pandas\n",
    "- matplotlib\n",
    "- datetime \n",
    "- math\n",
    "- googlemaps\n",
    "- geopandas\n",
    "- descartes\n",
    "\n",
    "### Libreria Googlemaps para python\n",
    "\n",
    "#### Instalación\n",
    "\n",
    "$ pip install -U googlemaps\n",
    "#### The Python Client for Google Maps Services accede a las siguientes APIs de Google (Las marcadas en negrita serán las de uso de este TFM):\n",
    "\n",
    "- Directions API\n",
    "- **Distance Matrix API**\n",
    "- Elevation API\n",
    "- **Geocoding API**\n",
    "- Geolocation API\n",
    "- Places API\n",
    "- Roads API\n",
    "- Time Zone API\n",
    "\n",
    "Recuerda que solo se necesita una API key, pero hay que habilitar en el código todas los servicios (single key) que sean necesarias. Para más información mira la guí de API keys\n",
    "\n",
    "### Librería Geopandas y Descartes\n",
    "\n",
    "#### Instalación\n",
    "\n",
    "GEOPANDAS\n",
    "- ! pip install geopandas\n",
    "\n",
    "DESCARTES: necesario para poder plotear un geopanda\n",
    "- ! pip install descartes\n",
    "\n",
    "\n",
    "**NOTA:** El algoritmo de clusterización no se basa en ninguna librería existente. Los modelos tienen los algoritmos creados al efecto siguiendo las necesidades reales del problema a tratar"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## 4) MANIFIESTO DE ARCHIVOS\n",
    "\n",
    "En este ejercicio se verán, como adelanté en el resumen explciativo, dos modelos con la misma finalidad y diferente metodología. Ambos requerirán las mismas librerías, con la diferencia de que el modelo escogido será el que requiera las librerías de visualización, descartando por ello el uso de dichas librerías para el otro modelo\n",
    "\n",
    "#### 1) Modelo_1.ypinb\n",
    "Modelos de Clusteres fragmentados a los que aplicar un linkage de 1º y 2º grado (explicado sobre el desarrollo del modelo)\n",
    "#### 2) Modelo_2.ypinb\n",
    "Modelo de Optimización sobre la bbdd  a la que se aplica el algoritmo de clusterización creado a tal efecto\n",
    "#### 3) info_tfm.py\n",
    "Archivo importado para la llamda de la API, creado por motivos de seguridad en el uso de la API. Este archivo se pasa al examinador por correo para mayor seguridad\n",
    "#### 4) final_document.xls\n",
    "Archivo que contiene la base de datos final, necesaria para aplicar la visualización. Contempla los datos necesarios para el usuario\n",
    "#### 5) tableau_final_document.twb\n",
    "Archivo de Tableau con la visualiación interactiva por la cual el usuario podrá guiarse \n",
    "#### 6) tableau_final_document.twbx\n",
    "Archivo empaquetado de tableau. Sirve para visulizar el contenido sin tener acceso a la base de datos. En este caso nuestro archivo excel"
   ]
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.6.5"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 2
}
