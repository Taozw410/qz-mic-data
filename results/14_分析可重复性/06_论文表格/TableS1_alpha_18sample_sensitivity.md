# Table S1. Alpha-diversity group tests with 15 and 18 samples.

| Domain | Pipeline | Metric | Primary P (15) | Primary η² | df1 primary | df2 primary | Sensitivity P (18) | Sensitivity η² | df1 sensitivity | df2 sensitivity | Delta P (18-15) | Same P<0.05 decision |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 16S | OriginalOTU | Observed | 0.238 | 0.599 | 4 | 4.74 | 0.278 | 0.544 | 5 | 5.37 | +0.040 | True |
| 16S | OriginalOTU | Shannon | 0.516 | 0.305 | 4 | 4.68 | 0.328 | 0.307 | 5 | 5.34 | -0.187 | True |
| 16S | OriginalOTU | Simpson | 0.348 | 0.343 | 4 | 4.54 | 0.191 | 0.342 | 5 | 5.28 | -0.157 | True |
| 16S | CurrentASV | Observed | 0.002 | 0.727 | 4 | 4.45 | 0.002 | 0.639 | 5 | 5.08 | -0.000 | True |
| 16S | CurrentASV | Shannon | 0.142 | 0.707 | 4 | 4.77 | 0.171 | 0.666 | 5 | 5.41 | +0.029 | True |
| 16S | CurrentASV | Simpson | 0.486 | 0.489 | 4 | 4.85 | 0.449 | 0.461 | 5 | 5.44 | -0.038 | True |
| ITS | OriginalOTU | Observed | 0.205 | 0.523 | 4 | 4.91 | 0.161 | 0.563 | 5 | 5.51 | -0.044 | True |
| ITS | OriginalOTU | Shannon | 0.815 | 0.152 | 4 | 4.70 | 0.622 | 0.195 | 5 | 5.44 | -0.193 | True |
| ITS | OriginalOTU | Simpson | 0.940 | 0.139 | 4 | 4.69 | 0.336 | 0.194 | 5 | 4.82 | -0.604 | True |
| ITS | CurrentASV | Observed | 0.152 | 0.347 | 4 | 4.45 | 0.195 | 0.329 | 5 | 5.11 | +0.043 | True |
| ITS | CurrentASV | Shannon | 0.800 | 0.124 | 4 | 4.35 | 0.686 | 0.172 | 5 | 5.19 | -0.114 | True |
| ITS | CurrentASV | Simpson | 0.899 | 0.087 | 4 | 4.04 | 0.044 | 0.157 | 5 | 5.15 | -0.855 | False |

Note: Primary comparisons contain five groups with three samples each; sensitivity comparisons contain the same groups plus the three-record unmapped group code 23. df1 is the Welch numerator df and df2 is the Welch-Satterthwaite denominator df. Eta-squared is classical SS_between/SS_total and is descriptive. The final column compares only whether P crossed 0.05; it is not a full repeatability test or evidence that two groups are equivalent.
