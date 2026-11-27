# PROJENER
Modulación de Señales - UAX Master IA -MARIODELVALLE
# Clasificación de Modulaciones de Comunicaciones (AMC) con SNR Bajo

**Trabajo Fin de Máster (TFM)** — Máster Universitario en Inteligencia Artificial  
**Universidad Alfonso X el Sabio (UAX)** — Facultad de Estudios Superiores / Departamento de Ingeniería Informática  
**Autor:** Mario Del Valle Álvarez

---

## Descripción general

Este repositorio reúne los experimentos, cuadernos y scripts desarrollados para la clasificación automática de modulaciones (**AMC**, *Automatic Modulation Classification*) en escenarios de baja relación señal-ruido (**SNR**) utilizando el conjunto de datos **RadioML `RML2016.10a`** (11 modulaciones, rangos de SNR desde `-20 dB` hasta `+18 dB`).

El trabajo analiza el comportamiento de modelos de aprendizaje profundo —en particular arquitecturas híbridas **CNN–Transformer** y técnicas de apoyo sintético mediante **cWGAN-GP**— frente al ruido en la señal I/Q, así como la trazabilidad del flujo de decisión a través de módulos especializados (`T1`–`T5`) y un gestor de consolidación (`T6` / `IA 6`).

---

## Alcance y enfoque técnico

* **Conjunto de datos:** `RML2016.10a` (muestras I/Q de forma `(2, 128)` repartidas en 11 clases y múltiples niveles de SNR).
* **Línea base y análisis por SNR:** Evaluación de exactitud global y por nivel de SNR, observando el comportamiento cercano al azar en SNR muy bajo, la transición en SNR negativo/intermedio y la estabilización en SNR positivo.
* **Arquitectura y módulos del flujo:**
  * **T1 (DRL — PPO/SAC):** Gestión adaptativa según contexto espectral y SNR.
  * **T2 (CNN–Transformer):** Extracción de características locales y secuenciales para clasificación de modulaciones.
  * **T3 (VAE):** Estimación de anomalía / desviación frente a comportamiento nominal.
  * **T4 (cWGAN-GP):** Apoyo y generación sintética orientada a escenarios exigentes o de bajo SNR.
  * **T5 (Baseline determinista):** Regla de respaldo y salvaguarda ante condiciones críticas o baja fiabilidad.
  * **T6 / IA 6 (Gestor / MCDA-AHP):** Consolidación del recorrido, ponderación multicriterio y emisión del dictamen final con visualización.

---

## Entorno de ejecución

* **Lenguaje y librerías principales:** Python, PyTorch, NumPy, Pandas, Matplotlib.
* **Entornos habituales:** Google Colab / Jupyter Notebooks.

---

## Nota de trazabilidad y rigor académico

Cuando un script de demostración incluye módulos sin pesos entrenados cargados o reglas de prueba para ilustrar el recorrido completo hasta `IA 6`, se indica explícitamente en la salida y en las visualizaciones para distinguir con claridad los resultados experimentales reales de las simulaciones o demostraciones de flujo.
