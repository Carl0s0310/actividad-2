# actividad-2
# 🧠 Student Dropout Classification  
**Universidad de la Costa – Data Mining**  
**Curso:** MINERIA DE DATOS 
**Integrantes del equipo**
Hernando Luiz Calvo Ochoa
Carlos Antonio Ardila Ruiz
**Actividad 2 – Entrenamiento de Modelos (José Escorcia-Gutiérrez, Ph.D.)**  

## Descripción del problema  
La Universidad enfrenta altos índices de deserción estudiantil en los programas de pregrado.  
Con el fin de anticipar qué estudiantes podrían abandonar durante el primer año, se desarrolló un modelo de predicción usando datos históricos de estudiantes, incluyendo información **demográfica, académica y financiera**.  

## Objetivo del proyecto  
Entrenar y comparar dos modelos de Machine Learning (Regresión Logística y Árbol de Decisión) que permitan **predecir si un estudiante abandonará sus estudios**.  
El mejor modelo podrá servir como base para un sistema de **alerta temprana**, ayudando a tomar acciones preventivas.  

## Metodología  

1. **Carga y limpieza de datos:**  
   Se utilizó el dataset `student_dropout.csv` con 4424 registros y 37 variables.  
   La columna `Target` contiene tres categorías: `Graduate`, `Dropout` y `Enrolled`.  
   Para la predicción, se transformó en un valor binario:  
    `Dropout = 1`  
    `Graduate` o `Enrolled = 0`.

2. **Análisis exploratorio (EDA):**  
    No se encontraron valores nulos.  
    Se identificaron variables numéricas y categóricas.  
    Se observó un desbalance moderado (Dropout ≈ 32%).  

3. **Preprocesamiento:**  
    Numéricos → imputación por mediana + escalado estándar (`StandardScaler`).  
    Categóricos → imputación por moda + codificación One-Hot (`OneHotEncoder`).  
    Se aplicó `ColumnTransformer` para automatizar el flujo.  

4. **Entrenamiento de modelos:**  
    **Regresión Logística** (`LogisticRegression`)  
    **Árbol de Decisión** (`DecisionTreeClassifier`)  
   Ambos dentro de pipelines con preprocesamiento.  

5. **Validación cruzada (5-fold CV)** en el conjunto de entrenamiento, usando `scoring='f1'`.  

6. **Evaluación final:**  
   Se calcularon las métricas en el conjunto de prueba:  
   Accuracy  
   Precision  
   Recall  
   F1-score  
   Matriz de confusión  
   Curva ROC y AUC  

## Resultados  

| Modelo | Accuracy | Precision | Recall | F1-score | ROC AUC |
|:-------|:----------|:-----------|:--------|:----------|:---------|
| **Regresión Logística** | 0.888 | 0.897 | 0.736 | **0.809** | **0.927** |
| Árbol de Decisión | 0.795 | 0.666 | 0.729 | 0.696 | 0.778 |

 La **Regresión Logística** obtuvo mejor desempeño general (mayor F1 y AUC).  
 El Árbol de Decisión fue más simple de interpretar, pero menos preciso.  

## Conclusiones  
El modelo de **Regresión Logística** resulta más confiable para predecir la deserción estudiantil.  
Este modelo puede servir como punto de partida para un **sistema de alerta temprana**, ayudando a identificar a los estudiantes en riesgo.  
Se sugiere explorar mejoras como:
   Balanceo de clases (SMOTE o ponderación de clase).  
   Selección de variables relevantes.  
   Probar modelos más complejos (Random Forest, XGBoost).  

## Archivos incluidos  
student_dropout_activity_corrected.ipynb` → Notebook con todo el proceso.  
student_dropout.csv` → Dataset base.  
logistic_pipeline_corrected.joblib` y `decisiontree_pipeline_corrected.joblib` → Modelos entrenados 


> *“El verdadero valor de los datos está en las decisiones que nos ayudan a tomar.”*  
