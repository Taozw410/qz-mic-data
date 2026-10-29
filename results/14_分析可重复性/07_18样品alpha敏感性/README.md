# 18-sample alpha-diversity sensitivity

## Definition

- Primary set: 15 plot-level records, five treatment groups with three records each.
- Sensitivity set: all 18 records. Raw sequencing group 23 remains `Unassigned`.
- Test: Welch one-way ANOVA for Observed, Shannon and Simpson.
- Effect size: classical eta squared, descriptive only.

## Result

11/12 pipeline-metric significance decisions remained unchanged
after adding the unassigned group.

The only change was current-ASV ITS Simpson:

- primary 15: P = 0.8987;
- sensitivity 18: P = 0.0436.

The Unassigned group had the highest mean Simpson value in the 18-sample set,
but it has no treatment identity. The change therefore demonstrates sensitivity
to including an unlabelled group and cannot be interpreted as a treatment effect.

## Comparison table

| Domain | Pipeline | Metric | P_primary15 | P_sensitivity18 | DeltaP_18_minus_15 | DF_num_primary15 | DF_den_primary15 | DF_num_sensitivity18 | DF_den_sensitivity18 | Significance_primary15 | Significance_sensitivity18 | Same_threshold_decision |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 16S | OriginalOTU | Observed | 0.2383 | 0.2781 | +0.03987 | 4 | 4.742119157597192 | 5 | 5.367898422110708 | False | False | True |
| 16S | OriginalOTU | Shannon | 0.5156 | 0.3284 | -0.1872 | 4 | 4.684180667630444 | 5 | 5.335275131064863 | False | False | True |
| 16S | OriginalOTU | Simpson | 0.3483 | 0.191 | -0.1573 | 4 | 4.54056744800355 | 5 | 5.276914130770092 | False | False | True |
| 16S | CurrentASV | Observed | 0.001764 | 0.00157 | -0.0001941 | 4 | 4.4451340997698265 | 5 | 5.080920997961484 | True | True | True |
| 16S | CurrentASV | Shannon | 0.1419 | 0.1707 | +0.0288 | 4 | 4.768230148571928 | 5 | 5.412773802218636 | False | False | True |
| 16S | CurrentASV | Simpson | 0.4863 | 0.4486 | -0.03763 | 4 | 4.853971872229943 | 5 | 5.442320334707628 | False | False | True |
| ITS | OriginalOTU | Observed | 0.2055 | 0.1613 | -0.04413 | 4 | 4.911469937596387 | 5 | 5.514320840820899 | False | False | True |
| ITS | OriginalOTU | Shannon | 0.815 | 0.6218 | -0.1932 | 4 | 4.700108600311363 | 5 | 5.440316401973494 | False | False | True |
| ITS | OriginalOTU | Simpson | 0.9397 | 0.3356 | -0.6041 | 4 | 4.690881913039164 | 5 | 4.820448437066563 | False | False | True |
| ITS | CurrentASV | Observed | 0.1522 | 0.1952 | +0.04298 | 4 | 4.453174917845128 | 5 | 5.108472847197384 | False | False | True |
| ITS | CurrentASV | Shannon | 0.8004 | 0.6862 | -0.1142 | 4 | 4.352032202926116 | 5 | 5.190763266968943 | False | False | True |
| ITS | CurrentASV | Simpson | 0.8987 | 0.04357 | -0.8551 | 4 | 4.044676937748476 | 5 | 5.145863816153352 | False | True | False |

## Files

- `alpha_omnibus_15_vs_18.csv`: F, P and eta squared for both sample sets.
- `alpha_group_means_15_and_18.csv`: group means, SD, SE and mean rank.
- `alpha_primary_vs_sensitivity.csv`: direct P-value comparison.
- `analysis_parameters.csv`: fixed analysis settings.
- `VALIDATION.md`: experiment-agent validation report and 11/11 fallacy scan.

## Supplementary figure

- `../../../04_图表/14_分析可重复性/alpha_18sample_sensitivity.png`
- Generator: `../../../02_脚本/33_alpha_18sample_figure.py`
