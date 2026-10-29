# 门水平初步结果文件说明（历史敏感性记录）

> 本目录仅用于追溯早期门水平筛查。论文2主分析已改为从原始 FASTQ 重建的
> ASV 数据；不得从本目录引用主结论。当前结果入口为
> `../00_ASV结果总表/README.md`。

- `alpha_group_summary_*.csv`：各处理 α多样性均值和标准误。
- `alpha_omnibus_*.csv`：α多样性和分类序列数的总体检验。
- `alpha_pairwise_*.csv`：处理两两比较和 BH 校正。
- `beta_omnibus_*.csv`：Bray-Curtis、Aitchison、PERMANOVA 和离散度。
- `beta_pairwise_*.csv`：处理两两 PERMANOVA 和 BH 校正。
- `natural_reference_distances_*.csv`：各处理到天然参照的距离。
- `domain_concordance_*.csv`：16S 与 ITS 距离矩阵的 Mantel 和 Procrustes 检验。
- 文件名中的 `primary` 为论文五组；`sensitivity` 额外纳入未分配的原始组23。

