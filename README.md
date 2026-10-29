# QZ microbiome claim-stability data

This repository contains the analysis-ready bacterial and fungal amplicon data,
sample metadata, derived results, and checksums used by the manuscript
*Claimstab: a reconstruction-aware framework for endpoint-specific
reproducibility of microbiome claims*.

## Version

Data release: `v1.0.0`  
Release date: 2026-10-29

## Repository contents

- `data/ASV_16S/`: DADA2 16S ASV counts, representative sequences, SILVA
  taxonomy, read tracking, and filtering summaries.
- `data/ASV_ITS/`: DADA2 ITS ASV counts, representative sequences, UNITE
  taxonomy, read tracking, and filtering summaries.
- `data/sample_sheet.csv`: sample-to-treatment crosswalk used by the analysis.
- `results/`: numerical results, manuscript tables, supporting result notes,
  and figures generated from the analysis-ready data.
- `metadata/data_inventory.csv`: source inventory and identity notes.
- `MANIFEST.sha256`: SHA256 checksums for all deposited files.

The four public datasets (`GlobalPatterns`, `enterotype`, `soilrep`, and
`atlas1006`) are distributed by the `phyloseq` and `microbiome` R packages.
They are not duplicated here. Their source studies are identified in the
manuscript.

## Exclusions

- Raw sequencing reads are not redistributed in this repository. They remain
  subject to the terms of their original archive.
- Public third-party human microbiome data are not duplicated.
- No credentials, caches, temporary files, or private author information are
  included.

## Code

The manuscript analysis scripts and the `claimstab` software are maintained at:

<https://github.com/Taozw410/qz-mic-claimstab>

## License

The deposited data and derived tables are licensed under the Creative Commons
Attribution 4.0 International License. See `LICENSE-DATA.md`.

## Citation

Cite the data release using `CITATION.cff`, the repository URL, the release
tag, and the permanent archive DOI to be added after Zenodo archiving.
