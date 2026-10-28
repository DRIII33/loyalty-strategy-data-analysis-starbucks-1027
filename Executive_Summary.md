# Executive Summary

## Decision question

Which simulated loyalty engagement intervention, if any, should be tested further to improve repeat purchasing and retention while protecting incremental contribution and customer experience?

## Business context

Starbucks publicly announced a redesigned Rewards program with Green, Gold, and Reserve levels, launched March 10, 2026. The public rationale includes more meaningful benefits, personalization, and engagement. Public reporting is context only; internal member-level performance data is not available to this project.

## Project approach

1. Define the business decision and primary outcome before analyzing data.
2. Generate reproducible synthetic portfolio, member profile, transaction, offer-event, and assignment datasets.
3. Validate grain, keys, chronology, missingness, event lifecycles, and financial fields.
4. Transform data in BigQuery into customer-, offer-, and period-level marts.
5. Analyze retention, repeat purchase, offer funnel, tier/cohort differences, and financial sensitivity.
6. Estimate treatment effects only when a valid synthetic randomized assignment exists.
7. Publish a Looker Studio dashboard and decision memo with limitations and follow-up design.

## Findings

**Populate only after the analysis has run.** Do not enter example numbers as if they were results.

- Primary outcome and observation window: `[computed result]`
- Treatment/control sample sizes, if applicable: `[computed result]`
- Estimated effect and confidence interval: `[computed result]`
- Incremental contribution after campaign costs: `[computed result]`
- Material data-quality caveats: `[computed result]`

## Recommendation

`[Decision supported by the completed evidence: stop / refine / run a follow-up test / scale within a defined scope.]`

The recommendation must state the evidence strength, key assumption, financial downside, owner role, milestone, and success/guardrail metrics.

## Important limitation

All modeled data and results are synthetic. No conclusion in this portfolio should be presented as an actual Starbucks Rewards performance finding.
