---
description: Simulate a dollar-cost-averaging plan on real price history, e.g. /dca $50 weekly into bitcoin since 2018
---

Run the plan described in `$ARGUMENTS` through the BTC DCA Engine and report what it would be worth.

1. Read the amount, the schedule (daily, weekly, monthly or quarterly), the asset and the start date
   out of the request. If the asset is anything but obvious, call `list_assets` first and match it to
   an exact key; if a start date is missing, use the earliest date that asset covers and say so.
2. Call `run_dca`. For two or more plans in one request, call `compare_plans` instead and rank them.
3. Report: total invested, value at the last close, profit, the money-weighted return, and the units
   held. Name the date the prices run to.
4. Finish with the share link from the result, so the run can be opened and checked.

Historical arithmetic only — no advice, no forecast.
