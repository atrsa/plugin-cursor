---
name: dualentry-reporting
description: Answer questions about the numbers in DualEntry, including totals, aging, overdue balances, and period comparisons. Use for "how much", "compare", "what changed", or "what is overdue" questions. DualEntry exposes no report endpoint, so every answer here is assembled from record searches.
---

# Reporting and analysis

These are questions about the shape of the books rather than a single record: what is owed, what changed, what is overdue.

## There is no report tool

DualEntry's connection exposes no profit and loss, balance sheet, trial balance, or aging endpoint. Every number you give comes from searching records and adding them up yourself.

Say so when it matters. A user who asks for "the P&L" should hear that you can total posted records for a period, and that this is not the same thing as their reviewed financial statements.

Never estimate, extrapolate, or fill a gap from general knowledge. An accounting answer that is approximately right is wrong.

## Search is the only source

Record search filters on record type, vendor, customer, company, GL account, memo, reference number, date range, amount range, payment status (paid, unpaid, partially paid), due date before or after, and intercompany status. Between them these cover most of what gets asked.

Two defaults will silently skew an answer:

- **Only posted records come back.** Drafts and archived records are excluded unless you ask for them. "Every unpaid invoice" quietly means "every posted unpaid invoice" until you widen it.
- **Results are paginated.** A response carries the rows, a page size, and a flag saying whether more exist. There is no grand total. To total a set honestly you must page until that flag goes false, and if you stop early, say the figure covers only what you read.

## Totals you compute yourself

Since no endpoint returns a sum, you are adding the rows. That puts the burden on you:

- Page to the end before quoting a total, or label the number as partial.
- Never mix currencies in one sum. Each row carries its own currency and there is no conversion. Total per currency and present them separately.
- Total per company when more than one is in scope, since a combined figure across legal entities is rarely what the user means.

## Framing the answer

State the period and the company before the number. "Q3 2026, SaaS Co.: 184,200 USD outstanding across 23 invoices" is usable; "184,200" alone is not.

Then give the breakdown that makes it actionable: the largest items, the aging buckets, or the movement since the comparison period.

## Aging and what is overdue

Filter unpaid records by due date to build buckets, then group by how far past due, count and total each bucket, and name the largest items.

Distinguish overdue from merely outstanding. An invoice inside its terms is not a problem, and presenting it as one erodes trust in the whole answer.

## Comparisons

When comparing periods, say what moved and by how much, in both absolute and percentage terms. Flag anything that makes the comparison unfair: a period that is not yet complete, a company added partway through, or a currency that differs between the two sets.

## Be explicit about limits

If a question cannot be answered from records, such as a forecast, a tax position, or a treatment that depends on policy, say so and describe what the books do show. Point the user to their accountant for judgment calls rather than offering one.
