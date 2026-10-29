# 可重复性结论汇总

## `pipeline_endpoint_matrix.csv`

逐端点汇总：

- 分析类型（α、β、天然参照）；
- 域、分析流程、样品集合、指标和对比；
- 统计量、R²、P值；
- 初步证据分类。

流程标签：

- `original_otu`：原文α多样性表；
- `original_phylum`：原文门水平计数表；
- `current_asv_phylum`：当前ASV按门聚合；
- `current_asv_level`：当前ASV特征水平；
- `original_published_summary`：原文作者报告的PERMANOVA汇总。

## `claim_stability_matrix.csv`

逐项记录原论文主张能否在重分析中保持：

- `DirectionStable`：方向或排序是否保持；
- `InferenceStable`：显著性或确认性推断是否保持；
- `Verdict`：当前可接受的表述；
- `EvidenceGrade`：证据等级；
- `SourceFiles`：唯一来源文件。

关键原则：

- 方向稳定不等于统计确认；
- 同一批数据的ASV重分析不等于独立验证；
- 原结果不可精确重算时写“not verifiable”，不写成“false”。
