# Colmena inteligente: prototipo simulado (Apícola San Juan)

Esta carpeta contiene el prototipo del sistema de recomendación para las colmenas de Apícola San Juan. Como todavía no hay sensores instalados, el sistema se probó con **un mes de datos simulados**: 6 colmenas durante 30 días, con una lectura por hora de temperatura, peso y sonido.

Con esas lecturas, el sistema muestra un **semáforo** por colmena (verde, azul, amarillo o rojo) y **recomienda la acción de manejo** que conviene hacer (revisar, alimentar, poner o quitar alza, trampa de polen o alimentador, o recolectar), siempre con su motivo. Las recomendaciones salen de reglas y de comparar el estado de la colmena con el perfil de cada acción; no se usan modelos de inteligencia artificial ni de aprendizaje automático.

## Contenido de la carpeta

| Archivo o carpeta | Qué es |
|---|---|
| `Analisis_Caso_Apicola_San_Juan.docx` | Documento final: análisis del caso y explicación de la simulación (sección 5), con la figura de la colmena con IoT y los enlaces a los videos. |
| `recomendador_colmenas.ipynb` | Notebook con todo el código: simulador, semáforo, recomendador, demostración y evaluación. |
| `datos/` | Datos simulados y resultados en formato CSV (se generan al ejecutar el notebook). |
| `figuras/` | Las 7 gráficas del notebook en PNG (se generan al ejecutar el notebook). |

### Archivos de `datos/`

| Archivo | Contenido |
|---|---|
| `lecturas_sensores.csv` | Las 4 320 lecturas simuladas (temperatura, peso, frecuencia y nivel del zumbido) con la configuración de manejo y el estado real de cada colmena. |
| `eventos_simulados.csv` | Qué le pasó a cada colmena y cuándo (calor, frío, orfandad, enjambrazón, etc.) y los cambios de la bitácora. |
| `catalogo_acciones.csv` | Las acciones que puede recomendar el sistema y su perfil. |
| `recomendaciones_por_hora.csv` | Semáforo, estado identificado y recomendaciones de cada colmena hora por hora. |
| `horas_por_color_semaforo.csv` | Horas en cada color del semáforo por colmena. |
| `resultados_precision.csv` | Precision@3, Recall@3 y Acierto@3 del sistema frente a la referencia por popularidad. |
| `resultados_por_estado.csv` | Aciertos del sistema según el estado de la colmena. |
| `resultados_deteccion.csv` | Cuántas horas tardó el sistema en detectar cada evento. |
| `resultados_prioridad_colmenas.csv` | Orden de las colmenas por urgencia (a cuál ir primero). |

## Videos

Los videos están publicados en YouTube (no están dentro de esta carpeta):

1. **Presentación del proyecto:** de qué se trata, las problemáticas y cómo se piensa solucionar. https://youtu.be/QvSuWsxsv2A
2. **Explicación de la simulación:** cómo funciona el prototipo y qué resultados dio. https://youtu.be/tmlDMycYr8M

Los mismos enlaces están en la sección 5 del documento `Analisis_Caso_Apicola_San_Juan.docx`.

## Gráficas

Las gráficas se ven de tres formas: abriendo los PNG de la carpeta `figuras/`, dentro del notebook (debajo de cada celda) o en el documento Word.

| Gráfica | Qué muestra |
|---|---|
| `figuras/fig01_lecturas_por_estado.png` | Cómo se ven la temperatura, el peso y el sonido en cada estado de la colmena. |
| `figuras/fig02_semaforo_apiario.png` | El semáforo de las 6 colmenas hora por hora durante todo el mes. |
| `figuras/fig03_demo_c04_calor.png` | Colmena C04 durante una ola de calor. |
| `figuras/fig04_demo_c04_orfandad.png` | Colmena C04 cuando pierde la reina (orfandad). |
| `figuras/fig05_precision_por_estado.png` | Qué tanto acierta el sistema en cada estado. |
| `figuras/fig06_matriz_confusion.png` | Estado real frente al estado que identificó el sistema. |
| `figuras/fig07_cobertura_acciones.png` | Qué acciones recomienda el sistema y con qué frecuencia. |

La figura de la colmena con la ubicación de cada componente IoT (antena, panel solar, procesador, sensor de temperatura, micrófono y balanza) está dentro del documento Word, en la sección 5.2.

## Cómo ejecutar el notebook

1. Instalar Python 3 con `numpy`, `pandas`, `matplotlib` y Jupyter.
2. Abrir `recomendador_colmenas.ipynb` desde esta carpeta y ejecutar todas las celdas (tarda unos 10 segundos).
3. Al terminar se regeneran las carpetas `datos/` y `figuras/`, y la última celda confirma que todas las verificaciones automáticas pasaron (✔ OK).

Los datos simulados siempre salen iguales porque el simulador usa una semilla fija (2026).
