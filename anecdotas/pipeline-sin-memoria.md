# El pipeline que se quedó sin memoria

## Ficha

| Campo | Valor |
| --- | --- |
| Tipo | Ficticia |
| Categoría | Incidentes |
| Rol o contexto | Data engineer |
| Fuente | No aplica |

## Contexto

Un pipeline de ETL nocturno procesaba datos de ventas de la semana para generar reportes ejecutivos. El job corría en un contenedor con 4 GB de RAM y había funcionado sin problemas durante meses.

## Qué ocurrió

Una noche, el pipeline falló con un error de `OutOfMemoryError`. El equipo descubrió que una fuente de datos había crecido un 300% debido a un cambio en el proceso de recolección: ahora incluía eventos duplicados por un bug en el productor de datos.

El pipeline intentaba cargar todos los datos en memoria antes de procesarlos, y con el volumen triplicado, superó el límite del contenedor.

## Aprendizaje

- **Monitorear el crecimiento de las fuentes de datos**: Un cambio en el volumen puede romper pipelines que antes funcionaban.
- **Diseñar para la escalabilidad**: Los pipelines deben manejar variaciones en el volumen de datos, no solo el caso base.
- **Alertas tempranas**: Configurar alertas de uso de memoria y tiempo de ejecución para detectar problemas antes de que afecten a los reportes.

## Pregunta para conversar

¿Qué estrategias usan en sus equipos para manejar el crecimiento inesperado en el volumen de datos sin aumentar la infraestructura?
