---
name: vento-carrusel
description: Convertir una idea o un video en un carrusel. Usar cuando pide un carrusel o un post de varias imágenes.
---

# Carrusel desde una idea

Claude escribe el contenido; Vento lo valida con las reglas de la app y lo guarda **en borrador**. El diseño final y el render de imágenes se terminan en Vento. Requiere el módulo de carruseles habilitado en la cuenta.

## Pasos

1. **Marca:** `get_brand_context` (si no la llamaste ya). Para las reglas de carrusel del creador, pedí `prompts: ["carousel"]`.
2. **Material.** Si parte de una idea, `get_idea`; si parte de un video, `get_video`. Sin material, preguntá el tema.
3. **Plantillas.** `get_carousel_templates` **siempre antes de escribir**: trae las plantillas, los campos de cada una con sus topes y las reglas de armado. Sin esto se inventan campos.
4. **Formato de diseño.** Mostrale las opciones de `design_format` (diario, punk, minimalista, tech, esquemas, afiche, guia, prisma) y elegí con el usuario.
5. **Slides.** De 4 a 8. La primera es una portada válida y la última es `T5CTA`. Cada slide usa solo los campos de su plantilla y respeta los topes de largo. Una idea por slide, voz del creador.
6. **Guardá:** `create_carousel { concept, design_format, slides, idea_id?, cta_keyword? }`. Si la validación falla, leé el error, corregí y reintentá.
7. **Avisá** que quedó en borrador y que se renderiza y programa desde Vento (link `/app/creador/carousels/<id>`).

## No hagas

- No inventes campos ni plantillas. No excedas los topes.
- No prometas imágenes ni programación: eso no se hace desde Claude.
- Para ajustar una slide después, `update_carousel_slide` (solo con el carrusel listo; una slide ya renderizada vuelve a pendiente).

## Un buen resultado

Un borrador que pasó la validación al primer o segundo intento, con portada fuerte, un mensaje por slide y un cierre claro.
