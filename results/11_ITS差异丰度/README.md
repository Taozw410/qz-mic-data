# ITS 属水平差异丰度

## 方法

- 使用15个主分析样品，每组3个小区层记录。
- 使用UNITE两轮一致的属级分类；未分类属不进入可解释的属水平检验。
- 使用未抽平整数计数。
- 属表保留至少在2/15个样品出现且总计数≥10的属；主分析共262个属。
- ALDEx2使用Welch t检验，`mc.samples=256`；命中要求
  `we.eBH < 0.05`且`|effect| > 1`。
- ANCOM-BC2使用Natural为参考、BH校正、10%流行率、结构零和伪计数敏感性；
  `diff_robust == TRUE`才作为稳健候选。
- 双工具交集定义为高置信结果。

## 主分析结果

| 对比 | ALDEx2 | ANCOM-BC2稳健 | 双工具共识 |
| --- | ---: | ---: | ---: |
| As vs Natural | 0 | 1 | 0 |
| AFP vs Natural | 0 | 1 | 0 |
| AEFP vs Natural | 0 | 2 | 0 |
| BP vs Natural | 0 | 4 | 0 |

ALDEx2没有任何属通过Welch BH与效应量联合门禁。ANCOM-BC2的8个单工具候选为：

- As vs Natural：`GS11_gen_Incertae_sedis`
- AFP vs Natural：`Rozellomycota_gen_Incertae_sedis`
- AEFP vs Natural：`Itersonilia`、`Vishniacozyma`
- BP vs Natural：`Ascobolus`、`Enterocarpus`、`GS11_gen_Incertae_sedis`、
  `Vishniacozyma`

因此目前没有可表述为“稳健差异属”的结果。

## 流行率敏感性

将属流行率门槛提高到4/15（26.7%）后：

- 保留200个属。
- ANCOM-BC2候选减少到5个，没有新增候选。
- 仍没有任何ALDEx2或双工具共识命中。
- `Itersonilia`、`Ascobolus`和BP中的`GS11_gen_Incertae_sedis`消失。

候选清单对流行率阈值和工具选择均敏感。

## 解释边界

- ANCOM-BC2明确警告每组n=3时方差估计不稳定。
- 单工具ANCOM-BC2结果只能作为探索性候选，不能写成已确认差异属。
- 结果描述相对丰度份额，不是绝对丰度或生物量。
- `gen_Incertae_sedis`是分类位置未定的属级谱系，不应赋予具体生态功能。

## 文件

- `genus_counts_primary.csv`：用于主分析的属计数。
- `ALDEx2_pairwise_vs_natural.csv`：四个处理与Natural的ALDEx2结果。
- `ANCOMBC2_pairwise.csv`：ANCOM-BC2结果及伪计数敏感性。
- `ALDEx2_ANCOMBC2_consensus_all.csv`：两工具逐属合并结果。
- `consensus_summary.csv`：各对比命中数。
- `prevalence25/`：25%流行率敏感性结果。
