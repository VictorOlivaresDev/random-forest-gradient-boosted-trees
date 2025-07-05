# Clasificación de Fármacos con Modelos de Ensamble

## 📝 Descripción del Proyecto

Este proyecto compara la efectividad de tres algoritmos de ensamble (**Random Forest**, **Gradient Boosted Trees** y **AdaBoost**) para resolver un problema de clasificación multiclase. El objetivo es predecir el fármaco más adecuado para un paciente basándose en sus datos médicos y demográficos, utilizando el mismo conjunto de datos que en el proyecto de Árbol de Decisión.

---

## 📊 Datos Utilizados

El conjunto de datos, cargado desde el archivo `drugs.csv`, contiene información sobre 200 pacientes.

- **Características Predictoras:**

  - `Age`: Edad del paciente.
  - `Sex`: Sexo (F/M).
  - `BP`: Nivel de presión arterial (BAJA, NORMAL, ALTA).
  - `Cholesterol`: Nivel de colesterol (NORMAL, ALTO).
  - `Na_to_K`: Proporción de sodio a potasio en sangre.

- **Variable Objetivo:**
  - `Drug`: El tipo de fármaco recomendado (drugA, drugB, drugC, drugX, drugY).

---

## 🛠️ Técnicas y Metodología

El flujo de trabajo del proyecto fue el siguiente:

### **1. Preprocesamiento de Datos**

- **Codificación de Variables Categóricas:** Las características no numéricas (`Sex`, `BP`, `Cholesterol`) se convirtieron a valores numéricos utilizando `LabelEncoder` de Scikit-learn para ser procesadas por los modelos.

### **2. División del Conjunto de Datos**

- El dataset se dividió en un conjunto de **entrenamiento (80%)** y un conjunto de **prueba (20%)**.

### **3. Modelado y Comparación**

Se entrenaron y evaluaron tres modelos de ensamble distintos:

1.  **Random Forest Classifier:** Un modelo que construye múltiples árboles de decisión y combina sus resultados para mejorar la precisión y controlar el sobreajuste. Se utilizó con `n_estimators=100`.
2.  **Gradient Boosting Classifier:** Un modelo de boosting que construye árboles de forma secuencial, donde cada nuevo árbol corrige los errores de los anteriores. También se usó con `n_estimators=100`.
3.  **AdaBoost Classifier:** Otro algoritmo de boosting que ajusta secuencialmente copias de un clasificador base (por defecto, un árbol de decisión) sobre los datos, dando mayor peso a las instancias mal clasificadas en iteraciones posteriores.

---

## 📈 Resultados y Comparación

El rendimiento de cada modelo se midió utilizando el reporte de clasificación, que proporciona métricas como la precisión (accuracy), precision, recall y F1-score.

| Métrica                            | Random Forest | **Gradient Boosting (Ganador)** | AdaBoost |
| :--------------------------------- | :-----------: | :-----------------------------: | :------: |
| **Accuracy**                       |     0.975     |            **1.00**             |   0.85   |
| **Precision (promedio ponderado)** |     0.98      |            **1.00**             |   0.79   |
| **Recall (promedio ponderado)**    |     0.97      |            **1.00**             |   0.85   |
| **F1-Score (promedio ponderado)**  |     0.97      |            **1.00**             |   0.81   |

- **Gradient Boosting Classifier** logró un rendimiento perfecto, clasificando correctamente todas las instancias del conjunto de prueba.
- **Random Forest** también mostró un rendimiento excelente, con solo una clasificación errónea.
- **AdaBoost** tuvo el rendimiento más bajo de los tres, con una precisión notablemente inferior, especialmente para las clases `drugB` y `drugC`.

## ⭐ Conclusiones

Para este conjunto de datos, los modelos de ensamble basados en árboles de decisión demostraron ser extremadamente efectivos.

El **Gradient Boosting Classifier fue el modelo con mejor rendimiento**, alcanzando métricas perfectas en la evaluación. Esto sugiere que su enfoque de corrección secuencial de errores fue ideal para capturar los patrones en estos datos.

El **Random Forest** se posicionó como una alternativa muy sólida y casi perfecta. Por otro lado, el modelo **AdaBoost** no fue tan eficaz en este problema de clasificación multiclase, mostrando dificultades para identificar correctamente algunas de las clases de fármacos.
