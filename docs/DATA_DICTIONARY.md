# Data Dictionary (Proposed Synthetic Schema)

The schema is a portfolio design, not an internal Starbucks schema. Names can change only if the change is documented and all dependent SQL is updated.

## `dim_member` — one row per synthetic member

| Field | Type | Definition |
|---|---|---|
| member_id | STRING | Stable synthetic primary key |
| enrollment_date | DATE | Synthetic enrollment date |
| synthetic_tier | STRING | GREEN / GOLD / RESERVE; simulated membership label |
| cohort_month | DATE | Month of enrollment or first qualifying purchase; declare which |
| is_eligible | BOOL | Eligibility under study-specific rule |
| profile_version | STRING | Generator version for traceability |

Optional demographics should be omitted unless needed for a clear analytical question. Never use generated demographic correlations as real-world evidence.

## `dim_offer` — one row per offer

| Field | Type | Definition |
|---|---|---|
| offer_id | STRING | Stable synthetic offer key |
| offer_type | STRING | E.g., personalized_discount, bonus_stars, informational |
| start_date | DATE | Offer start date |
| end_date | DATE | Offer end date |
| channel | STRING | Synthetic channel |
| eligibility_rule | STRING | Human-readable rule name |
| assumed_cost_per_completion | NUMERIC | Explicit simulation assumption, not Starbucks cost |
| offer_version | STRING | Version of synthetic offer specification |

## `fact_transaction` — one row per transaction

| Field | Type | Definition |
|---|---|---|
| transaction_id | STRING | Unique synthetic transaction ID |
| member_id | STRING | Foreign key to dim_member |
| transaction_ts | TIMESTAMP | Transaction timestamp |
| net_sales | NUMERIC | Synthetic net sales under declared tax/discount convention |
| discount_amount | NUMERIC | Synthetic discount amount |
| variable_cost | NUMERIC | Synthetic variable cost if modeled |
| channel | STRING | app / in_store / other simulated channel |
| is_qualifying | BOOL | Qualifying purchase under analysis rules |

## `fact_offer_event` — one row per event

| Field | Type | Definition |
|---|---|---|
| event_id | STRING | Unique synthetic event ID |
| member_id | STRING | Foreign key to member |
| offer_id | STRING | Foreign key to offer |
| event_ts | TIMESTAMP | Event timestamp |
| event_type | STRING | assigned / delivered / viewed / completed / redeemed / expired |
| event_payload_json | STRING | Optional raw JSON for ingestion practice |
| generator_run_id | STRING | Reproducibility key |

Do not infer purchase from a `completed` event unless the business definition and a supporting transaction establish that relationship.

## `fact_assignment` — one row per member per experiment

| Field | Type | Definition |
|---|---|---|
| experiment_id | STRING | Synthetic experiment key |
| member_id | STRING | Member key |
| assigned_group | STRING | treatment / control |
| assignment_ts | TIMESTAMP | Assignment timestamp |
| eligible_at_assignment | BOOL | Eligibility at assignment |
| randomization_stratum | STRING | Optional pre-specified stratum |
| exposure_observed | BOOL | Whether exposure was recorded; not the primary grouping variable |

## `fact_reward_event` — optional

One row per Stars earn/redeem/adjustment event. Include event ID, member ID, event timestamp, event type, Stars delta, and synthetic reward category. Define whether the field is signed and how reversals are represented.

## Table grain and join policy

- `dim_member`: member
- `dim_offer`: offer
- `fact_transaction`: transaction
- `fact_offer_event`: lifecycle event
- `fact_assignment`: member × experiment
- `fact_reward_event`: reward ledger event

Aggregate facts to compatible grains before joining. Validate row counts and financial totals before and after every join.
