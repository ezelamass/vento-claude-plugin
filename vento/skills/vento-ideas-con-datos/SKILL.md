---
name: vento-ideas-con-datos
description: Proponer ideas de contenido basadas en lo que ya funcionó. Usar cuando el usuario pide ideas, "qué grabo", o "más como mi mejor video".
---

# Ideas con datos

Las buenas ideas salen de lo que ya funcionó en la cuenta del creador y de lo que funciona a los que admira, no de la nada.

## Pasos

1. **Marca, una vez por conversación:** `get_brand_context` (pilares, objetivos, a quién le habla).
2. **Lo que funcionó.** `list_top_videos { order_by: "multiplier", limit: 5 }` y, de los 2–3 mejores, `get_video { video_id }` para ver el hook, la transcripción y la retención.
3. **Los referentes (opcional).** Si el usuario tiene referentes, `list_referent_videos` (con `since_days: 60`) para ver qué les funciona a ellos y por qué.
4. **La audiencia.** `get_audience_insights` para ver qué pide la gente y dónde se cae.
5. **Proponé 5 ideas.** Cada una con: concepto en una frase, hook posible y **el porqué con datos** ("tu video X hizo 3,2x con este ángulo"). Sin datos suficientes, decilo: no rellenes con ideas genéricas.
6. **Creá solo las que el usuario elija:** `create_ideas { ideas: [...] }`. Si una salió de un video de un referente, pasá su `referent_video_id`. Sin pedido distinto, nacen aprobadas en "Mis ideas".

## No hagas

- No inventes métricas ni videos. Todo número sale de las tools; si no hay videos, `list_top_videos` devuelve un `hint`: contáselo al usuario.
- No copies un video de un referente: tomá el patrón (ángulo, estructura) y llevalo a la voz del creador.
- No crees ideas sin que el usuario las haya elegido.

## Un buen resultado

Cinco ideas con una razón verificable cada una, alineadas con los pilares del creador, y las elegidas ya guardadas en Vento.
