---
name: finance-hledger
description: Record or update personal finance transactions in this Obsidian vault using hledger plaintext accounting. Use for income, expenses, transfers, refunds, balances, or finance transaction corrections.
---

# Finance hledger

Use `30 Personal/Finance/hledger/main.journal` as the entry point. Store transactions in `30 Personal/Finance/hledger/transactions/YYYY.journal` based on the transaction date.

Rules:
- Use valid double-entry hledger journal syntax.
- Reuse existing account names when possible.
- Never invent a bank, wallet, credit card, balance, date, currency, or transaction detail that the user did not provide or that cannot be inferred safely from existing journal data.
- For a new real account, add an `account` declaration to `accounts.journal` when useful.
- Use `Expenses:*` for spending, `Income:*` for income, `Assets:*` for owned balances, `Liabilities:*` for debts, and `Equity:*` for opening/adjustment entries.
- Prefer one posting amount and let hledger infer the balancing amount when there are exactly two postings.
- Preserve comments or source/context the user provides when useful.
- For transfers, post between the two asset/liability accounts; do not classify a transfer as income or expense.
- For refunds, reverse the original economic direction when the original account/category is known.
- Do not record passwords, full card numbers, account credentials, recovery codes, or other secrets.
- Do not rewrite or reorder unrelated historical transactions.

When the hledger CLI is available, validate changes with:

`hledger -f "30 Personal/Finance/hledger/main.journal" check`

If a required accounting detail is genuinely missing and cannot be inferred from existing data, leave the transaction unrecorded rather than fabricating it.
