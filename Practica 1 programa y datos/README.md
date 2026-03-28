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
* **Entrenamiento:** Utiliza el algoritmo de **Levenberg-Marquardt (`trainlm`)**.
* **Normalización:** Aplicación automática de `mapstd` para asegurar la convergencia de la red.

---

## 🛠️ Funcionamiento y Salidas
Al ejecutar el script, el sistema realiza las siguientes tareas de forma automática:

1.  **Iteración:** Prueba cada combinación de la rejilla de parámetros definida.
2.  **Métricas:** Calcula para cada modelo los índices **MAPE, MAE, MSE, RMSE y R²**.
3.  **Visualización:** Genera y guarda automáticamente una gráfica `.png` por cada experimento.
4.  **Ranking:** Muestra en la consola una tabla resumen ordenada de menor a mayor **RMSE**.

---

## 📁 Estructura del Repositorio
* `Practica 1 programa y datos/Derechos_CO2/PredMLP_3.mlx`: Script principal con la lógica de búsqueda para "Derechos_CO2".
* `Practica 1 programa y datos/consumos_eii/PredMLP_3.mlx`: Script principal con la lógica de búsqueda para "consumos_eii".
* `Practica 1 programa y datos/Gas_Natural/PredMLP_3.mlx`: Script principal con la lógica de búsqueda para "Gas_Natural".
* * `Practica 1 programa y datos/Petroleo_Brent/PredMLP_3.mlx`: Script principal con la lógica de búsqueda para "Petroleo_Brent".
---

## 📉 Ejemplo de Resultados
| Serie | Retardos | Neuronas | Epochs | R² | RMSE |
| :--- | :---: | :---: | :---: | :---: | :---: |
| Consumo EII | 10 | 50 | 50 | 0.904 | 5.77 |
| Derechos CO2 | 5 | 40 | 100 | 0.880 | 6.00 |

---

## 👨‍💻 Requisitos
* MATLAB (R2021b o superior recomendado)
* Deep Learning Toolbox
