# Dashboard Executive Summary

## Purpose

The dashboard is a decision-support surface, not a decorative gallery of charts. It should answer: What changed? For whom? What may explain the change? What action or investigation follows?

## Page 1 — Executive performance

- Unique eligible members
- Active-member rate (with explicit activity window and eligible denominator)
- Repeat-purchase rate
- Transactions per eligible member
- Net sales per eligible member
- Estimated contribution per eligible member, only if cost assumptions are populated
- Offer funnel: eligible → assigned/exposed → viewed → completed/redeemed
- Trend line by week or month, with incomplete periods clearly flagged

## Page 2 — Retention and lifecycle

- Cohort retention by enrollment or first-purchase month
- Repeat interval distribution
- Reactivation rate under a declared inactivity rule
- Retention by synthetic tier and acquisition cohort
- Guardrail: population size and cohort maturity

## Page 3 — Offer and experiment evaluation

- Eligibility and assignment counts
- Exposure and engagement rates
- Primary outcome by treatment/control
- Absolute effect, relative lift where defined, confidence interval, and sample sizes
- Campaign cost and incremental contribution scenario
- Label results as causal only if assignment and analysis design justify it

## Page 4 — Data quality and governance

- Latest synthetic-data generation timestamp / version
- Row counts by source
- Duplicate primary-key count
- Orphan foreign-key count
- Invalid event sequence count
- Null/invalid critical-field count
- Data freshness / date coverage
- Link to metric dictionary and disclaimer

## Required filters

Date range, synthetic tier, offer type, channel, cohort, and treatment assignment where applicable. Filters must not silently change the denominator without clear labels.

## Visual rules

- Put the primary business outcome first.
- Show baseline and comparison period where meaningful.
- Do not use the same color to imply causality and descriptive performance.
- Do not show a target unless it is approved or explicitly labeled as a simulated target.
- Add a visible “Synthetic educational data — not actual Starbucks results” banner.
- Avoid presenting member counts as rates or averaging percentages without weighting.
