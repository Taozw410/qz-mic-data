# 门水平差异丰度流程敏感性

## 范围

- 5组15个小区层记录，每组3个。
- 两种数据层：
  - `original_phylum`：原文门水平计数表；
  - `current_asv_phylum`：当前ASV按SILVA/UNITE门名重新聚合。
- 四个对比：As、AFP、AEFP、BP分别对Natural。
- 流行率阈值：10%，即至少2个样品检出。
- 最小总计数：10。

## 方法

- ALDEx2：Welch t检验，256个Monte-Carlo实例；
  命中条件为`we.eBH < 0.05`且`|effect| > 1`。
- ANCOM-BC2：BH校正、结构零、负下界、伪计数敏感性；
  以`diff_robust == TRUE`作为稳健候选。
- 只有ALDEx2和ANCOM-BC2同时命中的门才记为“共识”。

## 结果

- ALDEx2在所有域、数据层和四个对比中均无命中。
- ANCOM-BC2共保留4个单工具候选：

| 数据层 | 域 | 对比 | 门 | q |
| --- | --- | --- | --- | ---: |
| 原门水平 | ITS | AEFP vs Natural | Cercozoa | 0.0105 |
| 原门水平 | ITS | AEFP vs Natural | Rozellomycota | 0.0105 |
| 原门水平 | ITS | BP vs Natural | Rozellomycota | 0.00306 |
| 当前ASV门水平 | ITS | As vs Natural | Rozellomycota | 0.0245 |

- 16S在两种数据层中均无ANCOM-BC2稳健候选。
- 两域、两数据层均无双工具共识。
- Rozellomycota在旧表中由AEFP/BP对比命中，在当前表中改为As对比，说明候选
  本身受分类重建和组间相对结构影响。

## 方差警告

ANCOM-BC2对四组人工处理和Natural均报告每组n=3、方差估计不稳定；同时用于
估计样品偏倚的门数仅11–31，低于稳定估计通常需要的50个以上。因此这些候选
只能用于比较“流程是否重现同一信号”，不能升级为稳健生物标志物。

## 文件

- `ALDEx2_phylum_pairwise.csv`
- `ANCOMBC2_phylum_pairwise.csv`
- `phylum_DA_candidates.csv`
- `phylum_DA_summary.csv`
- `analysis_parameters.csv`
