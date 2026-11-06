# mglurs-brain-sc-datasets

Notes on public single-cell and single-nucleus RNA-seq datasets of the brain, for looking at mGluR (Grm1-8) expression by brain region and neuronal subtype. Current focus: rodent (mouse first), healthy baseline, dissociated single-cell only. Spatial data is parked. Human catalogs are parked in `docs/catalog/external_brain_human_datasets.md` and `docs/catalog/census_brain_human_datasets.csv`.

Last built 2026-11-04. Tables are generated; edit the source lists, not this file. Full CSVs are in `docs/catalog/`.

Legend: `✓` accession/region confirmed on a source page during research; `~` from memory, check before relying on it. Priority P1 = large or multi-region healthy adult, P2 = region-focused healthy, P3 = development, aging, glia-only, perturbed or small.

## 1. Repositories and portals

| Source | Species | What is there | Access | How to get it | Ver |
|---|---|---|---|---|---|
| [CZ CELLxGENE Discover + Census](https://cellxgene.cziscience.com/) | mouse, human | Harmonized h5ad collections and a TileDB-SOMA Census with unified tissue, cell_type, disease, development_stage, sex fields. | open | cellxgene_census.open_soma(); get_anndata(); download_source_h5ad(dataset_id) | ✓ |
| [Allen Brain Cell Atlas (AWS Open Data)](https://alleninstitute.github.io/abc_atlas_access/intro.html) | mouse (human WHB too) | Whole mouse brain atlas: WMB-10Xv2 1.7M cells, WMB-10Xv3 2.3M cells, 10x Multiome 1,687 cells; 4.0M combined; MERFISH 3.9M cells (spatial). | open (license CC BY-NC 4.0 on the WMB-10Xv2 page) | aws s3 sync --no-sign-request s3://allen-brain-cell-atlas/expression_matrices/WMB-10Xv2/20230630/ (104 GB); abc_atlas_access package | ✓ |
| [Allen Brain Map RNA-seq data portal](https://brain-map.org/atlases-and-data/rnaseq) | mouse, human | Mouse: Whole Cortex and Hippocampus 10x (2020), Whole Cortex and Hippocampus SMART-seq (2019), V1 and ALM SMART-seq (2018), ACA and MOp SMART-seq (2018). | open (download pages) | Download pages per dataset | ✓ |
| [NeMO Archive (BICCN/BICAN)](https://nemoarchive.org/) | mouse, human, primate | BRAIN Initiative raw and processed omics. Langlieb 2023 raw 10x snRNA-seq (25 TB, open); Yao 2021 isocortex/hippocampus raw (15 TB, open). | mixed: many collections open, some restricted | Collection pages (dat-xxxx) list file manifests | ✓ |
| [Broad Single Cell Portal](https://singlecell.broadinstitute.org/) | mouse, human | Study pages with processed matrices: SCP97 (Campbell arcuate), SCP263 (Ximerakis aging brain), SCP332 (BICCN cerebellum CB-G9), SCP795 (Kozareva cerebellum). | explore open; downloads need sign-in | Sign in, Download tab, or bulk download curl command | ✓ |
| [NCBI GEO](https://www.ncbi.nlm.nih.gov/geo/) | mouse, rat, all | Primary home for author deposits; the only practical source for most rat datasets. | open | ftp.ncbi.nlm.nih.gov/geo/series/GSExxxnnn/GSExxxxxx/suppl/; GEOparse; this script's E-utilities sweep | ✓ |
| [NCBI SRA / ENA](https://www.ncbi.nlm.nih.gov/sra) | all | Raw reads behind GEO series (SRP/PRJNA accessions). | open | pysradb; fasterq-dump; ENA FTP | ✓ |
| [EMBL-EBI Single Cell Expression Atlas](https://www.ebi.ac.uk/gxa/sc/home) | mouse, human, others | Uniformly reprocessed single-cell experiments, e.g. E-GEOD-121891 (Tepe olfactory bulb, 39,850 cells). | open | Experiment page Download tab (normalised counts, clusters) | ✓ |
| [ArrayExpress / BioStudies](https://www.ebi.ac.uk/biostudies/arrayexpress) | all | E-MTAB and mirrored E-GEOD series. | open | Study pages, FTP | ~ |
| [DropViz](http://dropviz.org/) | mouse | Saunders 2018 Drop-seq atlas of nine adult mouse brain regions, browsable by region and cell type. | open | Web explorer; raw and processed via GEO GSE116470 | ✓ |
| [mousebrain.org (Linnarsson lab)](http://mousebrain.org/) | mouse | Zeisel 2018 mouse nervous system atlas (CNS and PNS), loom files. | open | Loom downloads; Bioconductor scRNAseq::ZeiselNervousData() | ~ |
| [Bioconductor scRNAseq (ExperimentHub)](https://bioconductor.org/packages/scRNAseq) | mouse, human | One-line loaders for many published single-cell datasets including several mouse brain sets. | open | scRNAseq::surveyDatasets(); fetchDataset() | ~ |
| [UCSC Cell Browser](https://cells.ucsc.edu/) | mouse, human | Hosted browsable single-cell datasets with downloadable matrices. | open | Dataset pages | ~ |
| [BrainPalmSeq (UBC)](https://brainpalmseq.med.ubc.ca/) | mouse, human | Aggregator browser for brain RNA-seq: Kozareva cerebellum, DropViz, thalamus, hypothalamus (Chen 2017), striatum, amygdala, hippocampus. | open (viewer) | Links out to source repositories | ✓ |
| [Thalamoseq (Janelia)](https://thalamoseq.janelia.org/about) | mouse | Thalamic nuclei transcriptomes (Phillips 2019). | open | Web portal | ✓ |
| [Cambridge Apollo repository (HypoMap)](https://www.repository.cam.ac.uk/handle/1810/340518) | mouse | HypoMap: 384,925-cell integrated mouse hypothalamus atlas as Seurat 4 RDS. | open | Repository download | ✓ |
| [Tabula Muris / Tabula Muris Senis](https://tabula-muris-senis.ds.czbiohub.org/) | mouse | Whole-mouse organ atlases including brain, FACS Smart-seq2 and 10x, ages 1 to 30 months. | open | Portal, figshare, GEO, CELLxGENE | ~ |
| [Mouse Cell Atlas](http://bis.zju.edu.cn/MCA/) | mouse | Microwell-seq atlas of mouse organs incl. brain. | open | Portal; GEO | ~ |
| [Zenodo / Figshare / Mendeley Data / Dryad](https://zenodo.org/) | all | Author-deposited h5ad, rds, loom files, often the best processed form. | open | DOI in each paper's data availability statement | ~ |
| [Brain Image Library (spatial)](https://www.brainimagelibrary.org/) | mouse | Spatial/MERFISH data (e.g. Zhuang lab whole-brain). Out of scope for now (single-cell dissociated only). | open | Dataset pages | ~ |
| [OmicsDI](https://www.omicsdi.org/) | all | Cross-repository index (GEO, ArrayExpress, PRIDE) useful for quick metadata lookups. | open | Search by accession | ✓ |

Quick access:

```python
import cellxgene_census
v = "2025-11-08"
with cellxgene_census.open_soma(census_version=v) as census:
    adata = cellxgene_census.get_anndata(census, organism="Mus musculus",
        var_value_filter="feature_name in ['Grm1','Grm5']",
        obs_value_filter="tissue_general == 'brain' and disease == 'normal'")
cellxgene_census.download_source_h5ad("<dataset_id>", to_path="data/<dataset_id>.h5ad", census_version=v)
```

GEO supplementary files: `https://ftp.ncbi.nlm.nih.gov/geo/series/GSExxxnnn/GSExxxxxx/suppl/`. Allen whole-brain matrices: `aws s3 sync --no-sign-request s3://allen-brain-cell-atlas/expression_matrices/WMB-10Xv2/20230630/ <dir>`.

## 2. Curated rodent datasets

| Study | Sp. | Regions | Assay | Cells | Age | Healthy | Accession / source | Prio | Ver |
|---|---|---|---|---|---|---|---|---|---|
| [Steuernagel et al. HypoMap](https://www.repository.cam.ac.uk/handle/1810/340518) | Mouse | Hypothalamus | Integrated scRNA/snRNA (multiple studie… | 384,925 | adult (mixed) | mostly (some diet/perturbat… | Cambridge Apollo 1810/340518; CELLxGENE Census:dbb4e1ed (1.00) | P1 | ✓ |
| [Kozareva et al. cerebellum snRNA-seq](https://singlecell.broadinstitute.org/single_cell/study/SCP795) | Mouse | Cerebellum | 10x snRNA-seq | ~600k nuclei (memory) | adult | yes | Broad SCP795 (BrainPalmSeq link) Census:35081d47 (0.67) | P1 | ~ |
| [Langlieb et al. adult mouse brain snRNA-seq (BICCN/Macosko)](https://assets.nemoarchive.org/dat-y5zxh0y) | Mouse | Whole brain | 10x snRNA-seq | ~4M nuclei (not page-verifi… | adult | yes | NeMO dat-y5zxh0y (raw, 25 TB, 1,068 fil… Census:3bbb6cf9 (0.60) | P1 | ✓ |
| [Saunders et al. DropViz, nine adult brain regions](http://dropviz.org/) | Mouse | 9 regions (cortex, hippocampus, striatum, thalamus, cerebel… | Drop-seq | ~690k (memory) | adult | yes | GSE116470 | P1 | ✓ |
| [Tasic et al. V1 and ALM SMART-seq](https://brain-map.org/atlases-and-data/rnaseq) | Mouse | Visual cortex (V1), anterolateral motor cortex (ALM) | SMART-seq v4 | ~23k (memory) | adult | yes | GSE115746 Census:28c696bb (1.00) | P1 | ~ |
| [Yao et al. isocortex and hippocampal formation taxonomy](https://assets.nemoarchive.org/dat-jb2f34y) | Mouse | Isocortex, hippocampal formation | 10x v2 + SMART-seq (and Patch-seq) | >1M 10x + SMART-seq (memory) | adult | yes | NeMO dat-jb2f34y (raw ~15 TB, open); Al… Census:d7291f04 (1.00) | P1 | ✓ |
| [Yao et al. whole mouse brain atlas (Allen)](https://alleninstitute.github.io/abc_atlas_access/descriptions/WMB_dataset.html) | Mouse | Whole brain | 10x v2, v3, Multiome scRNA-seq | 4.0M (v2 1.7M, v3 2.3M, mul… | adult (not page-verified) | yes | ABC Atlas WMB-10X; also CELLxGENE | P1 | ✓ |
| [Zeisel et al. mouse nervous system](http://mousebrain.org/) | Mouse | CNS and PNS (brain regions, spinal cord, DRG) | 10x scRNA-seq | ~500k (memory) | postnatal to adult (check) | yes | mousebrain.org; Bioconductor ZeiselNerv… | P1 | ~ |
| [Allen ACA and MOp SMART-seq](https://brain-map.org/atlases-and-data/rnaseq) | Mouse | Anterior cingulate (ACA), primary motor cortex (MOp) | SMART-seq |  | adult | yes |  | P2 | ✓ |
| [Campbell et al. arcuate-median eminence](https://singlecell.broadinstitute.org/single_cell/study/SCP97) | Mouse | Arcuate hypothalamus, median eminence | Drop-seq | 20,921 | adult | yes (includes fed/fasted) | GSE93374 | P2 | ✓ |
| [Chen et al. hypothalamus Drop-seq](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE87544) | Mouse | Hypothalamus | Drop-seq | ~14k (memory) | adult | yes | GSE87544 | P2 | ~ |
| [Chen et al. nucleus accumbens scRNA-seq + MERFISH](https://www.nature.com/articles/s41593-021-00938-x) | Mouse | Nucleus accumbens | 10x scRNA-seq (+ MERFISH) |  | adult | yes |  | P2 | ~ |
| [Hochgerner et al. developing dentate gyrus](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE104323) | Mouse | Dentate gyrus | scRNA-seq (10x, memory) | 24,185 | E16.5 to P132 | yes | GSE104323 | P2 | ✓ |
| [Hochgerner et al. amygdala neuronal types and fear conditioning](https://www.nature.com/articles/s41593-023-01469-3) | Mouse | Amygdala | snRNA-seq (10x, memory) |  | adult | mixed (naive + fear conditi… |  | P2 | ~ |
| [Huang et al. dorsal raphe nucleus](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE134163) | Mouse | Dorsal raphe | scRNA-seq | 39,411 | adult | yes | GSE134163 | P2 | ✓ |
| [Dopamine neuron heterogeneity (Grp/Neurod6)](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE115070) | Mouse | VTA, substantia nigra pars compacta | scRNA-seq |  | adult | yes (6-OHDA experiments are… | GSE115070 | P2 | ✓ |
| [Phillips et al. thalamus (Thalamoseq)](https://thalamoseq.janelia.org/about) | Mouse | Thalamus | single-cell + TRAP (see portal) |  | adult | yes |  | P2 | ~ |
| [Ren et al. serotonin neurons, dorsal and median raphe](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE135132) | Mouse | Dorsal and median raphe | Smart-seq2 (FACS Sert-Cre/Ai14) |  | adult | yes | GSE135132 | P2 | ✓ |
| [Stanley et al. striatal spiny projection neurons](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE139412) | Mouse | Striatum | scRNA-seq (platform not stated) |  | adult | yes | GSE139412 | P2 | ✓ |
| [Tepe et al. olfactory bulb](https://www.ebi.ac.uk/gxa/sc/experiments/E-GEOD-121891) | Mouse | Olfactory bulb | scRNA-seq (10x, memory) | 39,850 | adult | mixed (activity manipulatio… | GSE121891 | P2 | ✓ |
| [Atlas of the rat ventral tegmental area](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE168156) | Rat | Ventral tegmental area | 10x snRNA-seq (FACS-sorted nuclei) |  | adult | yes | GSE168156 | P2 | ✓ |
| [Rat mediobasal hypothalamus snRNA-seq atlas](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE172462) | Rat | Mediobasal hypothalamus | snRNA-seq |  | adult | yes | GSE172462 | P2 | ✓ |
| [BICCN cerebellum CB-G9 (MD733)](https://singlecell.broadinstitute.org/single_cell/study/SCP332) | Mouse | Cerebellum | snRNA-seq | 467 nuclei | adult (C57BL/6) | yes | Broad SCP332 | P3 | ✓ |
| [Developing murine cerebellum single-cell atlas](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE224466) | Mouse | Cerebellum | scRNA-seq | 39,245 | 12 developmental timepoints | yes | GSE224466 | P3 | ✓ |
| [Di Bella et al. developing cortex](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE153164) | Mouse | Cortex (embryonic to postnatal) | scRNA-seq (10x, memory) |  | E10-P4 (memory) | yes | GSE153164 | P3 | ~ |
| [Gokce et al. striatum](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE82187) | Mouse | Striatum | scRNA-seq (Fluidigm C1, memory) | ~1.2k (memory) | adult | yes | GSE82187 Census:3a15ab1c (0.71) | P3 | ~ |
| [Habib et al. Div-Seq (hippocampus, spinal cord)](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE84371) | Mouse | Hippocampus (and spinal cord) | snRNA-seq (Div-Seq/DroNc) |  | adult | yes | GSE84371 | P3 | ~ |
| [Hammond et al. microglia across lifespan](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE121654) | Mouse | Multiple brain regions (microglia only) | scRNA-seq |  | E14.5 to P540 (memory) | yes (plus injury arm) | GSE121654 | P3 | ~ |
| [La Manno et al. developing midbrain (mouse + human)](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE76381) | Mouse | Ventral midbrain | scRNA-seq (Fluidigm C1) |  | embryonic (mouse E11.5-E18.… | yes | GSE76381 | P3 | ~ |
| [Marques et al. oligodendrocyte lineage](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE75330) | Mouse | Multiple CNS regions (oligodendrocyte lineage) | scRNA-seq (Fluidigm C1) | ~5k (memory) | juvenile and adult | yes | GSE75330 | P3 | ~ |
| [Mouse Cell Atlas (brain portion)](http://bis.zju.edu.cn/MCA/) | Mouse | Brain | Microwell-seq |  | adult | yes | GSE108097 Census:e0ed3c55 (0.60) | P3 | ~ |
| [Romanov et al. hypothalamic organization](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE74672) | Mouse | Hypothalamus | scRNA-seq (Fluidigm C1) | ~3k (memory) | juvenile/adult (check) | yes | GSE74672 | P3 | ~ |
| [Rosenberg et al. developing brain and spinal cord (SPLiT-seq)](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE110823) | Mouse | Brain and spinal cord (multiple) | SPLiT-seq | ~156k nuclei (memory) | neonatal (P2, P11) | yes | GSE110823 | P3 | ~ |
| [Tasic et al. V1 cortical taxonomy](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE71585) | Mouse | Visual cortex (V1) | SMART-seq | ~1.8k (memory) | adult | yes | GSE71585 Census:3a15ab1c (1.00) | P3 | ~ |
| [Tabula Muris (brain)](https://tabula-muris.ds.czbiohub.org/) | Mouse | Brain | FACS Smart-seq2 + 10x |  | young adult | yes | GSE109774 Census:98e5ea9f (0.62) | P3 | ~ |
| [Tabula Muris Senis (brain)](https://tabula-muris-senis.ds.czbiohub.org/) | Mouse | Brain (myeloid and non-myeloid fractions) | FACS Smart-seq2 + 10x |  | 1-30 months | yes (aging series) | GSE132042 Census:98e5ea9f (1.00) | P3 | ~ |
| [Vladoiu et al. developing cerebellum](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE118068) | Mouse | Cerebellum | scRNA-seq (10x, memory) |  | embryonic to postnatal | yes | GSE118068 | P3 | ~ |
| [Ximerakis et al. aging mouse brain](https://singlecell.broadinstitute.org/single_cell/study/SCP263/) | Mouse | Whole brain (dissociated) | scRNA-seq (10x, memory) | 37,069 | young vs old | yes (aging comparison) | GSE129788 Census:3bbb6cf9 (0.71) | P3 | ✓ |
| [Zeisel et al. cortex and CA1](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE60361) | Mouse | Somatosensory cortex (S1), hippocampus CA1 | STRT-seq (Fluidigm C1) | 3,005 (memory) | juvenile (P22-P32, memory) | yes | GSE60361 | P3 | ~ |
| [Rat cortex, hippocampus, thalamus after 40 Hz electrical stimulation](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE253672) | Rat | Cortex, hippocampus, thalamus | snRNA-seq |  | adult | mixed (stimulated vs contro… | GSE253672 | P3 | ✓ |
| [Rat cortex electroacupuncture and BBB opening](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE272895) | Rat | Cerebral cortex | scRNA-seq |  | adult | no (treated vs control) | GSE272895 | P3 | ✓ |
| [Rat nucleus accumbens, cocaine response (Savell et al.)](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE137763) | Rat | Nucleus accumbens | 10x snRNA-seq (FACS-sorted) |  | adult | mixed (cocaine vs saline) | GSE137763 | P3 | ✓ |
| [Rat nucleus accumbens Reln CRISPRi (cocaine ensembles)](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE269490) | Rat | Nucleus accumbens | snRNA-seq |  | adult | no (CRISPRi; lacZ guide con… | GSE269490 | P3 | ✓ |

Columns `geo_title`, `geo_n_samples`, `geo_release`, `geo_supp` and `geo_check` in `docs/catalog/rodent_curated_datasets.csv` come from NCBI GEO; `(?)` above means the GEO record did not match the expected keywords for that entry. `Census:` shows a likely title match in the Census catalog (id prefix, token overlap).

## 3. CELLxGENE Census: mouse brain

Release 2025-11-08, primary data, `tissue_general == 'brain'`: **19 datasets, 3,600,251 cells**; 2,370,111 cells are disease == normal and adult (age heuristic: 56 to 539 days). 13 datasets have at least one healthy adult cell. Full table: `docs/catalog/census_brain_mouse_datasets.csv`.

| Collection | Dataset | Cells | Healthy adult | Donors | Assay | Regions | Main age | Neuronal frac |
|---|---|---|---|---|---|---|---|---|
| [A taxonomy of transcriptomic cell types across …](https://cellxgene.cziscience.com/collections/e3aa612b-0d7d-4d3f-bbea-b8972a74dd4b) | Single-cell RNA-seq for all cortical & hipp… | 1,169,213 | 670,549 | 55 | 10x 3' v2 | Cortex; Hippocampus; Other | adult | 0.987 |
| [A transcriptomic atlas of the mouse cerebellum …](https://cellxgene.cziscience.com/collections/f70ebd97-b3bc-44fe-849d-c18e08fe773d) | A transcriptomic atlas of the mouse cerebel… | 611,034 | 611,034 | 6 | 10x 3' v3 | Cerebellum | adult | 0.892 |
| [An integrated transcriptomic and epigenomic atl…](https://cellxgene.cziscience.com/collections/ae1420fe-6630-46ed-8b3d-cc6056a66467) | An integrated transcriptomic and epigenomic… | 406,187 | 406,187 | 75 | 10x 3' v2; 10x 3' v3; Smart-s… | Cortex | adult | 0.849 |
| [HypoMap – a unified single cell gene expression…](https://cellxgene.cziscience.com/collections/d86517f0-fa7e-4266-b82e-a521350d6d36) | HypoMap – a unified single cell gene expres… | 384,925 | 292,967 | 24 | 10x 3' v1; 10x 3' v2; 10x 3' … | Hypothalamus | adult | 0.57 |
| [Thyroid hormone remodels cortex to coordinate b…](https://cellxgene.cziscience.com/collections/c450e15d-321a-42d6-986b-11409d04896d) | Single-nucleus RNA sequencing of M2: WT-THR… | 205,722 | 205,722 | 10 | 10x 3' v3 | Cortex | adult | 0.722 |
| [Thyroid hormone remodels cortex to coordinate b…](https://cellxgene.cziscience.com/collections/c450e15d-321a-42d6-986b-11409d04896d) | Single-nucleus RNA sequencing of M2: T3 vs … | 107,742 | 107,742 | 8 | 10x 3' v3 | Cortex | adult | 0.7 |
| [A taxonomy of transcriptomic cell types across …](https://cellxgene.cziscience.com/collections/e3aa612b-0d7d-4d3f-bbea-b8972a74dd4b) | Single-cell RNA-seq for all cortical & hipp… | 66,979 | 33,298 | 518 | Smart-seq v4 | Cortex; Hippocampus; Other; Whole/unspecifi… | juvenile | 0.973 |
| [Transcriptional profiling of murine oligodendro…](https://cellxgene.cziscience.com/collections/886ff63c-af9e-4fcc-9c51-64a92cb6fd48) | Transcriptional profiling of murine oligode… | 38,807 | 13,580 | 20 | 10x 3' v3 | Cortex | juvenile | 0.0 |
| [Humoral immunity at the brain borders in homeos…](https://cellxgene.cziscience.com/collections/e9eec7f5-8519-42f6-99b4-6dbd9cc5ef03) | A scRNA-seq atlas of immune cells at the CN… | 15,019 | 10,238 | 12 | 10x 3' v2; 10x 3' v3 | Whole/unspecified | adult | 0.007 |
| [Cellular development and evolution of the mamma…](https://cellxgene.cziscience.com/collections/72d37bc9-76cc-442d-9131-da0e273862db) | snRNA-seq data for mouse cerebella from 9-1… | 115,282 | 9,046 | 24 | 10x 3' v2; 10x 3' v3 | Cerebellum | embryonic | 0.653 |
| [Tabula Muris Senis](https://cellxgene.cziscience.com/collections/0b9d8a04-bb9d-44da-aa27-705bb65b54eb) | All - A single-cell transcriptomic atlas ch… | 20,666 | 7,974 | 15 | Smart-seq2 | Whole/unspecified | aged | 0.04 |
| [Adult mouse cortical cell taxonomy revealed by …](https://cellxgene.cziscience.com/collections/a3c37598-b8e8-47db-92a9-eb91a77c9529) | Adult mouse cortical cell taxonomy revealed… | 1,679 | 1,679 | 72 | Smart-seq | Cortex | adult | 0.874 |
| [Shared and distinct transcriptomic cell types a…](https://cellxgene.cziscience.com/collections/45f0f67d-4b69-4a3c-a4e8-a63b962e843f) | Shared and distinct transcriptomic cell typ… | 95 | 95 | 7 | Smart-seq v4 | Cortex | adult | 0.884 |
| [Type I interferon responsive microglia shape co…](https://cellxgene.cziscience.com/collections/4828d33d-fb26-42e7-bf36-18293b0eec85) | Type I interferon responsive microglia shap… | 12,330 | 0 | 4 | 10x 3' v3 | Cortex | neonatal | 0.0 |
| [Developmental trajectories of thalamic nuclei r…](https://cellxgene.cziscience.com/collections/d5cad3f0-56b6-4fbe-8f2b-be92a8c7820f) | Atlas of the developing mouse thalamus | 249,071 | 0 | 24 | 10x 3' v3 | Whole/unspecified | embryonic | 0.72 |
| [Molecular and spatial signatures of mouse brain…](https://cellxgene.cziscience.com/collections/31937775-0602-4e52-a799-b6acdd2bac2e) | BrainAgingSpatialAtlas_snRNAseq | 79,667 | 0 | 4 | 10x 3' v3 | Whole/unspecified | juvenile | 0.582 |
| [Single-cell transcriptomics characterization of…](https://cellxgene.cziscience.com/collections/0faa1af6-e504-4b88-a47b-69347e1bace5) | Microglia - 24 months old wild-type and Rag… | 15,601 | 0 | 1 | 10x 3' v3 | Whole/unspecified | aged | 0.0 |
| [Single-cell census of murine glioblastoma subty…](https://cellxgene.cziscience.com/collections/6d7d23d0-237d-4430-9200-92858abba2d8) | Single-cell census of murine glioblastoma s… | 94,181 | 0 | 10 | 10x 3' v3 | Whole/unspecified | adult | 0.001 |
| [Single-cell transcriptomics characterization of…](https://cellxgene.cziscience.com/collections/0faa1af6-e504-4b88-a47b-69347e1bace5) | Single-cell of aged oligodendrocytes | 6,051 | 0 | 1 | 10x 3' v3 | Whole/unspecified | aged | 0.0 |

Region and age labels are harmonized heuristics over Census `tissue` and `development_stage`; cell-class flags come from Census cell_type labels (coarse). Fine neuronal subtypes usually live in author annotations inside each h5ad, not in the Census fields.

## 4. Region by cell-class coverage (Census, healthy adult)

Number of datasets with at least 20 healthy adult cells of that class in that region. Cell counts (thousands) in `docs/catalog/census_mouse_coverage_kcells_healthy_adult.csv`.

| Region | Glutamatergic | GABAergic | GABA: PV | GABA: SST | GABA: VIP | GABA: Lamp5/Sncg | Medium spiny | Purkinje | Granule | Other neuron | Astrocyte | Oligodendrocyte lineage | Microglia/immune | Vascular/other |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Cerebellum | 1 | 2 | . | . | . | . | . | 2 | 2 | . | 2 | 2 | 1 | 2 |
| Hippocampus | 2 | 2 | 2 | 2 | 2 | 2 | . | . | . | 2 | 1 | 1 | 1 | . |
| Hypothalamus | . | . | . | . | . | . | . | . | . | 1 | 1 | 1 | 1 | 1 |
| Cortex | 7 | 6 | 4 | 4 | 4 | 4 | . | . | . | . | 6 | 7 | 6 | 6 |
| Other | 1 | 1 | 1 | 1 | 1 | 1 | . | . | . | . | . | . | . | . |
| Whole/unspecified | . | 1 | . | . | . | . | 1 | . | . | 2 | 1 | 1 | 2 | 2 |

## 5. GEO sweep (mouse and rat, brain, single-cell/nucleus)

GEO stage not run.

## 6. Leads to vet

- [Hahn et al. aging mouse brain white-matter atlas (Cell 2023)](https://singlecell.broadinstitute.org/single_cell/study/SCP263/): Follow-up to Ximerakis; find GEO accession.
- Munoz-Manchado et al. striatum (Cell Rep 2018): Striatal interneurons; accession not confirmed.
- Mickelsen et al. lateral hypothalamus; Kim et al. VMH: Hypothalamic subregions; accessions not confirmed.
- [Mouse pons and medulla single-cell atlas (Nat Commun 2024)](https://www.nature.com/articles/s41467-024-45907-7): Brainstem coverage; confirm this is the right paper and accession.
- Rat nucleus accumbens medium spiny neuron atlas (PMID 39107568): Rat MSN subtypes; find GEO accession.
- [Locus coeruleus (Mulvey 2018 sex differences, GSE100005 superseries)](https://www.omicsdi.org/dataset/geo/GSE100005): Check which subseries are single-cell.
- Mouse Patch-seq (Gouwens 2020, Scala 2021): Single-cell with electrophysiology; DANDI/Allen, to vet.
- Superior colliculus, PAG, septum/BNST, claustrum, habenula: Regions with sparse coverage; search GEO sweep output.
- [Zhuang lab MERFISH whole mouse brain](https://www.brainimagelibrary.org/): Spatial; parked until dissociated data reviewed.

## 7. Notes

- Mouse first: sample quality and region annotation are better than human postmortem; human is parked.
- Census has no rat. Rat comes from GEO and is sparse (VTA, mediobasal hypothalamus, nucleus accumbens, a few treated cortex/hippocampus series).
- Single-nucleus and 10x data detect low-abundance receptor transcripts poorly; prefer deeper plate-based sets (Smart-seq) or large 10x atlases and check Grm detection per dataset before conclusions.
- Next: per-dataset Grm1-8 detection pass on the shortlisted P1/P2 datasets, then region/subtype figures.

