---
name: dualentry
description: Start here for anything involving DualEntry, the user's live accounting ledger. Covers signing in, what the connection can and cannot do, and which DualEntry skill to use for records, bank matching, or questions about the numbers.
---

# DualEntry

DualEntry is an accounting system. This plugin talks to the user's live ledger through DualEntry's hosted server, so what you read is the real state of their books, not a copy or a sample.

Assume the person asking is an accountant, bookkeeper, or business owner rather than a developer. Answer in the language of their books: invoices, bills, vendors, periods. Do not explain tool calls, payloads, or IDs unless asked.

## Signing in

The first DualEntry request opens a browser for DualEntry sign-in. The user approves once and the connection stays authorized. There is no API key to create or paste. If a user offers one, tell them it is not needed.

A user only sees data their DualEntry account already permits. The connection does not widen their access.

## What the connection can do

- Search invoices, bills, journal entries, and other records
- Resolve vendors, customers, accounts, companies, and items
- Inspect history, related payments, and bank-match suggestions
- Preview and create contracts and fixed assets
- Save records and entities, after the user confirms the values

## Choosing the right skill

- Finding, reading, or drafting a record → **dualentry-records**
- Bank transactions, matching, or payments against a record → **dualentry-reconciliation**
- "How much", "compare", "what changed", aging or period questions → **dualentry-reporting**

## Before changing anything

Reading is free; writing is not. Never save, post, or delete until the user has seen the exact values and agreed. The **safe-accounting** rule covers this in full and applies to every DualEntry request.

## When something is missing

If the ledger returns nothing, say so plainly and show what was searched. An empty result usually means a filter was too narrow, the record sits in a different company, or the period is outside the range searched. Say which of those you suspect rather than guessing at an answer.

## Learn more

- MCP integration guide: https://docs.dualentry.com/developers/guides/mcp-integration
- Product: https://dualentry.com
- Support: support@dualentry.com
