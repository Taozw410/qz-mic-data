## Material Passport

- Origin Skill: experiment-agent
- Origin Mode: validate
- Origin Date: 2026-10-25
- Verification Status: VERIFIED
- Version Label: alpha18_validation_v1

## Validation Report

- **Source**: `P2-ALPHA18-20261025`
- **Overall Confidence**: CAUTION

The numerical outputs were reproduced exactly in a second execution. The
caution level reflects the small treatment-level sample size and the inclusion
of an unassigned group in the sensitivity set, not an execution failure.

### Statistical Findings

| Metric | Test | Primary 15 | Sensitivity 18 | Effect size | Confidence |
| --- | --- | ---: | ---: | --- | --- |
| 16S OTU Observed | Welch one-way | P=0.238 | P=0.278 | eta²=0.599→0.544 | SOLID for stable null |
| 16S ASV Observed | Welch one-way | P=0.00176 | P=0.00157 | eta²=0.727→0.639 | SOLID for stable support |
| 16S ASV Shannon | Welch one-way | P=0.142 | P=0.171 | eta²=0.707→0.666 | SOLID for stable null |
| 16S ASV Simpson | Welch one-way | P=0.486 | P=0.449 | eta²=0.489→0.461 | SOLID for stable null |
| ITS ASV Simpson | Welch one-way | P=0.899 | P=0.0436 | eta²=0.0872→0.1571 | CAUTION: changed with Unassigned group |

Eleven of 12 pipeline-metric significance decisions remained unchanged. The
exception was current-ASV ITS Simpson. The Unassigned group had the highest
mean Simpson value (0.9735), so this result is a sensitivity to an unlabelled
sample group and is not a treatment contrast.

### Warnings

| Type | Detail | Affected |
| --- | --- | --- |
| Small group size | Three records per group | All alpha tests |
| Unassigned group | Raw group 23 has no treatment identity | 18-sample set |
| Multiplicity | The sensitivity grid contains 12 tests and is not used to select a significant endpoint | All alpha tests |

### Fallacy Scan

- **Coverage**: 11/11 fallacy types checked

| Fallacy | Severity | Detail | Recommendation |
| --- | --- | --- | --- |
| Simpson's paradox | NOTE | No reversal is inferred from aggregated and subgroup directions | Keep group-level reporting |
| Ecological fallacy | NOTE | Plot records are group observations, not plant-level measurements | Restrict conclusions to plot-level communities |
| Berkson's paradox | NOTE | No outcome-dependent selection filter identified | None |
| Collider bias | NOTE | No covariate model or collider adjustment used | None |
| Base-rate neglect | NOTE | No diagnostic sensitivity/specificity claim | None |
| Regression to the mean | NOTE | No repeated measure or extreme-group selection | None |
| Survivorship bias | NOTE | No attrition or survival-based inclusion | None |
| Look-elsewhere effect | CAUTION | 12 pipeline-metric tests form a sensitivity grid | Do not select one endpoint as a confirmatory finding |
| Garden of forking paths | CAUTION | Multiple defensible pipelines are explicitly reported | Interpret as a sensitivity analysis, not a confirmation test |
| Correlation ≠ causation | NOTE | No causal treatment language used | Retain association language |
| Reverse causality | NOTE | No directional causal claim made | None |

### Reproducibility

- **Method**: deterministic re-run of the same Python script
- **Verdict**: REPRODUCIBLE
- **Numeric outputs**: 3 CSV files plus the parameter file matched SHA256 exactly
  across the repeated execution.

| Output | Status |
| --- | --- |
| `alpha_omnibus_15_vs_18.csv` | MATCH |
| `alpha_group_means_15_and_18.csv` | MATCH |
| `alpha_primary_vs_sensitivity.csv` | MATCH |
| `analysis_parameters.csv` | MATCH |
