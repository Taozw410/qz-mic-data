# 天然参照距离与稳健性分析

## 重采样单位

主分析共有5组、每组3个小区层测序记录，共15个记录。每个`Sample`在
`01_数据/sample_sheet.csv`中有唯一的`PlotRecordID`。bootstrap、精确标签置换
和逐一剔除均以小区层记录为单位；OTU、ASV和序列数没有被当作重复。

唯一主表表明小区层映射已确认，但田间真实随机排列ID和区组仍待核对，因此本
分析没有加入区组项或区组配对检验。

## 方法

- 天然参照：3个Natural小区记录的相对丰度质心。
- 样品距离：样品相对丰度与天然质心的Bray-Curtis距离。
- Bootstrap：20,000次；在每个处理内对3个小区记录有放回抽样，同时独立重抽
  3个Natural记录并重算天然质心。
- 精确标签置换：对12个人工处理小区记录枚举所有4组×3记录的分组方式，
  共369,600种；检验总体组间范围和AEFP两两差异。两两P值采用Holm校正。
- 逐一剔除：每次删除15个主分析记录之一，重算天然参照排序、α多样性、
  Bray-Curtis和Aitchison PERMANOVA。PERMANOVA敏感性重复999次。
- 随机种子：20261023。

## 主要结果

| 域 | AEFP观测距离 | 95% bootstrap区间 | bootstrap排第一概率 | 精确总体P | 逐一剔除仍排第一 |
| --- | ---: | ---: | ---: | ---: | ---: |
| 16S | 0.5145 | 0.4881–0.6281 | 0.225 | 0.444 | 1/15 |
| ITS | 0.6146 | 0.5296–0.7385 | 0.643 | 0.871 | 14/15 |

ITS 中 AEFP 与 As、AFP、BP 的 bootstrap 差值区间均跨0，三个两两精确置换的
Holm校正P均为1.000。完全删除 AFP 的 `20_3` 后，AFP降至0.593、AEFP仍为
0.615，AEFP从第一降为第二。

因此：

- 可以写：ITS中AEFP的平均天然参照距离在四个人工处理中数值最小。
- 不能写：AEFP已被统计确认最接近天然草地，或AEFP实现了向天然群落的趋同。
- 16S没有AEFP优势，精确总体P=0.444。

## 文件

- `bootstrap_group_distance.csv`：各组观测距离、bootstrap区间和排名概率。
- `bootstrap_pairwise_difference.csv`：AEFP与其它人工处理的差值分布。
- `exact_label_permutation.csv`：369,600种精确标签重组的总体与两两检验。
- `leave_one_out_influence.csv`：15次逐一剔除的完整结果。
- `leave_one_out_summary.csv`：排序、α和β方向稳定性的汇总。
- `analysis_parameters.csv`：种子、迭代数和重采样单位。
