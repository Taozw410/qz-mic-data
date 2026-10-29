# 可重复性分析基础矩阵

本目录把原文派生表和当前ASV数据转换为同一样品顺序、同一门名的比较矩阵。

## 样品

- 18个测序样品全部保留。
- 主分析5组：T1/As、T6/AFP、T7/AEFP、T22/BP、T23/Natural。
- 原始组23标记为Unassigned，只进入18样品敏感性分析。
- 原始样品映射固定为T1←raw1、T6←raw20、T7←raw7、T22←raw22、
  T23←raw24。

## 门名统一

原文常见的旧门名已映射到当前SILVA命名，例如：

- Actinobacteria→Actinobacteriota；
- Acidobacteria→Acidobacteriota；
- Bacteroidetes→Bacteroidota；
- Gemmatimonadetes→Gemmatimonadota；
- Verrucomicrobia→Verrucomicrobiota。

逐项映射见`phylum_crosswalk.csv`。

## 文件

- `sample_mapping_audit.csv`：样品和处理映射；
- `original_phylum_counts_16S.csv`、`original_phylum_counts_ITS.csv`：
  原文门水平计数；
- `current_asv_phylum_counts_16S.csv`、`current_asv_phylum_counts_ITS.csv`：
  当前ASV按门聚合计数；
- `sample_level_old_vs_current_concordance.csv`：同一样品的旧/新门组成
  Bray与Spearman一致性；
- `phylum_cross_sample_correlations.csv`：各门在18个样品上的跨流程相关；
- `group_phylum_mean_comparison.csv`：五组和一个未分配组的门均值；
- `phylum_crosswalk.csv`：门名和是否共同存在；
- `original_alpha.csv`：原文α多样性表长表；
- `original_published_permanova.csv`：原文PERMANOVA汇总；
- `taxonomy_audit.csv`：当前分类注释数量。

## 解释边界

- 共同门比较会分别将两套数据限制在共同门集后重新归一化；
- 全门集比较保留仅出现在一个分类体系中的门和未分类类别；
- ITS的旧`unclassified Fungi`被当前UNITE进一步分类，因此部分样品差异来自
  分类深度，而不是生物学差异。
