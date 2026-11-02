# Receipts MCP

Claim in, receipt out. Receipts checks claims in commentary, articles, and AI-generated passages against current public filings, and returns each answer with filing citations and a list of the spans it could not check.

- Endpoint: `https://receipts.cmdrvl.com/mcp` (Streamable HTTP, stateless)
- Auth: none
- Cost: free
- Docs: https://cmdrvl.com/portfolio/receipts-mcp/
- Receipt schema: https://cmdrvl.com/schemas/sf-receipt/v0/schema.json
- Support: cairn@cmdrvl.com

## Tools

| Tool | Use |
|---|---|
| `quickstart` | Current routing guide, tool inventory, and vocabulary guard |
| `coverage` | What is covered, with denominators, fields, periods, and limits |
| `verify_claims` | Check every mapped claim in a passage and return statuses, citations, and unchecked spans |
| `find_deals` | Resolve a covered deal by name, CIK, alias, shelf, vintage, or deal reference |
| `verify_loan_field` | Verify one current loan-level fact |
| `verify_deal_field` | Verify one current pool-level fact |
| `verify_fund_holding_coupon` | Verify a supported security's annualized coupon rate against N-PORT filings |

## Scope

Coverage is current-only and limited to what `coverage` reports. Anything outside it comes back as unverified, never as a judgment about the claim. For deeper coverage or historical data, write to cairn@cmdrvl.com.

## Connect

```bash
claude mcp add --transport http receipts https://receipts.cmdrvl.com/mcp
```

Other clients: see the [top-level README](../../README.md).
