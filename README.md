# Modelo de Predicción de Probabilidad de Impago (Credit Scoring)

Este proyecto desarrolla un sistema de **Scoring Crediticio** para predecir la probabilidad de que un cliente incumpla con sus pagos (*Default*). Utilizando técnicas de **Ciencia de Datos** y **Aprendizaje Supervisado**, se comparan distintos algoritmos para optimizar la toma de decisiones en la aprobación de créditos y reducir el riesgo financiero.

## 📊 Objetivo del Proyecto

El objetivo principal es diferenciar automáticamente a un "Buen Cliente" (0) de un "Mal Cliente" (1), permitiendo al negocio:

* **Reducir la tasa de morosidad:** Identificación temprana de perfiles de riesgo.
* **Agilizar la operación:** Automatización del proceso de aprobación de solicitudes.
* **Análisis de Variables:** Identificación de los factores críticos que determinan la capacidad de pago.

## 🛠️ Stack Tecnológico

* **Lenguaje:** Python 3.x
* **Librerías Principales:**
    * `Pandas` y `NumPy`: Limpieza, tratamiento de nulos y manipulación de datos.
    * `Matplotlib` y `Seaborn`: Visualización estadística y diagnóstico de modelos.
    * `Scikit-Learn`: Entrenamiento de algoritmos y métricas de evaluación.

## 📈 Metodología y Proceso

1. **Tratamiento de Datos:** Imputación de valores nulos mediante mediana y codificación de variables categóricas (*One-Hot Encoding*).
2. **Análisis de Desequilibrio:** Estrategias para manejar el sesgo natural de la cartera (proporción desigual entre clientes buenos y morosos).
3. **Modelado Comparativo:** Se evaluaron 4 metodologías: Regresión Logística, Árboles de Decisión, Random Forest y **Gradient Boosting (XGBoost)**.
4. **Auditoría de Modelos:** Evaluación bajo métricas industriales de riesgo: **AUC (ROC)**, **Gini** y el coeficiente **K-S (Kolmogorov-Smirnov)**.

## 🏆 Resultados y Hallazgos

* **Capacidad de Separación:** Los modelos superaron el umbral industrial de **K-S > 0.25**, alcanzando un rendimiento máximo de **0.34**.
* **Naturaleza del Riesgo:** Se determinó que el riesgo crediticio es no lineal; los modelos basados en árboles capturaron mejor las combinaciones complejas de variables.
* **Factor Determinante:** La verificación de la capacidad de pago propia fue el predictor con mayor influencia en el éxito de las 4 predicciones.

## 📁 Contenido del Repositorio

* `analisis_impago.py`: Script de Python con el pipeline completo de datos.
* `Probabilidad_de_impago_JORR.pdf`: Presentación ejecutiva con la radiografía del riesgo y recomendaciones estratégicas.

---
**Desarrollado por:** [Juan Oscar Ramos Rosas](https://www.linkedin.com/in/juan-oscar-ramos-a8a0341a0)  
*Ingeniero Matemático | Especialista en Diagnóstico de Procesos y Ciencia de Datos*
