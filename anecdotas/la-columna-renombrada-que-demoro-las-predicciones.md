# La columna renombrada que demoró las predicciones

## Ficha

| Campo | Valor |
| --- | --- |
| Tipo | Ficticia, basada en situaciones habituales de trabajo |
| Categoría | Producción |
| Rol o contexto | Ingeniero de machine learning |
| Fuente | No aplica |

## Contexto

Un equipo mantiene un pipeline de predicción diaria que consume datos de una fuente externa mediante un proceso ETL nocturno. La feature principal del modelo es `monto_ultima_transaccion`, calculada desde una tabla que llega por FTP cada madrugada.

## Qué ocurrió

Durante una actualización de versión del proveedor (marcada como "menor" en las release notes), la columna `monto_ultima_transaccion` fue renombrada a `ultimo_monto_tx` en el archivo CSV de entrega. El proceso ETL no falló porque la validación de esquema solo verificaba la presencia de columnas esperadas por posición, no por nombre. Como resultado, la feature quedó vacía (`NULL`) para todo el lote del día.

El modelo, al recibir `NULL` en su feature más predictiva, empezó a emitir scores sesgados hacia la media histórica. Las predicciones se usaron para ofertas automáticas y el equipo notó la anomalía recién al mediodía, cuando las métricas de conversión cayeron un 15 %. Tardaron tres horas en rastrear el origen: el cambio de nombre de columna no comunicado.

## Aprendizaje

Los contratos de datos (data contracts) deben validarse por nombre y tipo, no solo por posición. Cualquier cambio en el esquema de una fuente externa —aunque el proveedor lo considere menor— rompe la compatibilidad si no hay versionado explícito. Implementá validaciones de esquema estrictas en el borde de entrada (schema registry, Great Expectations, pandera) y exigí notificación previa de cambios a proveedores críticos.

## Pregunta para conversar

¿Cómo diseñarías un contrato de datos que permita evolucionar el esquema de la fuente sin romper consumidores, y qué mecanismo de alerta pondrías para detectar un cambio silencioso en la primera hora?