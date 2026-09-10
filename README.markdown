# Payday Planner v2

Payday Planner answers one narrow question: **how much of the currently available checking balance is already spoken for before the next paycheck?**

## Source-of-truth contract

- `kjk.csv` is the single recurring-bill source. The web page loads it directly; bills are not duplicated inside JavaScript.
- The current available balance is entered deliberately and stored only in the browser with a verification timestamp. It is never committed to this public repository.
- Paid/unpaid marks are stored only in the browser.
- The planner calculates the next paycheck, unpaid listed bills before that paycheck, and the amount safe after those bills.
- The Daily Briefing should consume a verified snapshot; it should not independently maintain the bill list or imply that a stale balance is live.

## Daily Briefing snapshot contract

The compact snapshot contains:

1. `AVAILABLE_BALANCE`
2. `BALANCE_VERIFIED_AT`
3. `REQUIRED_UNTIL_PAYDAY`
4. `SAFE_AFTER_LISTED_BILLS`
5. `NEXT_PAYDAY`
6. `FRESHNESS` (`FRESH`, `STALE`, or `UNVERIFIED`)

Recommended briefing behavior:

- `FRESH`: show available, needed, and safe amounts.
- `STALE`: hide the apparent safe-to-spend conclusion and request a refresh.
- `UNVERIFIED`: show no balance-derived conclusion.
- Never scrape a banking website as part of the report build. Authentication, MFA, delayed posting, and changing markup make that unsuitable for a dependable morning workflow.

## Realistic routine

1. Open the bank and enter the **available** balance in Payday Planner.
2. Mark any listed bill due today as paid only after it has actually cleared or been intentionally covered.
3. Copy the three-line Briefing snapshot into the private Briefing finance input.
4. Refresh `kjk.csv` when a recurring amount or due day changes—not every morning.

The unavoidable bookkeeping is one verified balance entry. Everything else is calculated from the bill file and explicit paid marks.

## Bill CSV

Required columns:

```csv
title,description,amount,day
Spotify,Monthly subscription,21.64,14
```

`day` is the recurring calendar day from 1–31. For shorter months, the planner uses that month’s last valid day.
