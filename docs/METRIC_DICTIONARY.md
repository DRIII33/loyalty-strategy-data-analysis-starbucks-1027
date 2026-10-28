# Metric Dictionary

All definitions below are recommended for this synthetic portfolio. They are not asserted to be Starbucks' internal definitions.

| Metric | Recommended definition | Required caveat |
|---|---|---|
| Eligible members | Distinct members satisfying eligibility at the defined point in time | Define whether eligibility is static or time-varying |
| Active members | Distinct eligible members with ≥1 qualifying transaction in window | Do not use app login alone unless that is the agreed activity rule |
| Active-member rate | Active members / eligible enrolled members | State denominator and window |
| Repeat-purchase rate | Members with ≥2 qualifying transactions / eligible members | Use same observation window for all groups |
| Retention | Original cohort members active in period k / original cohort size | Compare cohorts only when mature enough |
| Transactions per eligible member | Qualifying transactions / eligible members | Include zero-transaction eligible members |
| AOV | Net sales / qualifying transactions | Exclude or handle returns consistently |
| Offer view rate | Members with a view event / specified assigned or delivered population | Define whether denominator is assignment or delivery |
| Offer completion rate | Members completing offer / eligible assigned members | Alternative denominators answer different questions |
| Treatment effect | Treatment outcome mean − control outcome mean | Causal only under valid design and assumptions |
| Relative lift | (Treatment − control) / control | Undefined when control = 0 |
| Contribution | Net sales − applicable variable costs − attributable promotion costs | Use consistent cost coverage |
| Incremental contribution | Estimated treatment-control contribution difference after treatment-specific costs | Must not attribute all treatment spend to treatment |
| LTV | Discounted expected future contribution net of attributable costs | Requires justified forecast horizon, survival, margin, discount assumptions |

## Primary analysis specification

- Unit: member.
- Primary outcome: binary repeat-purchase indicator within fixed follow-up window.
- Primary estimate: difference in repeat-purchase proportions, treatment minus control.
- Report: group n, group rates, absolute percentage-point difference, relative lift if defined, 95% confidence interval, p-value only as secondary context, and practical/financial interpretation.
- Financial primary outcome, if modeled robustly: contribution per eligible member, not raw treatment-group sales.
- Guardrails: follow-up repeat purchase, offer cost per eligible member, and modeled customer-experience proxy if available.
