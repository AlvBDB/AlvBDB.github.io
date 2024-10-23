---
title: "Proyecto PyMongoDB + Machine Learning: Análisis en Spotify"
layout: post
date: 2024-10-20 20:10
image: /assets/images/markdown.jpg
headerImage: false
tag:
- python
- machine learning
- mongoDB
- sql
- pymongodb
- data science
- pandas
- scikit-learn
- análisis de datos
category: blog
author: Álvaro López Hurtado
description: Análisis sobre Spotify
---

# Análisis de Salarios y Factores Relacionados con el Empleo (2020-2022)

En este proyecto, analicé las canciones más reproducidas en Spotify utilizando una base de datos almacenada en MongoDB. A través de este análisis, profundicé en las características que influyen en la popularidad de las canciones, medida por el número de streams. Respondí a las siguientes preguntas clave:

## Preguntas de Investigación

Este proyecto aborda las siguientes preguntas clave:

1. **¿Cuál es la canción más reproducida en Spotify?**
   Este análisis permite identificar la canción que ha logrado la mayor popularidad en la plataforma.

2. **¿Cuántas canciones de cada artista hay en la lista?**
   Aquí se examina la distribución de canciones por artista, lo que ayuda a entender la representación de cada uno en las listas más populares.

3. **¿Cuál es el artista con más canciones en la lista?**
   Esta pregunta busca destacar al artista más relevante en términos de cantidad de canciones en el ranking de popularidad.

4. **¿Cuáles son las canciones más "bailables"?**
   Se analizan las canciones con ritmos que invitan a bailar, proporcionando información sobre las tendencias en la música bailable.

5. **¿Qué canciones tienen la mayor "energía"?**
   Este análisis permite identificar las canciones que generan más energía y entusiasmo entre los oyentes.

6. **¿Qué canciones son más acústicas?**
   Aquí se evalúa la proporción de canciones con un estilo acústico, lo que puede reflejar preferencias en ciertos géneros musicales.

7. **¿Cuántas canciones por mes han sido lanzadas en 2023?**
   Este análisis proporciona una visión de la producción musical a lo largo del año y cómo ha evolucionado mes a mes.

8. **¿Qué relación hay entre el número de playlists y la cantidad de streams?**
   Esta pregunta busca entender si hay un vínculo entre la presencia en playlists y el número de reproducciones.

9. **¿Cuál es la canción que aparece en más playlists de Spotify?**
   Identificar la canción más incluida en playlists ofrece una perspectiva sobre su popularidad y aceptación en diversas audiencias.

10. **¿Cuál es la canción que aparece en más playlists de Apple?**
    Similar a la pregunta anterior, se analiza la presencia de canciones en playlists de Apple para comparar su popularidad en diferentes plataformas.

## Objetivos del Proyecto

El propósito principal de este análisis es ofrecer una perspectiva clara de las tendencias musicales y el comportamiento de los streams en Spotify. Para alcanzar este objetivo, se plantean los siguientes objetivos específicos:

- **Identificar la canción más reproducida:**
   Determinar cuál es la canción que ha alcanzado la mayor popularidad en la plataforma.

- **Analizar la representación de artistas:**
   Examinar cuántas canciones de cada artista están en la lista y quién es el artista con más canciones.

- **Evaluar características musicales:**
   Investigar qué canciones son más "bailables", tienen mayor "energía" o son más acústicas, proporcionando un entendimiento más profundo de las preferencias de los oyentes.

- **Examinar la producción musical:**
   Estudiar cuántas canciones han sido lanzadas mensualmente en 2023, lo que permite observar la evolución de la industria musical a lo largo del año.

- **Establecer relaciones entre variables:**
   Analizar la relación entre el número de playlists y la cantidad de streams, así como identificar las canciones más incluidas en playlists de Spotify y Apple.

## Metodología

Utilizando técnicas de análisis de datos y visualización, este proyecto busca proporcionar respuestas basadas en datos a las preguntas planteadas. Las herramientas y métodos utilizados incluyen:

- **Análisis de datos:** para obtener las respuestas a las preguntas clave planteadas.
- **Visualización de datos:** mediante gráficos para ilustrar los hallazgos de forma clara y accesible.
- **Técnicas de Machine Learning:** para profundizar en los análisis y realizar predicciones sobre la popularidad de las canciones.


