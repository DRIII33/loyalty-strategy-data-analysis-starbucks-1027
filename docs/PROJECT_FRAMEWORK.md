# End-to-End Project Framework

**Version:** 1.0  
**As-of:** 2026-10-27  
**Project:** Loyalty Strategy Data Analyst Portfolio

## 1. Business scenario

The Loyalty Strategy & Performance team needs a defensible way to evaluate whether a loyalty engagement intervention changes customer behavior enough to justify its cost, and whether the observed response persists beyond the promotional period.

The scenario is motivated by Starbucks' publicly announced 2026 Rewards redesign and the job specification's emphasis on owned, syndicated, and behavioral data; forward-looking KPIs; LTV and engagement; analytical frameworks; dashboards/data products; cross-functional problem-solving; and executive narratives.

**This is a hypothetical decision scenario, not a claim that Starbucks has a known current problem or commissioned this analysis.** The project tests the workflow using synthetic data because proprietary member-level data is not publicly available.

### Stakeholder request (simulated)

“Evaluate which loyalty engagement mechanic merits a controlled follow-up test. Determine whether the intervention is associated with higher repeat purchasing and whether plausible incremental contribution can cover the cost without harming longer-term retention or customer experience.”

### Decision to support

Choose one:
- Stop the intervention.
- Refine targeting or offer economics and retest.
- Run a larger, pre-registered experiment.
- Recommend a limited rollout only if the evidence and economics support it.

Do not make a scale recommendation from synthetic results as if they predicted actual Starbucks outcomes.

## 2. Business problem and issue tree

### Primary problem

Loyalty activity measures (views, offer completions, Stars earned, or member spending) do not by themselves establish incremental customer value. The analyst must connect exposure to behavior, behavior to retention, and incremental behavior to contribution after costs.

### Diagnostic branches

1. **Member lifecycle**
   - Are newly enrolled members activating?
   - Is time to first qualifying purchase changing?
   - Which cohorts retain or lapse under the defined activity rule?
   - Are inactive members reactivating?

2. **Purchase behavior**
   - Are transactions per eligible member, repeat purchase, or basket value changing?
   - Is apparent growth due to member mix, seasonality, or shifts in observation windows?
   - Is a promoted purchase incremental or merely shifted from another day/product?

3. **Offer funnel**
   - Are members eligible and correctly assigned?
   - Are offers delivered, viewed, completed, and redeemed in sequence?
   - Where is the funnel drop-off?
   - Are offers reaching people who would have purchased anyway?

4. **Tier and benefit economics**
   - Do synthetic tiers differ in engagement and retention?
   - Are differences explained by selection into tier rather than the tier itself?
   - What are the assumed costs of Stars, free customizations, discounts, or other benefits?
   - Do conclusions change under different cost and margin assumptions?

5. **Digital experience**
   - Are app events complete and correctly ordered?
   - Do notification views/clicks correspond to later purchases?
   - Are card reload, offer exposure, and purchase events linked reliably?
   - Does the instrumentation allow the analyst to distinguish missing events from no activity?

6. **Measurement and data product**
   - Are KPI definitions consistent across dashboards?
   - Are joins multiplying sales or member counts?
   - Can results be refreshed reproducibly?
   - Are data-quality exceptions visible to decision-makers?

## 3. Primary study design

### Main portfolio question

Does a simulated personalized engagement intervention increase the probability of a qualifying repeat purchase during a fixed follow-up window, relative to a valid randomized control group, and does the estimated incremental contribution justify intervention cost?

### Design

- Unit of randomization: member.
- Population: synthetic members eligible under pre-defined rules.
- Treatment: simulated intervention assignment.
- Control: business-as-usual / no incremental intervention.
- Primary outcome: at least one qualifying repeat purchase during the follow-up window.
- Secondary outcomes: transactions per eligible member, net sales per eligible member, offer engagement, reactivation, and retention after the intervention.
- Financial outcome: incremental contribution per eligible member after intervention costs, using explicitly simulated cost assumptions.
- Guardrails: unsubscribe/notification fatigue proxy if modeled, redemption burden, long-term repeat purchase, and segment disparities.
- Analysis: intention-to-treat as primary; treatment-on-treated is not primary unless exposure compliance and assumptions are appropriately handled.

**Important:** If the generator does not create randomized assignment, do not use causal language. Analyze associations and describe a future experiment instead.

## 4. Research hypotheses

H1: The treatment group has a higher repeat-purchase rate than control during the defined outcome window.

H2: The intervention's estimated incremental contribution per eligible member is positive after modeled variable and campaign costs.

H3: Treatment response differs across pre-specified behavioral segments; segment findings are exploratory unless powered and pre-registered.

