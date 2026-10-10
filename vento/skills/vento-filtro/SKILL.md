---
name: vento-filtro
description: Filtrar ideas con el filtro de 3 segundos. Usar cuando pide "cuáles grabo" o "filtrá mis ideas".
---

# Filtro de 3 segundos

El creador define sus propias preguntas de filtro en Vento. Claude las contesta idea por idea y **Vento calcula el veredicto** (Grabar / Producir / Descartar) con el mismo código de la app. Requiere el filtro de ideas habilitado en la cuenta.

## Pasos

1. **Las preguntas.** `get_idea_filter`. Si devuelve `configured: false`, el creador no tiene preguntas armadas: decile que las configure en Vento y parate acá.
2. **Las ideas.** `list_ideas` (o las que el usuario nombre). Hasta 20 por lote.
3. **Evaluá cada idea** con `get_idea` si hace falta, contestando las preguntas del creador: `q1` y `q2` según sus preguntas, `q3` = necesita historia, demo o pizarra (candidata a video largo) y `format_no` = el formato está en su lista de formatos que NO. Una frase de motivo por idea (`reason`).
4. **Guardá:** `apply_idea_filter { results: [{ idea_id, q1, q2, q3, format_no?, reason }] }`. Si una idea no es del usuario, se rechaza el lote entero.
5. **Resumí** en tres grupos: **Grabar**, **Producir**, **Descartar**, con el motivo de cada una. Ofrecé armar la tanda con las de Grabar (skill `vento-tanda`).

## No hagas

- No calcules el veredicto vos: contestá las preguntas y dejá que la tool lo decida.
- No descartes por gusto propio: aplicá las preguntas del creador, no las tuyas.
- No toques las ideas más allá del filtro (no las edites ni las rechaces).

## Un buen resultado

Cada idea con su veredicto y una razón corta, guardados en Vento, y una lista clara de qué grabar primero.
