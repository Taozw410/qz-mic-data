# 多数据集框架验证

日期：2026-10-29

## 结论先行

本轮把 `claimstab` 从单一 QZ 草地案例推进为四个公共微生物组数据集的
基准分析，并加入了多数规则、严格规则和标签置换阴性对照。结果支持三项结论：

1. 四成分框架能够明确识别“多数规格显著，但不是端点全域稳定”的过度自信：
   公共数据中共有 5 个 claim 被多数规则判为 supported，但 `claimstab`
   不判为 supported。
2. 标签置换阴性对照中，400 个 claim 评估是标签置换零假设下的嵌套评估，
   不是 400 个独立试验。在匹配的 999 次 PERMANOVA 内部置换下，多数规则、
   `claimstab` 和严格规则均为 0/400 个支持判定。因此本基准没有证明
   `claimstab` 的二元判定优于“全部规格均显著”的严格规则。
3. 框架的可验证增量主要是可审计的规格依赖诊断、重建门禁、stable-null 区分和
   条件化证据等级；不是新的统计功效或必然高于严格规则的分辨能力。

因此，不能写成“claimstab 比现有 multiverse 方法更准确”。可以写成：

> 在同一决策边界下，claimstab 将“为什么一个多数显著的结果仍不能升级为
> 稳定结论”展开为重建、依赖、稳定性和证据等级四个可复核层次；相对严格规则
> 它不是更高的二元准确率，而是更完整的审计信息。

## 公共数据集

| 数据集 | 来源研究 | 平台 | 有效样本 | 主要对比 |
| --- | --- | --- | ---: | --- |
| GlobalPatterns | Caporaso et al. 2011, PNAS | Illumina 16S | 26 | sample type；mock vs environment |
| enterotype | Arumugam et al. 2011, Nature | mixed sequencing genus profiles | 280 | sequencing technology |
| soilrep | Zhou et al. 2011, ISME Journal | 454 16S | 24 | warmed；clipped |
| atlas1006 | Lahti et al. 2014, Nature Communications | HITChip | 1006 | BMI；sex，仅 time 0 |

四个数据集来自不同研究、样本体系和平台。它们不是 QZ 田间结论的外部复制，
而是 `claimstab` 的方法学可移植性和判别行为测试。

## 有效样本修正

`soilrep` 原始表有 56 条测序记录，但只有 24 个独立土壤微宇宙；每个微宇宙
包含 2–3 个技术重复。最终分析先按 `Sample` 汇总技术重复，再做 α/β 分析，
避免将 56 条记录当作 56 个独立重复。

ATLAS 原始表含多个时间点。本轮只使用 `time == 0` 的 1006 个受试者，
避免把同一受试者的重复测量当作独立样本。

## 端点空间

- 公共主分析：32 个 claim，176 个可测试或不可测试端点；
- α 多样性：Observed、Shannon、Simpson；
- β 组成：Bray-Curtis、Aitchison；
- 比较 OTU、属、科、门、过滤规则、稀释深度和样本子集；
- 主分析 PERMANOVA：999 次置换；
- 标签置换：每个数据集 20 次标签置换，共 400 个零效应 claim；
- 阴性对照 PERMANOVA：999 次置换；
- 固定随机种子：20261027。

## 三种决策规则

| 规则 | supported 判定 |
| --- | --- |
| majority | 超过一半的可测试规格显著 |
| strict | 全部可测试规格显著 |
| claimstab | 重建门禁后的证据等级为 strong 或 moderate |

该比较是规则层面的正式基准，不是对某个具体 R/Python multiverse 软件包实现
的逐行复刻。它检验的是现有流程最常用的两个简化判定原则。

## 主要结果

### 观测标签

| 数据集 | claims | majority supported | claimstab supported | majority-only |
| --- | ---: | ---: | ---: | ---: |
| GlobalPatterns | 7 | 7 | 5 | 2 |
| enterotype | 5 | 5 | 4 | 1 |
| soilrep | 10 | 0 | 0 | 0 |
| atlas1006 | 10 | 5 | 3 | 2 |
| 合计 | 32 | 17 | 12 | 5 |

5 个 majority-only claim 为：

- GlobalPatterns：mock vs environment，Bray-Curtis；
- GlobalPatterns：mock vs environment，Aitchison；
- enterotype：sequencing technology，Simpson；
- atlas1006：BMI，Observed richness；
- atlas1006：BMI，Shannon。

这些 claim 的共同特征是部分规格显著、部分规格不显著，或最高 P 值位于
0.05–0.27，不能仅凭多数投票升级为端点全域稳定。

### 阴性对照

