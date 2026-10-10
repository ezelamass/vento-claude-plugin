# Vento para Claude

Plugin de [Vento](https://getvento.app), la app de contenido para creadores. Conecta Claude con tu cuenta de Vento y le da el método: en qué orden usar tus datos, cómo se escribe un hook que frena el scroll, cómo se arma una tanda de grabación y una semana de publicación.

## Qué incluye

- **Skills** (se activan solas según lo que pidas): `vento-guion`, `vento-ideas-con-datos`, `vento-tanda`, `vento-semana`, `vento-carrusel`, `vento-filtro`.
- **Comandos**: `/vento:semana`, `/vento:guiones`, `/vento:analizar-mes`.
- **Conector** a `https://mcp.getvento.app` (ideas, guiones, métricas, calendario, carruseles, historias).

## Cómo se usa

1. Instalá el plugin (claude.ai: *Customize → Plugins*; Claude Code: `claude plugin install`) y conectá Vento desde la pestaña *Connectors* con tu login de Vento.
2. Pedile cosas como "escribime el guion de mi última idea", "qué grabo hoy" o "planificá mi semana".

Tu voz, tus pilares y tus reglas salen de tu cuenta de Vento (`get_brand_context`), no del plugin: cada creador escribe con lo suyo.

## Qué datos manda y guarda

Lee tus ideas, guiones, métricas de videos, referentes, calendario y marca desde Vento; escribe ideas, guiones, borradores de carruseles e historias y la programación que vos confirmes. Nada se publica en el momento: programar siempre pasa por una vista previa y tu confirmación. Los datos quedan en Vento. Para revocar el acceso, borrá el conector en Claude o revocá el permiso desde tu cuenta de Vento.

## Requisitos

Una cuenta de Vento con *Vento en Claude* habilitado. Las skills `vento-semana`, `vento-carrusel` y `vento-filtro` usan tools de producción y formatos que cada cuenta puede tener o no habilitadas.

Licencia MIT.
