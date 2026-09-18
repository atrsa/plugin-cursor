---
name: dualentry-records
description: Find, read, and draft DualEntry records such as invoices, bills, journal entries, contracts, and fixed assets, and resolve vendors, customers, accounts, companies, and items. Use for any request to look up, create, or change a record in the books.
---

# DualEntry records

Covers the things the ledger is made of: invoices, bills, journal entries, contracts, fixed assets, and the entities they point at.

## Find before you write

Search first, always. Most requests that sound like "create" are really "find the existing one". A user asking to add a vendor usually has that vendor already, spelled differently.

When a name could match several entities, list the candidates with enough detail to tell them apart and let the user choose. Never pick between two similar vendors yourself.

## Searching

Only posted records come back by default. Drafts and archived records are excluded until you ask for them, so "all the unpaid bills" means "all the posted unpaid bills" unless you widen the status.

Results are paginated and carry a flag saying whether more exist. Never present the first page as if it were everything.

## Refer to records the way the ledger does

Every record has two different numbers, and mixing them up is the easiest mistake to make here.

- The **number** is what people read: an invoice numbered 7276 is `IN-7276`, the first fixed asset is `FA-1`.
- The **id** is an internal handle, often five or six digits, for passing to other tools.

Search results hand you the finished reference; detail responses give you the number to build it from. Either way, use what the ledger returned. A reference assembled from the id points at nothing the user can find, so an invoice whose id happens to be 513425 is still `IN-7276` and never `IN-513425`.

Record prefixes cover roughly thirty types, among them `IN` invoice, `BI` bill, `JE` journal entry, `DE` direct expense, `CP` customer payment, `VP` vendor payment, `FA` fixed asset, and `REV` revenue recognition.

## Related records

Asking for a record's related records returns matches grouped by relationship, capped at 25 per relationship. When that cap is hit, say so rather than implying the list is complete.

Related records include drafts and archived items, unlike a search, so check the status on each row before describing something as settled.

## Reading a record

Lead with what the user asked for. Then give the context that makes it usable:

- Amount with currency, and the date in full
- Status: open, paid, partially paid, or void
- The entity on the other side of it
- Related payments and history when the question implies them

Quote figures exactly as the ledger returns them. Do not round, convert currencies, or add up totals yourself. If a total is needed and not returned, say you are computing it and show the parts.

Amounts arrive with their currency attached. Keep them together, and never total across currencies, since the ledger does no conversion for you.

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
