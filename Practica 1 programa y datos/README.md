# Predicción de Series Temporales mediante MLP: Optimización Automática

Este proyecto implementa una red neuronal de tipo **Perceptrón Multicapa (MLP)** utilizando el Deep Learning Toolbox de MATLAB para predecir la evolución de distintas series temporales relacionadas con el sector energético.

A diferencia de un enfoque tradicional, este código utiliza un algoritmo de **búsqueda sistemática (Grid Search)** para encontrar automáticamente la configuración de hiperparámetros que minimiza el error de predicción.

## 📊 Series Temporales Estudiadas
El sistema está preparado para procesar y analizar las siguientes fuentes de datos:
* **Derechos de emisión de CO2** (`Derechos_CO2.xlsx`)
* **Consumo eléctrico industrial** (`consumos_eii_2022.xlsx`)
* **Precio del Petróleo Brent** (`Petroleo_Brent.xlsx`)
* **Precio del Gas Natural** (`Gas_Natural.xlsx`)

---

## 🚀 Características del Algoritmo de Optimización
El script recorre múltiples combinaciones de parámetros para identificar el modelo más eficiente:

* **Retardos de entrada (Lags):** Analiza cómo influye el número de datos pasados (5, 10, 15, 20) en la predicción futura.
* **Arquitecturas Flexibles:** Prueba capas ocultas simples (40, 50 neuronas) y arquitecturas profundas (ej. `[20 10]`, `[40 20]`).
* **Entrenamiento:** Algoritmo **Levenberg-Marquardt (`trainlm`)**.
* **Normalización:** Aplicación automática de `mapstd` para asegurar la convergencia de la red.

---

## 🛠️ Funcionamiento y Salidas
1. **Iteración:** Prueba cada combinación de la rejilla de parámetros definida.
2. **Métricas:** Calcula automáticamente **MAPE, MAE, MSE, RMSE y R²**.
3. **Visualización:** Genera y guarda una gráfica `.png` por cada experimento.
4. **Ranking:** Muestra en consola una tabla ordenada por precisión.

---

## 📉 Resumen de Mejores Configuraciones Encontradas
Tras ejecutar el proceso de optimización, estas son las configuraciones que obtuvieron el **menor error (RMSE)** para cada activo:

| Serie | Retardos | Neuronas | Epochs | % Entr. | RMSE | R² |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **Petróleo Brent** | 5 | 40 | 50 | 70% | **1.642** | **0.994** |
| **Consumo EII** | 10 | 50 | 50 | 80% | **5.777** | **0.904** |
| **Gas Natural** | 5 | 50 | 50 | 70% | **0.665** | **0.829** |
| **Derechos CO2** | 5 | 40 | 200 | 70% | **12.725** | **0.753** |

---

## 📁 Estructura del Repositorio
* `Derechos_CO2/PredMLP_3.mlx`: Script de búsqueda para CO2.
* `consumos_eii/PredMLP_3.mlx`: Script de búsqueda para Consumo Eléctrico.
* `Gas_Natural/PredMLP_3.mlx`: Script de búsqueda para Gas.
* `Petroleo_Brent/PredMLP_3.mlx`: Script de búsqueda para Brent.

---

## 👨‍💻 Requisitos
* MATLAB (R2021b o superior recomendado)
* Deep Learning Toolbox
