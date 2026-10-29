# 分析可重复性研究：首轮结果

日期：2026-10-25

## 结论先行

本轮把论文2从“再描述一次微生物群落”改为“同一批数据在不同分析流程下结论是否
稳定”的可重复性研究。首轮结果显示：

1. **门水平组成本身高度可重建**。当前ASV重新聚合后的16S门组成与原文门水平
   计数表几乎一致；ITS大部分一致，但少数样品受旧版“unclassified Fungi”重新
   分类影响。
2. **“处理改变群落组成”是否显著，取决于分类分辨率和距离尺度**。ASV水平下
   16S、ITS均强支持；门水平Bray-Curtis不支持，门水平Aitchison则支持或处于
   边界。
3. **Shannon/Simpson无显著差异较稳定，Observed丰富度不稳定**。16S Observed
   从原OTU流程的P=0.238变为当前ASV流程的P=0.00176，而两个流程的Shannon、
   Simpson均不显著。
4. **ITS中AEFP到天然参照距离最小是稳定方向，但未被统计确认**。原门水平、
   当前ASV门水平和当前ASV水平三种分析均显示AEFP最小；16S不支持。精确处理
   标签置换的总体P仍不显著。
5. **原论文的类群清单不能稳定重建**。ALDEx2在所有门水平比较中均无命中；
   ANCOM-BC2的候选随旧/当前分类体系和对比组改变，且没有双工具共识。
6. **LEfSe、网络互作、绝对丰度和土壤因果路径无法精确重复验证**，原因是输入、
   代码、参数或独立数据缺失。不能把“无法验证”写成“原结果被推翻”。
7. **16S参考库已精确核验为SILVA 138.1 SSURef NR99**，本地重建为DADA2训练集，
   按338F/806R区域截取；源库447,690条、区域库346,744条，文件哈希和构建日志
   见`../../05_稿件/13_SILVA_reference_audit.md`。

完整文献核验见`../../05_稿件/15_reference_verification_report.md`：当前22条
参考文献中17条完全一致，5条仅有在线年/卷年或页码缺失提示；正文引用与BibTeX
DOI集合完全一致。

四阶段可复用框架与执行代码见`../../07_可复用框架/`。当前QZ示例可从14条claim、
6条重建记录和跨流程端点表直接生成`claim_stability_matrix.csv`。

独立公共数据案例使用`GlobalPatterns`（26样品、19,216 OTU、9类样本）。OTU、
属、门三个层级及全样本/去Mock样品集的5个α和整体组成claim均为strong；
Mock—环境分离claim因门水平不显著被降级为not supported。该案例仅验证框架
可移植性，不构成QZ田间结论的外部复制。

首轮汇总图：

![Pipeline sensitivity](</D:/CodexWork/QZ-mic/论文2-微生物/04_图表/14_分析可重复性/pipeline_endpoint_sensitivity.png>)

图注：A为不同分类分辨率和距离尺度下的β组成PERMANOVA R²与P值；
B为原OTU与当前ASV的α多样性组间检验；C为样品水平的门组成重建差异；
D、E分别为ITS和16S天然参照距离及bootstrap区间；F为门水平ALDEx2与
ANCOM-BC2候选总数。星号表示P<0.05，具体数值见对应CSV。

## 分析口径

- 主分析：5组15个小区层测序记录，每组3个。
- 敏感性分析：加入未分配原始组23，共18个样品。
- 原始样品映射：T1←raw1、T6←raw20、T7←raw7、T22←raw22、
  T23←raw24。
- 比较对象：
  - `original_phylum`：原文门水平计数表；
  - `current_asv_phylum`：当前ASV重新聚合到门；
  - `current_asv_level`：已有当前ASV水平主分析。
- α比较只比较样本排序、方向和组间检验，不比较不同分辨率的绝对数值。
- 原表Simpson是dominance型数值，比较时转换为`1-Simpson`。
- 随机种子：20261023。
- PERMANOVA/PERMDISP：9,999次置换。
- 天然参照bootstrap：20,000次分层重采样。
- 精确标签置换：12个人工处理样品全部枚举，共369,600种。

完整口径见：
`../../口径裁决_2026-10-25_可重复性.md`。

## 1. 样品和分类重建

18个样品在两个域、旧表和当前表中均可一一对应。原始组23仍不赋处理含义。

| 域 | 共同门数 | 共同门Bray均值 | 共同门Bray最大 | 全门集Bray均值 | 全门集Bray最大 | 样品内Spearman均值 |
| --- | ---: | ---: | ---: | ---: | ---: | ---: |
| 16S | 22 | 0.027 | 0.035 | 0.059 | 0.080 | 0.971 |
| ITS | 8 | 0.052 | 0.307 | 0.088 | 0.364 | 0.889 |