H4: The observed difference persists into a post-offer follow-up window rather than reflecting only short-term purchase timing.

H5: Data quality and event instrumentation are sufficient to measure assignment, exposure, outcome, and cost consistently.

For each hypothesis, document the null, alternative, primary metric, minimum effect of business interest, test, assumptions, sample size, and decision rule before analysis.

## 5. Methodology

### Phase 0 — Project governance and intake

- Write a one-page brief.
- Define stakeholder, decision, target population, scope, deadline, and constraints.
- Classify each question as descriptive, diagnostic, predictive, or causal.
- Create an assumptions register and decision log.

**Gate:** No analysis starts until the primary outcome, denominator, observation window, and decision are defined.

### Phase 1 — Source and data plan

Use synthetic data generated for this project. Do not rely on a public dataset as if it reflected the 2026 program. The classic public Starbucks Capstone dataset can be an optional schema-learning reference, but its older offer/profile/transcript structure does not represent the 2026 Rewards tiers or current internal performance.

Required synthetic entities:
- `dim_member`: synthetic member profile and membership start.
- `dim_offer`: offer metadata, eligibility, type, validity, cost assumptions.
- `fact_transaction`: one row per synthetic transaction.
- `fact_offer_event`: one row per offer lifecycle event.
- `fact_assignment`: one row per member/experiment assignment.
- `fact_reward_event` (optional): Stars earned/redeemed, explicitly synthetic.
- `dim_date` (optional): date spine for cohorts and reporting.

Keep event-level logs in a long format. If using a JSON `value` field, retain raw JSON and extract typed columns in staging.

### Phase 2 — Synthetic generation

Use Python in Colab with `numpy`, `pandas`, and a fixed seed. Start with rule-based plus sequential simulation; do not start with GANs. Rule-based generation is easier to audit, test, and explain.

Suggested initial scale:
- 10–20 offer definitions
- 10,000–20,000 synthetic members
- 100,000–300,000 transactions/events combined, depending on runtime
- At least 8–12 weeks of observed time, preferably longer if retention windows are analyzed

These are project design choices, not claims about Starbucks' current population. Generate IDs deterministically. Generate transactions independently from offer events, and do not automatically count an offer completion as a purchase unless a transaction event supports it.

Include configurable assumptions for:
- enrollment and member tier distribution
- transaction frequency and basket values
- offer eligibility and assignment
- view and completion probabilities
- treatment effect (including a zero-effect configuration for validation)
- variable contribution rate and offer costs
- time windows and seasonality
- data-quality defect injection for QA testing

**Do not hard-code income as the cause of engagement.** If demographic fields are included, use them for data-modeling practice only; avoid unsupported behavioral stereotypes and keep the project focused on behavioral/transactional evidence.

### Phase 3 — Local data validation

Before upload:
- Check row counts and schemas.
- Check unique primary keys.
- Check foreign keys to member and offer tables.
- Check event timestamps and event sequence.
- Check transaction amount is nonnegative unless returns are modeled explicitly.
- Check assigned treatment/control counts against intended randomization.
- Check no outcomes occur before assignment where the design forbids it.
- Check eligibility and observation windows.
- Save a validation report and generator configuration.

Critical failures stop the load. Noncritical exceptions must be listed and quantified.

### Phase 4 — BigQuery ingestion and modeling

Project: `driiiportfolio`.

Recommended datasets:
- `loyalty_raw`: append-only loaded synthetic files.
- `loyalty_stg`: typed, cleaned, normalized staging views/tables.
- `loyalty_mart`: reusable analytical marts for dashboards and analysis.
- `loyalty_qa`: validation outputs and run metadata.

Use a single region consistently. Create date-partitioned tables only when a date column and query pattern justify it. Avoid a short partition expiration that would silently delete historical data needed for a multi-month cohort analysis. For this project, leave expiration unset initially or set it only after documenting retention requirements.

Use BigQuery SQL for:
- type casting and date parsing
- JSON extraction
- standardizing event names and categories
- deduplication with explicit rules
- orphan-key checks
- customer/offer/transaction marts
- cohort retention
- offer-funnel metrics
- treatment/control outcome tables
- dashboard views

Use dry runs and inspect bytes processed before large queries. The first version should fit well within the published free query allowance if scans are limited, but always verify current pricing and billing configuration.

### Phase 5 — Analysis

