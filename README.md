# Anécdotas de datos e inteligencia artificial

Repositorio colaborativo para recopilar historias breves sobre el trabajo con datos y el desarrollo de inteligencia artificial. El contenido es simple a propósito: el objetivo principal es practicar un flujo real de Kanban, issues, ramas, pull requests, revisión y merge.

## Cómo empezar

1. Elegir una issue disponible del tablero.
2. Asignársela y moverla a `In progress`.
3. Crear una rama corta desde `main`.
4. Realizar el cambio usando solamente Markdown.
5. Abrir una pull request vinculada a la issue y solicitar una revisión.
6. Otra persona revisa, aprueba y realiza el merge.

Una actividad llega a `Done` únicamente después de que su pull request fue revisada y fusionada.

## Qué recopilamos

Las historias pueden tratar sobre:

- incidentes y errores con datos;
- aprendizajes durante el desarrollo de sistemas de IA;
- decisiones técnicas y sus consecuencias;
- trabajo en equipo, comunicación y procesos;
- ética, privacidad y uso responsable de datos;
- experiencias en producción.

Se aceptan anécdotas reales, anonimizadas o ficticias. Una historia ficticia debe indicarlo claramente; una historia real no debe revelar información privada, confidencial ni atribuida sin autorización.

## Estructura

```text
anecdotas/
  README.md              índice de historias
  plantilla.md           estructura para nuevas anécdotas
.github/
  ISSUE_TEMPLATE/        plantillas para proponer trabajo
  pull_request_template.md
CONTRIBUTING.md           acuerdos y flujo de colaboración
```

## Tipos de contribución

Una issue no tiene que limitarse a agregar una historia. También puede proponer:

- revisar, anonimizar o mejorar una anécdota;
- verificar o agregar fuentes;
- clasificar historias y mantener índices;
- detectar contenido duplicado;
- preparar una colección temática;
- mejorar plantillas y acuerdos de colaboración.

## Reglas esenciales

- Cada cambio comienza con una issue.
- Cada issue tiene una persona responsable.
- Las ramas parten de `main` y duran lo mínimo posible.
- Nadie aprueba su propia pull request.
- Quien revisa realiza el merge cuando se cumplen los controles.
- El contenido versionado del proyecto se mantiene en Markdown, salvo archivos técnicos indispensables como `.gitignore`.

Consultá [CONTRIBUTING.md](CONTRIBUTING.md) para conocer el flujo completo.
