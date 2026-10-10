---
description: Planificá mi semana de contenido en Vento
---

Planificá mi semana de publicación con Vento.

1. Mirá el calendario con get_calendar (esta semana) y decime qué días están vacíos.
2. Traé mis videos editados con list_ready_videos y, para cada uno que quieras ubicar, los horarios libres con get_publish_slots.
3. Proponeme un plan: qué video va qué día y a qué hora, y por qué ahí. No más de un video por día salvo que yo lo pida.
4. Para cada video que yo acepte, llamá schedule_video SIN confirm, mostrame la vista previa y esperá mi OK. Solo con mi OK lo llamás de nuevo con confirm: true.

Nunca publiques nada ya: solo se programa, y solo lo que yo confirme. Los horarios salen de get_publish_slots; no los calcules vos.
