# Table 1. Operational definitions of the four framework components.

| Component | Question answered | Inputs and calculation | Operational output | Missing-data rule |
| --- | --- | --- | --- | --- |
| Data reconstruction | Can the alternative workflow recover the data layer or measurement required by the claim? | Source and reconstructed matrices; identifier correspondence; sample totals; distance or agreement metrics | Stable, partial, unstable, or not available, with the metric and threshold recorded | Missing source data yields not available; a partial data layer cannot support a strong grade |
| Dependence on analytical choices | Which data transformations or model choices change an endpoint? | The same endpoint across declared pipelines, taxonomic levels, sample sets, distances, and models | Stable or mixed direction; stable support, stable null, or mixed significance; stable or mixed rank; minimum and maximum effects | A planned specification that cannot run remains in the planned count and is reported as missing; it never counts as support |
| Inference stability | Does the substantive claim remain consistent after endpoint-level variation is considered? | Stage-2 endpoint summaries and claim type | Stable, conditional, unstable, or not verifiable | Directionally opposed results are unstable; no interpretable result yields not verifiable |
| Evidence grading | How should reconstruction and stability be combined into an auditable grade? | Reconstruction status, endpoint dependence, specification coverage, and any documented manual review | Strong, moderate, descriptive, not supported, or not verifiable | Strong requires complete proposed-specification coverage; any missing specification caps an otherwise strong claim at moderate |

Note: Significance is evaluated at the stated alpha threshold, but it is not the
only criterion. Direction is required for effect claims and rank for ranking
claims. Effect magnitudes are reported as ranges and used as empirical
diagnostics; they do not enter an arbitrary universal threshold. An analyst may
raise or lower a grade manually, but the automatic grade remains visible and a
reason is required. The status `cannot verify` is not evidence that a claim is
false.
