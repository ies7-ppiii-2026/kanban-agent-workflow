# Validación del flujo de colaboración

Checklist para comprobar el flujo documentado en [`CONTRIBUTING.md`](CONTRIBUTING.md) de punta a punta: desde elegir una issue hasta llegar a `Done`. Nació de la issue #6 y sirve para repetir la comprobación con la próxima contribución.

No reemplaza el acuerdo de colaboración. Registra qué pasó en una vuelta real y qué instrucciones fallaron al ejecutarse.

## Estado de la captura

Estos hallazgos describen el repositorio en un momento concreto, no una propiedad permanente. Antes de repetir la comprobación hay que volver a capturar:

- Fecha: 2026-10-02.
- Cliente: `gh 2.46.0`.
- Tablero: project 2, "Anécdotas de datos e IA", de la organización `ies7-ppiii-2026`.

Las ramas de la fricción 3 se borran al fusionarse la PR que las originó, así que esa tabla es una foto y no un inventario.

## Cómo se usa

1. Elegir una issue abierta y asignársela.
2. Moverse por el flujo hasta `Done`, anotando toda instrucción que genere fricción.
3. Anotar cada fricción abajo, con el comando o el paso que la produjo.
4. Convertir solo las fricciones **reproducibles** en cambios documentales.

Una fricción sin pasos para reproducirla no es una fricción: es una opinión. El mismo rigor va en las dos direcciones: un veredicto de «Sin fricción» sin forma de comprobarlo tampoco es un veredicto, es una impresión.

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
| 8 | Reviewer aprueba y hace merge | `gh api repos/ies7-ppiii-2026/kanban-agent-workflow/rulesets` | Sin fricción |
| 9 | Confirmar cierre de la issue y mover a `Done` | ¿El cierre y el tablero quedan alineados? | Fricción 5 |

## Fricciones observadas en la vuelta #6

### 1. El tablero no se puede encontrar desde el repositorio

`CONTRIBUTING.md` llama al tablero "la fuente compartida", pero ningún archivo del repositorio dice cuál es. No hay enlace en el `README.md` ni en la guía. La única forma de hallarlo fue consultando la API de la organización.

Es la primera fricción del recorrido y ocurre antes de cualquier trabajo: sin el tablero no se puede elegir una issue.

### 2. `gh issue view` falla sin `--json`, y la causa es el cliente

El comando más obvio para leer una issue devuelve un error y no muestra el contenido:

```console
$ gh issue view 6
GraphQL: Projects (classic) is being deprecated in favor of the new Projects experience,
see: https://github.blog/changelog/2024-05-23-sunset-notice-projects-classic/.
(repository.issue.projectCards)
```

**La causa no es el tablero ni este repositorio.** `gh issue view` pide en su consulta por defecto el campo `repository.issue.projectCards`, que pertenece a Projects (classic) y ya no existe. Es una limitación del cliente `gh`.

Se reproduce con `gh 2.46.0` y se esquiva sin tocar nada del repositorio:

```console
$ gh issue view 6 --repo ies7-ppiii-2026/kanban-agent-workflow --json number,title,state
{"number":6,"state":"OPEN","title":"mejora: comprobar el flujo con la primera contribución"}
```

El error depende de la versión del cliente, así que actualizar `gh` también lo resuelve. Queda registrada porque en esta vuelta produjo fricción real, pero **no es una corrección que le corresponda al tablero ni al equipo**, y por eso no figura en "Qué queda pendiente".

### 3. La convención de ramas no está documentada y no se puede deducir

El paso 3 dice "crear una rama corta", pero no hay convención escrita. Estas son todas las ramas abiertas en el momento de la captura:

| Rama | Prefijo |
| --- | --- |
| `anecdota-modelo-aprendio-respuesta` | sin prefijo |
| `anecdota-pipeline-sin-memoria` | sin prefijo |
| `docs/coleccion-primeros-incidentes` | docs/ |
| `docs/guia-de-estilo-anecdotas` | docs/ |
| `docs/validar-categorias-iniciales` | docs/ |
| `mejora/comprobar-flujo-primera-contribucion` | mejora/ |