1. **Descriptive baseline:** member population, transactions, spend, frequency, offers and time coverage.
2. **KPI decomposition:** separate customer count, frequency, and average transaction value.
3. **Cohorts:** retention by enrollment or first-purchase month with consistent maturity windows.
4. **Offer funnel:** eligibility → assignment/delivery → view → completion/redemption → qualifying transaction.
5. **Experiment:** intention-to-treat outcome differences, confidence intervals, sample sizes, balance checks, sample-ratio mismatch checks, and guardrails.
6. **Financial economics:** incremental contribution = estimated incremental qualifying outcomes × defensible contribution per outcome − attributable campaign/benefit costs. Avoid counting all treatment-group spend as incremental.
7. **Sensitivity:** conservative/base/upside assumptions without invented scenario probabilities.
8. **Robustness:** alternate definitions, missing events, outliers, seasonality, treatment compliance, multiple testing, and subgroup exploration.
9. **Forecasting (optional):** compare a simple baseline to a more complex model on a holdout period. Do not forecast actual Starbucks outcomes from synthetic data.

### Phase 6 — Dashboard and executive deliverables

Dashboard must contain:
- headline KPIs with clear denominators
- trend and cohort views
- offer funnel
- experiment effect and uncertainty
- cost/contribution scenario
- segment comparison with sample sizes
- data-quality and freshness panel
- definitions and synthetic-data notice

Executive narrative:
1. Decision required.
2. Finding.
3. Evidence and uncertainty.
4. Financial implications.
5. Risks and limitations.
6. Recommendation and alternatives.
7. Owner, timeline, success criteria, and follow-up.

### Phase 7 — Close the loop

Create a decision log entry with decision, rationale, approver role (simulated), action owner role, due date, KPI, baseline, target/threshold, monitoring window, and next review date.

For the portfolio, the “implementation” is a proposed follow-up experiment and measurement plan—not a real deployment.

## 6. Metric standards

Each metric must specify:
- name and business purpose
- formula
- numerator and denominator
- unit of analysis
- eligibility rules
- event/transaction exclusions
- time window
- source view
- owner
- refresh cadence
- known limitations

Never compare rates with different denominators or time windows. Never average member-level rates when the business question requires a population-weighted rate.

## 7. Key metrics

- Active-member rate = unique active members / eligible enrolled members.
- Repeat-purchase rate = eligible members with ≥2 qualifying purchases in the window / eligible members.
- Retention at period k = original cohort members active in period k / original cohort size.
- Offer view rate = eligible assigned/exposed members who viewed / defined eligible assigned/exposed members.
- Offer completion rate = members completing offer / members eligible for completion, with denominator explicitly specified.
- Transactions per eligible member = qualifying transactions / eligible members.
- Net sales per eligible member = qualifying net sales / eligible members.
- Treatment effect (binary outcome) = treatment rate − control rate.
- Relative lift = (treatment rate − control rate) / control rate; undefined if control rate is zero.
- Incremental contribution per eligible member = treatment-control contribution difference under a valid design, net of relevant per-member treatment cost.
- ROI = (incremental benefit − investment cost) / investment cost; only if costs and incremental benefit are defined consistently.

These are recommended operational definitions for the portfolio, not Starbucks' confirmed internal KPI definitions.

## 8. Risks and mitigations

| Risk | Mitigation |
|---|---|
| Synthetic output presented as real | Banner, disclaimer, and evidence labels in every deliverable |
| Bad joins inflate sales | Declare grain, assert key uniqueness, reconcile pre/post-join totals |
| Event logging incomplete | QA panel and sensitivity checks |
| Selection bias | Random assignment in simulation; intention-to-treat |
| Short-term lift masks pull-forward | Post-intervention follow-up window |
| More spend mistaken for profit | Contribution model with costs and sensitivity |
| Overfitting | Baseline comparison and holdout validation |
| Unsupported tier assumptions | Use public facts only for scenario context; simulated tiers clearly labeled |
| Free-tier charges | Dry runs, scoped queries, no unnecessary paid services |
| Dashboard ambiguity | Definitions, denominators, date coverage, sample sizes |

## 9. Mission and values integration

Use the supplied Starbucks values as an analytical quality lens:
- **Craft:** reproducible, carefully validated work.
- **Courage:** disclose null or unfavorable results.
- **Results:** link analysis to measurable decisions and follow-up.
- **Belonging:** examine aggregate results for meaningful segment differences without overclaiming.
- **Joy:** make the evidence understandable and useful to partners.

## 10. Completion criteria

The project is complete only when:
- all pipeline steps are reproducible;
- QA checks pass or exceptions are approved and documented;
- SQL output reconciles;
- statistical claims match the design;
- costs and assumptions are explicit;
- dashboard metrics match validated query outputs;
- four required markdown files are complete;
- the final recommendation is decision-ready;
- follow-up measures and limitations are recorded.
