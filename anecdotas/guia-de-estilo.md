# Guía de estilo para las anécdotas

La estructura de una historia está en [plantilla.md](plantilla.md) y las reglas de contenido en [../CONTRIBUTING.md](../CONTRIBUTING.md). Esta guía define cómo se escribe.

## Tono y voz

- Tercera persona o impersonal: "el equipo descubrió", no "descubrí" ni "resulta que mágicamente".
- Una historia por archivo. Si hay dos incidentes separados, son dos anécdotas.
- Jerga solo cuando aporta, y la primera vez se explica entre paréntesis: *data leakage (información del futuro filtrada al modelo)*.
- Se narra el hecho y su consecuencia; no se juzga ni se nombra a las personas.
- Números redondeados sí, números inventados exactos solo en historias marcadas como ficticias.

## Longitud

| Sección | Extensión |
| --- | --- |
| Ficha | las cuatro filas de la plantilla, sin texto libre |
| Contexto | 1 párrafo (3 a 5 líneas) |
| Qué ocurrió | 1 o 2 párrafos |
| Aprendizaje | 1 párrafo, máximo 4 líneas |
| Pregunta para conversar | 1 sola oración |

- **Mínimo:** las cinco secciones presentes y unas 150 palabras.
- **Máximo:** unas 400 palabras. Si no entra, la historia contiene dos lecciones: separalas.
- El nombre del archivo va en `kebab-case`, sin número de issue ni año.

## Cómo citar fuentes

- **Hecho verificable** (documentación, paper, artículo): enlace con título, con el formato `[Título del documento](https://…)`. El enlace va en el texto, no al final de la sección.
- **Hecho atribuible a una persona o equipo**: fuente **y** autorización, o se anonimiza y se retira la atribución (regla completa en CONTRIBUTING).
- **Cita textual**: entrecomillada, con enlace y con autorización, aunque no se nombre a la persona.
- **Sin fuente**: se escribe como interpretación del autor ("interpretamos que...") o no se escribe.
- En la ficha, `Fuente` lleva el enlace; si no hay fuente, se escribe `no aplica`.

## Pregunta para conversar

- Exactamente una, al final, en la sección `## Pregunta para conversar`.
- Abierta: empieza con "¿cómo…?", "¿qué…?" o "¿en qué…?" y admite más de una respuesta razonable.
- No se contesta dentro de la historia: si ya está respondida, no sirve para conversar.
- Puede responderse sin datos privados ni conocer el sistema original.

## Antes de enviar

- [ ] Las cinco secciones de la plantilla están presentes.
- [ ] El aprendizaje se entiende sin saber nada del sistema donde ocurrió.
- [ ] Los enlaces relativos resuelven y el Markdown se ve bien.
- [ ] No quedaron nombres de personas, clientes, sistemas ni fechas exactas.
