# Análisis del Desarrollo comercial y predicción de estrategias para una cadena de Supermercados
*LINK NOTEBOOK:* https://colab.research.google.com/drive/1ZCIfpeKWFkXaryYgr1fGCvNif2BklRO-
*LINK PRESENTACIÓN CORPORATIVA:* https://docs.google.com/presentation/d/1us61vaIW6h0UnMxbI3MekwJOIGbCBxDz/edit?slide=id.p1#slide=id.p1

# 🛒 Análisis de Datos de Supermercados y Modelado Predictivo

## 🎯 Objetivos del Proyecto

El objetivo principal de este análisis es **identificar patrones y tendencias** en los datos de supermercados para optimizar las estrategias de promoción, ventas y segmentación de clientes.

Las **predicciones específicas** que se buscaron obtener incluyen:
* El impacto de diferentes promociones en las ventas.
* Diferencias de ventas y costos por región (país).
* Preferencias de compra de clientes según su nivel educativo y características demográficas.
* La influencia de las características específicas de las tiendas en el rendimiento.

---

## 💾 Exploración Inicial de Datos (EDA)

### 📊 Panorama General
* **Tamaño Inicial del Dataset:** 60,429 registros y 40 columnas.
* **Procesamiento:**
    * Renombrado de columnas para mayor claridad.
    * Identificación inicial de tipos de datos, con predominio de la categoría `object`.
    * Transformación inicial de algunas columnas numéricas.

### 💰 Métricas Financieras Clave
| Métrica | Promedio | Total |
| :--- | :--- | :--- |
| Ventas (Sales) | $20.28 (millones) | $1,225,502.94 (millones) |
| Costos de Tienda (Store Cost) | $9.38 (millones) | $566,693.30 (millones) |
| Costos Totales (Total Cost) | $15.54 (millones) | $938,811.51 (millones) |

### Distribución
Se analizaron las categorías principales y la distribución de variables clave, observando la alta variabilidad en las métricas financieras.

---

## ⚙️ Procesamiento de Datos (Data Wrangling)

### Limpieza y Transformación
* **Valores Nulos:** Se confirmó la **ausencia total** de valores nulos en el conjunto de datos.
* **Duplicados:** Se eliminaron las columnas que presentaban información duplicada.
* **Conversión de Tipos:** Se realizó la conversión final de tipos de datos a formatos numéricos adecuados para el modelado.

### 📈 Análisis de Outliers
* Se realizó un análisis exhaustivo de valores atípicos.
* La columna `store_cost(in millions)` presentó el **mayor porcentaje de valores atípicos**.
* **Conclusión:** Los *outliers* se consideraron **ventas legítimas de alto valor** y no errores de entrada. Por lo tanto, no se eliminaron para evitar sesgar el análisis de rendimiento real de alto impacto.

---

## 🤖 Modelos de Machine Learning (Regresión)

### Preparación del Modelo
1.  **Codificación:** Se aplicó **Label Encoding** a las variables categóricas.
2.  **División de Datos:** El dataset se dividió en conjuntos de entrenamiento (70%) y prueba (30%).

### Modelos Evaluados
Se utilizaron tres modelos de regresión para predecir las ventas:

| Modelo | $R^2$ (Precisión) | MAE | MSE | RMSE | Tiempo de Ejecución |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Regresión Lineal** | **0.9999** | **0.02** | **0.00** | **0.05** | **Más Rápido** |
| Árbol de Decisión | 0.9995 | 0.08 | 0.01 | 0.05 | Intermedio |
| Random Forest | 0.9999 | 0.03 | 0.00 | 0.06 | Más Lento |

**Conclusión del Modelo:**
La **Regresión Lineal** fue seleccionada como la mejor opción. Ofreció una **precisión comparable (casi perfecta)** a Random Forest y el Árbol de Decisión, pero con un **tiempo de ejecución significativamente menor**, lo que la hace ideal para la implementación en producción y escenarios de alta velocidad.

---

## 💡 Insights Clave y Conclusiones de Hipótesis

Se validaron las siguientes conclusiones:

### Hipótesis 1: Impacto de las Promociones
* `Weekend Markdown` es la promoción más exitosa en términos de volumen de ventas.
* `Two Day Sale` y `Price Savers` generan altas ventas y superan consistentemente el costo promedio.
* `Green Light Special` es la menos eficiente, ya que no logra superar el costo promedio.

### Hipótesis 2: Rendimiento por Países
* **EE. UU.** genera las mayores ventas y costos, pero también el **mayor margen de beneficio neto**.
* **Canadá** tiene costos notablemente altos en proporción a sus ventas.

### Hipótesis 3: Educación y Tiendas
* Clientes con **educación secundaria o universitaria** prefieren el formato de tienda `'Deluxe Supermarket'`.
* **Oportunidad de Marketing:** Focalizar campañas en áreas cercanas a instituciones educativas.

### Hipótesis 4: Género y Costos
* La mediana del costo de venta es ligeramente superior para los hombres.
* **Conclusión:** La diferencia es **no significativa** para implementar estrategias de marketing basadas únicamente en el género.

### Hipótesis 5: Compras de Bebidas Alcohólicas
* Los clientes **casados** compran más bebidas alcohólicas (**53.5%**) que los solteros, contradiciendo la suposición inicial.

### Hipótesis 6: Rendimiento de la Tarjeta de Membresía
* La tarjeta **`Bronze`** genera la **mayor frecuencia de ventas**, con montos recurrentes entre 5 y 10 millones.
* La tarjeta `Golden` no es la que impulsa la mayor actividad de ventas.

---

## 🚀 Recomendaciones y Pasos a Seguir

* **Implementación del Modelo:** Implementar el modelo de **Regresión Lineal** para la predicción de ventas debido a su **alta eficiencia y precisión**.
* **Enfoque de Promociones:** Priorizar las campañas `Weekend Markdown`, `Two Day Sale` y `Price Savers`. Evaluar si `Green Light Special` debe ser descontinuada o reestructurada.
* **Focalización Geográfica:** Investigar la alta proporción de costos en Canadá para implementar medidas de optimización.
* **Monitoreo Continuo:** Establecer un sistema de monitoreo de los datos para detectar desviaciones en el impacto de las promociones y los cambios en las preferencias de los clientes.
* **Análisis Futuro:** Considerar la exploración de otros modelos de Machine Learning (como SVM, GBM, Neural Networks, KNN, y XGBoost) para escenarios de predicción más complejos o específicos.


