# 16S 属水平差异丰度

## 方法

- 使用 15 个主分析样品。
- 将 16S ASV 按 SILVA Genus 汇总，未分类属合并为 `Unclassified`。
- 差异分析使用未抽平原始计数。
- ALDEx2：Welch t 检验，技术比较为每个人工处理与 Natural；显著标准为
  `we.eBH < 0.05` 且 `|effect| > 1`。`we.eBH`与`test="t"`匹配；旧版误用了
  Wilcoxon对应的`wi.eBH`，现已纠正。
- ANCOM-BC2：以 Natural 为参考，BH 校正，10% 流行率过滤，并开启伪计数敏感性分析。
- 高置信结果取两种工具的交集。

## 结果数量

| 对比 | ALDEx2 | ANCOM-BC2稳健 | 共识 |
|---|---:|---:|---:|
| As vs Natural | 0 | 1 | 0 |
| AFP vs Natural | 0 | 0 | 0 |
| AEFP vs Natural | 0 | 0 | 0 |
| BP vs Natural | 0 | 0 | 0 |

没有属通过两种工具的共识门禁。As vs Natural中的
`Allorhizobium-Neorhizobium-Pararhizobium-Rhizobium`仅由ANCOM-BC2支持
（log fold change=-1.760，q=0.0203）；其ALDEx2 Welch `we.eBH=0.791`，
因此只能列为单工具探索性候选。

## 解释边界

- ANCOM-BC2 检测到每组只有 3 个样品，明确提示方差估计不稳定。
- ANCOM-BC2的单独命中只能视为探索性候选。
- 16S目前没有属级高置信差异。
- 结果不能解释为微生物功能或因果作用。

