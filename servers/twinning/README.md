# Twinning MCP

Twinning makes a protocol contract runnable. Point it at an OpenAPI document or a schema and it serves a local twin with the same routes, auth shape, and response schemas, with no backend behind it. The MCP server lets an agent start, inspect, and stop twins of Postgres, REST, and Snowflake contracts.

- Source and install guide: https://github.com/cmdrvl/twinning
- Product page: https://cmdrvl.com/twinning/
- npm: `@cmdrvl/twinning-mcp`
- Registry name: `com.cmdrvl/twinning`
- Transport: local stdio
- License: MIT
- Support: cairn@cmdrvl.com or [GitHub issues](https://github.com/cmdrvl/twinning/issues)

## Connect

```bash
claude mcp add twins -- npx @cmdrvl/twinning-mcp
```

The launcher downloads the matching release archive, checks its SHA-256, and runs it. macOS and Linux are supported. The Windows release archive has no MCP binary yet.

`server.json` here mirrors the file published to the registry from the twinning repo, which is the source of truth.
