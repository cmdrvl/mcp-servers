# Vigil KYC screening API

A pay-per-screen HTTP API for agents. It is not an MCP server. It is listed in the Stripe Directory and takes payment through the Machine Payments Protocol (MPP).

- Endpoint: `POST https://cairn.cmdrvl.com/vigil-paid/v1/screen`
- Offer (current price, terms, and limits): https://cairn.cmdrvl.com/vigil-paid/v1/
- OpenAPI: https://cairn.cmdrvl.com/vigil-paid/v1/openapi.json
- Service guide for agents: https://cairn.cmdrvl.com/vigil-paid/v1/llms.txt
- Guide: https://cmdrvl.com/developers/kyc-screening/
- Support: cairn@cmdrvl.com

## What you get

One screen covers one company and up to three named people against supported sanctions, export-control, and debarment lists. It costs $1 per completed screen. The result has structured findings, source evidence, and a PDF.

## How it works

1. Send the JSON request to the endpoint.
2. The API answers 402 with a payment challenge. The challenge expires about 5 minutes after it is issued.
3. Pay with an MPP wallet or client: a card through Stripe Link, or USDC on Tempo. No account or API key is needed.
4. Retry the request with the payment credential.
5. If the API answers 202, poll the returned result URL. Screens take 40 to 100 seconds, so `wait_seconds` of about 120 usually returns the result in one call.
6. Fetch the findings and the PDF. Retrieval needs no further payment.

The guide has the exact Link CLI and Tempo commands.

## Limits

The screen reports potential matches and coverage gaps for a person to review. It does not clear anyone, verify identity, find beneficial owners, or check PEP status. Source coverage and refund terms can change, so read the live offer.

## Not the Vigil MCP server

CMD+RVL also runs a keyed Vigil MCP server. That is a different product and needs an API key. This API does not.

For larger lists, custom policies, or other sources: https://hirecairn.com/
