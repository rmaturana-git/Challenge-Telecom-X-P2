---

# Telecom X - Fase 2: Predicción de Churn con Machine Learning

## 📝 Propósito del Proyecto

El objetivo principal de este análisis es desarrollar un sistema de **detección temprana de cancelación de clientes (Churn)**. Mediante el uso de algoritmos de clasificación, buscamos identificar patrones de comportamiento en los usuarios de Telecom X para permitir que el equipo de retención actúe preventivamente antes de que el cliente abandone el servicio.

El enfoque técnico se centró en maximizar el **Recall** (sensibilidad), garantizando que el modelo detecte la mayor cantidad posible de fugas reales, incluso a costa de generar algunos falsos positivos.

---

## 📂 Estructura del Proyecto

* `TelecomX_LATAM-Parte-2.ipynb`: Cuaderno principal con el flujo completo de ciencia de datos.
* `datos_tratados.csv`: Datos originales.
* `churn_processed_test.csv`: Dataset final con datos de prueba.
* `churn_processed_train.csv`: Dataset final con datos de entrenamiento.
* `README.md`: Documentación actual.

---

## 🛠️ Preparación de Datos y Modelización

### 1. Clasificación de Variables

* **Numéricas:** `tenure`, `MonthlyCharges`, `TotalCharges` y la variable calculada `Cuentas_Diarias`.
* **Categóricas:** `gender`, `InternetService`, `Contract`, `PaymentMethod`, entre otras (11 en total).

### 2. Ingeniería de Características (Preprocessing)

* **Codificación:** Se aplicó *One-Hot Encoding* (`pd.get_dummies`) con `drop_first=True` para transformar variables de texto en binarias, evitando la redundancia matemática.
* **Normalización:** Se utilizó `StandardScaler` para estandarizar las variables numéricas (media 0, desviación 1). Esto es crítico para que modelos como la Regresión Logística no se vean sesgados por la magnitud de los cargos totales.
* **Balanceo de Clases:** Debido al desbalance original (73% activos / 26% churn), se aplicó **Random Oversampling** en el conjunto de entrenamiento para equilibrar la muestra al 50/50.

### 3. División del Dataset

Se utilizó una partición de **80% Entrenamiento** y **20% Prueba**, asegurando que el modelo se evaluara con datos que nunca "vio" durante el aprendizaje.

---

## 📊 Insights y Visualizaciones (EDA)

Durante el Análisis Exploratorio de Datos, se identificaron factores críticos:

* **Puntos de Fuga:** Los clientes con **Fibra Óptica** y pagos por **Cheque Electrónico** presentan la mayor tasa de deserción.
* **Retención:** La antigüedad (`tenure`) y los contratos a largo plazo (1 y 2 años) son los predictores de lealtad más fuertes.

---

## 📈 Rendimiento de Modelos

Se compararon dos arquitecturas distintas:

| Modelo | Recall (Clase 1) | F1-Score | Diagnóstico |
| --- | --- | --- | --- |
| **Regresión Logística** | **0.777** | **0.62** | **Ganador:** Alta capacidad de detección. |
| **Random Forest** | 0.509 | 0.56 | **Overfitting:** Capturó ruido del entrenamiento. |

**Justificación:** Se seleccionó la **Regresión Logística** por su alto Recall. Para Telecom X, es más rentable intervenir a un cliente leal que perder a un desertor por falta de detección.

---

## 💻 Instrucciones de Ejecución

### Requisitos Previos

Es necesario tener instalado Python 3.8+ y las siguientes librerías:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn

```

### Ejecución

1. Clona el repositorio.
2. Asegúrate de que el archivo `churn_raw.csv` esté en la carpeta `data/`.
3. Abre el cuaderno `Telecom_X_Fase2.ipynb` en Jupyter o Google Colab.
4. Ejecuta las celdas en orden. El script realizará automáticamente la limpieza, el escalado y el entrenamiento de los modelos.

---

**Análisis realizado por:**
  - Rodrigo Maturana

**Rol:** 
  - AI Solutions Architect / Junior Data Scientist

**Contacto**
  - rmaturanad@gmail.com
  - www.linkedin.com/in/rodrigo-maturana-donoso
    
**Fecha:** Marzo 2026

---

