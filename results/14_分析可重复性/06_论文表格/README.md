# Manuscript tables

## Table 1

`Table1_data_and_analysis_levels.md` / `.csv`

Describes the original and current data layers, sample sizes, feature counts,
the question each comparison can answer, and its main limitation.

## Table 2

`Table2_endpoint_sensitivity.md` / `.csv`

Reports the principal alpha, beta, natural-reference, and differential-abundance
endpoints under the available analysis pipelines. P values below 0.001 are
shown as `<0.001`; exact values are retained in the source CSV files.

## Table 3

`Table3_claim_stability.md` / `.csv`

Classifies each original claim by directional stability, inferential stability,
current judgement, and evidence grade. `cannot verify` means the required input,
code, parameter set, or independent measurement is unavailable; it is not a
negative finding.

## Table S1

`TableS1_alpha_18sample_sensitivity.md` / `.csv`

Compares Welch one-way tests for all alpha-diversity endpoints in the
15-sample primary set and the 18-sample sensitivity set. Group 23 is retained as
`Unassigned`; the table reports P values, eta squared, and whether the
significance decision changed.

## Table S2

`TableS2_globalpatterns_claim_stability.md` / `.csv`

External application of the framework to the public `GlobalPatterns` dataset.
It reports claim type, reconstruction status, analysis dependency, inference
stability and evidence grade. The external case tests framework portability and
is not a replication of the QZ ecological results.

## Source files

- `../02_多样性与参照/`
- `../03_差异丰度/`
- `../04_结论汇总/claim_stability_matrix.csv`
- `../07_18样品alpha敏感性/`
- `../../07_可复用框架/claimstab/examples/globalpatterns/output/`

## Generation

Run:

```text
python ../../02_脚本/28_build_manuscript_tables.py
```

The generator reads the frozen result files rather than retyping outcome values.
