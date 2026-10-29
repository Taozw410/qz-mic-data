# α/β多样性与天然参照的流程敏感性

## 比较对象

- `original_phylum`：原文门水平计数表；
- `current_asv_phylum`：当前ASV重新聚合到门；
- `current_asv_level`：当前ASV水平结果，用于和门水平比较分辨率效应。

原始OTU α与当前ASV α只比较样本排序、方向和组间显著性；由于特征分辨率不同，
不比较绝对Observed或Shannon值。

## α多样性

- 16S Observed从原OTU的P=0.238变为当前ASV的P=0.00176，结论不稳定。
- 16S Shannon和Simpson在两个流程中均不显著。
- ITS三种α指标在两个流程中均不显著。
- 样本排序相关性：
  - 16S Observed ρ=0.634，Shannon ρ=0.589；
  - ITS Shannon ρ=0.975，Simpson ρ=0.971。

文件：

- `alpha_sample_pipeline_comparison.csv`
- `alpha_pipeline_concordance.csv`
- `alpha_group_tests.csv`
- `alpha_group_means.csv`

## β组成

5组主分析：

- ASV水平：16S/ITS的Bray与Aitchison均P<0.001；
- 原门水平和当前ASV门水平：16S/ITS Bray-Curtis均不显著；
- 门水平Aitchison：16S原表P=0.050、当前表P=0.0038；
  ITS两张表均显著。

18样品敏感性：

- ITS门水平Bray从不显著变为P≈0.035–0.039；
- 16S门水平Aitchison变得更显著；
- ASV水平主结论不改变。

文件：

- `beta_pipeline_sensitivity.csv`

## 天然参照

- ITS中AEFP在原门水平、当前ASV门水平和当前ASV水平均为平均距离最小。
- 16S中原门水平和当前门水平均为As最小、AEFP第二；ASV水平为BP最小、AEFP第三。
- ITS精确总体置换：
  - 原门水平P=0.104；
  - 当前ASV门水平P=0.176；
  - 当前ASV水平P=0.871。
- 逐一剔除：
  - 原门水平ITS：15/15仍为第一；
  - 当前ASV门水平ITS：12/15；
  - 当前ASV水平ITS：14/15。

文件：

- `natural_reference_bootstrap.csv`
- `natural_reference_bootstrap_differences.csv`
- `natural_reference_exact_permutation.csv`
- `natural_reference_leave_one_out.csv`

## 参数

- 随机种子：20261023；
- PERMANOVA/PERMDISP：9,999次；
- bootstrap：20,000次；
- 精确人工处理标签重排：369,600次。

见`analysis_parameters.csv`。
