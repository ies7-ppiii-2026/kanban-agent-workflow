# Los contactos duplicados en una campaña

## Ficha

| Campo | Valor |
| --- | --- |
| Tipo | Ficticia |
| Categoría | Incidentes |
| Rol o contexto | Ingeniero de datos |
| Fuente | No aplica |

## Contexto

Un equipo de marketing preparaba una campaña de correo y necesitaba una audiencia única. Los contactos venían de dos fuentes: la exportación del CRM, con el historial de compras, y la lista de suscripciones al blog, con los formularios que cargaban las personas. Las dos se consideraban complementarias y nadie las había integrado antes.

## Qué ocurrió

La unión se hizo usando el correo como clave, pero cada fuente lo guardaba distinto: una con mayúsculas y espacios, la otra con un alias de dominio. Al normalizar de manera inconsistente, parte de los contactos quedó duplicada con dos identificadores distintos. El conteo final de la audiencia dio cerca de un 12% más de destinatarios que el estimado del plan.

La diferencia apareció al comparar el total contra la lista base, antes de enviar. En lugar de mandar igual, el equipo frenó, definió una clave de identidad única (correo en minúsculas, sin alias) y una regla de precedencia: gana el registro más reciente. Después de depurar, la audiencia volvió al número esperado y la campaña salió un día más tarde.

## Aprendizaje

Los criterios de identidad y de deduplicación se definen antes de integrar fuentes, no cuando ya aparecieron los duplicados. Conviene acordar cuál es la clave canónica, cómo se normaliza y qué registro prevalece, y dejar esa decisión escrita en el contrato del dato. Un conteo de control contra una base conocida, antes de cada envío, hace visible el problema en minutos y evita escribir dos veces a la misma persona.

## Pregunta para conversar

¿En qué momento de tu flujo de integración definirías la clave de identidad de un contacto y quién tendría que aprobarla?
