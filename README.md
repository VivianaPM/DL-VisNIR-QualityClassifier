# DL-VisNIR-QualityClassifier
## Redes Neuronales para Clasificación de Calidad Agrícola con Espectroscopía Vis-NIR

[![Python 3.9](https://img.shields.io/badge/python-3.9-blue.svg)](https://www.python.org/)
[![TensorFlow 2.12](https://img.shields.io/badge/TensorFlow-2.12-orange.svg)](https://www.tensorflow.org/)

---

## Índice

- [Contexto del Problema](#contexto-del-problema)
- [Descripción del Proyecto](#descripción-del-proyecto)
- [Metodología](#metodología)

---

## Contexto del Problema

La calidad de productos agrícolas como **manzanas** y **champiñones** tradicionalmente se evalúa mediante inspección visual manual, lo que introduce subjetividad, variabilidad y altos costos operativos. Este proyecto propone una solución automatizada usando **espectroscopía Vis-NIR** (Visible - Near Infrared) combinada con **redes neuronales profundas** para clasificar calidad de manera objetiva y reproducible.

**Beneficios Potenciales:**
- Evaluación objetiva y reproducible
- Reducción de costos operativos en líneas de producción
- Clasificación en tiempo real
- Escalabilidad a otros productos agrícolas

---

## Datos

### Características del Dataset

| Característica | Manzanas | Champiñones |
|----------------|----------|-------------|
| **Clases** | 3 (Óptima, Estándar, Aceptable) | 6 (Excelente a Muy Mala) |
| **Muestras** | [N] registros espectrales | [N] registros espectrales |
| **Características** | [N] bandas espectrales Vis-NIR | [N] bandas espectrales Vis-NIR |
| **Rango espectral** | 400-2500 nm | 400-2500 nm |
| **Preprocesamiento** | SNV + Derivada 1ra | SNV + MSC |


---

## Descripción del Proyecto

Este proyecto implementa y evalúa múltiples arquitecturas de redes neuronales para clasificar calidad de productos agrícolas basados en espectros Vis-NIR.

**Objetivos:**
1. Determinar arquitectura óptima mediante validación cruzada 5-fold
2. Comparar rendimiento de 6 arquitecturas por dataset
3. Optimizar hiperparámetros iterativamente (dropout, learning rate, capas)
4. Analizar errores a nivel de muestra individual
5. Proporcionar pipeline reproducible para futuros desarrollos

**Alcance:**
- Implementación en Jupyter Notebooks
- TensorFlow/Keras
- Visualización de curvas de aprendizaje
- Matrices de confusión por clase
- Análisis de confianza por predicción

---

## Metodología

### 1. Validación Cruzada Estratificada
- **5 folds** manteniendo proporción de clases
- Métrica principal: **F1-Score** (macro y ponderado)
- Razón: Desbalanceo significativo en manzanas

### 2. Proceso de Optimización Iterativa

Partiendo de arquitecturas baseline del estado del arte, se ajustaron los siguientes parámetros:

| Parámetro | Rango Explorado | Valor Óptimo (PA_A) |
|-----------|-----------------|---------------------|
| Capas ocultas | 2-4 | 3 |
| Neuronas/capa | 32-256 | [128, 64, 32] |
| Activación | ReLU, Tanh, ELU | ReLU |
| Dropout | 0.1-0.5 | 0.2, 0.3 |
| Learning Rate | 1e-5 - 1e-2 | 1e-3 |
| Optimizador | Adam, SGD, RMSprop | Adam |
| Oversampling | SMOTE, ADASYN | SMOTE |
| Batch Size | 16-128 | 32 |
| Épocas | 50-200 | 100 (early stopping) |

### 3. Análisis de Errores
- **10 muestras aleatorias** por dataset para inferencia
- **Distribución de probabilidades** por clase
- **Umbral de confianza** para decisiones críticas

 Software is
furnished to do so, subject to the following conditions:
...
