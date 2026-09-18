# DualEntry plugin

Official DualEntry plugin, for asking your live accounting ledger questions in plain language.

The plugin lives in [`plugins/dualentry`](plugins/dualentry). Its [README](plugins/dualentry/README.md) covers what it does, how sign-in works, and what it can change.

## What ships

- Skills covering DualEntry overall, records, bank reconciliation, and reporting
- Commands: `unpaid-invoices`, `invoice-payments`, `vendor-bills`, `review-bank-matches`
- A `safe-accounting` rule holding the guardrails for changing the ledger
- DualEntry's hosted MCP server at `https://api.dualentry.com/mcp/`, authenticated with OAuth

## Validate before submitting

```bash
node scripts/validate-template.mjs
```

## License

Proprietary. Use of the hosted MCP is governed by DualEntry's terms.
