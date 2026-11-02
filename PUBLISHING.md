# Publishing to the MCP Registry

Notes for maintainers. Nothing here is automated, and each publish needs the maintainer's explicit go-ahead.

## Namespace proof

The `com.cmdrvl/*` namespace is proven by an HTTP file on cmdrvl.com, already in place:

```
https://cmdrvl.com/.well-known/mcp-registry-auth
```

It holds one line, `v=MCPv1; k=ed25519; p=<public key>`. The matching private key stays with the maintainer and is never committed or pasted anywhere. The file must return 200 directly, with no redirect, as plain text under 4096 bytes. Check it the way the registry fetches it:

```bash
curl -sS -H 'Accept: text/plain' -A 'mcp-registry/1.0' https://cmdrvl.com/.well-known/mcp-registry-auth
```

## Publish a server

Use Homebrew's OpenSSL (the macOS system one cannot make Ed25519 keys) and keep the key in the shell:

```bash
brew install mcp-publisher
PRIVATE_KEY="$(openssl pkey -in <path-to-private-key.pem> -noout -text | grep -A3 "priv:" | tail -n +2 | tr -d ' :\n')"
mcp-publisher login http --domain cmdrvl.com --private-key "$PRIVATE_KEY"; unset PRIVATE_KEY
cd servers/receipts && mcp-publisher publish
```

Then confirm:

```bash
curl -s 'https://registry.modelcontextprotocol.io/v0/servers?search=com.cmdrvl/receipts'
```

A published version cannot be edited. Fix mistakes in a new version.

## Status

| Server | Registry name | Status |
|---|---|---|
| Twinning | `com.cmdrvl/twinning` | Published 0.7.1. Source of truth is `registry/server.json` in the twinning repo |
| Receipts | `com.cmdrvl/receipts` | Draft `server.json`, not published |

Vigil KYC is an HTTP API, not an MCP server, so it has no registry entry. It is listed in the Stripe Directory.
