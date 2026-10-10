# Vento para Claude

Plugin oficial de [Vento](https://getvento.app), la app de contenido para creadores. Conecta Claude con tu cuenta de Vento y le enseña el método: escribir guiones en tu voz, proponer ideas a partir de lo que ya te funcionó, armar tu próxima tanda de grabación y planificar tu semana de publicación.

## Instalar

**Claude Code**

```
/plugin install vento --marketplace ezelamass/vento-claude-plugin
```

**claude.ai / Cowork:** *Customize → Plugins → Add*, o conectá solo el conector con la URL `https://mcp.getvento.app`.

Después conectá Vento con tu login (OAuth). Tus datos, tu voz y tus reglas salen de tu cuenta de Vento, no del plugin.

## Qué trae

El plugin está en [`vento/`](vento/): seis skills, tres comandos (`/vento:semana`, `/vento:guiones`, `/vento:analizar-mes`) y la conexión al servidor MCP de Vento. Detalle en [`vento/README.md`](vento/README.md).

Nada se publica en el momento: programar siempre pasa por una vista previa y tu confirmación.

## Fuente

Este repo es una copia publicada. La fuente se mantiene junto al servidor de Vento y se sincroniza acá; los issues y pedidos se reciben en este repo.

Licencia MIT.
