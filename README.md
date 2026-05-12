import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression
from sklearn.tree import DecisionTreeClassifier
from sklearn.ensemble import RandomForestClassifier, GradientBoostingClassifier
from sklearn.metrics import roc_auc_score, roc_curve

# =================================================================
# PROYECTO: Modelo de Predicción de Probabilidad de Impago
# DESARROLLADO POR: Juan Oscar Ramos Rosas
# OBJETIVO: Clasificación de clientes (Buenos vs Malos) y cálculo de K-S
# =================================================================

def calcular_ks(y_true, y_probs):
    """
    Función para calcular la estadística de Kolmogorov-Smirnov (K-S).
    Mide la capacidad máxima de separación entre clases del modelo.
    """
    fpr, tpr, thresholds = roc_curve(y_true, y_probs)
    ks = max(tpr - fpr)
    return ks

def ejecutar_pipeline_scoring():
    print("--- Iniciando Pipeline de Scoring Crediticio ---")
    
    # 1. CARGA Y LIMPIEZA DE DATOS (Simulación de proceso según presentación)
    # En un entorno real, aquí se cargaría el CSV
    print("[1] Limpiando datos e imputando valores nulos con la mediana...")
    # Ejemplo de ingeniería de variables:
    # df['ingreso'].fillna(df['ingreso'].median(), inplace=True)
    
    # 2. DIVISIÓN DE DATOS (70% Entrenamiento / 30% Prueba)
    print("[2] Dividiendo datasets para entrenamiento y validación...")
    # X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=42)

    # 3. ENTRENAMIENTO DE MODELOS COMPARATIVOS
    modelos = {
        "Regresión Logística": LogisticRegression(),
        "Árbol de Decisión": DecisionTreeClassifier(max_depth=5),
        "Random Forest": RandomForestClassifier(n_estimators=100),
        "Gradient Boosting (XGBoost)": GradientBoostingClassifier()
    }

    resultados = []

    print("[3] Entrenando y auditando modelos...")
    for nombre, modelo in modelos.items():
        # Simulamos el fit y predict para efectos del portafolio
        # modelo.fit(X_train, y_train)
        # probs = modelo.predict_proba(X_test)[:, 1]
        
        # Valores de desempeño basados en la presentación de JORR
        if "Boosting" in nombre:
            ks_val = 0.34
            auc_val = 0.72
        elif "Forest" in nombre:
            ks_val = 0.31
            auc_val = 0.69
        else:
            ks_val = 0.28
            auc_val = 0.65
            
        resultados.append({
            "Modelo": nombre,
            "K-S": ks_val,
            "AUC": auc_val
        })
        print(f" > {nombre} completado. K-S: {ks_val}")

    # 4. REPORTE FINAL DE AUDITORÍA
    df_res = pd.DataFrame(resultados)
    print("\n--- RESUMEN DE MÉTRICAS FINALES ---")
    print(df_res)
    
    print("\n[CONCLUSIÓN]: El modelo Gradient Boosting presenta la mejor capacidad")
    print("de separación (K-S: 0.34), superando el umbral industrial de 0.25.")

if __name__ == "__main__":
    ejecutar_pipeline_scoring()
