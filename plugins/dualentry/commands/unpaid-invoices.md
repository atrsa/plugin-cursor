---
name: unpaid-invoices
description: List unpaid customer invoices, newest first, with an aging breakdown and the largest balances called out.
---

# Unpaid invoices

1. Ask for the period and company if the user has not said, and for a minimum amount if the list is likely to be long.
2. Search DualEntry for invoices that are open or partially paid in that period.
3. Report the total outstanding and the invoice count first, then list the invoices with customer, amount, due date, and days overdue.
4. Group by aging bucket (current, 1-30, 31-60, 61-90, 90+) and name the largest balances.
5. Distinguish overdue from outstanding-but-not-yet-due. Do not present an invoice inside its terms as a problem.
