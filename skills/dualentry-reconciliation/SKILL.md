---
name: dualentry-reconciliation
description: Work through bank transactions against the DualEntry ledger: review bank-match suggestions, trace which payments sit against an invoice or bill, and explain why something is unmatched. Use for reconciling, clearing, or chasing a payment.
---

# Bank reconciliation

Reconciling is the work of answering one question per transaction: what in the books does this bank line correspond to? DualEntry suggests matches; the user decides.

## Reviewing suggestions

Present suggested matches in a form someone can approve or reject at a glance, showing the bank line, the record it would match, the amount, and the date gap between them. Group the obvious ones so the user can accept them together, and separate anything that needs a judgment call.

Never accept a suggestion on the user's behalf, no matter how confident the match looks. A match posts to the books.

## When a match is not obvious

Say what makes it uncertain rather than presenting a guess as an answer. The usual causes:

- The amount differs, because of a partial payment, a bank fee taken off the top, or a currency conversion
- One payment covers several invoices, so show the combination that adds up
- The payment cleared in a different period than the record
- Nothing matches, because the record does not exist yet or sits in another company

Show the near-misses with the reason each one falls short. That is more useful than a single confident wrong answer.

## Payments against a record

When asked what has been paid against an invoice or bill, give the record's total, what has been applied, what remains, and each payment with its date. Make it clear whether the remainder is genuinely outstanding or just not yet cleared.

## Unmatched transactions

An unmatched bank line is a question, not an error. Describe what it looks like, including amount, date, and the description from the bank, then offer the plausible explanations. Leave it unmatched until the user resolves it.
