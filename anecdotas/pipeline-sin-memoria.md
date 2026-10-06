# El pipeline que se quedó sin memoria

## Ficha

| Campo | Valor |
| --- | --- |
| Tipo | Ficticia |
| Categoría | Incidentes |
| Rol o contexto | Data engineer |
| Fuente | No aplica |

## Contexto

Un pipeline de ETL (extracción, transformación y carga) nocturno procesaba datos de ventas de la semana para generar reportes ejecutivos. El job corría en un contenedor con 4 GB de RAM y había funcionado sin problemas durante meses.

## Qué ocurrió

Una noche, el pipeline falló con un error de `OutOfMemoryError` (falta de memoria). El equipo descubrió que una fuente de datos había crecido un 300% debido a un cambio en el proceso de recolección: ahora incluía eventos duplicados por un bug en el productor de datos.

El pipeline intentaba cargar todos los datos en memoria antes de procesarlos, y con el volumen triplicado, superó el límite del contenedor.

## Aprendizaje

Un pipeline que carga todo en memoria falla en cuanto la fuente crece. Conviene alertar sobre el uso de memoria y el tiempo de ejecución, y diseñar el procesamiento para tolerar variaciones de volumen, no solo el caso base.

## Pregunta para conversar

¿Qué estrategias usan en sus equipos para manejar el crecimiento inesperado en el volumen de datos sin aumentar la infraestructura?
