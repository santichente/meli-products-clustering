# Mercado Libre Product Clustering

Este repositorio contiene la solución para el **Meli Data Science Challenge**, donde agrupamos productos similares usando técnicas de **Procesamiento de Lenguaje Natural (NLP)** y **Machine Learning**.

## 🚀 Requisitos

1. Python 3.8+
2. Instalar dependencias con:
   ```bash
   pip install -r requirements.txt



### 1. **Contexto del Problema**

- **Marketplace con múltiples sellers:**  
  En el marketplace se pueden encontrar productos que, aunque son idénticos o muy similares, son vendidos por diferentes vendedores. Esto puede generar una experiencia confusa para el usuario, ya que se le presentan muchas opciones que en realidad corresponden al mismo producto o a variantes muy cercanas.

- **Accesibilidad de la información:**  
  La API de Mercado Libre permite obtener datos relevantes de cada producto, como los títulos y las imágenes, lo que posibilita analizar y comparar estos productos desde un punto de vista textual y visual.

---

### 2. **Objetivo Principal**

- **Identificar productos similares o idénticos:**  
  El reto consiste en desar rollar una estrategia que permita detectar, dentro de un gran volumen de ítems, aquellos que son iguales o muy parecidos, pese a provenir de distintos sellers.

- **Agrupar y hacer comparables estos ítems:**  
  Una vez identificados, el objetivo es agruparlos para que se puedan comparar de manera directa. Esto mejora la experiencia del usuario al facilitar la elección entre productos similares.

---

### 3. **Aspectos Técnicos y Metodológicos a Considerar**

- **Extracción de datos:**  
  - **Títulos:** Son fundamentales para el análisis textual y permiten evaluar similitudes en la descripción del producto.  
  - **Imágenes:** Pueden utilizarse para comparar visualmente los productos y confirmar si realmente se trata del mismo artículo o de uno muy similar.

- **Preprocesamiento y Transformación de Datos:**
  - **Texto:**  
    - Limpieza (minúsculas, eliminación de signos de puntuación, stop words, etc.).  
    - Tokenización y normalización (por ejemplo, lematización o stemming).  
    - Conversión a vectores mediante técnicas como TF-IDF o embeddings para capturar el significado de los títulos.
  - **Imágenes:**  
    - Descarga y procesamiento (redimensionamiento, normalización).  
    - Extracción de características visuales usando modelos pre-entrenados (por ejemplo, CNN como ResNet, VGG, etc.) para obtener embeddings de las imágenes.

- **Medición de similitud:**
  - **Entre textos:**  
    - Utilizar métricas como la similitud del coseno sobre los vectores de TF-IDF o embeddings para medir la proximidad semántica entre los títulos.
  - **Entre imágenes:**  
    - Calcular similitudes entre los embeddings de las imágenes, nuevamente empleando métricas como la similitud del coseno o distancia euclidiana.
  - **Fusión de Modalidades:**  
    - Combinar la similitud textual y la visual para obtener una puntuación global que determine qué tan similares son dos productos.

- **Agrupamiento (Clustering):**
  - Emplear técnicas de clustering (por ejemplo, DBSCAN, clustering jerárquico, K-Means, etc.) que permitan formar grupos de productos similares basándose en las puntuaciones de similitud.
  - Ajustar los parámetros del algoritmo para lograr clusters coherentes y minimizar falsos positivos o negativos.

---

### 4. **Impacto y Beneficios del Enfoque**

- **Mejora en la experiencia de usuario:**  
  Al agrupar ítems similares, el marketplace puede presentar opciones comparativas de manera más ordenada, evitando que el usuario se sienta abrumado por muchas opciones idénticas o muy parecidas.

- **Optimización en la toma de decisiones:**  
  Los compradores podrán evaluar mejor las opciones disponibles, considerando factores como precio, condiciones y reputación del seller, una vez que se han agrupado productos equivalentes.

- **Posibles extensiones:**  
  - Validar los grupos de productos mediante retroalimentación (feedback) de usuarios o expertos.
  - Implementar soluciones supervisadas si se dispone de datos etiquetados en el futuro, para afinar aún más la detección de productos similares.

---

### 5. **Resumen de lo que se Pide**

- **Problema:**  
  Detectar y agrupar productos que, pese a ser ofrecidos por distintos sellers, son idénticos o muy similares.

- **Datos a utilizar:**  
  Títulos y/o imágenes extraídas de la API de Mercado Libre (y, potencialmente, otros atributos relevantes).

- **Metodología a implementar:**  
  - Extracción y preprocesamiento de la información.  
  - Transformación de los datos en representaciones comparables (vectorización de texto y extracción de características de imágenes).  
  - Cálculo de similitudes entre productos.  
  - Aplicación de técnicas de clustering para formar grupos de ítems similares.

- **Objetivo final:**  
  Crear grupos de productos comparables que permitan al usuario diferenciar y elegir de forma más eficiente entre opciones muy similares, mejorando así la experiencia de compra en el marketplace.


