---
title: "Proyecto Python + Machine Learning: Análisis Salarial"
layout: post
date: 2024-09-20 19:10
image: /assets/images/markdown.jpg
headerImage: false
tag:
- python
- machine learning,
- data science
- pandas
- scikit-learn
- análisis de datos
category: blog
author: Álvaro López Hurtado
description: Análisis sobre el salario
---

# Análisis de Salarios y Factores Relacionados con el Empleo (2020-2022)

Como el análisis de datos se ha convertido en una herramienta fundamental para la toma de decisiones en diversas áreas, hice este proyecto con el objetivo de analizar salarios y otros factores relacionados con el empleo, tomando como referencia los años 2020, 2021 y 2022. El objetivo es responder preguntas clave sobre cómo han evolucionado los salarios y las características del trabajo en este período.

## Preguntas de Investigación

Este proyecto aborda las siguientes preguntas clave:

1. **¿Cuál es el salario promedio para cada tipo de trabajo en 2020, 2021 y 2022?**
   Este análisis permitirá observar las diferencias salariales según el tipo de trabajo y cómo han cambiado a lo largo del tiempo.

2. **¿Cuántos trabajos hay por cada tamaño de empresa en 2020, 2021 y 2022?**
   Se analizará la distribución de trabajos en función del tamaño de las empresas (pequeñas, medianas y grandes), proporcionando una visión sobre cómo varía la oferta laboral según la estructura empresarial.

3. **¿Cuál es el salario máximo y mínimo para cada nivel de experiencia en 2020, 2021 y 2022?**
   Aquí se estudiará la relación entre el nivel de experiencia (junior, medio, senior, experto) y los salarios máximos y mínimos en los distintos años.

4. **¿Cuál es el salario promedio por porcentaje de trabajo remoto en 2020, 2021 y 2022?**
   Se examinará la relación entre el trabajo remoto y los salarios, evaluando cómo la creciente adopción del trabajo remoto ha afectado las compensaciones salariales.

5. **¿Cuál es el salario promedio de los trabajos por país de residencia del empleado en 2020, 2021 y 2022?**
   Este análisis se centrará en la diferencia de salarios según el país de residencia de los empleados, buscando tendencias geográficas en la compensación.

6. **¿Cuántos trabajos hay por cada nivel de experiencia (EN, MI, SE, EX) en 2020, 2021 y 2022?**
   Finalmente, se analizará cómo se distribuyen los trabajos según los niveles de experiencia a lo largo del tiempo.

## Objetivos del Proyecto

El propósito principal de este análisis es ofrecer una perspectiva clara de las tendencias salariales y laborales en los últimos tres años. En particular, buscamos:

- Visualización del salario promedio por remoto.
- Visualización del salario promedio por trabajo.

## Metodología

Utilizando técnicas de análisis de datos y visualización, este proyecto busca proporcionar respuestas basadas en datos a las preguntas planteadas. Las herramientas y métodos utilizados incluyen:

- Análisis de los datos para obtener las respuestas.
- Visualizaciones mediante gráficos para ilustrar los hallazgos.
- Técnicas de Machine Learning para profundizar en los análisis y realizar predicciones.

![Descripción de la imagen](/assets/images/PYTHON/Importacion_Librerias.png)
![Descripción de la imagen](/assets/images/PYTHON/df.png)

## Información de las Columnas

- **work_year**: El año en el que se pagó el salario.
- **experience_level**: Nivel de experiencia en el trabajo durante el año con los siguientes valores posibles:
  - **EN**: Nivel Inicial.
  - **MI**: Nivel Medio.
  - **SE**: Nivel Senior.
  - **EX**: Nivel Ejecutivo.
  - **Director**: Director.
- **employment_type**: Tipo de empleo de la función:
  - **PT**: Tiempo parcial.
  - **FT**: Tiempo completo.
  - **CT**: Contrato.
  - **FL**: Freelance.
- **job_title**: Función desempeñada durante el año.
- **salary**: Importe bruto total del salario pagado.
- **salary_currency**: Moneda en la que se pagó el salario.
- **salary_in_USD**: Salario convertido a USD (Dólar estadounidense).
- **employee_residence**: País de residencia del empleado durante el año laboral.
- **remote_ratio**: Cantidad de trabajo realizado a distancia:
  - **0**: Sin trabajo a distancia.
  - **50**: Parcialmente a distancia.
  - **100**: Totalmente a distancia.
- **company_location**: País de la oficina principal del empleador o de la sucursal.
- **company_size**: Número medio de personas que trabajan para la empresa durante el año:
  - **S**: Menos de 50 personas (pequeña).
  - **M**: Entre 50 y 250 personas (mediana).
  - **L**: Más de 250 personas (grande).

![Descripción de la imagen](/assets/images/PYTHON/df_head.png)
![Descripción de la imagen](/assets/images/PYTHON/df_describe.png)
![Descripción de la imagen](/assets/images/PYTHON/df_null_y_drop.png)

## Contestación a las preguntas

![Descripción de la imagen](/assets/images/PYTHON/1_pre.png)
![Descripción de la imagen](/assets/images/PYTHON/2_3_pre.png)
![Descripción de la imagen](/assets/images/PYTHON/4_5_pre.png)
![Descripción de la imagen](/assets/images/PYTHON/6_pre.png)

