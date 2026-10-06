# Los registros que no aparecían en el tablero

## Ficha

| Campo | Valor |
| --- | --- |
| Tipo | Ficticia |
| Categoría | Incidentes |
| Rol o contexto | Analista de negocio |
| Fuente | No aplica |

## Contexto

Un equipo de análisis publicaba un tablero que agrupaba los pedidos por categoría y mostraba el total de cada una. El equipo de negocio lo usaba para repartir presupuesto entre categorías, y el cierre semanal terminaba con la suma de esos grupos.

## Qué ocurrió

Los totales individuales de cada categoría eran correctos, pero su suma no coincidía con el total de la fuente. La diferencia era chica y siempre del mismo signo, así que durante un tiempo se leyó como un redondeo.

La causa apareció al cruzar los números: los registros cuyo valor de categoría estaba vacío no entraban en ningún grupo. Al agrupar, el tablero los descartaba en lugar de mostrarlos como sin categoría, y esas filas desaparecían sin dejar rastro. Cada grupo sumaba exactamente lo que decía sumar, por eso los parciales se veían bien; el faltante sólo se veía al comparar contra un total que viniera de la fuente y no del agrupado.

Se corrigió mostrando los vacíos como una categoría con nombre propio y agregando una comprobación que compara la suma de los grupos contra el total de origen. A partir de ahí esa diferencia dejó de pasar desapercibida.

## Aprendizaje

Agrupar es una operación que descarta lo que no encaja, y el descarte no avisa. Un tablero puede ser correcto en cada una de sus partes y equivocado en su total, y la única señal es contrastar contra un número que no haya pasado por el mismo agrupamiento. Los valores faltantes conviene tratarlos como un caso visible en la visualización, no como una ausencia.

## Pregunta para conversar

¿Qué comprobaciones mínimas exigirías en un tablero para que un grupo vacío o incompleto se vea antes de que alguien tome una decisión con esos números?
