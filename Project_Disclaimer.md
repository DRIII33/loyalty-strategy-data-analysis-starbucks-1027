# Project Disclaimer

This portfolio project is an independent educational simulation created to demonstrate skills relevant to the publicly supplied Data Analyst, Loyalty Strategy job specification.

## Data provenance

- All generated customer, transaction, offer, engagement, and experiment records must be synthetic.
- Do not upload or publish real customer data, credentials, private company information, or restricted data.
- Publicly available Starbucks announcements may be cited as context; they are not a source of member-level performance data.
- Do not imply access to Starbucks internal systems, including Deep Brew, internal Rewards databases, or proprietary dashboards.

## Claims and interpretation

- Results calculated from generated records describe only this simulation.
- Synthetic results are not evidence of actual Starbucks member behavior, campaign performance, program profitability, churn, or lifetime value.
- Any simulated treatment effect is a property of the generator unless a valid experiment design and data support the inference.
- Observational differences must not be described as causal effects.
- Financial outputs depend on stated assumptions and must be labeled illustrative until validated with authorized real-world inputs.

## Program context

Starbucks publicly announced the redesigned Green, Gold, and Reserve Rewards levels in January 2026, with launch on March 10, 2026. Public program terms describe tier-specific benefits and earning rates. These public facts may inform scenario design; they do not establish internal performance or justify assuming any internal campaign, partner integration, or tier KPI.

## Naming and branding

“Starbucks-style” describes the educational use case only. This project is not sponsored by, affiliated with, or endorsed by Starbucks. Logos and proprietary visual assets should not be used unless permitted. The repository should clearly state that it is an independent candidate portfolio.

## Model assumptions

Maintain an `assumptions.csv` or equivalent table with:
- assumption name
- value or rule
- rationale
- source type (public fact, analytical convention, or simulation assumption)
- sensitivity range
- owner/date
- downstream metrics affected

## Publication checklist

Before publishing:
1. Remove secrets, tokens, account identifiers, and private data.
2. Confirm that all datasets are synthetic.
3. Re-run the notebook from a clean runtime.
4. Confirm README metrics match the latest reproducible outputs.
5. Mark uncomputed results as “not yet evaluated,” never as zero.