**El prefijo no se puede deducir de las ramas existentes.** Conviven tres prefijos distintos (`docs/`, `mejora/` y ninguno) y ninguna regla los separa. Los contraejemplos son explícitos:

| Issue | Labels | Rama |
| --- | --- | --- |
| #4 | `mejora`, `documentacion`, `prioridad:media` | `docs/validar-categorias-iniciales` |
| #6 | `mejora`, `documentacion`, `prioridad:media`, `bloqueada` | `mejora/comprobar-flujo-primera-contribucion` |

Dos issues del mismo tipo, con labels casi idénticos y prefijos distintos. Los dos cambios son de solo documentación, así que la idea de que el prefijo depende de si el cambio es o no solo documentación queda descartada por sus propios contraejemplos.

Lo que queda es un hecho y no una regla: sin convención escrita, cada persona deduce el nombre a su manera. Fijarla requiere un acuerdo del equipo, no se puede extraer de las ramas que hay.

### 4. El paso 5 pide un estado que el tablero no tiene

El paso 5 indica mover la actividad a `In review`, pero el campo `Status` del tablero solo tiene tres opciones: `Todo`, `In progress` y `Done`. `In review` no existe, así que el paso no se puede completar como está escrito.

### 5. El tablero no registra el historial de estados

El tablero guarda el estado actual de cada item, no la secuencia de estados por los que pasó. La vuelta #6 pudo confirmar que la issue #3 terminó en `Done` y que su PR fue aprobada por otra persona, pero no puede confirmar que el item recorriera `Todo → In progress → In review → Done`. El criterio de aceptación #2 de la issue #6 ("la issue y la pull request recorrieron el tablero") queda sin forma de verificarse.

## Cómo se comprueban los veredictos de «Sin fricción»

Los pasos 2, 4, 6, 7 y 8 no produjeron fricción, pero que no haya habido fricción no es una prueba. Estos son los comandos con los que se comprobó cada uno:

| Paso | Comprobación |
| --- | --- |
| 2 | `gh project item-edit` sobre la tarjeta, cambiando el campo `Status` a `In progress`. |
| 4 | `git diff main...HEAD --stat`: el alcance queda acotado a los archivos previstos. |
| 6 | `gh api repos/ies7-ppiii-2026/kanban-agent-workflow/pulls/15/requested_reviewers` lista al reviewer. |
| 7 | `CONTRIBUTING.md` paso 7 describe el procedimiento; se ejecuta sin ambigüedad. |
| 8 | `gh api repos/ies7-ppiii-2026/kanban-agent-workflow/rulesets` |

El paso 8 era el único que dependía de tooling invisible desde el working tree. El ruleset `Protect main — pull requests only` está activo y declara `required_approving_review_count: 1`, `dismiss_stale_reviews_on_push: true` y `require_last_push_approval: true`. El merge sin aprobación efectivamente no pasa.

Una trampa que conviene registrar, porque se cometió durante esta vuelta: `GET /branches/main/protection` devuelve `404` en este repositorio aunque el ruleset esté activo. Branch protection y rulesets son mecanismos distintos, así que consultar solo el primero hace creer que no hay ningún control. Para verificarlo hay que usar `/rulesets`.

## Cómo verificar los criterios de la issue #6

| Criterio | Verificable | Evidencia |
| --- | --- | --- |
| Contribución con assignee y reviewer diferentes | Sí | PR #9: autora `solddomm`, aprobación de `laureanomag` |
| La issue y la PR recorrieron el tablero | No | El tablero no guarda historial de estados (fricción 5) |
| Mejoras basadas en dificultades observadas | Sí | Este documento |

## Qué queda pendiente

- [ ] Decidir si se documenta el tablero y su enlace en `CONTRIBUTING.md` (fricción 1).
- [ ] Documentar la convención de ramas (fricción 3).
- [ ] Resolver la diferencia entre el estado `In review` del paso 5 y las opciones reales del tablero (fricción 4).
- [ ] Definir cómo se verifica el recorrido de estados si el tablero no guarda historial (fricción 5).
- [ ] Repetir esta validación con la próxima contribución completa.

Las decisiones sobre el tablero y el proceso son del equipo: este documento solo registra lo observado.
