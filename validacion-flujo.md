# Validación del flujo de colaboración

Checklist para comprobar el flujo documentado en [`CONTRIBUTING.md`](CONTRIBUTING.md) de punta a punta: desde elegir una issue hasta llegar a `Done`. Nació de la issue #6 y sirve para repetir la comprobación con la próxima contribución.

No reemplaza el acuerdo de colaboración. Registra qué pasó en una vuelta real y qué instrucciones fallaron al ejecutarse.

## Cómo se usa

1. Elegir una issue abierta y asignársela.
2. Moverse por el flujo hasta `Done`, anotando toda instrucción que genere fricción.
3. Anotar cada fricción abajo, con el comando o el paso que la produjo.
4. Convertir solo las fricciones **reproducibles** en cambios documentales.

Una fricción sin pasos para reproducirla no es una fricción: es una opinión.

## Checklist del recorrido

| # | Paso documentado | Verificación | Resultado de la vuelta #6 |
| --- | --- | --- | --- |
| 1 | Elegir issue disponible del tablero | ¿Se puede ver el tablero desde el repositorio? | Fricción 1 |
| 2 | Asignarse y mover a `In progress` | ¿Se puede cambiar el estado? | Sin fricción |
| 3 | Crear rama corta desde `main` actualizado | ¿El nombre de la rama tiene una convención? | Fricción 3 |
| 4 | Cambio enfocado, enlaces y Markdown verificados | ¿El alcance es verificable? | Sin fricción |
| 5 | Abrir PR con `Closes #<número>` y mover a `In review` | ¿Existe el estado `In review`? | Fricción 4 |
| 6 | Solicitar revisión a otra persona | ¿Hay alguien disponible? | Sin fricción |
| 7 | Resolver comentarios y re-solicitar si hubo cambios | ¿El proceso está escrito? | Sin fricción |
| 8 | Reviewer aprueba y hace merge | ¿Los controles bloquean el merge sin aprobación? | Sin fricción |
| 9 | Confirmar cierre de la issue y mover a `Done` | ¿El cierre y el tablero quedan alineados? | Fricción 5 |

## Fricciones observadas en la vuelta #6

### 1. El tablero no se puede encontrar desde el repositorio

`CONTRIBUTING.md` llama al tablero "la fuente compartida", pero ningún archivo del repositorio dice cuál es. No hay enlace en el `README.md` ni en la guía. La única forma de hallarlo fue consultando la API de la organización.

Es la primera fricción del recorrido y ocurre antes de cualquier trabajo: sin el tablero no se puede elegir una issue.

### 2. `gh issue view` falla en issues del tablero

El comando más obvio para leer una issue devuelve un error y no muestra el contenido:

```console
$ gh issue view 6
GraphQL: Projects (classic) is being deprecated in favor of the new Projects experience,
see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.
(repository.issue.projectCards)
```

La causa es que el tablero usa Projects (V2) y `gh issue view` sigue pidiendo un campo de Projects (classic) que ya no existe. No afecta a `gh issue list` ni a `gh project item-list`, que sí funcionan.

### 3. La convención de ramas no está documentada

El paso 3 dice "crear una rama corta", pero no hay convención escrita. Las ramas que existen en el repositorio sí siguen un patrón reconocible:

| Rama | Tipo | Descripción |
| --- | --- | --- |
| `docs/anecdota-zona-horaria-ventas` | `docs/` | título de la anécdota en `kebab-case` |
| `docs/criterios-privacidad-atribucion` | `docs/` | tema en `kebab-case` |
| `anecdota-modelo-aprendio-respuesta` | sin prefijo | tipo de issue + tema |

El prefijo es opcional y depende de si el cambio es solo documentación. Sin la convención escrita, cada persona deduce un nombre distinto.

### 4. El paso 5 pide un estado que el tablero no tiene

El paso 5 indica mover la actividad a `In review`, pero el campo `Status` del tablero solo tiene tres opciones: `Todo`, `In progress` y `Done`. `In review` no existe, así que el paso no se puede completar como está escrito.

### 5. El tablero no registra el historial de estados

El tablero guarda el estado actual de cada item, no la secuencia de estados por los que pasó. La vuelta #6 pudo confirmar que la issue #3 terminó en `Done` y que su PR fue aprobada por otra persona, pero no puede confirmar que el item recorriera `Todo → In progress → In review → Done`. El criterio de aceptación #2 de la issue #6 ("la issue y la pull request recorrieron el tablero") queda sin forma de verificarse.

## Cómo verificar los criterios de la issue #6

| Criterio | Verificable | Evidencia |
| --- | --- | --- |
| Contribución con assignee y reviewer diferentes | Sí | PR #9: autora `solddomm`, aprobación de `laureanomag` |
| La issue y la PR recorrieron el tablero | No | El tablero no guarda historial de estados (fricción 5) |
| Mejoras basadas en dificultades observadas | Sí | Este documento |

## Qué queda pendiente

- [ ] Decidir si se documenta el tablero y su enlace en `CONTRIBUTING.md` (fricciones 1 y 2).
- [ ] Documentar la convención de ramas (fricción 3).
- [ ] Resolver la diferencia entre el estado `In review` del paso 5 y las opciones reales del tablero (fricción 4).
- [ ] Definir cómo se verifica el recorrido de estados si el tablero no guarda historial (fricción 5).
- [ ] Repetir esta validación con la próxima contribución completa.

Las decisiones sobre el tablero y el proceso son del equipo: este documento solo registra lo observado.
