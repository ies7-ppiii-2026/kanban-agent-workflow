# Guía de colaboración

Este acuerdo define cómo convertimos cada cambio en una práctica completa de Kanban, Git y revisión colaborativa.

## Tablero y prioridades

El tablero es la fuente compartida sobre prioridades, responsables y estado del trabajo. Cada participante debe actualizarlo cuando inicia, bloquea, pausa o finaliza una actividad, vinculando la issue y la pull request correspondientes.

Estados de referencia: `Todo → In progress → In review → Done`.

- `Todo`: trabajo definido y todavía no iniciado.
- `In progress`: cambio asignado y en preparación.
- `In review`: pull request abierta y lista para revisión.
- `Done`: pull request aprobada y fusionada; la issue quedó cerrada.

Un bloqueo debe registrar su causa y la siguiente acción. Antes de comenzar otra issue, se recomienda ayudar a revisar o desbloquear trabajo existente.

## Responsabilidades por cambio

| Rol | Responsabilidad |
| --- | --- |
| Responsable (assignee) | Coordinar la issue, crear la rama, realizar el cambio, comunicar avances y atender la revisión. |
| Reviewer | Revisar el contenido y el alcance, solicitar correcciones cuando corresponda, aprobar y realizar el merge. |

Los roles deben alternarse entre issues. La asignación indica responsabilidad de coordinación, no propiedad exclusiva del contenido.

## Flujo habitual

1. Elegir una issue viable según prioridad y dependencias.
2. Asignársela y moverla a `In progress`.
3. Crear una rama corta desde `main` actualizado.
4. Realizar un cambio enfocado y verificar los enlaces y el formato Markdown.
5. Abrir una pull request vinculada con `Closes #<número>` y mover la actividad a `In review`.
6. Solicitar revisión a otra persona del equipo.
7. Resolver los comentarios y volver a solicitar revisión si hubo cambios sustanciales.
8. El reviewer aprueba y realiza el merge.
9. Confirmar que la issue se cerró y moverla a `Done`.

## Criterios para las anécdotas

Cada historia debe:

- seguir [`anecdotas/plantilla.md`](anecdotas/plantilla.md);
- escribir según [`anecdotas/guia-de-estilo.md`](anecdotas/guia-de-estilo.md): tono, longitud, citas y pregunta final;
- identificar si es real, anonimizada o ficticia;
- expresar un aprendizaje relacionado con datos o IA;
- cumplir los criterios de privacidad y confidencialidad;
- cumplir los criterios de atribución;
- distinguir hechos comprobables de interpretaciones del autor.

### Privacidad y confidencialidad

Son dos problemas distintos y la corrección para cada uno es distinta.

- **Privacidad**: hay una persona identificable. Se anonimiza o se quita la persona.
- **Confidencialidad**: hay información reservada del cliente o del empleador, aunque no haya ninguna persona identificable. Se describe el caso de forma genérica, sin exponer el dato.

Una persona se vuelve identificable sin nombrarla. Rol, organización y momento juntos identifican: "el CTO del cliente dijo que el modelo ya estaba listo" alcanza para encontrar a la persona.

También hay que retirar referencias que identifican por sí solas aunque el caso parezca genérico:

- nombres de clientes, proveedores o empresas;
- nombres de sistemas internos, tablas o columnas;
- fechas exactas de incidentes;
- cualquier valor concreto que permita reconstruir el caso.

### Atribución

No es lo mismo citar un hecho que atribuir palabras, y la obligación cambia según el caso.

- **Hecho comprobable** → se cita la fuente.
- **Palabras o acciones atribuidas a una persona identificable** → se cita la fuente **y** se cuenta con su autorización, o se anonimiza a la persona y se retira la atribución.

Una cita textual exige autorización aunque la persona no esté nombrada: la forma de escribir y el contexto la identifican.

No se aceptan historias presentadas como reales cuando no pueden atribuirse responsablemente.

Ante una duda de privacidad o atribución, el orden es el siguiente:

1. **Anonimizar primero.** Suele alcanzar y conserva el realismo que hace que la historia enseñe algo.
2. **Usar ficticia solo si el hecho en sí no es publicable**, con independencia de quién esté en la historia. En ese caso marcarla claramente como ficticia.

## Bloqueos, prioridades y excepciones

- Registrar dependencias entre issues cuando una necesita el resultado de otra.
- Un cambio de prioridad no interrumpe automáticamente una tarea iniciada; documentar si se termina o pausa.
- Coordinar cualquier modificación sobre una rama ajena y dejar constancia en la issue o pull request.
- Documentar las excepciones al flujo, quiénes las acordaron y cómo se retomará el proceso habitual.

## Controles de integración

La rama `main` debe exigir:

- cambios mediante pull request;
- al menos una aprobación de otra persona;
- aprobación de alguien distinto de quien realizó el último push;
- descarte de aprobaciones obsoletas después de nuevos cambios;
- resolución de conversaciones antes del merge;
- bloqueo de force-push y eliminación de la rama.

Todas las personas colaboradoras con permiso de escritura pueden ser asignadas, solicitadas como reviewers y realizar el merge cuando no sean autoras del cambio ni responsables del último push.

## Referencias

- [Kanban Guide](https://kanbanguides.org/english/)
- [Google Engineering Practices: Code Review](https://google.github.io/eng-practices/review/)
- [Trunk-Based Development](https://trunkbaseddevelopment.com/)
