Titanic — Reto de clasificación

**Resumen**
- **Objetivo:** Construir un clasificador binario para predecir la supervivencia de pasajeros en el conjunto de datos Titanic.
- **Enfoque:** Análisis exploratorio breve, selección y codificación de features sencillas, normalización, entrenamiento de un modelo de Regresión Logística y evaluación con varias umbrales de decisión.

**Datos**
- **Archivos usados:** `train.csv` (con etiquetas) y `test.csv` (sin etiquetas para envío).
- **Contenido relevante:** variables como `Pclass`, `Sex`, `SibSp`, `Parch` y la columna objetivo `Survived` en el conjunto de entrenamiento.

**Exploración y observaciones iniciales**
- Se observó una diferencia clara en la tasa de supervivencia por sexo: las mujeres tienen mayor probabilidad de supervivencia que los hombres.
- También hay señales de que la clase socioeconómica (`Pclass`) influye en la supervivencia.
- Visualizaciones simples (conteos y barras) se usaron para verificar estas tendencias antes del modelado.

**Características y preprocesamiento**
- **Features seleccionadas:** `Pclass`, `Sex`, `SibSp`, `Parch`.
- **Codificación:** Se aplicó one-hot encoding a las variables categóricas mediante `pd.get_dummies(..., drop_first=True)`.
- **Escalado:** `StandardScaler` sobre los conjuntos de entrenamiento y validación.
- **División:** `train_test_split` con `test_size=0.2` y `random_state=42` para evaluación interna.

**Modelo**
- Se entrenó una **Regresión Logística** con los datos preprocesados.
- Se inspeccionaron los coeficientes del modelo y se calculó el **Odds Ratio** para interpretar el efecto relativo de cada feature en la probabilidad de supervivencia.

**Evaluación**
- Para las probabilidades de la clase positiva se probaron distintos umbrales de decisión (`0.3`, `0.5`, `0.7`) y se calcularon la matriz de confusión, precision, recall y F1-score para cada umbral.
- El umbral elegido para generar la predicción final en `test.csv` fue `0.5` (archivo `submission_logistic.csv`).

**Resultados y hallazgos**
- Las métricas varían según el umbral: un umbral más bajo aumenta recall a costa de precision, y un umbral más alto hace lo contrario — esto es consistente con la interpretación clásica del trade-off precision/recall.
- La variable `Sex` (femenino) mostró el mayor impacto positivo en las probabilidades de supervivencia; el gráfico de Odds Ratio ayuda a visualizar esa influencia relativa.

**Archivos en este proyecto**
- `Clasification_1_Titanic.ipynb` — notebook con el flujo completo de trabajo.
- `train.csv`, `test.csv` — datos originales.
- `submission_logistic.csv` — ejemplo de salida generada por el notebook.

