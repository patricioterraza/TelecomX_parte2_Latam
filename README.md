# Análisis y Predicción de Cancelación de Clientes (Churn) 📈📉

## Resumen del Proyecto 📝

Este proyecto tiene como objetivo principal identificar los factores clave que influyen en la cancelación de clientes (churn) y desarrollar modelos predictivos para anticipar este comportamiento. A través de un análisis exploratorio de datos, preparación de la base de datos y la construcción de modelos de Machine Learning, hemos logrado extraer información valiosa para proponer estrategias de retención efectivas.

---

## Tareas Realizadas ✅

A continuación se detallan las principales etapas y tareas completadas en este proyecto:

### 1. Exploración y Preparación de Datos 📊🧹

* **Análisis Inicial:** Se cargó el conjunto de datos `df_tratados.csv`, que contiene información detallada sobre los clientes y sus servicios.
* **Manejo de Datos:** Se identificaron y trataron los valores no numéricos en la columna `charges.total`, rellenando los valores faltantes con 0 para asegurar la compatibilidad con los modelos numéricos.
* **Correlación de Variables:**
    * Se calculó y visualizó una matriz de correlación para entender las relaciones entre todas las variables numéricas.
    * Se prestó especial atención a las variables con mayor correlación con la variable objetivo `churn`. Se identificaron `tenure`, `contract_month-to-month` y la ausencia de servicios de seguridad como los principales factores de influencia.

---

### 2. Preprocesamiento para el Modelado ⚙️🔬

* **Identificación de Desbalance de Clases:** Se verificó que el conjunto de datos estaba significativamente desbalanceado, con la clase 'No Churn' (0) siendo la mayoría y la clase 'Churn' (1) la minoría.
* **División de Datos:** El conjunto de datos se dividió en un 70% para entrenamiento y un 30% para prueba. Se utilizó la estrategia de `stratify=y` para garantizar que la proporción de clases se mantuviera en ambos conjuntos.
* **Manejo de Desbalance con Undersampling:** Para abordar el desbalance de clases, se aplicó la técnica de `NearMiss` **exclusivamente al conjunto de entrenamiento**. Esta técnica redujo el número de instancias de la clase mayoritaria para igualar el tamaño de la clase minoritaria, preparando así un conjunto de datos equilibrado para el entrenamiento.

---

### 3. Creación y Evaluación de Modelos 🤖🧠

Se construyeron dos modelos predictivos, cada uno seleccionado en base a si requieren o no normalización de los datos.

#### **Modelo 1: Regresión Logística** 📈
* **Características:** Es un modelo lineal que requiere que los datos estén en la misma escala para un rendimiento óptimo.
* **Normalización:** Se aplicó `StandardScaler` para normalizar las características numéricas del conjunto de entrenamiento y de prueba, asegurando que el modelo no se sesgue por la magnitud de las variables.
* **Evaluación:** Se entrenó el modelo con los datos balanceados y normalizados, y se evaluó con las siguientes métricas en el conjunto de prueba:
    * Exactitud (`Accuracy`)
    * Precisión (`Precision`)
    * Recall (`Recall`)
    * F1-score
    * Matriz de Confusión

#### **Modelo 2: Árbol de Decisión** 🌳
* **Características:** Este modelo basado en árboles no es sensible a la escala de los datos, por lo que no se aplicó normalización.
* **Evaluación:** Se entrenó el modelo con los datos balanceados (sin normalizar) y se evaluó con las mismas métricas que la Regresión Logística.

---

### 4. Análisis Crítico y Propuesta de Estrategias 🎯💡

* **Rendimiento de los Modelos:** Se comparó el rendimiento de ambos modelos, prestando especial atención a las métricas de la clase minoritaria (Precision, Recall y F1-score). Este análisis permitió identificar cuál de los modelos se ajusta mejor a los objetivos de negocio de la retención de clientes.
* **Análisis de Importancia de Variables:**
    * Para la Regresión Logística, se analizaron los **coeficientes** de las variables para entender su contribución a la predicción.
    * Para el Árbol de Decisión, se utilizaron las **importancias de las características** para identificar las variables más influyentes.
* **Factores Clave y Estrategias de Retención:** Se elaboró un informe detallado que identifica los factores de mayor riesgo de churn y se propusieron estrategias de retención específicas para mitigar estos riesgos. Los factores principales incluyen la baja antigüedad, los contratos mes a mes y la falta de servicios de soporte.

Este proyecto ha proporcionado un marco robusto para entender y predecir el comportamiento de churn, ofreciendo a la empresa herramientas valiosas para tomar decisiones informadas y mejorar la lealtad de sus clientes.
