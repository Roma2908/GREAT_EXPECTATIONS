# GREAT_EXPECTATIONS

#  Limpieza y Validación Automática de Datos

Este proyecto realiza una **pipeline automatizada** para la **limpieza, imputación y validación de calidad de datos** a partir de un archivo `.csv` utilizando `pandas`, `numpy`, `scikit-learn`, y `great_expectations`.

---

##  Funcionalidades principales

### 1.  Carga de Datos
- Se lee un archivo `.csv` de entrada utilizando `pandas`.

### 2.  Limpieza del Dataset
- Se eliminan **columnas con más del 50% de valores nulos**.
- Se eliminan **columnas con un único valor** (constantes).
- Se imprime el `shape` del DataFrame tras la limpieza.

### 3.  Imputación de Datos Faltantes
- Soporta dos métodos:
  - `mediana/moda`: imputación rápida y robusta.
  - `KNN`: imputación basada en vecinos más cercanos (`sklearn.impute.KNNImputer`).
- Imputación categórica por **moda**.
- Incluye **manejo de errores** para evitar fallos por columnas problemáticas.

### 4. Validación Automática con Great Expectations
- Se generan reglas automáticamente para todas las columnas:
  - No se permiten valores nulos.
  - Para columnas numéricas: se valida que los valores estén entre los percentiles 1% y 99%.
  - Para columnas categóricas con ≤ 20 valores distintos: se valida que los valores estén dentro del conjunto observado.
- Se ejecuta la validación y se imprime un **resumen claro del resultado**:
  - Éxito o fallos.
  - Detalle de qué columnas y reglas no se cumplieron.

---

##  Requisitos

Instalar dependencias:

```bash
%pip install pandas numpy scikit-learn great_expectations
