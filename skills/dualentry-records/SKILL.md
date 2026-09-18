---
name: dualentry-records
description: Find, read, and draft DualEntry records such as invoices, bills, journal entries, contracts, and fixed assets, and resolve vendors, customers, accounts, companies, and items. Use for any request to look up, create, or change a record in the books.
---

# DualEntry records

Covers the things the ledger is made of: invoices, bills, journal entries, contracts, fixed assets, and the entities they point at.

## Find before you write

Search first, always. Most requests that sound like "create" are really "find the existing one". A user asking to add a vendor usually has that vendor already, spelled differently.

When a name could match several entities, list the candidates with enough detail to tell them apart and let the user choose. Never pick between two similar vendors yourself.

## Reading a record

Lead with what the user asked for. Then give the context that makes it usable:

- Amount with currency, and the date in full
- Status: open, paid, partially paid, or void
- The entity on the other side of it
- Related payments and history when the question implies them

Quote figures exactly as the ledger returns them. Do not round, convert currencies, or add up totals yourself. If a total is needed and not returned, say you are computing it and show the parts.

## Drafting a change

Building a record is a conversation, not a form:

1. Gather what the record needs. Ask for anything missing, and never infer a date, currency, account, or company.
2. Show the complete draft back in plain language, with every value visible.
3. Name the company it will land in.
4. Wait for an explicit yes. "Looks good", "go ahead", "yes" all count; silence and a follow-up question do not.
5. Save, then confirm what was created and how to find it.

If the user changes a value mid-review, show the whole draft again. Partial confirmations are where wrong entries come from.

## Contracts and fixed assets

You can preview these before creating them. Use that: show the preview, let the user read it, then create. A fixed asset carries a schedule that is tedious to unwind once posted, so the preview step matters more here than anywhere else.

## Closed periods

If a change would touch a closed period, stop and say so. Do not attempt a workaround, and do not suggest reopening the period unless the user raises it.
