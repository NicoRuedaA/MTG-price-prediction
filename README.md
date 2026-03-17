![Logo del Proyecto](images/title.png)

# 🧙‍♂️ Magic: The Gathering - Price Prediction & Market Analysis

![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-Machine%20Learning-orange.svg)
![Status](https://img.shields.io/badge/Status-Completed-success.svg)

## 📌 Visión General

Este proyecto aplica técnicas de Machine Learning y Análisis Exploratorio de Datos (EDA) para predecir el valor de mercado de las cartas de **Magic: The Gathering**. Utilizando la API oficial de Scryfall, el modelo extrae, limpia y analiza más de 300,000 registros para descubrir cómo las estadísticas físicas de una carta influyen en su precio.

## 🎯 Objetivos del Proyecto

1. **Predicción de Precios:** Entrenar un modelo de Bosque Aleatorio (`RandomForestRegressor`) para estimar el precio de cartas estándar.
2. **Tratamiento de Outliers:** Demostrar cómo el mercado de coleccionismo (cartas > 30$) distorsiona las predicciones y cómo solucionarlo mediante un recorte de dominio.
3. **Reducción de Dimensionalidad:** Utilizar **PCA** y **t-SNE** para visualizar el mercado en 2D y 3D, descubriendo "nichos" y agrupaciones de cartas según sus características.

## 📊 Resultados Clave

Al separar las cartas de coleccionista (ruido) de las cartas de juego (señal), el modelo optimizado logró una mejora drástica:

- **Modelo Base (Con Outliers):** Incapaz de generalizar el precio debido a cartas de valor histórico anómalo (escala de error y predicción desorbitada).
- **Modelo Optimizado (Cartas <= 30$):** El Error Absoluto Medio (MAE) se redujo significativamente. Se demuestra que estadísticas como Fuerza, Resistencia, Coste de Maná y Rareza sí explican el precio en el mercado de jugadores estándar.

_(Añade aquí tu imagen comparativa de barras)_
![Comparativa de Modelos](images/comparativa_modelos.png)

## 🧠 Arquitectura y Flujo de Datos

1. **Extracción:** Conexión directa a la API Bulk Data de Scryfall (no requiere descargar archivos pesados de cientos de MB al clonar el repo).
2. **Feature Engineering:** Conversión de arrays de colores, cálculo de longitudes de texto (`oracle_text`) y mapeo numérico de rarezas.
3. **Modelado:** `RandomForestRegressor` escalado con `StandardScaler`.
4. **Interpretabilidad:** Análisis de componentes principales (PCA Loadings) mediante mapas de calor y agrupación no lineal con t-SNE.

_(Añade aquí tu imagen del gráfico PCA o t-SNE)_
![Visualización PCA / t-SNE](images/pca_magic.png)

## 📁 Estructura del Repositorio

\`\`\`text
mtg-price-predictor/
├── data/ # Carpeta de datos (descarga automática vía API)
├── images/ # Gráficos generados por el EDA y evaluación de modelos
├── notebooks/  
│ └── mtg_price_model.ipynb # Cuaderno principal con el código y explicaciones
├── .gitignore # Archivos ignorados por Git
├── requirements.txt # Dependencias del proyecto
└── README.md # Documentación del proyecto
\`\`\`

## 🚀 Cómo ejecutar este proyecto

1. Clona el repositorio:
   \`\`\`bash
   git clone https://github.com/TU_USUARIO/mtg-price-predictor.git
   \`\`\`
2. Navega al directorio del proyecto:
   \`\`\`bash
   cd mtg-price-predictor
   \`\`\`
3. Instala las dependencias necesarias:
   \`\`\`bash
   pip install -r requirements.txt
   \`\`\`
4. Abre el Jupyter Notebook:
   \`\`\`bash
   jupyter notebook notebooks/mtg*price_model.ipynb
   \`\`\`
   \_Nota: El cuaderno se conectará automáticamente a la API de Scryfall en la primera ejecución para trabajar con los datos más recientes del mercado.*

## 🛠️ Tecnologías Utilizadas

- **Manipulación de Datos:** `pandas`, `requests`
- **Machine Learning:** `scikit-learn` (RandomForest, PCA, t-SNE, SimpleImputer, StandardScaler)
- **Visualización:** `matplotlib`, `seaborn`, `plotly` (para gráficos interactivos en 3D)

---

**Desarrollado por Nico Rueda**
