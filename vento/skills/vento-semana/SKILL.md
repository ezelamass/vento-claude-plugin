---
name: vento-semana
description: Planificar la semana de publicación. Usar cuando dice "planificá mi semana" o "qué publico".
---

# Semana de publicación

Programar es lo único de Vento que tiene consecuencias visibles afuera. Regla de oro: **nunca se programa sin que el usuario vea la vista previa y confirme.** Nada se publica en el momento; el sistema de Vento publica a la hora programada.

## Pasos

1. **Calendario.** `get_calendar` (por defecto esta semana; `from` / `to` en YYYY-MM-DD, hasta 31 días). Anotá los días sin posts y los guiones que el usuario ya planificó.
2. **Qué hay para publicar.** `list_ready_videos`: videos editados, sin programar. Cada uno trae `edit_job_id`, sus redes y si tiene portada. Sin portada no se puede programar: avisá que la asigne en Vento.
3. **Horarios.** Para cada video que quieras ubicar: `get_publish_slots { edit_job_id }`. Es la **única** fuente de horarios (respeta los horarios y topes por red del usuario, en hora de Buenos Aires): no los calcules ni los inventes.
4. **Proponé el plan** en una tabla corta: día, hora, video, red y por qué ahí (rellená huecos, no apiles dos el mismo día). Preguntá qué ajusta.
5. **Vista previa, uno por uno.** Para cada video aceptado: `schedule_video { edit_job_id, slot }` **sin `confirm`**. Mostrale la vista previa al usuario tal cual vino.
6. **Programá solo lo confirmado.** Con el OK explícito del usuario, repetí la llamada con `confirm: true`. Si dice "programá todo" luego de ver el plan completo, igual hacé la vista previa de cada uno y pedí un OK general antes de confirmar.
7. **Cerrá** con el estado de cada uno (`get_post_status` si hace falta) y lo que quedó pendiente.

## No hagas

- No pases `confirm: true` en la primera llamada ni sin un "sí" del usuario sobre ESA vista previa.
- No cancelés posts (`cancel_scheduled_post`) salvo que el usuario lo pida, y también con vista previa primero.
- Si una tool avisa que un envío pudo haber salido, no reintentes: contáselo al usuario.

## Un buen resultado

Un plan semanal sin huecos ni apilados, con cada programación confirmada por el usuario y nada publicado antes de tiempo.
