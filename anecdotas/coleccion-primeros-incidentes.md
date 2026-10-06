# Primeros incidentes con datos

Colección temática que reúne las dos primeras historias del índice. No repite su contenido: las enlaza y explica qué tienen en común.

## Qué conecta a las historias

Las dos historias fallan de la misma forma, aunque una ocurra en un pipeline de datos y la otra en un modelo:

- **Ninguna avisa.** En ambos casos el sistema siguió corriendo y publicando números plausibles; la señal de error no era un error técnico, sino un total que parecía razonable.
- **La suposición estaba implícita.** Una definió "día" con la fecha local del servidor sin declararlo; la otra mezcló la etiqueta futura con las variables de entrada. En los dos, el dato existía y estaba bien formado: lo que falló fue el supuesto que nadie había escrito.
- **Se descubrió tarde y por fuera.** Ninguno se detectó con un test automático: uno cuando las ventas superaron el stock físico, el otro al auditar el script de features.
- **La defensa es la misma.** Hacer explícito el supuesto en el borde del pipeline (zona horaria única, separación estricta de features y target) y probarlo con los casos límite que hoy no se están probando.

## Las historias

| Historia | Categoría | Incidente |
| --- | --- | --- |
| [La zona horaria que duplicó las ventas](zona-horaria-que-duplico-ventas.md) | Producción | Un reporte diario inflado por agrupar eventos UTC con la fecha local del servidor. |
| [El modelo que aprendió la respuesta](el-modelo-que-aprendio-la-respuesta.md) | Incidentes | Un AUC de 0.98 sostenido por la variable que contenía el resultado futuro. |

## Pregunta para conversar

Si tuvieras que revisar un pipeline existente mañana, ¿qué supuesto escribirías primero y con qué prueba lo confirmarías?
