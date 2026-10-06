# El dataset que había que anonimizar

## Ficha

| Campo | Valor |
| --- | --- |
| Tipo | Ficticia |
| Categoría | Ética y privacidad |
| Rol o contexto | Data scientist |
| Fuente | No aplica |

## Contexto

Un equipo de datos preparaba un conjunto de registros de clientes para entregarle a un proveedor externo que iba a construir el primer tablero de la compañía. El objetivo era salir del análisis manual, y el plazo era de unas semanas.

## Qué ocurrió

En la revisión previa a la entrega, alguien revisó las columnas y vio que no hacía falta ningún nombre para identificar a personas concretas: rol, zona y frecuencia de compra alcanzaban para reconocer a alguien en una localidad chica. No era un dataset anónimo; era un dataset sin nombres.

Había dos caminos: entregar lo que ya estaba armado y revisar después, o frenar. Frenaron. Generalizaron la zona a región, redondearon los importes y reemplazaron los identificadores directos por claves internas que solo se resuelven dentro de la compañía. La entrega se corrió unas semanas y una de las copias que ya circulaban se retiró el mismo día.

Lo que hizo que la decisión fuera rápida no fue la herramienta: fue que existía una regla escrita antes —si los datos salen de la compañía, primero pasan por revisión de privacidad— y que alguien tenía que firmarla.

## Aprendizaje

Una persona se vuelve identificable sin nombrarla: rol, organización y momento juntos alcanzan. Por eso anonimizar no es quitar una columna de nombres al final del pipeline, sino una condición de salida que se decide antes de que los datos lleguen a un reporte, a un modelo o a un proveedor. Cada día sin esa regla son más copias del dataset circulando y menos control sobre quién las tiene.

## Pregunta para conversar

¿En qué punto de tu pipeline se decide que un dataset puede salir de la compañía, y quién tiene que firmar esa decisión?
