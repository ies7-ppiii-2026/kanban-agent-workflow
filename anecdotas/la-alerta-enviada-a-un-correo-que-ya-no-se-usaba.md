# La alerta enviada a un correo que ya no se usaba

## Ficha

| Campo | Valor |
| --- | --- |
| Tipo | Ficticia |
| Categoría | Incidentes |
| Rol o contexto | Equipo de operaciones de datos |
| Fuente | No aplica |

## Contexto

Un equipo de operaciones mantenía una tarea programada que consolidaba los datos de una fuente externa cada mañana y alimentaba el tablero con el que arrancaba la jornada. El proceso llevaba meses corriendo sin intervención.

## Qué ocurrió

La tarea empezó a tardar más del doble de lo habitual. El sistema seguía emitiendo su alerta, pero por correo, hacia la casilla del equipo: una dirección que se dejó de usar cuando el equipo se reorganizó y que quedó sin dueño. La alerta salía igual que siempre y llegaba a nadie.

El retraso se detectó durante el control de la mañana siguiente, cuando el tablero apareció vacío y el reporte no había salido. Recién ahí alguien se dio cuenta de que nadie había recibido el aviso. La tarea se recuperó el mismo día, sin pérdida de datos, pero el reporte salió tarde y hubo que explicar por qué nadie lo supo antes.

## Aprendizaje

Una alerta que nadie recibe no es peor que no tener alertas: es peor, porque produce la sensación de que hay monitoreo. Revisar periódicamente a qué canales llegan las alertas y quién es responsable de ellas es mantenimiento, igual que revisar credenciales o dependencias. Una prueba periódica del canal y un dueño claro por destino evitan que un proceso silencioso se descubra recién cuando alguien mira el resultado a mano.

## Pregunta para conversar

Si mañana fallara uno de tus procesos programados, ¿a quién le llegaría la alerta y cuándo fue la última vez que esa persona la abrió?
