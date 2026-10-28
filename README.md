# Starbucks Loyalty Strategy Data Analyst Portfolio Project

**Project status:** Framework / implementation-ready starter  
**As-of date:** 2026-10-27  
**Target role:** Data Analyst, Loyalty Strategy — Job ID 260079240  
**Warehouse project:** `driiiportfolio`  
**Evidence standard:** Synthetic data only unless explicitly labeled otherwise.

## Project objective

Build an end-to-end loyalty analytics workflow that demonstrates business problem structuring, synthetic data generation, data quality assurance, BigQuery SQL modeling, customer retention and offer analysis, experiment evaluation, financial scenario modeling, Looker Studio reporting, and executive recommendations.

This is a candidate portfolio simulation. It is **not** an internal Starbucks project and does not use Starbucks proprietary data, systems, internal KPIs, or results.

## Primary business question

Which simulated loyalty engagement intervention, if any, is associated with improved repeat purchasing and retention at acceptable incremental contribution cost—and what additional evidence would be required before a real-world rollout?

## Recommended tools

- GitHub: version control, documentation, review trail
- Google Colab: reproducible synthetic data generation and Python statistical analysis
- Google BigQuery: raw/staging/mart datasets and SQL transformations
- Looker Studio: executive dashboard
- Google Sheets or Excel: optional QA reconciliation and scenario review
- Python libraries: pandas, numpy, scipy, statsmodels, matplotlib/seaborn only if appropriate; keep the first version simple

## Repository map

```text
.
├── README.md
├── Executive_Summary.md
├── Project_Disclaimer.md
├── Dashboard_Executive_Summary.md
├── docs/
│   ├── PROJECT_FRAMEWORK.md
│   ├── DATA_DICTIONARY.md
│   ├── METRIC_DICTIONARY.md
│   ├── ANALYSIS_PLAN.md
│   ├── ALTERNATIVE_BUSINESS_PROBLEMS.md
│   └── EXECUTION_LOG.md
├── notebooks/
│   └── synthetic_data_generation_plan.py
├── data/synthetic/                 # generated data only; large outputs normally gitignored
├── sql/
│   ├── staging/
│   └── marts/
├── analysis/
├── dashboard/
└── tests/
```

## Execution sequence

1. Read `Project_Disclaimer.md` and `docs/PROJECT_FRAMEWORK.md`.
2. Confirm the business question, decision, KPI definitions, and assumptions.
3. Generate reproducible synthetic data in Colab.
4. Validate the files locally in Colab before loading them.
5. Create BigQuery datasets/tables under project `driiiportfolio`; use a region consistently.
6. Load raw tables, run SQL QA checks, and stop if critical checks fail.
7. Build analytical marts at documented grain.
8. Perform descriptive, cohort, offer, and financial analysis.
9. Conduct a randomized experiment analysis only if the synthetic data includes valid randomized assignment; otherwise label the comparison observational.
10. Build the Looker Studio dashboard from validated views.
11. Complete executive and dashboard summaries using computed results—not invented findings.
12. Record decisions, limitations, and follow-up measures.

## BigQuery cost controls

The BigQuery free tier currently lists 10 GiB of storage and 1 TiB of query processing per month, subject to Google Cloud terms and billing configuration. Use dry runs, select only required columns, avoid repeated `SELECT *`, and do not enable paid services without checking the billing account and current pricing. A billing account may be required for some configurations even when usage remains within free allowances. Review current official pricing before execution.

## Definition of done

- Data files have reproducible generation parameters and a fixed seed.
- Referential integrity and event-sequence checks pass or documented exceptions are approved.
- SQL marts have declared grain and reconcile to source totals.
- Metric definitions and denominators are documented.
- Conclusions distinguish description, association, and causation.
- Financial results disclose every cost and margin assumption.
- Dashboard labels show date range, population, definitions, and synthetic-data warning.
- Executive recommendation names an action, owner role, timeline, risk, and follow-up metric.
