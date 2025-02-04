# Mercado Libre Product Clustering

Este repositorio contiene la solución para el **Meli Data Science Challenge**, donde se agrupan productos similares o idénticos utilizando técnicas de **Procesamiento de Lenguaje Natural (NLP)**, **Visión por Computador** y **Machine Learning**.

---

## 🚀 Requisitos

1. **Python 3.11** (recomendado).
2. **Conda environment**:  
   - Crear el entorno con:
     ```bash
     conda env create -f environment.yml
     conda activate meli_env
     ```
   - Asegurarse de que el entorno se active antes de ejecutar los notebooks.

---

## 1. Estructura de Carpetas

```
meli-products-clustering/
├── data/
│   ├── df_propuesto.csv
│   └── Meli Data Science Challenge.pdf
├── notebooks/
│   ├── 1_api_exploracion_inicial.ipynb
│   ├── 2_exploracion_extraccion_datos.ipynb
│   └── 3_limpieza_estandarizacion_datos.ipynb
├── models/  (carpeta destinada a guardar futuros modelos entrenados)
├── environment.yml
└── README.md  (este documento)
```

- **`data/`:** contiene el CSV de productos (`df_propuesto.csv`) y el PDF con la descripción del reto.  
- **`notebooks/`:** alberga los Jupyter Notebooks donde se realizan la exploración, extracción y limpieza de datos.  
- **`models/`:** se destina a almacenar los modelos entrenados o embeddings generados en el futuro.  
- **`environment.yml`:** especifica las dependencias y versiones de librerías necesarias.

---

## 2. Contexto del Problema

- **Marketplace con múltiples vendedores:**  
  Varios sellers pueden publicar productos idénticos o muy similares, resultando en listas redundantes.  
- **API de Mercado Libre:**  
  Proporciona títulos, imágenes y otros datos de producto, lo que permite un análisis desde enfoques textuales y/o visuales.

---

## 3. Objetivo Principal

- **Identificar y agrupar productos similares o idénticos:**  
  Facilitar la detección de ítems duplicados para mejorar la usabilidad del marketplace.
- **Mejorar la experiencia de compra:**  
  Al agrupar o comparar productos similares, el usuario ve claramente las opciones sin saturarse con listados repetidos.

---

## 4. Metodología Propuesta

1. **Preprocesamiento de Datos**  
   - **Texto:** limpieza, normalización, tokenización, posible lematización.  
   - **Marca (`brand_std`):** unificación de minúsculas, eliminación de tildes y variantes redundantes.  
   - **GTIN:** validación, limpieza de comas/guiones, opcionalmente manejar varios GTINs por producto.  
   - **Precio (`price_std`):** convertir a número limpio, posible filtrado de outliers.  
   - **Imágenes (`thumbnail`):** validación de URLs, descarga opcional y normalización si se quieren embeddings.

2. **Análisis de Similitud** (texto/imágenes)  
   - Para texto: TF-IDF o embeddings (ej. *Sentence Transformers*).  
   - Para imágenes: embeddings con redes preentrenadas (opcional).  
   - Fusionar ambas modalidades si se pretende un enfoque multimodal.

3. **Clustering o Comparaciones**  
   - Algoritmos como DBSCAN, K-Means o búsqueda de vecinos cercanos para agrupar ítems con alta similitud.  
   - Ajuste de parámetros (distancia, umbral) para evitar sobre o subagrupar.

---

## 5. Notebooks Principales

1. **`1_api_exploracion_inicial.ipynb`**  
   - Explica la conexión con la API de Mercado Libre (o un mock de datos si no se realiza conexión real).  
   - Exploración básica de la estructura de datos.

2. **`2_exploracion_extraccion_datos.ipynb`**  
   - Procesa y extrae campos clave (título, marca, precio, etc.) de los productos.  
   - Genera un primer DataFrame con la información relevante.

3. **`3_limpieza_estandarizacion_datos.ipynb`**  
   - Aplica las funciones de limpieza y normalización a cada columna (título, brand, gtin, price, etc.).  
   - Prepara los datos para la posterior etapa de similitud y clustering.

> **Nota:** En futuros notebooks, se podrían integrar técnicas de **embeddings** y **clustering**, así como la validación final de los grupos formados.

---

## 6. Beneficios y Aplicaciones

- **Menor saturación:** se evita mostrar al usuario decenas de listados equivalentes.  
- **Mejora en la decisión de compra:** el usuario compara opciones de distintos sellers (mismo producto) en un único lugar.  
- **Base para análisis avanzado:** una vez agrupados, se puede analizar precios, calificaciones, e incluso sugerir al usuario la mejor oferta.

---

## 7. Ejecución del Proyecto

1. **Preparar el entorno**  
   - Clonar este repositorio.  
   - Crear el entorno con `conda env create -f environment.yml` y activarlo con `conda activate meli_env`.

2. **Cargar y explorar datos**  
   - Ejecutar el notebook `1_api_exploracion_inicial.ipynb` para una introducción.  
   - Revisar `2_exploracion_extraccion_datos.ipynb` para ver cómo se obtiene y organiza la información.

3. **Limpieza y estandarización**  
   - En `3_limpieza_estandarizacion_datos.ipynb`, se transforman los campos textual, numérico y de imagen para obtener un dataset homogéneo.

4. **(Futuras etapas) Clustering y comparaciones**  
   - Se podrán crear notebooks adicionales para aplicar algoritmos de similitud y clustering, valiéndose de las columnas limpias.

---

## 8. Conclusiones

- Se presenta una **base sólida** para abordar la problemática de **productos redundantes** en Mercado Libre, usando una pipeline de exploración, limpieza y posterior agrupamiento.  
- La arquitectura permite **escalar** a métodos más avanzados (embeddings multimodales, reglas de negocio específicas, etc.) que perfeccionen la detección de duplicados o productos muy similares.

---

### Próximos Pasos

- **Notebook de clustering**: Incorporar técnicas (DBSCAN, K-Means) y calcular similitudes (texto, imágenes) para formar grupos reales.  
- **Validación humana**: Verificar manualmente algunos grupos para ajustar parámetros.  
