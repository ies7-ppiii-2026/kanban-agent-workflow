# El CSV exportado con otro separador

## Ficha

| Campo | Valor |
| --- | --- |
| Tipo | Ficticia |
| Categoría | Incidentes |
| Rol o contexto | Analista de datos |
| Fuente | No aplica |

## Contexto

Cada mes, un analista de datos exportaba un reporte desde una planilla compartida para cargarlo en una herramienta de visualización. El archivo se generaba y se procesaba igual en cada ciclo, así que el control del formato se había dejado de hacer: si la carga no marcaba error, el archivo se daba por bueno.

## Qué ocurrió

En una de esas corridas, la exportación salió con punto y coma como separador en lugar de coma. El CSV (valores separados por comas) se generó completo, pero con otro carácter delimitador (el que divide los campos dentro de cada fila), y el proceso de carga no falló: aceptó el archivo y lo guardó sin quejarse.

El problema apareció después, al revisar el reporte. Varios campos habían quedado todos juntos en una sola columna y los totales no coincidían. Hubo que identificar el separador real, volver a exportar el archivo y repetir la importación. La corrección ocupó unas horas y el reporte salió con demora, pero no se perdió ni se corrompió ningún dato.

## Aprendizaje

Que la carga no falle no significa que el archivo esté bien: muchas herramientas aceptan un formato equivocado y lo guardan igual. Validar separador, columnas esperadas y unas filas de muestra antes de procesar traslada el error al inicio, cuando corregirlo cuesta minutos y no hay que repetir la importación.

## Pregunta para conversar

¿Cómo conviene configurar la carga para que un archivo con un formato inesperado se rechace en lugar de guardarse?
