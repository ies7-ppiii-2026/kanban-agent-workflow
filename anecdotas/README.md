# Índice de anécdotas

Las anécdotas se incorporan mediante pull requests y se agregan a este índice durante el mismo cambio.

## Colecciones

| Colección | Historias que reúne |
| --- | --- |
| [Primeros incidentes con datos](coleccion-primeros-incidentes.md) | [Zona horaria](zona-horaria-que-duplico-ventas.md), [fuga de target](el-modelo-que-aprendio-la-respuesta.md) |

## Categorías

| Categoría | Descripción | Anécdotas |
| --- | --- | --- |
| Incidentes | Fallas, errores y recuperaciones. Ej.: una fuga de datos contamina el entrenamiento y hay que corregirlo. | [El modelo que aprendió la respuesta](el-modelo-que-aprendio-la-respuesta.md), [La alerta enviada a un correo que ya no se usaba](la-alerta-enviada-a-un-correo-que-ya-no-se-usaba.md), [Los registros que no aparecían en el tablero](los-registros-que-no-aparecian-en-el-tablero.md), [El pipeline que se quedó sin memoria](pipeline-sin-memoria.md), [Los contactos duplicados en una campaña](contactos-duplicados-en-una-campana.md), [El CSV exportado con otro separador](csv-exportado-con-otro-separador.md) |
| Aprendizajes | Descubrimientos surgidos de la práctica. Ej.: una prueba revela una regla de negocio que nadie había documentado. | — |
| Decisiones técnicas | Elecciones, alternativas y consecuencias. Ej.: se comparan dos formatos de almacenaje y se elige uno. | — |
| Trabajo en equipo | Comunicación, coordinación y procesos. Ej.: dos equipos acuerdan quién valida los datos antes del reporte. | — |
| Ética y privacidad | Uso responsable de datos e IA. Ej.: un dataset con datos personales obliga a anonimizar antes de publicar. | [El dataset que había que anonimizar](el-dataset-que-habia-que-anonimizar.md) |
| Producción | Despliegue, operación y mantenimiento. Ej.: un reporte nocturno en ejecución publica totales incorrectos. | [La zona horaria que duplicó las ventas](zona-horaria-que-duplico-ventas.md), [La columna renombrada que demoró las predicciones](la-columna-renombrada-que-demoro-las-predicciones.md) |

## Cómo elegir la categoría

Cada anécdota va en **una sola** categoría. La regla es clasificar por el **evento central** de la historia (de qué trata), no por el lugar donde ocurrió ni por las secciones que repita la plantilla.

- **Incidentes vs. Producción.** En [La zona horaria que duplicó las ventas](zona-horaria-que-duplico-ventas.md) hay una falla dentro de un pipeline en ejecución, pero el eje de la historia es cómo opera un reporte que corre todas las noches: por eso está en Producción. Si el eje fuera detectar y recuperar de una caída, correspondería Incidentes.
- **Aprendizajes frente al resto.** Toda anécdota incluye una sección *Aprendizaje*, así que esa sección no decide la categoría: Aprendizajes es para historias cuyo eje es un descubrimiento, no para las que solo contienen uno.
- **Trabajo en equipo vs. Ética y privacidad.** Si el eje es cómo se comunicaron o coordinaron las personas, corresponde Trabajo en equipo; si es una decisión sobre el uso responsable de datos o IA, corresponde Ética y privacidad.

No se agregan categorías nuevas sin un caso de uso concreto que las justifique.

Para proponer una historia, copiá [plantilla.md](plantilla.md), usá un nombre descriptivo en `kebab-case` y agregá el enlace en la categoría correspondiente.