# Telecom churn customer segments

Status: Planned — no new analysis or findings claimed.

Planned week: November 30–December 6, 2026. Time budget: six hours.

## Business question
Which customer groups show the highest observed churn, and which three groups deserve further investigation?

## Data prerequisite
Locate and inspect the original project dataset before writing queries. Record its source URL, license, extraction date, grain, row count, missing values, and churn definition. Do not assume a schema or fabricate data. If the original extract is unavailable, identify an openly licensed replacement and document the change.

## Weekly steps
- Monday (45 min): define the question, scope, metric dictionary, and source.
- Tuesday (60 min): clean types, duplicates and missing values in Python or SQL; preserve a reproducible script.
- Wednesday (60 min): compare churn by tenure cohort and contract type, showing group sizes and consistent denominators. Reconcile totals to the source.
- Thursday (75 min): build a Tableau dashboard with three clear views and useful filters.
- Friday (45 min): write three evidence-based findings, limitations, and reproduction instructions.
- Saturday (45 min): validate calculations, publish the reviewed code and dashboard, and add the portfolio card.
- Sunday (30 min): practice a 90-second business explanation.

## Suggested project structure
`analysis/` for SQL and Python; `outputs/` for permitted aggregate exports; `tableau/` for workbook and screenshots; `docs/` for definitions and source notes. Do not commit credentials or restricted customer data.

## Acceptance checklist
- [ ] Dataset provenance and permitted use documented.
- [ ] Reproducible cleaning and analysis with dependencies.
- [ ] Churn numerator, denominator, group sizes and missing-data rules documented.
- [ ] Three findings supported by actual results.
- [ ] Associations described without claiming causal effects.
- [ ] Tableau calculations reconciled with SQL/Python.
- [ ] GitHub files and Tableau Public share URL verified.
- [ ] Portfolio card links to both destinations.

Publication URLs are intentionally pending until the work is completed and verified.