## Información de la base de datos

Los datos originales provienen de un archivo CSV obtenido en la página web [Kaggle](https://www.kaggle.com), el cual fue cargado e introducido en MongoDB para su posterior análisis. A través de este análisis, profundicé en las características que influyen en la popularidad de las canciones.

![Descripción de la imagen](/assets/images/PyMongoDB/MONGO.png)
![Descripción de la imagen](/assets/images/PyMongoDB/MONGO1.png)


## Contestación a las preguntas

![Descripción de la imagen](/assets/images/PyMongoDB/1_importar.png)
![Descripción de la imagen](/assets/images/PyMongoDB/consulta_1y2.png)
![Descripción de la imagen](/assets/images/PyMongoDB/consulta_3y4.png)
![Descripción de la imagen](/assets/images/PyMongoDB/consulta_5.png)
![Descripción de la imagen](/assets/images/PyMongoDB/consulta_6.png)
![Descripción de la imagen](/assets/images/PyMongoDB/consulta_7.png)
![Descripción de la imagen](/assets/images/PyMongoDB/consulta_8.png)
![Descripción de la imagen](/assets/images/PyMongoDB/consulta_9y10.png)

## Visualización Gráfica del Top 10 Canciones con Más Visualizaciones

En este gráfico, se mostrarán las canciones con más streams, proporcionando una representación visual clara de las diez canciones más populares en la plataforma. Este análisis no solo permite identificar cuáles son las canciones más escuchadas, sino que también ofrece un contexto sobre su impacto en la audiencia. Al visualizar estos datos, se puede obtener una mejor comprensión de las preferencias musicales de los usuarios de Spotify y el éxito comercial de estas canciones.


![Descripción de la imagen](/assets/images/PyMongoDB/grafica_1.png)
![Descripción de la imagen](/assets/images/PyMongoDB/grafica_2.png)
![Descripción de la imagen](/assets/images/PyMongoDB/grafica_3.png)

## Visualización Gráfica de la Evolución de Canciones Lanzadas por Año (Tendencias)

En este gráfico, se presenta la evolución del número de canciones lanzadas por año, lo que permite observar las tendencias a lo largo del tiempo en la producción musical. Este análisis proporciona una visión clara de cómo ha cambiado la cantidad de lanzamientos en los últimos años y qué patrones emergen en la industria..

![Descripción de la imagen](/assets/images/PyMongoDB/grafico_5.png)
![Descripción de la imagen](/assets/images/PyMongoDB/grafico_6.png)

## Aplicación Machine Learning (streams)

En este apartado, emplearé el método de regresión lineal como el algoritmo principal para predecir el número de streams de las canciones en Spotify. Al implementar este enfoque, se espera obtener un modelo efectivo que ayude a predecir el éxito de las canciones en función de sus características musicales.

![Descripción de la imagen](/assets/images/PyMongoDB/ML1.png)
![Descripción de la imagen](/assets/images/PyMongoDB/ML2.png)
![Descripción de la imagen](/assets/images/PyMongoDB/MLLINEAR.png)
![Descripción de la imagen](/assets/images/PyMongoDB/MLGRAFICA.png)
![Descripción de la imagen](/assets/images/PyMongoDB/MLGRAFICA1.png)

Opté por la regresión lineal ya que una técnica de aprendizaje supervisado que se utiliza para modelar la relación entre una variable dependiente y una o más variables independientes



## Conclusión

En este proyecto, he realizado un análisis del conjunto de datos de las canciones más reproducidas en las plataformas de streaming, explorando la relación entre diversas características como el número de streams, la bailabilidad de las canciones, la popularidad en playlists, y el lanzamiento por meses durante el año 2023. A través de consultas eficientes en MongoDB ,con su respectiva API de Python, y visualizaciones detalladas, se han obtenido insights valiosos para la industria musical

Esto ayuda a entender las dinámicas detrás de la popularidad de las canciones en plataformas de streaming, sino que también ofrece un enfoque práctico para aplicar técnicas de MongoDB y análisis de datos, preparando una base sólida para trabajos futuros en análisis de bases de datos musicales.