## Visualización Gráfica de Trabajos Remotos y Salarios Promedio (2020-2022)

Este gráfico mostrará los trabajos remotos y sus salarios promedio para los años 2020, 2021 y 2022. Si un trabajo no tiene datos para un año, simplemente no aparecerá una barra en ese punto, pero el resto se mantendrá agrupado por trabajo.

### Explicación del Enfoque:

- **`reset_index()`**: Para facilitar el análisis y la manipulación de los datos, se convierte la estructura de series agrupadas en DataFrames, utilizando este método.
- **Renombrar columnas**: Esto ayuda a la manipulación de los datos en etapas posteriores.
- **`concat()`**: Se utiliza para realizar el análisis comparativo entre los diferentes DataFrames y años.

![Descripción de la imagen](/assets/images/PYTHON/graf_1_1.png)
![Descripción de la imagen](/assets/images/PYTHON/graf_1_2.png)
![Descripción de la imagen](/assets/images/PYTHON/graf_1_3.png)

## Visualización Gráfica del Salario Promedio por Trabajo (2020, 2021 y 2022)

Este gráfico mostrará todos los trabajos y sus salarios promedio para los años 2020, 2021 y 2022. Si un trabajo no tiene datos para un año, simplemente no aparecerá una barra en ese punto, pero el resto se mantendrá agrupado por trabajo.

### Explicación del Enfoque:

- **trabajos_totales**: Uní los índices de los tres años para crear una lista con todos los trabajos.
- **`reindex()`**: Con la lista de trabajos_totales, hice un `reindex` a los salarios promedio para cada año, añadiendo un `NaN` a los trabajos que no están en un determinado año.
- **Ajustes en la gráfica de barras**: Desplacé las barras para mantener un ancho y posición correctos en el gráfico.

![Descripción de la imagen](/assets/images/PYTHON/graf_2_1.png)
![Descripción de la imagen](/assets/images/PYTHON/graf_2_2.png)

## Aplicación Machine Learning (employe_level)

En este apartado, se entrenará varios modelos para seleccionar el más óptimo para el aprendizaje supervisado.

![Descripción de la imagen](/assets/images/PYTHON/ML_1_1.png)
![Descripción de la imagen](/assets/images/PYTHON/ML_1_2.png)
![Descripción de la imagen](/assets/images/PYTHON/ML_1_3.png)
![Descripción de la imagen](/assets/images/PYTHON/ML_1_4.png)
![Descripción de la imagen](/assets/images/PYTHON/ML_1_5.png)
![Descripción de la imagen](/assets/images/PYTHON/ML_1_6.png)

Opté por la matriz de confusión en el árbol de decisiones porque proporciona una visión detallada de cómo el modelo clasifica cada categoría, lo que es importante para problemas de clasificación multiclase.

## Aplicación Machine Learning (salary_in_usd)

En este apartado, se entrenará varios modelos para seleccionar el más óptimo para el aprendizaje supervisado.

![Descripción de la imagen](/assets/images/PYTHON/ML_2_1.png)
![Descripción de la imagen](/assets/images/PYTHON/ML_2_2.png)
![Descripción de la imagen](/assets/images/PYTHON/ML_2_3.png)
![Descripción de la imagen](/assets/images/PYTHON/ML_2_4.png)
![Descripción de la imagen](/assets/images/PYTHON/ML_2_5.png)
![Descripción de la imagen](/assets/images/PYTHON/ML_2_7.png)
![Descripción de la imagen](/assets/images/PYTHON/ML_2_8.png)

Opté por la regresión lineal para predecir salary_in_usd debido a su simplicidad, eficiencia, capacidad para manejar relaciones lineales, interpretabilidad de los coeficientes y porque es adecuada para predecir variables continuas como los salarios.

## Conclusión

En este proyecto, he realizado un análisis del conjunto de datos para explorar las relaciones entre el salario y diversas variables, como el tipo de trabajo, el nivel de experiencia, el tamaño de la empresa, la modalidad de trabajo remoto, y el país de residencia del empleado entre los años 2020 y 2022. A través de visualizaciones detalladas y modelos predictivos, se han podido extraer conclusiones valiosas:

1. **Salario promedio por tipo de trabajo remoto**: Mostré tendencias salariales específicas, evidenciando el impacto del trabajo remoto en los salarios.

2. **Salario promedio por tipo de trabajo**: Identifiqué diferencias en los salarios promedio dependiendo del tipo de trabajo, permitiendo ver cómo ciertos roles han ganado mayor importancia y retribución en los últimos años.

3. **Modelos predictivos**: Utilicé varios modelos para comprobar cuál es el más acertado, eligiendo así:
   - **La matriz de confusión para el árbol de decisiones**: Para clasificar niveles de experiencia, mostrando un buen rendimiento en términos de precisión y recall.
   - **La regresión lineal**: Fue el más adecuado para predecir el salario en USD, ya que se trata de una variable continua.

### Anotación Importante

El CSV lo obtuve de la página web [www.Kaggle.com](https://www.kaggle.com), ayudándome así a entrenar análisis de datos. Aunque la aplicación de modelos predictivos para la primera pregunta fue satisfactoria, en la segunda no fue tanto debido a que había muchísimos datos distintos para que pudiese entrenar. Por todo lo demás, fue gratificante el proceso de análisis.
