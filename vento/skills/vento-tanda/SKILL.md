---
name: vento-tanda
description: Armar la próxima sesión de grabación. Usar cuando dice "qué grabo hoy" o "armame la tanda".
---

# Tanda de grabación

Una tanda es el grupo de ideas cortas que se graban de corrido en una sesión. Claude la arma; **la sesión la empieza el usuario desde Vento** (Modo grabación): es en vivo, con cámara.

## Pasos

1. **Marca, una vez por conversación:** `get_brand_context`.
2. **Candidatas.** `list_ideas` (aprobadas, sin grabar). Pregunta de tiempo: cuánto tiene para grabar (cada idea corta ronda 5 minutos). Armá entre 3 y 10 ideas; el tope de la tanda es 15.
3. **Orden por energía:** primero la más fácil de decir y la más suelta, después las que piden más intensidad, al final las más técnicas. Explicá el orden en una línea.
4. **Completá lo que falte.** Para cada idea sin guion o sin hooks: `get_idea` y, si hace falta, seguí el método de la skill `vento-guion` (proponer 3 hooks y guardar con `save_script`). `update_idea { hook_options }` guarda opciones de hook.
5. **Dejá la tanda:** `plan_recording { idea_ids: [...] }` en el orden elegido. Reemplaza la tanda anterior.
6. **Cerrá:** decile que abra Vento → Modo grabación, donde la tanda ya está preseleccionada.

## No hagas

- No incluyas ideas de video largo ni ya grabadas (la tool las rechaza y explica por qué).
- No intentes empezar la sesión de grabación desde acá.
- Si no hay ideas aprobadas, ofrecé usar `vento-ideas-con-datos`.

## Un buen resultado

Una tanda ordenada, cada idea con su guion o sus hooks listos, el tiempo estimado total y la indicación de dónde grabar.