16S门组成高度一致，说明DADA2 ASV和原OTU流程在“属门汇总”这一层可以互相
重建。

ITS整体也较高，但存在一个明显的分类敏感样品：`1_2`（As）。该样品旧分类中
35.8%为`unclassified Fungi`，当前UNITE结果中只有1.4%未分类，主要是由于
ASV被进一步分配。受此影响，As组Basidiomycota均值从旧表13.06%变为当前
25.05%。这是**分类库/分类深度导致的门均值变化**，不能解释为处理效应改变。

### 文件

- `01_基础矩阵/sample_mapping_audit.csv`
- `01_基础矩阵/sample_level_old_vs_current_concordance.csv`
- `01_基础矩阵/phylum_cross_sample_correlations.csv`
- `01_基础矩阵/group_phylum_mean_comparison.csv`
- `01_基础矩阵/phylum_crosswalk.csv`

## 2. α多样性：最明显的流程依赖

### 样本排序一致性

| 域 | 指标 | Spearman（原OTU vs 当前ASV） |
| --- | --- | ---: |
| 16S | Observed | 0.634 |
| 16S | Shannon | 0.589 |
| 16S | Simpson | 0.889 |
| ITS | Observed | 0.659 |
| ITS | Shannon | 0.975 |
| ITS | Simpson | 0.971 |

### 5组主分析的Welch检验

| 域 | 指标 | 原OTU P | 当前ASV P | 判断 |
| --- | --- | ---: | ---: | --- |
| 16S | Observed | 0.238 | 0.00176 | 流程敏感 |
| 16S | Shannon | 0.516 | 0.142 | 都无证据 |
| 16S | Simpson | 0.348 | 0.486 | 都无证据 |
| ITS | Observed | 0.205 | 0.152 | 都无证据 |
| ITS | Shannon | 0.815 | 0.800 | 都无证据 |
| ITS | Simpson | 0.940 | 0.899 | 都无证据 |

因此原论文“Shannon/Simpson总体无显著差异”是稳定的；但把“丰富度”也写成
无处理效应并不稳定。16S Observed在ASV流程中显著，主要由不同ASV分辨率带来。

18样品敏感性中，12个“流程×指标”的显著性判断有11个保持不变。唯一变化是
当前ASV的ITS Simpson：15样品P=0.899，加入Unassigned组后P=0.0436。由于
Unassigned组的Simpson均值最高（0.974）且无处理身份，这一变化只能说明对
未分配组的敏感性，不能解释为处理效应。

`文件：02_多样性与参照/alpha_pipeline_concordance.csv`、
`alpha_group_tests.csv`、`alpha_group_means.csv`；
18样品结果见`07_18样品alpha敏感性/`，补充图见
`../../04_图表/14_分析可重复性/alpha_18sample_sensitivity.png`。

## 3. β组成：ASV支持强，门水平Bray消失

### 5组主分析

| 域 | 流程 | 距离 | R² | P |
| --- | --- | --- | ---: | ---: |
| 16S | 原门水平 | Bray-Curtis | 0.256 | 0.588 |
| 16S | 当前ASV门水平 | Bray-Curtis | 0.256 | 0.582 |
| 16S | 当前ASV水平 | Bray-Curtis | 0.415 | 0.0002 |
| 16S | 原门水平 | Aitchison | 0.369 | 0.050 |
| 16S | 当前ASV门水平 | Aitchison | 0.412 | 0.0038 |
| 16S | 当前ASV水平 | Aitchison | 0.361 | <0.001 |
| ITS | 原门水平 | Bray-Curtis | 0.370 | 0.132 |
| ITS | 当前ASV门水平 | Bray-Curtis | 0.391 | 0.128 |
| ITS | 当前ASV水平 | Bray-Curtis | 0.469 | 0.0002 |
| ITS | 原门水平 | Aitchison | 0.537 | <0.001 |
| ITS | 当前ASV门水平 | Aitchison | 0.517 | 0.0018 |
| ITS | 当前ASV水平 | Aitchison | 0.444 | <0.001 |

这里出现明确的“分析选择依赖”：

- **分辨率**：ASV水平强支持组成差异；门水平Bray-Curtis不支持。
- **距离尺度**：到门水平后，Aitchison仍能检测组成差异，Bray-Curtis不能。
- 原因是门水平聚合抹去了大量低分类层级组成变化，并改变零值和相对差异结构。

### 18样品敏感性

加入未分配组23后：

- ITS门水平Bray从P=0.132变为0.035（旧表）；
- 当前ASV门水平Bray从P=0.128变为0.039；
- 16S门水平Aitchison从不稳定边界变为显著。

