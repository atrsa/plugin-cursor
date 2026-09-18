---
name: review-bank-matches
description: Walk through DualEntry's suggested bank matches so the user can approve or reject them, with unclear matches separated out.
---

# Review bank matches

1. Fetch the current bank-match suggestions for the account and period the user names.
2. Separate the clear matches from the ones needing judgment.
3. Present clear matches together, showing bank line, matched record, amount, and date gap, so the user can approve them in one pass.
4. For each unclear match, say what makes it uncertain: a differing amount, one payment across several invoices, a date gap, or no candidate record at all. Show the near-misses and why each falls short.
5. Never accept a match on the user's behalf. Apply only what they approve, then report what was matched and what is still open.
