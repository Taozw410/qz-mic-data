# Independent public-data case: GlobalPatterns

## Purpose

This case tests whether the four-stage claim-stability framework can run on an
independent public dataset. It is not an external replication of the QZ
grassland ecological conclusions.

## Data

- Dataset: `GlobalPatterns` distributed with `phyloseq`
- Citation: Caporaso et al. (2011), DOI `10.1073/pnas.1000080107`
- 26 samples, 19,216 OTUs, nine sample types
- Sensitivity set: 23 samples after excluding three mock communities
- Feature levels: OTU, genus, phylum
- Rarefaction depth: 58,688 reads

## Framework result

Five claims were graded `strong` across OTU/genus/phylum and all/environmental
sample sets:

- Observed richness differs by sample type;
- Shannon diversity differs by sample type;
- Simpson diversity differs by sample type;
- Bray-Curtis composition differs by sample type;
- Aitchison composition differs by sample type.

The claim that mock communities differ from environmental samples was
`not_supported`. Two of three feature levels were significant, but phylum-level
tests were not:

- Bray-Curtis P=0.0913;
- Aitchison P=0.1057.

The framework therefore retained stable claims and rejected a
resolution-dependent claim in an independent dataset.

## Files

- `../../../07_可复用框架/claimstab/examples/globalpatterns/README.md`
- `../../../07_可复用框架/claimstab/examples/globalpatterns/output/claim_stability_matrix.csv`
- `../../../07_可复用框架/claimstab/examples/globalpatterns/output/endpoint_dependency.csv`
- `../06_论文表格/TableS2_globalpatterns_claim_stability.csv`
