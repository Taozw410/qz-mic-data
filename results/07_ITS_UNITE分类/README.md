# ITS UNITE 分类与复核

## 参考库

- 数据库：UNITE v10.0，2025-02-19
- 数据集：General FASTA release for Fungi，动态物种假设
- DOI：`10.15156/BIO/3301229`
- 安装目录：
  `D:\bioenv\envs\riz16s\share\unite\v10.0_2025-02-19`
- 主参考文件：
  `sh_general_release_dynamic_19.02.2025.fasta`
- 参考文件SHA256：
  `1BB35A664B20EF03484FE74E857929CCD537D9D51C9EEF0305B99A1486E7386E`

压缩包为官方原始文件，大小29,158,924字节；下载后压缩包SHA256为
`A340864F947C517B671F1054A261E613A6619EF88DD8000DE1699F5E1F21413B`。

## 分类与复核

- 输入：2,481条ITS ASV代表序列。
- 方法：`dada2::assignTaxonomy`
- `minBoot=50`
- `tryRC=TRUE`
- 8线程
- DADA2 1.38.0，R 4.5.3
- 随机种子：20261023

在相同参考库、输入和参数下独立运行两次。两次只有19/2,481个ASV的不同末端
分类（0.766%），说明少数ASV位于分类边界：

| 分类级 | 两次结果不同的ASV数 |
| --- | ---: |
| Kingdom | 0 |
| Phylum | 9 |
| Class | 1 |
| Order | 1 |
| Family | 2 |
| Genus | 5 |
| Species | 6 |

最终`taxonomy_unite.csv`采用保守的两轮一致分类：两次结果一致的分类级才保留，
不一致的层级置为`NA`。原始Run1、Run2和19条差异均保留，便于追溯。

## 保守注释结果

| 分类级 | 已注释ASV数 |
| --- | ---: |
| Kingdom | 2,481 |
| Phylum | 2,127 |
| Class | 1,663 |
| Order | 1,573 |
| Family | 1,392 |
| Genus | 1,265 |
| Species | 687 |

2,481条ASV全部注释到Fungi域，ASV编号与
`01_数据/ASV_ITS/asv_table.csv`逐行一致。

## 样品组成

- 15个主分析样品中共检测到147–283个已分类属/样品。
- 五组的优势门均为Ascomycota：As 41.7%、AFP 63.4%、AEFP 51.3%、
  BP 58.7%、Natural 44.7%。
- 各组平均相对丰度最高的已分类属：
  As为`Linnemannia`（11.8%），AFP为`Linnemannia`（11.3%），
  AEFP为`Tausonia`（16.0%），BP为`Plectosphaerella`（12.8%），
  Natural为`Hygrocybe`（25.2%）。
- 这些是未抽平计数的样品内相对丰度描述，不是绝对丰度，也未进行属水平显著性检验。

## 使用边界

- 论文主分析优先使用Phylum至Genus；Species仅在明确标记为UNITE物种假设时使用。
- `minBoot=50`是DADA2默认下限，不等于物种鉴定正确率。
- 本次只完成分类，不表示已完成ITS差异丰度、功能预测或生态解释。
- 后续ITS差异丰度应继续使用未抽平计数，并在属水平声明10%–25%流行率阈值。

## 文件

- `01_数据/ASV_ITS/taxonomy_unite.csv`：ASV分类表。
- `taxonomy_unite_run1.csv`、`taxonomy_unite_run2.csv`：两次独立分类原始结果。
- `taxonomy_unite_consensus.csv`：两次一致才保留的最终分类。
- `taxonomy_run_differences.csv`：19条边界ASV的逐级差异。
- `taxonomy_rank_counts.csv`：两轮及保守分类的各级注释数。
- `its_group_phylum_top10.csv`、`its_group_genus_top10_classified.csv`：组水平主要谱系。
- `its_*_relative_abundance_by_sample.csv`：18个样品的门/属相对丰度。
- `COMPLETE_rerun.txt`：第二次运行完成标记。
