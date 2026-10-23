# El feature que dejó de existir

## Ficha

| Campo | Valor |
| --- | --- |
| Tipo | Ficticia |
| Categoría | Producción |
| Rol o contexto | Ingeniero de machine learning |
| Fuente | No aplica |

## Contexto

Un equipo operaba un modelo de scoring crediticio que se ejecutaba todos los días para priorizar solicitudes. Entre las variables que usaba había una de ingresos verificados, calculada a partir de una tabla de validaciones que mantenía un proveedor externo. El pipeline tomaba esa tabla, armaba las variables y puntuaba cada solicitud; el modelo llevaba meses funcionando con resultados estables.

## Qué ocurrió

En una actualización, el proveedor cambió el esquema de la tabla: el campo que alimentaba la variable de ingresos dejó de llegar con el mismo nombre. El pipeline no falló. La transformación encontró el campo vacío, completó la variable con nulos y siguió adelante, porque nada validaba que la proporción de nulos estuviera dentro de un rango esperado.

Durante varias semanas el modelo puntuó con esa variable en null para todos los registros. Las predicciones seguían saliendo y el tablero de operación mostraba el proceso como exitoso: no había errores, solo una columna vacía que nadie miraba. La caída de calidad apareció cuando el área de negocio notó que las aprobaciones se apartaban de lo habitual. Al comparar contra ejecuciones anteriores, el equipo encontró la variable vacía en el 100% de los casos y rastreó el origen hasta el cambio de esquema del proveedor.

Se restableció la fuente, se reprocesaron las predicciones afectadas y se agregaron controles: una alerta cuando la proporción de nulos de una variable supera un umbral, una comparación de la distribución contra la última ejecución válida y una verificación de que los campos críticos llegan con datos.

## Aprendizaje

Un pipeline que no falla no está necesariamente sano: los nulos pueden reemplazar a un dato faltante sin romper nada y el modelo sigue respondiendo con menos información. Validar la presencia y la distribución de las variables críticas, alertar cuando cambian y tratar los nulos inesperados como un incidente permite detectar la degradación el mismo día en que empieza, no cuando el negocio nota el efecto.

## Pregunta para conversar

¿Qué controles agregarían a un pipeline para distinguir un nulo legítimo de una fuente que dejó de entregar un dato?
