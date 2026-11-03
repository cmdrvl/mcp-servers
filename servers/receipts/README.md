# Receipts MCP

Claim in, receipt out. Receipts checks claims in commentary, articles, and AI-generated passages against current public CMBS filings and NPORT-P coupons, and returns each answer with filing citations and a list of the spans it could not check.

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
| `covered_deals` | List every covered deal with its CIK, aliases, and filing periods (the full set, which can be long) |
| `verify_loan_field` | Verify one current loan-level fact |
| `verify_deal_field` | Verify one current pool-level fact |
| `verify_counterparty` | Verify who a deal's master or special servicer is, against the 10-D counterparty roster |
| `verify_loan_status_counts` | Verify counts of loans in special servicing, active, defeased, or paid off, derived from the ABS-EE loan tape |
| `verify_building_size` | Verify a loan's building size as stated at securitization (Annex A against ABS-EE) |
| `verify_appraised_value` | Verify a loan's appraised value as of securitization (Annex A against ABS-EE) |
| `verify_fund_holding_coupon` | Verify a supported security's annualized coupon rate against NPORT-P filings |

## Scope

Receipts covers public CMBS and NPORT-P coupons to start, with more coming soon. Coverage is current-only and limited to what `coverage` reports. Anything outside it comes back as unverified, never as a judgment about the claim. For deeper coverage or historical data, write to cairn@cmdrvl.com.

## Connect

```bash
claude mcp add --transport http receipts https://receipts.cmdrvl.com/mcp
```

Other clients: see the [top-level README](../../README.md).
