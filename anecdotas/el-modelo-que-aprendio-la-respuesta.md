# El modelo que aprendió la respuesta

## Ficha

| Campo | Valor |
| --- | --- |
| Tipo | Ficticia |
| Categoría | Incidentes |
| Rol o contexto | Data scientist |
| Fuente | No aplica |

## Contexto

Un equipo entrenaba un modelo para predecir la probabilidad de churn de clientes al final de cada mes. Usaban variables históricas de uso, tickets de soporte y facturación. El modelo mostraba un AUC de 0.98 en validación y el equipo estaba convencido de que habían dado en el clavo.

## Qué ocurrió

Al revisar la ingeniería de features, alguien notó que una columna llamada `churn_mes_siguiente` —que indicaba si el cliente efectivamente se fue el mes posterior— había quedado incluida en el set de entrenamiento por un error en el script de feature engineering. El modelo no aprendió patrones de comportamiento; simplemente memorizó la etiqueta que ya tenía frente a sus ojos.

Cuando se reentrenó sin esa variable, el AUC cayó a 0.72. El modelo original era inútil en producción porque, obviamente, no se conoce el churn del mes siguiente antes de que ocurra.

## Aprendizaje

La fuga de datos (data leakage) es uno de los errores más silenciosos y peligrosos: el modelo parece funcionar perfectamente, pero solo porque tiene acceso a información que no estará disponible en el momento de la inferencia. Separar estrictamente el target de los features, validar con splits temporales y auditar el pipeline de features son defensas indispensables.

## Pregunta para conversar

¿Qué controles automáticos agregarías a tu pipeline de features para detectar una fuga de target antes de que el modelo llegue a producción?