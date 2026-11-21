# Churn data intake and reconciliation worksheet

Prepared November 21, 2026 for the November 30–December 6 segment-analysis week.

**Status: preparation only.** No dataset has been inspected, no queries have been executed, and no findings are established by this worksheet. Read [the weekly brief](weekly-segment-analysis-plan.md) first. Complete the blank evidence fields before implementing analysis.

## 1. Source and grain gate

| Required evidence | Value to record |
| --- | --- |
| Original source URL and dataset version | Pending |
| License and permission to redistribute | Pending |
| Download/extraction timestamp and file checksum | Pending |
| Row count and field names/types | Pending |
| Grain: one row per customer, account, or customer-period | Pending |
| Observation period and churn-label definition | Pending |
| Is this sample/synthetic data? | Pending |
| Permitted publication: aggregate only or source rows | Pending |

If the original extract is unavailable, document the replacement and its different limitations. Do not claim a snapshot churn fraction is a monthly churn rate without an explicit observation window.

## 2. Map actual columns before coding

These are conceptual fields, not claims about source column names.

| Concept | Actual source field | Validation decision |
| --- | --- | --- |
| Entity key | Pending | Test nulls and duplicate keys at the declared grain |
| Churn outcome | Pending | List observed values; map known positive/negative labels; preserve unknowns |
| Tenure | Pending | Establish units, numeric conversion and invalid/negative values |
| Contract group | Pending | Inspect categories; normalize whitespace/case without merging different contracts |
| Observation period, if present | Pending | Prevent customer-period rows being mistaken for unique customers |

Do not guess that duplicates are expendable. Distinguish exact duplicates from conflicting records and legitimate repeated observations. Record the chosen rule and retained count.

## 3. Metric contract

For the validated cohort:

- **Eligible entities:** distinct entities at the confirmed analysis grain after documented exclusions.
- **Known-outcome entities:** eligible entities with a valid observed churn label.
- **Churned entities:** known-outcome entities mapped to the positive churn label.
- **Observed churn fraction:** churned entities / known-outcome entities. Return null when the denominator is zero.
- **Outcome coverage:** known-outcome entities / eligible entities; show missing outcomes separately.
- **Segment volume:** eligible entities in that segment, including an explicit unknown segment where needed.

Build separate tenure and contract summaries first. A customer may appear once in each separate segmentation; never add totals across those two tables. Publish chosen tenure boundaries only after inspecting the units and distribution. Each table must partition its cohort without overlap or gaps.

## 4. Reconciliation worksheet

Record expected value, actual value, pass/fail, and explanation for each check. No checks are passed yet.

1. Raw rows = retained rows + excluded rows, with mutually exclusive exclusion reasons.
2. Declared unique key has no unresolved duplicates or nulls in the analytic table.
3. Known-outcome entities + unknown-outcome entities = eligible entities.
4. Churned entities are between zero and known-outcome entities.
5. Within each segmentation, group counts sum to the cohort counts.
6. Overall churn fraction equals the denominator-weighted segment fraction, within the documented rounding tolerance.
7. Every exported fraction is within 0–1 or explicitly null.
8. Tableau totals and fractions match the executed SQL/Python outputs under the same filters.
9. Public outputs contain no personal identifiers, free-text customer details or credentials.

Suggested QA log headers: `check_id,expected,actual,status,explanation,run_timestamp`.
Leave values pending until a real execution produces them.

## 5. Aggregate handoff to Tableau

Proposed output headers for implementation after schema validation:

`segmentation,segment,eligible_entities,known_outcome_entities,churned_entities,observed_churn_fraction,outcome_coverage`

Use aggregate counts to recalculate rates when filtering. Do not average already-rounded segment percentages. Add the source/version and observation-period limitations to the workbook description.

Suggested views:
1. Cohort size, observed churn fraction and outcome coverage.
2. Tenure segment rates with denominator labels.
3. Contract segment rates with denominator labels.

Use a documented small-group threshold and flag small groups instead of presenting unstable rankings as strong evidence.

## 6. Publication evidence gate

- GitHub: actual source/mapping notes, executable cleaning/analysis, aggregate exports and QA log.
- Tableau: workbook verified against those exports, then an accessible live share URL.
- Portfolio: separate GitHub and Tableau links, screenshot, and findings supported by executed outputs.
- Interpretation: describe associations, uncertainty and missing-data limits; do not claim a retention intervention caused a change.

A live worksheet or plan is not a completed analysis or an independently verified resume achievement.
