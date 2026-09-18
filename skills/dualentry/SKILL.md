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

- **Records** across roughly thirty types, including invoices, bills, journal entries, expenses, payments, credits, prepayments, and refunds: search them, read their detail and history, find related records, and create or update them
- **Entities**: search vendors, customers, accounts, companies, and items, and create or update them
- **Companies**: list the legal entities in the organization
- **Bank reconciliation**: read match suggestions, list and inspect bank transactions, trigger matching, and match or unmatch
- **Contracts**: read one, preview its schedule, create it
- **Fixed assets**: preview and create, update or patch, delete, read depreciation schedules, and list depreciation books

## What it cannot do

There is no report endpoint. No profit and loss, balance sheet, trial balance, or aging report exists. Totals and comparisons are assembled from record searches, which is what **dualentry-reporting** is for.

The connection also does not convert currencies, and it does not create journal entries for you out of a described intent. It works on records, not on narrative instructions.

## Choosing the right skill

- Finding, reading, or drafting a record → **dualentry-records**
- Bank transactions, matching, or payments against a record → **dualentry-reconciliation**
- "How much", "compare", "what changed", aging or period questions → **dualentry-reporting**
- Capitalizing an asset, depreciation, or depreciation books → **dualentry-fixed-assets**

## Before changing anything

Reading is free; writing is not. Never save, post, or delete until the user has seen the exact values and agreed. The **safe-accounting** rule covers this in full and applies to every DualEntry request.

## When something is missing

If the ledger returns nothing, say so plainly and show what was searched. An empty result usually means a filter was too narrow, the record sits in a different company, or the period is outside the range searched. Say which of those you suspect rather than guessing at an answer.

## Learn more

- MCP integration guide: https://docs.dualentry.com/developers/guides/mcp-integration
- Product: https://dualentry.com
- Support: support@dualentry.com
