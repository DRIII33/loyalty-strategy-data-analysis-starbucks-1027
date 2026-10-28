# Analysis Plan and Statistical Decision Rules

## Before inspecting treatment outcomes

Record:
- experiment ID and version
- eligible population
- assignment method and allocation ratio
- primary outcome and observation window
- secondary outcomes and guardrails
- minimum effect of business interest
- test and confidence level
- sample-size/power rationale
- stopping rule
- segment analyses designated confirmatory vs exploratory

## Quality and balance checks

1. Verify unique member assignment per experiment.
2. Confirm eligible treatment/control counts and investigate sample-ratio mismatch.
3. Check baseline covariates if generated and relevant.
4. Check assignment precedes the outcome window.
5. Verify event coverage is similar between groups.
6. Analyze by intention-to-treat, preserving original assignment.
7. Document contamination and missing exposure.

## Primary binary outcome

For each group:
- rate = members with repeat purchase / eligible assigned members
- absolute effect = treatment rate − control rate
- relative lift = absolute effect / control rate, only if control rate > 0
- confidence interval: two-proportion method suitable for the design; use a robust or design-specific approach when assumptions require it.

Do not report only the p-value. Include effect size, interval, sample sizes, period, and business relevance.

## Financial translation

Estimate incremental outcomes as the treatment-control difference multiplied by the eligible treatment population, only when the design supports causal interpretation. Multiply by a defensible contribution amount per incremental outcome, then subtract attributable treatment costs. Do not double-count variable costs already included in contribution.

If cost or margin is unknown, show a sensitivity table rather than a single “ROI” claim. Label all inputs synthetic.

## Robustness checks

- Alternate activity/retention thresholds
- Follow-up window extension
- Exclusion of invalid or late events
- Transaction-level vs member-level outcome comparison
- Zero-effect generator run as a pipeline sanity check
- Treatment-effect parameter variation
- Outlier/winsorization sensitivity for spend
- Segment analysis with minimum sample thresholds
- Multiple-testing caution
- Event logging missingness scenario

## Causal language policy

Allowed for synthetic randomized data when design/QA are valid: “In this simulated randomized experiment, assignment to treatment changed the measured outcome by X.”

Not allowed: “Starbucks Rewards treatment caused X in real customers.”

For nonrandomized data, use “associated with,” “differed,” or “correlated,” and list plausible confounding explanations.
