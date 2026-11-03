# Modelado Comparativo en Minería de Datos - Grupo 1

Trabajo práctico integrador de Minería de Datos (IFTS N°18). Comparamos modelos de clasificación y de regresión sobre dos datasets y presentamos los resultados en un tablero web con lectura comercial.

**Integrantes:** Alcuri, Escudero, Lamonico, Noble y Vignau.

## Contenido

| Archivo | Descripción |
|---|---|
| TP_Modelado_Comparativo_final.ipynb | Notebook con todas las etapas, desde el EDA hasta la evaluación en test |
| index.html | Tablero con dos pestañas, una por dataset, con los hallazgos y la comparación de modelos |
| telco_churn.csv | Dataset de clasificación, bajas de clientes de una telefónica |
| insurance.csv | Dataset de regresión, costos médicos de un seguro de salud |

## Qué hicimos

En cada dataset seguimos el mismo proceso.

1. EDA con estadísticas descriptivas, distribuciones, outliers y correlaciones.
2. Limpieza de faltantes, duplicados y categorías inconsistentes.
3. Codificación con Label y One-Hot Encoding, y transformaciones ajustadas solo con train (Yeo-Johnson y StandardScaler).
4. Selección de variables con RFE en clasificación y con importancia de Random Forest en regresión.
5. Reducción de dimensiones con PCA, conservando el 90% de la varianza.
6. Comparación de un modelo lineal contra uno no lineal con tres conjuntos de variables, con validación cruzada de 10 particiones. Son 6 modelos por dataset.
7. Evaluación del modelo elegido sobre el 30% de test y predicción de casos nuevos.

## Resultados principales

**Telco Churn (clasificación).** Elegimos la regresión logística con las 10 variables de RFE.

- AUC de **0,848** en validación cruzada y **0,846** en test, con una accuracy de **0,802**.
- Llamando al 30% de clientes con más riesgo se llega al **66%** de las bajas.
- El contrato mes a mes y el primer año de antigüedad son los factores con más riesgo de baja.

**Insurance (regresión).** Elegimos la regresión lineal con las 5 variables de Random Forest.

- Error típico (RMSE) de **4.334 dólares** en test, contra 11.921 si se predice siempre el promedio. R² de **0,868**.
- La variable fumador con obesidad, creada a partir del EDA, es la más importante del modelo.
- Un fumador con obesidad cuesta en promedio **41.693 dólares** por año, cinco veces lo que cuesta un no fumador.

## Cómo verlo

El tablero se puede ver en GitHub Pages o abriendo index.html en el navegador. No necesita instalar nada.

Para ejecutar el notebook, dejar los dos CSV en la misma carpeta e instalar las librerías.

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
jupyter notebook TP_Modelado_Comparativo_final.ipynb
```

## Fuentes

- [Telco Customer Churn - Kaggle](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)
- [Medical Cost Personal Datasets - Kaggle](https://www.kaggle.com/datasets/mirichoi0218/insurance)
