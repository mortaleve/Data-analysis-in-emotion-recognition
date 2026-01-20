# Data-analysis-in-emotion-recognition

Este repositorio contiene el código utilizado para el análisis estadístico de un estudio experimental de reconocimiento emocional facial en estudiantes universitarios. Los análisis se realizaron en R y corresponden exactamente a los resultados reportados en el manuscrito asociado.

Descripción general

El estudio evalúa el desempeño en una tarea de reconocimiento emocional a partir de estímulos visuales dinámicos, considerando dos indicadores principales:
	•	Exactitud (respuesta correcta vs. incorrecta, a nivel de ensayo).
	•	Tiempo de reacción (RT), analizado únicamente en ensayos con respuestas correctas.

Asimismo, se examina el rol del grupo académico (primer vs. cuarto año), la emoción objetivo, y variables de control a nivel individual (edad, género y estado afectivo medido mediante PANAS).

El repositorio incluye:
	•	Preparación y limpieza de datos experimentales y psicométricos.
	•	Análisis descriptivos con intervalos de confianza bootstrap BCa.
	•	Modelos mixtos a nivel de ensayo para exactitud y tiempo de reacción.
	•	Comparaciones post hoc basadas en medias marginales estimadas.
	•	Generación de tablas y figuras utilizadas en el artículo.

⸻

Estructura del repositorio
	•	DataAnalisys.Rmd
Documento principal que contiene todo el flujo de análisis, desde la preparación de datos hasta los modelos finales reportados en el paper.
	•	trials_master
Base de datos experimental a nivel de ensayo (exactitud y tiempo de reacción).
	•	panas_master
Respuestas individuales al cuestionario PANAS en formato largo.
	•	Figuras exportadas (.png)
Gráficos descriptivos y de probabilidades predichas reportados en el manuscrito.

⸻

Preparación de los datos
	1.	Base experimental
	•	Conversión de variables a sus tipos adecuados (factores, numéricos).
	•	Codificación binaria de la exactitud.
	•	Filtrado de tiempos de reacción inválidos.
	2.	PANAS
	•	Limpieza y estandarización de etiquetas de ítems.
	•	Cálculo de puntajes compuestos de Afecto Positivo (PA) y Afecto Negativo (NA).
	•	Verificación de respuestas completas (20 ítems por participante).
	•	Estimación de la consistencia interna mediante alfa de Cronbach.
	3.	Integración de bases
	•	Unión de datos experimentales y psicométricos a nivel de participante.

⸻

Análisis estadísticos

Análisis descriptivos
	•	Exactitud y tiempo de reacción por emoción y grupo académico.
	•	Intervalos de confianza del 95% estimados mediante bootstrap BCa a nivel de participante.

Asociación entre estado afectivo y desempeño
	•	Correlaciones de Spearman entre PA, NA y:
	•	Exactitud media.
	•	Tiempo de reacción medio (ensayos correctos).

Modelos mixtos

Exactitud
	•	Modelo logístico mixto a nivel de ensayo.
	•	Efectos fijos:
	•	Emoción objetivo.
	•	Grupo académico.
	•	Edad, género, PA y NA.
	•	Intercepto aleatorio por participante.
	•	Evaluación de interacción emoción × grupo académico mediante comparación de modelos anidados.

Tiempo de reacción
	•	Modelo lineal mixto sobre RT transformado logarítmicamente.
	•	Análisis restringido a ensayos correctos.
	•	Mismos predictores y estructura aleatoria que el modelo de exactitud.
	•	Comparación entre modelo con y sin interacción emoción × grupo.

Comparaciones post hoc
	•	Exactitud: contrastes sobre odds ratios con corrección de Holm.
	•	Tiempo de reacción: contrastes sobre medias marginales estimadas (escala log-RT), con corrección de Holm.
	•	Resultados sintetizados mediante sistema de letras para facilitar la interpretación.

⸻

Reproducibilidad
	•	El código está diseñado para ejecutarse de forma secuencial y reproducible.
	•	Se fijan semillas cuando corresponde (bootstrap).
	•	Todas las decisiones analíticas reflejan exactamente lo reportado en el manuscrito.
	•	No se incluyen análisis exploratorios no reportados.

⸻

Requisitos

Paquetes principales utilizados:
	•	tidyverse
	•	lme4
	•	emmeans
	•	boot
	•	psych
	•	ggplot2

Versión de R recomendada: ≥ 4.2

⸻

Nota final

Este repositorio tiene como objetivo garantizar transparencia, reproducibilidad y trazabilidad analítica del estudio. Cualquier modificación al código debería reflejarse explícitamente en los resultados y en el manuscrito asociado.
