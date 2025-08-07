# Análisis y Predicción de Cancelación de Clientes (Churn) 📈

## 🚀 Propósito del Análisis

El objetivo principal de este proyecto es **predecir la cancelación (churn) de clientes** utilizando un conjunto de datos histórico. A través de un análisis exhaustivo, buscamos identificar los **factores más relevantes** que influyen en la decisión de un cliente de irse. La meta es proporcionar a la empresa información valiosa para desarrollar estrategias de retención proactivas y efectivas.

---

## 📂 Estructura del Proyecto

La estructura del proyecto está organizada de la siguiente manera:

* `TelecomX_parte2_LATAM.ipynb`: El cuaderno principal que abarca todas las etapas del proyecto, desde la carga de datos hasta la evaluación de modelos.
* `datos_tratados.csv`: El conjunto de datos final, tratado y listo para el modelado.

---

## 📝 Descripción del Proceso de Preparación de Datos

### 1. Clasificación de Variables 🏷️
* **Variables Categóricas:** Variables como `gender`, `multiplelines`, `internetservice` y `paymentmethod` fueron tratadas mediante **codificación One-Hot** para convertirlas en un formato numérico (0 y 1). Esto es esencial para que los modelos de Machine Learning puedan procesar esta información.
* **Variables Numéricas:** Variables como `tenure`, `charges.monthly` y `charges.total` se mantuvieron en su formato numérico original.

### 2. Normalización y Codificación 🛠️
* **Normalización:** Para el modelo de Regresión Logística, se aplicó la normalización (`StandardScaler`) a las variables numéricas continuas. Esta etapa es crucial porque asegura que todas las características tengan la misma escala, evitando que variables con rangos de valores grandes (ej. `charges.total`) dominen el proceso de optimización del modelo.
* **Separación de Datos:** El conjunto de datos se dividió en un **70% para entrenamiento** y un **30% para prueba**. Se utilizó el parámetro `stratify=y` para asegurar que la proporción de clientes que cancelan (churn) fuera la misma en ambos conjuntos, lo cual es vital en un dataset desbalanceado.

---

## 🧠 Justificaciones de las Decisiones de Modelado

* **Manejo del Desbalance de Clases:** El conjunto de datos original estaba severamente desbalanceado. Para abordar esto, se optó por el método de **undersampling NearMiss** en el conjunto de entrenamiento. Esta técnica se enfoca en las muestras de la clase mayoritaria que están más cerca de las de la clase minoritaria, lo que ayuda a que el modelo aprenda a diferenciar entre las clases en las zonas de riesgo.
* **Selección de Modelos:** Se eligieron dos modelos con diferentes sensibilidades a la escala de los datos para comparar su rendimiento:
    * **Regresión Logística:** Requiere normalización, lo que nos permitió evaluar cómo la estandarización afecta el desempeño del modelo.
    * **Árbol de Decisión:** No requiere normalización, lo que lo hace un modelo robusto y fácil de interpretar en su forma original.
* **Evaluación de Métricas:** En lugar de centrarnos solo en la exactitud (`accuracy`), se priorizaron métricas como **Precisión**, **Recall** y **F1-score**, especialmente para la clase minoritaria (`churn`). Esto se debe a que un alto `accuracy` puede ser engañoso en un dataset desbalanceado, mientras que el `recall` mide la capacidad del modelo para detectar a todos los clientes que realmente cancelan, lo cual es de gran importancia para el negocio.

---

## 📈 Ejemplos de Gráficos e Insights


**Matriz de Correlación:** Muestra la fuerte correlación negativa entre `tenure` (antigüedad) y `churn`.


**Boxplot de Antigüedad vs. Churn:** Este gráfico visualiza que los clientes que cancelan tienen una antigüedad promedio significativamente más baja que aquellos que no.


**Gráfico de Dispersión:** Muestra que los clientes que cancelan (`churn=1`) tienden a agruparse en la parte inferior izquierda, correspondiente a una baja antigüedad y un menor gasto total.

---

## ⚙️ Instrucciones para Ejecutar el Cuaderno

Para ejecutar el análisis completo, sigue estos pasos:

1.  **Instalar Bibliotecas:** Asegúrate de tener las siguientes bibliotecas instaladas. Puedes hacerlo con `pip`:
    ```bash
    pip install pandas numpy scikit-learn seaborn matplotlib imbalanced-learn
    ```
2.  **Cargar los Datos:** Asegúrate de que el archivo `datos_tratados.csv` se encuentre en la raíz del repositorio.
3.  **Ejecutar el Cuaderno:** Abre el archivo `TelecomX_parte2_LATAM.ipynb` ubicado en la raíz del repositorio y ejecutalo con Google Colab. A continuación, ejecuta cada celda en orden.

¡Con esto, podrás replicar el análisis y obtener todos los insights del proyecto!