说明“组23是否纳入”会改变门水平的边缘结论，但不会改变主分析中ASV水平的
强分离。

`文件：02_多样性与参照/beta_pipeline_sensitivity.csv`。

原论文报告PERMANOVA为：

- 16S R²=0.507，P=0.011；
- ITS R²=0.492，P=0.001。

原文只保存一则汇总，无法确认其输入矩阵和精确模型，因此只作结果对照，不作为
精确复现目标。

## 4. 天然参照排序

### 观察值

| 域 | 原门水平 | 当前ASV门水平 | 当前ASV水平 |
| --- | --- | --- | --- |
| 16S | As最接近；AEFP第二 | As最接近；AEFP第二 | BP最接近；AEFP第三 |
| ITS | AEFP最接近 | AEFP最接近 | AEFP最接近 |

### 不确定性

- 原门水平ITS：AEFP排名第一概率0.909；总体精确置换P=0.104。
- 当前ASV门水平ITS：AEFP排名第一概率0.680；总体精确置换P=0.176。
- 当前ASV水平ITS：AEFP排名第一概率0.643；总体精确置换P=0.871。
- 16S三种分析中AEFP均不是最接近天然参照；原门水平和当前门水平均排第二，
  当前ASV水平排第三。

逐一剔除：

- 原门水平ITS：15/15次AEFP仍为第一；
- 当前ASV门水平ITS：12/15次第一；
- 当前ASV水平ITS：14/15次第一。

结论应写成：

> ITS中AEFP较接近天然参照的方向在不同流程间可重复，但处理排序未获精确置换
> 支持，且对分辨率和单个记录敏感；16S没有AEFP优势。

`文件：02_多样性与参照/natural_reference_*.csv`。

## 5. 差异丰度

门水平统一使用ALDEx2 Welch和ANCOM-BC2：

- ALDEx2在16S、ITS、旧表和当前表的全部对比中均无命中。
- ANCOM-BC2仅有以下单工具候选：

| 流程 | 域 | 对比 | 类群 | q |
| --- | --- | --- | --- | ---: |
| 原门水平 | ITS | AEFP vs Natural | Cercozoa | 0.0105 |
| 原门水平 | ITS | AEFP vs Natural | Rozellomycota | 0.0105 |
| 原门水平 | ITS | BP vs Natural | Rozellomycota | 0.00306 |
| 当前ASV门水平 | ITS | As vs Natural | Rozellomycota | 0.0245 |

这些候选没有双工具共识，而且同一Rozellomycota在不同流程进入不同对比组。
原论文LEfSe输入和完整输出缺失，不能做LEfSe的精确重跑；因此只能判断：
**原论文类群清单对分类体系、分类层级和单工具阈值敏感，当前没有稳定的门水平
替代清单。**

`文件：03_差异丰度/`。

## 6. 不能精确验证的内容

- 原OTU×样品计数矩阵缺失，无法精确重跑原OTU97和LEfSe。
- 原分析代码、软件版本、随机种子和完整参数缺失。
- 原网络节点选择、相关显著性、模块参数和完整输入缺失；当前样本/节点比为
  0.06，不可作生态互作推断。
- 无qPCR Cq或拷贝数，不能比较绝对微生物量。
- 土壤指标为处理级且与空间/历史混杂，不能检验因果驱动。

## 7. 首轮论文主线

推荐把论文2定位为：

> 同一高寒混播试验的微生物结论有多稳健？——分类分辨率、距离尺度、样品集合
> 与差异丰度方法对群落结论的影响

可稳定主张：

1. 门水平组成在旧OTU表和当前ASV之间总体上高度可重建。
2. Shannon/Simpson无差异是稳定的，16S Observed丰富度结论不稳定。
3. “处理改变组成”在ASV水平很强，但门水平Bray-Curtis不能重现。
4. ITS中AEFP更接近天然参照是稳定方向，不是已确认的处理排序。
5. 原论文的类群清单和网络结论不能算作已复现结果。

## 8. 唯一结果入口

- 基础矩阵：`01_基础矩阵/`
- 多样性与参照：`02_多样性与参照/`
- 差异丰度：`03_差异丰度/`
- 结论稳定性表：`04_结论汇总/claim_stability_matrix.csv`
- 全端点比较：`04_结论汇总/pipeline_endpoint_matrix.csv`
- 材料完整性：`05_材料完整性/materials_inventory.csv`

## 多数据集扩展

四个独立公共微生物组数据集的框架验证、multiverse/敏感性规则比较、标签置换
阴性对照和端点条件汇总见：
`../15_多数据集框架验证/README.md`。

