# Alternative Loyalty Strategy Portfolio Problems

Use this list to build a second portfolio later. These are plausible problem types for a loyalty analytics function, not confirmed current Starbucks internal problems or hiring rationales. Choose one main question per portfolio to avoid an unfocused project.

| ID | Problem type | Core question | Primary methods | Data needed |
|---|---|---|---|---|
| P01 | Retention / churn | Which member cohorts become inactive, and when? | Cohorts, survival analysis, churn sensitivity | Membership, transaction history |
| P02 | Activation | Which newly enrolled members make a first qualifying purchase? | Activation funnel, time-to-event | Enrollment, transaction events |
| P03 | Offer incrementality | Does an offer create additional purchases? | Randomized experiment, confidence intervals | Eligibility, assignment, exposure, outcomes, costs |
| P04 | Offer fatigue | Do repeated offers reduce engagement or opt-outs? | Exposure-frequency analysis, experiment | Offer history, notification outcomes |
| P05 | Tier benefit economics | Are benefits associated with incremental value after costs? | Cohorts, contribution, sensitivity | Tier history, transactions, reward costs |
| P06 | Stars earning/redemption | How do earning and redemption patterns vary? | Ledger reconciliation, cohort analysis | Stars ledger, transaction data |
| P07 | Reward breakage/liability | What portion of eligible rewards remains unredeemed? | Cohort aging, accounting-aligned definitions | Earn, expire, redeem ledger and accounting rules |
| P08 | Digital funnel | Where do app journeys fail between offer view and purchase? | Funnel analysis, event QA | Event logs, assignment, transactions |
| P09 | Notification optimization | Which timing/channel yields useful incremental response? | Factorial test or controlled experiment | Delivery, view, click, purchase, assignment |
| P10 | Feature adoption | Does app feature adoption precede or cause better outcomes? | Funnel + randomized rollout where feasible | Feature exposure, usage, outcomes |
| P11 | Reload incentives | Do reload bonuses change purchase behavior or only payment method? | Incrementality, substitution, cost analysis | Reloads, payment, transactions, assignment |
| P12 | Promotion pull-forward | Does a promotion shift transactions from future days? | Time-series experiment analysis | Daily transactions, treatment/control |
| P13 | Basket expansion | Do targeted offers increase items/basket value profitably? | Basket analysis, experiment, contribution | Line items, prices, costs, offers |
| P14 | Price/promotion elasticity | How do price or discount changes relate to demand? | Experimental or quasi-experimental elasticity | Prices, units, exposure, seasonality, costs |
| P15 | Personalization quality | Are recommendations relevant and incrementally useful? | Offline evaluation, online A/B test | Recommendation exposure, clicks, purchases |
| P16 | Tier migration | What predicts tier progression and requalification? | Cohort transitions, state-transition analysis | Tier history, Stars earning, spend |
| P17 | Customer value/LTV | Which behaviors predict future contribution? | Cohorts, probabilistic CLV, holdout validation | Longitudinal transactions, costs, survival |
| P18 | Campaign budget allocation | Which campaigns merit additional spend? | Incremental ROI, constrained optimization | Campaign costs, effects, capacity constraints |
| P19 | Data quality / metric reconciliation | Why do dashboards disagree? | Source profiling, lineage, reconciliation | Raw and certified reporting tables |
| P20 | Identity resolution | Are transactions and digital events linked correctly? | Match-rate QA, duplicate/orphan analysis | Identity keys, POS, app events |
| P21 | Seasonality and forecasting | What is the expected baseline for loyalty outcomes? | Seasonal-naive, moving averages, forecast evaluation | Sufficient history and calendar variables |
| P22 | Customer fairness / segment variation | Are benefits or interventions uneven across segments? | Segment diagnostics, interaction analysis | Relevant lawful attributes and outcomes |
| P23 | Partner integration | Does a partner benefit generate incremental visits or retention? | Partner-linked cohort/experiment | Authorized partner events, transactions, costs |
| P24 | Product roadmap prioritization | Which feature opportunity merits investment? | Opportunity sizing, impact/effort, experiment plan | Feature funnel, engineering cost, outcome estimates |
| P25 | KPI framework redesign | Are current metrics aligned with long-term value? | KPI tree, metric governance, sensitivity | Certified metrics, business objectives |
| P26 | Operational load | Do promotions create demand spikes that affect execution? | Time-series and guardrail analysis | Offer calendar, store/time outcomes, operational measures |

## Suggested selection criteria

Select the alternative based on:
1. Clear decision owner and decision.
2. Data availability and a credible outcome measure.
3. A feasible identification strategy.
4. Financial or customer-experience relevance.
5. A deliverable that can be completed with free-tier tools.
6. A clear distinction between synthetic learning and real business evidence.
