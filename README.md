# Módulo 6 — Modelos Avanzados de IA y Aplicaciones Económicas

Material de clase del **Diplomado en Big Data e Inteligencia Artificial** (CEC EPN).

Siete jornadas (13 al 24 de noviembre de 2026) para entender y aplicar **modelos bayesianos y redes neuronales** en problemas económicos, retomando los modelos no paramétricos del Módulo 3 y el forecasting del Módulo 5. El principio del módulo: **antes de programar, cada idea se explica con un ejemplo, se calcula a mano con números pequeños y se interpreta**; después se comprueba en Python.

## Contenido

```
modulo6_modelos_avanzados_ia_aplicaciones_economicas/
├── README.md
├── presentaciones/      diapositivas por unidad (pptx y pdf)
├── notebooks/           un notebook por unidad
└── datos/
    ├── impago_tarjetas.csv       30 000 clientes de tarjeta de crédito (caso del módulo)
    └── series_economicas.csv     series mensuales del Ecuador (las del Módulo 5)
```

## Ruta por unidad

A diferencia del Módulo 5, aquí hay **un notebook por unidad**, no por día.

| Unidad | Notebook | Jornadas | Contenidos | Evaluación |
|---|---|---|---|---|
| 1. Modelos no paramétricos | `01_U1_Modelos_No_Parametricos` | 13-11 (2 h) | KNN a mano y escalado, kernel, árbol y Random Forest, bagging frente a boosting, guía de elección | Diagnóstica |
| 2. Modelos bayesianos | `02_U2_Modelos_Bayesianos` | 13-11 (1 h), 16-11 y 17-11 | Bayes con 1 000 clientes, prior y posterior, tasa base, actualización secuencial, intervalos creíbles, Naive Bayes, regresión bayesiana, red bayesiana, decisión con costos | Actividad 1 (20 pts) |
| 3. Introducción a Deep Learning | `03_U3_Introduccion_Deep_Learning` | 18-11, 19-11 y 23-11 (1 h) | Neurona a mano, propagación hacia adelante, pérdida, descenso del gradiente, retropropagación, Keras, sobreajuste, comparación con líneas base | Actividad 2 (20 pts) y Actividad 3 (20 pts) |
| 4. Aplicaciones económicas | `04_U4_Aplicaciones_Economicas` | 23-11 (2 h) | Objetivo y línea base, anomalías y falsos positivos, segmentación, Test con incertidumbre y costos, ficha ejecutiva | — |
| 5. Proyecto final | `05_U5_Proyecto_Final` | 24-11 (2 h) | Plantilla del proyecto: ruta de clasificación y ruta de pronóstico | Proyecto final (40 pts) |

### El caso que une el módulo

Un banco emisor de tarjetas quiere saber, en septiembre, **qué clientes no pagarán en octubre**. Las Unidades 1 a 4 usan los mismos 30 000 clientes y **la misma partición** (60 % Train, 20 % Validation, 20 % Test, semilla 42), de modo que los resultados se pueden comparar entre unidades. El Test se abre una sola vez, en la Unidad 4.

| Modelo | AUC Validation | AUC Test |
|---|---:|---:|
| Regla del atraso (línea base) | 0.683 | 0.676 |
| Regresión logística | 0.724 | 0.709 |
| Naive Bayes | 0.734 | 0.723 |
| Red neuronal 32 + 16 | 0.777 | 0.775 |
| Boosting | 0.781 | 0.778 |
| Random Forest | 0.783 | 0.768 |

### Cómo está organizado cada notebook

1. **Preparación**: instalación de librerías y datos (funciona igual en local y en Colab).
2. **La idea**, con un ejemplo de la vida diaria.
3. **A mano**, con números pequeños.
4. **En Python**, con el código comentado y una explicación antes y después de cada celda.
5. **Comparación con la línea base** en datos que el modelo no vio.
6. **Checklist** de la unidad.

## Preparación y ejecución

**En Google Colab:** abre el notebook y ejecuta las dos primeras celdas de código. Los datos se descargan de este repositorio.

**En tu computador:**

1. Instala **Python 3.10 o posterior** con Jupyter (por ejemplo, con Anaconda).
2. Abre la carpeta en Jupyter y ejecuta cada notebook **de arriba hacia abajo**. La primera celda instala lo que falte: `numpy`, `pandas`, `matplotlib`, `scikit-learn`, `scipy` y, desde la Unidad 3, `tensorflow` (incluye Keras).
3. Si la instalación de TensorFlow falla en tu equipo, usa Colab para las Unidades 3, 4 y 5.

Tiempos aproximados de ejecución completa: Unidad 1, 1 minuto; Unidad 2, 30 segundos; Unidad 3, 3 minutos; Unidad 4, 1 minuto; Unidad 5, 2 minutos.

La Unidad 3 guarda la red entrenada en `notebooks/resultados_modulo6/`. La Unidad 4 la carga si existe y, si no, la entrena de nuevo.

## Datos

Ver `datos/README.md` para el detalle de columnas y fuentes.

- `impago_tarjetas.csv`: *Default of Credit Card Clients* (Yeh y Lien, 2009; UCI Machine Learning Repository), con las columnas renombradas al español.
- `series_economicas.csv`: series mensuales del INEC y del Banco Central del Ecuador, la misma tabla del Módulo 5.
