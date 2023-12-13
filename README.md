# Optimización de planes de telefonía móvil: Desarrollo de un modelo predictivo para la recomendación de planes en megaline

## Introducción

Este proyecto busca mejorar la migración de los clientes de Megaline a sus nuevos planes "Smart" y "Ultra". Proponiendo el desarrollo de un modelo de clasificación que analice el comportamiento mensual de los usuarios para recomendar el plan más adecuado. Con datos detallados de clientes ya migrados, se explorará la segmentación, construcción y evaluación de modelos, ajustando hiperparámetros para lograr una precisión del 75%. Este enfoque basado en datos tiene como objetivo optimizar las decisiones estratégicas de Megaline y mejorar la satisfacción del cliente.

### Observaciones del análisis del DataFrame

En resumen, el conjunto de datos 'users_behavior_df', compuesto por 3214 registros y 5 columnas. Se verificó la consistencia de tipos de datos, no encontrando valores nulos. Se le cambió el nombre a la columna 'mb_used' por 'gb_used' para mayor claridad. Además, la columna 'gb_used' se convirtió de megabytes a gigabytes, redondeando a dos decimales. Estas modificaciones buscan mejorar la interpretación y coherencia de los datos, facilitando así su análisis.

### Observaciones de la segmentación de datos

Conjunto de Entrenamiento (train_data): Se asigna el 70% de los datos para el entrenamiento. Este tamaño es una elección común y proporciona una cantidad sustancial de datos para que el modelo aprenda patrones y relaciones en los datos.

Conjunto de Validación (valid_data): Se utiliza el 50% del 30% restante (es decir, el 15% original) para formar el conjunto de validación. La elección de usar el 15% es común y proporciona suficientes datos para ajustar los hiperparámetros del modelo y evitar el sobreajuste.

Conjunto de Prueba (test_data): Se utiliza el otro 50% del 30% restante (también el 15% original) para formar el conjunto de prueba. Este conjunto se mantiene separado durante todo el proceso de desarrollo del modelo y solo se utiliza al final para evaluar el rendimiento del modelo en datos no vistos.

La suma del porcentaje utilizado para entrenamiento, validación y prueba es del 100%, asegurando que todos los datos estén asignados y que no haya solapamiento entre los conjuntos. La elección de estos porcentajes puede variar según la naturaleza específica del problema y la cantidad total de datos disponibles. En este caso, se optó por una división equitativa y conservadora para garantizar un buen rendimiento del modelo en distintas fases del desarrollo.

### Observaciones de la selección de características y variable objetivo

Se ha establecido una lista de características (features) que abarca 'calls', 'minutes', 'messages' y 'gb_used'. Estas constituyen las variables que se emplearán para el entrenamiento de los modelos. La variable objetivo (target) se define como 'is_ultra', representando la variable que se busca predecir; en este contexto, se refiere al tipo de plan: 'Smart' (0) o 'Ultra' (1).

### Observaciones del entrenamiento de los modelos

El código realiza la búsqueda de hiperparámetros óptimos para tres modelos de clasificación (Árbol de Decisión, Bosque Aleatorio y Regresión Logística) utilizando GridSearchCV. Se exploran diferentes valores de hiperparámetros como la profundidad máxima del árbol, el número de árboles en el Bosque Aleatorio y los parámetros de regularización en la Regresión Logística. Se establece random_state para garantizar reproducibilidad, y se utiliza validación cruzada con 5 divisiones para evaluar el rendimiento de los modelos. Los resultados y métricas se almacenan para su posterior evaluación en conjuntos de validación y prueba.

### Observaciones de la evaluación el rendimiento de los modelos

En la evaluación de los modelos, se observa que el Bosque Aleatorio supera al Árbol de Decisión y a la Regresión Logística en términos de rendimiento. El Bosque Aleatorio exhibe la mayor exactitud en los conjuntos de validación (79.88%) y prueba (79.92%), demostrando un equilibrio sólido entre precisión y exhaustividad. Aunque el Árbol de Decisión muestra un rendimiento aceptable con una exactitud del 78.26% en prueba, enfrenta dificultades para identificar correctamente casos 'Ultra'. La Regresión Logística tiene la exactitud más baja (74.95% en prueba) y también muestra desafíos en la identificación de casos 'Ultra'. En general, se recomienda seleccionar el Bosque Aleatorio como el modelo preferido y se sugiere seguir ajustándolo para mejorar aún más su rendimiento mediante la optimización de hiperparámetros.

### Observaciones de la prueba de cordura

En la prueba de cordura, se utiliza un Dummy Classifier con la estrategia de predecir siempre la clase más frecuente. Los resultados muestran que este Dummy Classifier tiene una precisión del 69.57%. Al comparar este resultado con los modelos reales, se observa que tanto el Árbol de Decisión (79.46%) como el Bosque Aleatorio (81.46%) superan significativamente al Dummy Classifier en términos de precisión en el conjunto de prueba. La Regresión Logística, aunque tiene una precisión más baja (75.28%), sigue siendo superior al Dummy Classifier. Estos hallazgos indican que los modelos desarrollados ofrecen mejoras sustanciales sobre una estrategia de predicción simple como la del Dummy Classifier, lo que respalda la validez y utilidad de los modelos en la clasificación de los planes de telefonía móvil.

## Conclusión

El proyecto de optimización de planes de telefonía móvil para Megaline presenta un análisis sistemático y estructurado, desde la importación de librerías hasta la evaluación de modelos. Se destaca por la exploración detallada y mejoras en la preparación de datos, como el cambio de nombre de columnas y la conversión de unidades. La segmentación de datos y la selección de características son justificadas, y el entrenamiento de modelos, incluyendo Árbol de Decisión, Bosque Aleatorio y Regresión Logística, se realiza con optimización de hiperparámetros. La evaluación indica que el Bosque Aleatorio es la mejor opción, superando a los otros modelos en precisión. La prueba de cordura confirma que los modelos superan una estrategia simple. En conjunto, el proyecto ofrece un enfoque sólido para respaldar decisiones estratégicas en la migración de clientes a los nuevos planes de Megaline.
