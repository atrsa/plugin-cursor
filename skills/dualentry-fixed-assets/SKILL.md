---
name: dualentry-fixed-assets
description: Capitalize fixed assets in DualEntry, preview depreciation before it posts, and read schedules across book and tax depreciation books. Use for capitalizing an asset, checking depreciation, disposals, revaluations, or any question about depreciation books.
---

# Fixed assets

A fixed asset carries a depreciation schedule that runs for its whole life. Creating one is among the heaviest writes this connection makes, so it is worth slowing down.

## Always preview before creating

Previewing writes nothing. Creating posts to the general ledger on the first call and generates every depreciation period for the entire life of the asset at once. A long-lived asset across several books is hundreds of ledger rows from a single call.

The preview takes the same payload as the create, so checking costs nothing:

1. Preview with the payload you intend to use.
2. Show the user `total_periods`, `posting_book_periods` (how many reach the GL), the depreciable base, and the final net book value.
3. Create only after they agree.

A 1,200 asset over twelve months previews as twelve periods of 100, accumulating to 1,200 with a final net book value of zero. Numbers that plain are worth showing, because the ones that are wrong look just as plain.

## Building the payload

Every one of these is required, and the write fails without them:

`company_id`, `name`, `serial_number`, `memo`, `purchase_date`, `cost`, `currency_iso_4217_code`, `exchange_rate`, `status`, `asset_account_id`, `expense_account_id`, `accumulation_account_id`, and at least one entry in `depreciation_schedules`.

`serial_number` and `memo` are required but may be empty strings. The three account ids must be resolved first, and the generated entries have to balance to zero, so an asset account, a depreciation expense account, and an accumulated depreciation account all need to exist before you start.

`status` accepts only `active` or `inactive`. `disposed` and `fully_amortized` are system-managed, so never try to set them. Separately, `record_status` defaults to `posted`; pass `draft` when the user wants the asset staged without hitting the ledger.

Each schedule needs `depreciation_book_id`, `depreciation_method`, `depreciation_start_date`, and `convention`. Straight line additionally requires both `useful_life` and `salvage_value`, and omitting either is rejected.

**`useful_life` is counted in months.** Twelve means one year, not twelve.

## Depreciation books

An organization keeps several books and each schedule belongs to one, so read the list before creating anything.

Only one book posts to the general ledger. In a standard setup that is the book coded `BOOK`, financial reporting depreciation. The others, typically `FEDERAL` and `AMT`, are tax schedules that never touch the ledger.

Say which book a number came from, every time. Depreciation in a tax book changes the user's tax position but not their financial statements, and a figure quoted without its book is ambiguous.

## Reading a schedule

Fetching a schedule returns an event stream for one asset and one book, not a plain depreciation table. Events include the original `purchase`, a `depreciation_start` marker, each `depreciation` period, plus any revaluations and disposals, each with a status and a period label such as "Jan 2026". Date bounds narrow the range.

So a schedule read answers "what has happened to this asset", while a preview answers "what would happen if I created this". Do not confuse the two when reporting to a user.

Lead with what was asked. A question about this year's depreciation expense wants this year's depreciation events from the posting book, not the asset's whole life across three books.

## Referring to an asset

After it is saved, an asset is `FA-` plus its number, such as `FA-1`. That number is not the internal id. Use the number the ledger gives you and never assemble a reference from the id, or you will name an asset that does not exist.

## Changing an existing asset

Updates come in two forms: a full replacement and a partial change to named fields. Prefer the partial form when only a few fields move, so nothing is lost by omission.

Any change to cost, life, method, or start date reshapes the schedule. Treat it exactly like creating: describe what the schedule becomes before applying it.

## Disposal and deletion

Disposing of an asset and deleting it are different things. Disposal is an accounting event that lands in the asset's history with its own ledger effect; deletion removes the record. If a user says "get rid of this asset", find out which they mean first.

## What this cannot do

There is no report of all assets or of total depreciation for a period. Answer that kind of question by finding depreciation records through record search and totalling them yourself, and say that is what you did.
