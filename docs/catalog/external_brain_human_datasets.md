# External (non-Census) human brain sc/snRNA-seq datasets

Compiled 2026-11-04 from the source pages linked in the table. Blank cells were not stated on the pages read. Open means no credentials needed.

| source | study | accession | region | assay | donors | cells | condition | access |
|---|---|---|---|---|---|---|---|---|
| [allen_whb_siletti2023](https://alleninstitute.github.io/abc_atlas_access/descriptions/WHB-10Xv3.html) | Siletti et al., whole adult human brain (HCA Human Brain Cell Atlas v1.0) | ABC Atlas WHB-10Xv3; CELLxGENE collection 283d65eb-dd53-496d-adb7-7570c7caa443 | ~100 dissections: cortex, cerebellum, basal nuclei, thalamus, hypothalamus, hippocampus, midbrain, pons, medulla, spinal cord | 10x 3' v3 snRNA-seq | 3 | >3M nuclei | normal | open |
| [allen_seaad_mtg](https://brain-map.org/consortia/sea-ad/our-data) | SEA-AD middle temporal gyrus 10x snRNA-seq | Synapse syn26223298 (raw); AWS allen-sea-ad-atlas (processed) | Middle temporal gyrus | 10x snRNA-seq |  |  | Alzheimer's disease cohort | raw controlled; processed open |
| [allen_seaad_a9](https://brain-map.org/consortia/sea-ad/our-data) | SEA-AD prefrontal cortex (A9) 10x snRNA-seq | Synapse syn26223298 (raw); AWS allen-sea-ad-atlas (processed) | Prefrontal cortex (A9) | 10x snRNA-seq |  |  | Alzheimer's disease cohort | raw controlled; processed open |
| [allen_seaad_multiregion_microglia](https://brain-map.org/consortia/sea-ad/our-data) | SEA-AD multiregion microglia-annotated nuclei | AWS SEA-AD single-cell profiling (Multiregion_2026) | Multiple regions including MTG | 10x v3.1 3' snRNA-seq and 10x multiome |  | 240,651 nuclei (mostly microglia) | Alzheimer's disease cohort | open |
| [allen_m1_10x_2020](https://brain-map.org/atlases-and-data/rnaseq) | Allen human primary motor cortex 10x |  | Primary motor cortex (M1) | 10x Genomics |  |  |  | open (download page) |
| [allen_multicortical_smartseq_2019](https://brain-map.org/atlases-and-data/rnaseq) | Allen human multiple cortical areas SMART-seq |  | MTG, CgGr, V1C, M1C, S1C, A1C | SMART-seq |  |  |  | open (download page) |
| [allen_mtg_smartseq_2018](https://brain-map.org/atlases-and-data/rnaseq) | Allen human MTG SMART-seq |  | Middle temporal gyrus | SMART-seq |  |  |  | open (download page) |
| [allen_v1_acc_smartseq_2018](https://brain-map.org/atlases-and-data/rnaseq) | Allen human V1 and ACC SMART-seq |  | Primary visual cortex (V1C), anterior cingulate (ACC) | SMART-seq |  |  |  | open (download page) |
| [hca_cortical_atlas_v1](https://data.humancellatlas.org/hca-bio-networks/nervous-system/atlases/cortex-v1-0) | HCA Human Cortical Cell Atlas v1.0 |  | 9 cortical tissues | 2 assays (not named on page) |  | 638.9k | normal | open |
| [mathys2023_rosmap_pfc](https://compbio.mit.edu/ad_aging_brain/) | Mathys et al., aged human prefrontal cortex | Synapse syn52293417 (raw, controlled) | Prefrontal cortex | snRNA-seq | 427 | ~2.3M | aging, Alzheimer's disease, resilience | raw controlled (Data Use Certificate); processed linked, status unclear |
| [lau2020_gse157827](https://www.omicsdi.org/dataset/geo/GSE157827) | Lau et al., AD prefrontal cortex snRNA-seq | GSE157827 | Prefrontal cortex | snRNA-seq |  | 169,496 nuclei | Alzheimer's disease + controls | open (GEO) |
| [leng2021_gse147528](https://www.omicsdi.org/dataset/geo/GSE147528) | Leng et al., selectively vulnerable neurons in AD | GSE147528 | Caudal entorhinal cortex, superior frontal gyrus | snRNA-seq |  |  | Alzheimer's disease + controls | open (GEO) |
| [morabito2021_gse174367](https://www.omicsdi.org/dataset/geo/GSE174367) | Morabito et al., snATAC + snRNA of Alzheimer's disease | GSE174367 | not stated on fetched page | snRNA-seq + snATAC-seq (same samples) |  | 191,890 nuclei | late-stage Alzheimer's disease + controls | open (GEO) |
| [grubman2019_gse138852](https://omicsdi.org/dataset/geo/GSE138852) | Grubman et al., entorhinal cortex atlas in AD | GSE138852 | Entorhinal cortex | snRNA-seq | 12 | 13,214 nuclei (after QC) | Alzheimer's disease + controls | open (GEO) |
| [kamath2022_gse184950](https://www.omicsdi.org/dataset/geo/GSE184950) | Kamath et al., human substantia nigra in Parkinson's disease | GSE184950; HCA project 16cd6791-2adb-4d0f-8222-0184dada6456 | Substantia nigra | snRNA-seq |  |  | Parkinson's disease + controls | open (GEO) |
| [tran2021_reward_circuitry](https://www.biorxiv.org/content/10.1101/2020.10.07.329839v1) | Tran et al., reward circuitry in the human brain (LIBD) | not given on fetched page (GitHub + S3 links) | DLPFC, hippocampus, sACC, nucleus accumbens, amygdala | 10x Chromium snRNA-seq | 5 (male, ages 40-62) | 42,308 nuclei (14 samples) | neurotypical | open per page (S3 + GitHub links); GEO accession unconfirmed |
| [thompson_libd_hippocampus](https://bioconductor.statistik.tu-dortmund.de/packages/3.22/data/experiment/vignettes/humanHippocampus2024/inst/doc/humanHippocampus2024.html) | Thompson et al., snRNA-seq + spatial atlas of human hippocampus (LIBD) | GSE264624 (snRNA-seq); GSE264692 (spatial); Bioconductor humanHippocampus2024 EH9606 | Anterior hippocampus | 10x Chromium 3' snRNA-seq (+ Visium) | 10 | 75,411 nuclei (26 libraries) | neurotypical | open |
| [velmeshev2022_nemo_raw](https://assets.nemoarchive.org/dat-7aycjfr) | Kriegstein lab snRNA 10x human raw data (Velmeshev et al. 2022 preprint, prenatal and postnatal cortex) | NeMO dat-7aycjfr | cortex (not listed on page) | 10x snRNA-seq |  |  | development | restricted |

## Leads not yet vetted

- [Integrated AD atlas across community datasets](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC11709630/): Could index many AD snRNA-seq studies at once.
- [Mathys multi-region AD repository](https://compbio.mit.edu/ad_multiregion): Multi-region sibling of the Mathys PFC data.
- [Human Protein Atlas single-nuclei brain](https://v24.proteinatlas.org/humanproteome/single+cell/single+nuclei+brain): Derived summary view, useful for quick GRM checks.
- [NeMO Archive (BRAIN Initiative)](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC9825473/): Home for BICCN/BICAN data, mixed open and restricted.
- [Allen SEA-AD downloads and docs](https://portal.brain-map.org/explore/seattle-alzheimers-disease/seattle-alzheimers-disease-brain-cell-atlas-download): Official download page.

## Not yet researched

Fetal/developmental cortex (Bhaduri, Nowakowski), microglia-focused studies, MS and other disease cohorts, PsychENCODE, cerebellum, choroid plexus, hypothalamus/pituitary, spinal cord, and mouse datasets.
