# La zona horaria que duplicó las ventas

## Ficha

| Campo | Valor |
| --- | --- |
| Tipo | Ficticia |
| Categoría | Producción |
| Rol o contexto | Data engineer |
| Fuente | No aplica |

## Contexto

Un equipo de analítica construyó un pipeline nocturno que agrupaba los eventos de venta por día y publicaba un reporte con el total diario. El job corría sin problemas y el tablero se actualizaba todas las mañanas.

## Qué ocurrió

Los eventos llegaban en UTC, pero el reporte se calculaba usando la fecha local del servidor que ejecutaba el job. Al cambiar el horario de verano, una franja de eventos quedó fuera del día que le correspondía y se contó dos veces en el reporte siguiente. El total diario apareció un 8% más alto de lo real y el equipo tomó decisiones de stock basándose en un número inflado.

Nadie revisaba el total acumulado porque cada día "parecía razonable". El error se detectó recién cuando el número de ventas superó las unidades físicas disponibles en depósito.

## Aprendizaje

Guardá y procesá los timestamps siempre en una zona horaria única (UTC) y convertí a local solo en la capa de presentación. Si el negocio define el "día" según una zona distinta, hacelo explícito y probalo con casos límite de cambios de horario.

## Pregunta para conversar

¿En qué capa de tu pipeline definirías el concepto de "día" y cómo lo probarías para que un cambio de horario no altere un total?