| 数据集 | 标签置换 claim 评估 | majority 支持判定 | strict 支持判定 | claimstab 支持判定 |
| --- | ---: | ---: | ---: | ---: |
| GlobalPatterns | 100 | 0/100 | 0/100 | 0/100 |
| enterotype | 100 | 0/100 | 0/100 | 0/100 |
| soilrep | 100 | 0/100 | 0/100 | 0/100 |
| atlas1006 | 100 | 0/100 | 0/100 | 0/100 |

阴性对照说明三种规则都没有在标签置换零假设下给出支持；但 400 个评估来自
80 个“数据集—置换”组合，且共享标签和距离矩阵。不能把 0/400 解释成独立
伯努利试验中的零假阳性概率。

## 端点类型与条件规律

在 32 个公共数据 claim 中观察到以下经验规律：

1. **最差端点信号是强条件。** 最高 P 值 `<0.01` 的 11 个 claim 全部得到
   `claimstab` 支持；最高 P 值 `>0.05` 的 5 个 claim 全部未得到支持。
2. **效应保留率是第二条件。** 端点间最小/最大绝对效应比 `>=0.70` 的
   6 个 claim 全部得到支持；`<0.40` 的 20 个 claim 只有 4 个得到支持。
3. **不存在通用的 α 优于 β 或 Bray 优于 Aitchison。** α 支持率 6/18，
   β 支持率 6/14；Bray 与 Aitchison 均为 3/7。
4. **多数显著不等于稳定。** 最高 P 值进入 0.05–0.20 时，多数规则仍可能判为
   supported，但 `claimstab` 均不升级为支持。
5. **高维流程数量本身不是证据。** 增加分类层级或样本子集会暴露更多边界，
   但同时提高出现异质结果的机会，不能按流程数量直接加权。
6. **样本集合变化是压力测试而非重复。** 子集一致性只有在主效应足够强、
   聚合后效应保留较高时才有解释价值。

这些是当前四数据集、32 claim 基准中的经验条件，不是普适生态学定律。其价值
在于给出后续研究可直接检验的预注册条件，而不是替代真实外部复制。

## 重要限制

- `soilrep` 在本轮端点空间中没有重现原始研究所报告的 warm/clipped 对比；
  这必须表述为“在指定端点、聚合和距离空间下未获支持”，不能写成该处理
  没有生态效应，也不能写成原研究错误。
- GlobalPatterns、enterotype 和 ATLAS 的对比不是同一生态问题，不能合并成
  一个生态效应量。
- 标签置换只检验过度自信，不评价统计功效和阳性召回。
- `claimstab` 的二元支持边界与 strict 规则一致；本基准没有证明其在二元
  判定上优于 strict。
- 未对公共数据加入 qPCR、宏基因组、LEfSe、网络或因果模型，因此本轮验证
  只覆盖 α/β 端点与分类/样本/距离依赖。

## 唯一结果入口

- 方法、数据集和解释：
  `README.md`
- 主分析输入：`主分析/claims.csv`、`主分析/reconstruction.csv`、
  `主分析/endpoints.csv`
- claim 稳定性矩阵：`汇总/main_stability/claim_stability_matrix.csv`
- 规则比较：`汇总/main_comparison/framework_comparison.csv`
- 多数规则过度自信 claim：`汇总/framework_overconfident_claims.csv`
- 阴性对照：`汇总/permutation_support_summary.csv`
- 条件汇总：`汇总/condition_summary.csv`
- 端点与流程条件：`汇总/endpoint_condition_summary.csv`
- 自动报告：`汇总/benchmark_report.md`
- 2026-10-29 修订重跑与交付一致性：
  `复现状态_2026-10-29.md`
- 软件环境、随机种子与运行入口：`环境与运行说明.md`
- 主图：`../../04_图表/15_多数据集框架验证/multidataset_claim_stability.png`
- 图件来源、统计定义和 QA：
  `../../04_图表/15_多数据集框架验证/QA.md`

## 复现

原始数据来自已安装的 `phyloseq` 1.54.2 和 `microbiome` 1.30.0 包，
不包含再分发的大体量公共矩阵。运行环境为 R 4.5.3、vegan 2.7-6。

```powershell
conda run -p D:\bioenv\envs\riz16s Rscript 脚本\build_public_multiverse.R output
python 脚本\summarize_public_benchmark.py `
  --benchmark-root output `
  --claimstab-root ..\..\07_可复用框架\claimstab `
  --output-dir output\summary
```

第二次复现时，`build_public_multiverse.R` 已内置 24 个独立土壤微宇宙的聚合
逻辑；`rebuild_soil_corrected.R` 和 `merge_soil_corrected.py` 保留用于解释
本轮从技术重复口径修正到独立样本口径的审计链。
