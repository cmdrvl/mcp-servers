# CMD+RVL MCP servers and agent APIs

Where to find and connect to the MCP servers and agent-callable APIs from [CMD+RVL](https://cmdrvl.com). This repo holds docs, registry metadata, and editor plugin configs (`plugins/`). There is no server source code here.

Support: cairn@cmdrvl.com

## MCP servers

| Server | What it does | Connection | Auth | Cost |
|---|---|---|---|---|
| [Receipts](servers/receipts/) | Checks covered claims in commentary, articles, and AI-generated passages against current public CMBS filings, with citations and a list of what it could not check. Public CMBS filings and NPORT-P coupons to start, more coming soon | Remote, `https://receipts.cmdrvl.com/mcp` | None | Free |
| [Twinning](servers/twinning/) | Runs local twins of Postgres, REST, and Snowflake contracts so agents and tests never touch production | Local, `npx @cmdrvl/twinning-mcp` | None | Free, open source (MIT) |

Both are listed in the [official MCP Registry](https://registry.modelcontextprotocol.io) as `com.cmdrvl/receipts` and `com.cmdrvl/twinning`.

### Connect to Receipts

Claude Code:

```bash
claude mcp add --transport http receipts https://receipts.cmdrvl.com/mcp
```

Cursor, in `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "receipts": { "url": "https://receipts.cmdrvl.com/mcp" }
  }
}
```

Any other client that supports Streamable HTTP: point it at `https://receipts.cmdrvl.com/mcp`. No key is needed. Start with the `quickstart` and `coverage` tools.

### Connect to Twinning

Claude Code:

```bash
claude mcp add twins -- npx @cmdrvl/twinning-mcp
```

Cursor and other clients take the same command in their stdio config. A Cursor plugin for Twinning is in [plugins/twinning](plugins/twinning/) and is submitted to the Cursor Marketplace. Full install options, including prebuilt binaries and Homebrew, are in the [twinning repo](https://github.com/cmdrvl/twinning). Product page: https://cmdrvl.com/twinning/

## Paid HTTP APIs

These are HTTP APIs an agent can call and pay for in the request. They are not MCP servers.

| API | What it does | Price | Auth |
|---|---|---|---|
| [Vigil KYC screening](apis/vigil-kyc/) | Screens one company and up to three named people against supported sanctions, export-control, and debarment lists, and returns findings, source evidence, and a PDF | $1 per completed screen | None. Pay with the Machine Payments Protocol (card through Stripe Link, or USDC on Tempo) |

Vigil KYC is separate from the keyed Vigil MCP server, which needs an API key.

## More

- CMD+RVL: https://cmdrvl.com
- MCP servers overview: https://cmdrvl.com/mcp-servers/
- Developers: https://cmdrvl.com/developers/
- Cairn, a research assistant for public filings and structured finance, over text: https://textcairn.com

Larger lists, custom policies, or other sources: https://hirecairn.com/

## Keeping this current

When a server or API is added, or its URL or version changes, update this README and that entry's folder. `server.json` files follow the [MCP Registry schema](https://static.modelcontextprotocol.io/schemas/2025-12-11/server.schema.json). Publishing steps are in [PUBLISHING.md](PUBLISHING.md).
