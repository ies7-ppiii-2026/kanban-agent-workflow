# La columna renombrada que demoró las predicciones

## Ficha

| Campo | Valor |
| --- | --- |
| Tipo | Ficticia, basada en situaciones habituales de trabajo |
| Categoría | Producción |
| Rol o contexto | Ingeniero de machine learning |
| Fuente | No aplica |

## Contexto

Un equipo mantiene un pipeline de predicción diaria que consume datos de una fuente externa mediante un proceso ETL nocturno. La feature principal del modelo es `monto_ultima_transaccion`, calculada desde una tabla que llega por FTP cada madrugada. El pipeline valida el esquema de entrada antes de ejecutar el modelo.

## Qué ocurrió

Durante una actualización de versión del proveedor (marcada como "menor" en las release notes), la columna `monto_ultima_transaccion` fue renombrada a `ultimo_monto_tx` en el archivo CSV de entrega. La validación de esquema —que verificaba nombres y tipos esperados— detectó el cambio y **rechazó el lote completo**, impidiendo que el modelo se ejecutara con datos inválidos.

El pipeline se detuvo correctamente (fail-fast), pero el equipo no tenía un proceso ágil para actualizar el contrato de datos. Tuvieron que: 1) confirmar con el proveedor que el cambio era intencional y permanente, 2) ajustar la validación de esquema en el código, 3) volver a correr el pipeline manualmente. Las predicciones del día salieron con 4 horas de retraso, impactando las campañas matutinas.

## Aprendizaje

Validar el esquema en la entrada es necesario y correcto (fail-fast), pero sin un proceso de **gestión de cambios de esquema** (schema evolution) el sistema se vuelve frágil. Definí contratos de datos versionados, acordá SLA de notificación con proveedores críticos y automatizá la actualización de validadores cuando el cambio es compatible (ej. renombrado documentado). El objetivo no es evitar que falle, sino que la recuperación sea rutinaria, no una emergencia.

## Pregunta para conversar

¿Cómo diseñarías un contrato de datos versionado que permita renombrar columnas sin romper consumidores, y qué proceso pondrías para que la actualización del validador sea una tarea de minutos, no de horas?