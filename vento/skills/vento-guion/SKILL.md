---
name: vento-guion
description: Escribir el guion de una idea de Vento. Usar cuando el usuario pide un guion, un hook o "escribime el video de X".
---

# Guion de una idea de Vento

Un guion corto tiene tres partes: **hook** (la primera frase, la que frena el scroll), **desarrollo** y **CTA**. La voz y las reglas son del creador y salen de su cuenta, nunca de esta skill.

## Pasos

1. **Marca, una vez por conversación.** Llamá `get_brand_context` (con `prompts: ["voice", "scripting_rules", "hook_bank"]` si querés las reglas y el banco de hooks completos). Si ya la llamaste en esta conversación, no repitas.
2. **La idea.** Si el usuario no dio una, `list_ideas` y preguntá cuál. Leela con `get_idea { idea_id }`: trae el concepto, el ángulo, el guion que ya tenga y `hooks_all` (los hooks que ya existen).
3. **Tres hooks distintos**, uno de cada tipo: pregunta, dato y contradicción (ver `references/hooks.md`). No repitas los de `hooks_all`. Mostralos numerados y preguntá cuál prefiere (o si quiere mezclar).
4. **Desarrollo y CTA** con el hook elegido, en la voz de `voice` y respetando `scripting_rules` si existen. Corto: una idea, un recorrido, sin relleno. El CTA pide una sola acción.
5. **Guardá** con `save_script { idea_id, hook, development, cta }` (título, caption y texto en pantalla son opcionales). Si la idea ya tenía un guion en borrador, lo actualiza.
6. **Confirmá** en una línea: qué quedó guardado y dónde verlo en Vento.

## No hagas

- No inventes datos, cifras ni casos del usuario: si el guion necesita un número, pedíselo o sacalo de `get_video` / `list_top_videos`.
- No guardes antes de que el usuario elija el hook.
- Si `save_script` dice que el guion ya está grabado o publicado, no lo fuerces: ofrecé crear una idea nueva con `create_ideas`.
- Ideas de video largo: `save_script` las rechaza; esa estructura se arma en Vento.

## Un buen resultado

Hook de una frase que se entiende sin contexto, desarrollo que cumple lo que el hook promete, CTA concreto, y todo suena a la persona, no a un asistente.
