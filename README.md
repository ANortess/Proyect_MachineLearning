# Predicción de cancelaciones hoteleras

Proyecto de Machine Learning para identificar reservas con riesgo de cancelación y ayudar al hotel a priorizar su seguimiento.

## Datos

Se utiliza el dataset **Hotel Booking Demand**, con cerca de **119.000 reservas de dos hoteles**. Aproximadamente el **37 %** de las reservas se cancela.

La variable objetivo es `is_canceled`:
- `0`: reserva no cancelada.
- `1`: reserva cancelada.

## Metodología

1. Revisión de nulos, registros atípicos y variables con fuga de información.
2. Análisis exploratorio por hotel, canal, antelación, fecha de llegada y tarifa.
3. Creación de variables de huéspedes, noches y valor aproximado de la estancia.
4. Separación temporal: aproximadamente **80 % para Train y 20 % para Test**.
5. Comparación de regresión logística, árboles, Random Forest, XGBoost, LightGBM y SVM.
6. Optimización de XGBoost y LightGBM mediante validación cruzada temporal dentro de Train.
7. Interpretación del modelo seleccionado mediante importancia por permutación.

## Resultados principales

- Las reservas con mayor antelación presentan una mayor tasa de cancelación.
- City Hotel registra más cancelaciones y una tasa superior a Resort Hotel.
- Se selecciona **LightGBM**, con un **AUC medio de validación de 0,881**, frente a 0,879 de XGBoost.
- País, agencia y tipo de depósito presentan las mayores importancias por permutación en la muestra analizada.

El AUC mide la capacidad de discriminar entre clases, no el porcentaje de aciertos. Las relaciones observadas no demuestran causalidad.

## Ejecución

Coloca `reservas_hoteleras.csv` en la misma carpeta que el notebook. Selecciona un entorno con las dependencias importadas y ejecuta todas las celdas en orden desde un kernel limpio.

**Tecnologías:** Python, pandas, NumPy, Matplotlib, seaborn, scikit-learn, XGBoost y LightGBM.

## Limitaciones y aplicación

Test se consultó durante la exploración, por lo que no constituye una evaluación final independiente. Antes de implantar el modelo, es necesario evaluar nuevos periodos, comprobar la disponibilidad de las variables y ajustar el umbral según los costes del negocio.

Se propone un piloto de recordatorios y reconfirmaciones con grupo de control para medir su efecto sobre las cancelaciones.

## Fuente

Antonio, Almeida y Nunes (2019). *Hotel booking demand datasets*. Data in Brief, 22, 41–49.
