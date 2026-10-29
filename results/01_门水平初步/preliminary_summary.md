# Paper 2 preliminary phylum-level results

## Scope

- Primary set: five paper groups, 15 samples.
- Sensitivity set: six sequence groups, 18 samples; raw group 23 is retained as unassigned.
- Features: phylum-level relative abundance and existing alpha-diversity output.
- PERMANOVA and dispersion tests use 9,999 permutations; pairwise tests use 999.
- Bray-Curtis is primary; Aitchison is a sensitivity analysis.

## Alpha omnibus

```text
Domain          Metric  GroupCount        F        P     Eta2
   16S ClassifiedReads           5 0.597020 0.673118 0.192772
   16S            Sobs           5 3.731387 0.041513 0.598805
   16S         Shannon           5 1.095289 0.410192 0.304646
   16S         Simpson           5 1.305465 0.332255 0.343050
   16S        Coverage           5 0.347638 0.839865 0.122079
   ITS ClassifiedReads           5 2.159511 0.147498 0.463463
   ITS            Sobs           5 2.737039 0.089569 0.522631
   ITS         Shannon           5 0.448110 0.771779 0.151999
   ITS         Simpson           5 0.405119 0.800988 0.139450
   ITS        Coverage           5 1.695222 0.226983 0.404084
```

## Beta

```text
Domain      Metric        F       R2      P  DispersionF  DispersionP    PCoA1    PCoA2
   16S Bray-Curtis 0.859321 0.255802 0.5712     1.122288       0.9442 0.514236 0.392699
   16S   Aitchison 1.257395 0.334645 0.1923          NaN          NaN      NaN      NaN
   ITS Bray-Curtis 1.467236 0.369838 0.1293     2.228593       0.7192 0.449323 0.298638
   ITS   Aitchison 2.878329 0.535172 0.0011          NaN          NaN      NaN      NaN
```

## Domain concordance

```text
 N  MantelSpearman  MantelP  ProcrustesDisparity  ProcrustesP
15       -0.009164   0.4678             0.885886       0.6653
```
