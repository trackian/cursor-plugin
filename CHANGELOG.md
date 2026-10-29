# Changelog

## 2.0.0

- Cursor plugin format: `.cursor-plugin/plugin.json` manifest, `mcp.json`, logo.
- Connects to `https://api.trackian.app/mcp` over Streamable HTTP with browser sign-in (OAuth). Removes the local SSE bridge (`mcp-bridge.mjs`) and the `TRACKIAN_MCP_TOKEN` key.
- Adds the `trackian` and `trackian-get-started` skills, 27 `/trackian-*` commands and the `marketing-analyst` agent. Each command fetches its steps from Trackian with `get_command`.
- Removes the old `.cursor/rules`, which named tools the server no longer serves.
