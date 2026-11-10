<!-- readme-v2 -->
# mglurs-brain-sc-datasets

Dataset catalogs (human, rodent, repositories): [docs/datasets.md](docs/datasets.md)

Goal: mGluR (Grm1-8) expression by fine cell type and brain region in public single-cell data. Brain needs expression levels, not % detected: detection saturates in neurons.

## Brain regions

🟨 = regions of interest: depression circuits (prefrontal, anterior cingulate, hippocampus, amygdala, striatum) and Parkinson's (striatum). Hippocampus is the worked example below; all other regions are in the [appendix](#appendix-other-regions).

| | | |
|---|---|---|
| 🟨 **[Prelimbic/infralimbic/orbital areas  (PL-ILA-ORB)](#prelimbicinfralimbicorbital-areas--pl-ila-orb)** | 🟨 **[Anterior cingulate area (ACA)](#anterior-cingulate-area-aca)** | 🟨 **[Hippocampal region (HIP)](#hippocampal-region-hip)** |
| 🟨 **[Cortical subplate (CTXsp)](#cortical-subplate-ctxsp)** | 🟨 **[Striatum-like amygdalar nuclei (sAMY)](#striatum-like-amygdalar-nuclei-samy)** | 🟨 **[Striatum dorsal region (STRd)](#striatum-dorsal-region-strd)** |
| 🟨 **[Striatum ventral region (STRv)](#striatum-ventral-region-strv)** | [Agranular insular area (AI)](#agranular-insular-area-ai) | [Auditory areas (AUD)](#auditory-areas-aud) |
| [Auditory/temporal/perirhinal/ectorhinal areas (AUD-TEa-PERI-ECT)](#auditorytemporalperirhinalectorhinal-areas-aud-tea-peri-ect) | [Cerebellum (CB)](#cerebellum-cb) | [Entorhinal area (ENT)](#entorhinal-area-ent) |
| [Hypothalamus (HY)](#hypothalamus-hy) | [Lateral septal complex (LSX)](#lateral-septal-complex-lsx) | [Medulla (MY)](#medulla-my) |
| [Midbrain (MB)](#midbrain-mb) | [Olfactory areas (OLF)](#olfactory-areas-olf) | [Pallidum (PAL)](#pallidum-pal) |
| [Pons (P)](#pons-p) | [Primary motor area (MOp)](#primary-motor-area-mop) | [Primary somatosensory area (SSp)](#primary-somatosensory-area-ssp) |
| [Retrohippocampal region (RHP)](#retrohippocampal-region-rhp) | [Retrosplenial area (RSP)](#retrosplenial-area-rsp) | [Somatomotor - Frontal pole (MO-FRP)](#somatomotor---frontal-pole-mo-frp) |
| [Somatosensory/gustatory/visceral areas (SS-GU-VISC)](#somatosensorygustatoryvisceral-areas-ss-gu-visc) | [Temporal/perirhinal/ectorhinal areas  (TEa-PERI-ECT)](#temporalperirhinalectorhinal-areas--tea-peri-ect) | [Thalamus (TH)](#thalamus-th) |
| [Visual areas (VIS)](#visual-areas-vis) | [Visual/posterior parietal  areas (VIS-PTLp)](#visualposterior-parietal--areas-vis-ptlp) |  |

## Module 1: Allen whole mouse brain (10x)

- Data: Allen ABC Atlas WMB, 4.04M cells, 10x v2/v3/Multiome 3' GEX, log2(CPM+1), 29 dissection regions (ROI)
- Labels: class > subclass > supertype > cluster (Allen taxonomy). UMAP: Allen `x`,`y` (10 nearest neighbours share subclass 80-99%; shuffled 4-43%)
- Colors in all figures = class
- Enrichment = (mean CPM in subclass + 1) / (mean CPM in other neurons of the same region + 1); one-sided rank-sum, BH q < 0.05
- Tables: `results/allen_wmb/` (`master_enrichment.csv.gz`: region x chemistry x gene x subclass)

Overall % of cells detecting each receptor (all 4.04M cells):

| Grm1 | Grm2 | Grm3 | Grm4 | Grm5 | Grm6 | Grm7 | Grm8 |
|---|---|---|---|---|---|---|---|
| 52 | 17 | 60 | 24 | 76 | 0.03 | 77 | 43 |

### Whole brain: subclass x Grm (mean log2 CPM)

All data from Allen Brain Atlas single cell processing pipeline, across different 10x datasets
v2 and v3 are pooled uncorrected, but the chemistry is not a big confound here (see correlation, later in readme)

Top 5 subclasses per class by Grm expression; all subclasses: `figures/allen_wmb/ALL_fig4_heatmap_all_subclasses_full.png`.

<img src="figures/allen_wmb/ALL_fig4_heatmap_subclass_grm.png" width="900">

### Whole brain: Grm1-8 per neuronal class

The atlas has neuronal classes 01–29; each holds many subclasses (~340 total), and thousands of clusters
Below, are the vln plots showing Grm expression at the toplevel (neuronal classes)

Violin = distribution of per-cell log2(CPM+1) for one Grm across all neurons of a class (color = class).

<img src="figures/allen_wmb/ALL_wb_violin_scatter.png" width="900">

### Example region: hippocampus

UMAP by class and Grm violins per subclass. All other regions are in the appendix. Feature plots (Grm on UMAP) and enrichment tables: `figures/allen_wmb/`, `results/allen_wmb/master_enrichment.csv.gz`.

### Hippocampal region (HIP)

<img src="figures/allen_wmb/HIP_fig1_umap_subclass.png" width="760">

<img src="figures/allen_wmb/HIP_fig2_violins.png" width="900">

## Grm2 and Grm4 coexpression preliminary analysis

<img src="figures/allen_wmb/GRM2_GRM4_subclass_scatter.png" width="900">

log2(CPM) values for Grm2 and Grm4 are plotted, with each subclass represented.  This does not mean the transcripts were detected in the same single-cells, but reports the overall cluster's expression level

<img src="figures/allen_wmb/GRM2_GRM4_single_cells_panels.png" width="900">

For clusters identified in the previous plot as enriched for both Grm2 and 4, expression was examined within single cells. expression thresholds were: Grm2 >= 6.2 and Grm4 >= 6.4 log2(CPM+1) per cell (median of neurons with detected expression). Clusters were selected when both receptors were in the top quartile of subclass means (Grm2 >= 1.5, Grm4 >= 2.9); 12 subclasses are shown

## Caveats

- Dissection region (ROI) is coarse; fine identity comes from subclass/supertype/cluster
- `mean_log2` averages logs; `mean_cpm` is linear
- Ambient RNA: single-digit % detection is not expression (e.g. Plp1 in 30-50% of neurons)
- Enrichment is relative to other neurons in the same region; small subclasses (< 200 cells) excluded
- Allen data: mouse 10x only, CC BY-NC 4.0. Plate-based, spatial, rat, human: not yet

## Next

- Independent 10x 3' datasets per region (CELLxGENE Census, literature) to replicate Allen patterns
- Supertype/cluster-level breakdown of top hits; ambient-RNA flags

## Appendix: other regions

Prioritized (depression / Parkinson's) regions first, then the rest alphabetically.

### Replicate check: 10x v2 vs v3

Per region x subclass, log2 enrichment in v2 cells vs v3 cells (only subclasses with enough cells in both).

<img src="figures/allen_wmb/ALL_fig5_v2_v3_concordance.png" width="860">

| Grm1 | Grm2 | Grm3 | Grm4 | Grm5 | **Grm6 ⚠️** | Grm7 | Grm8 |
|---|---|---|---|---|---|---|---|
| 0.97 | 0.96 | 0.97 | 0.94 | 0.95 | **0.38** | 0.95 | 0.97 |

Spearman rho by gene.

**Grm6 does not replicate (rho = 0.38).** Grm6 is detected in only about 0.03% of brain cells (it is a retina-restricted receptor), so its per-subclass fold changes are driven by a handful of cells and background counts rather than real expression, while the other receptors are expressed in many cells and give stable estimates.

### Prelimbic/infralimbic/orbital areas  (PL-ILA-ORB)

<img src="figures/allen_wmb/PL-ILA-ORB_fig1_umap_subclass.png" width="760">

<img src="figures/allen_wmb/PL-ILA-ORB_fig2_violins.png" width="900">

### Anterior cingulate area (ACA)

<img src="figures/allen_wmb/ACA_fig1_umap_subclass.png" width="760">

<img src="figures/allen_wmb/ACA_fig2_violins.png" width="900">

### Cortical subplate (CTXsp)

<img src="figures/allen_wmb/CTXsp_fig1_umap_subclass.png" width="760">

<img src="figures/allen_wmb/CTXsp_fig2_violins.png" width="900">

### Striatum-like amygdalar nuclei (sAMY)

<img src="figures/allen_wmb/sAMY_fig1_umap_subclass.png" width="760">

<img src="figures/allen_wmb/sAMY_fig2_violins.png" width="900">

### Striatum dorsal region (STRd)

<img src="figures/allen_wmb/STRd_fig1_umap_subclass.png" width="760">

<img src="figures/allen_wmb/STRd_fig2_violins.png" width="900">

### Striatum ventral region (STRv)

<img src="figures/allen_wmb/STRv_fig1_umap_subclass.png" width="760">

<img src="figures/allen_wmb/STRv_fig2_violins.png" width="900">

### Agranular insular area (AI)

<img src="figures/allen_wmb/AI_fig1_umap_subclass.png" width="760">

<img src="figures/allen_wmb/AI_fig2_violins.png" width="900">

### Auditory areas (AUD)

<img src="figures/allen_wmb/AUD_fig1_umap_subclass.png" width="760">

<img src="figures/allen_wmb/AUD_fig2_violins.png" width="900">

### Auditory/temporal/perirhinal/ectorhinal areas (AUD-TEa-PERI-ECT)

<img src="figures/allen_wmb/AUD-TEa-PERI-ECT_fig1_umap_subclass.png" width="760">

<img src="figures/allen_wmb/AUD-TEa-PERI-ECT_fig2_violins.png" width="900">

### Cerebellum (CB)

<img src="figures/allen_wmb/CB_fig1_umap_subclass.png" width="760">

<img src="figures/allen_wmb/CB_fig2_violins.png" width="900">

### Entorhinal area (ENT)

<img src="figures/allen_wmb/ENT_fig1_umap_subclass.png" width="760">

<img src="figures/allen_wmb/ENT_fig2_violins.png" width="900">

### Hypothalamus (HY)

<img src="figures/allen_wmb/HY_fig1_umap_subclass.png" width="760">

<img src="figures/allen_wmb/HY_fig2_violins.png" width="900">

### Lateral septal complex (LSX)

<img src="figures/allen_wmb/LSX_fig1_umap_subclass.png" width="760">

<img src="figures/allen_wmb/LSX_fig2_violins.png" width="900">

### Medulla (MY)

<img src="figures/allen_wmb/MY_fig1_umap_subclass.png" width="760">

<img src="figures/allen_wmb/MY_fig2_violins.png" width="900">

### Midbrain (MB)

<img src="figures/allen_wmb/MB_fig1_umap_subclass.png" width="760">

<img src="figures/allen_wmb/MB_fig2_violins.png" width="900">

### Olfactory areas (OLF)

<img src="figures/allen_wmb/OLF_fig1_umap_subclass.png" width="760">

<img src="figures/allen_wmb/OLF_fig2_violins.png" width="900">

### Pallidum (PAL)

<img src="figures/allen_wmb/PAL_fig1_umap_subclass.png" width="760">

<img src="figures/allen_wmb/PAL_fig2_violins.png" width="900">

### Pons (P)

<img src="figures/allen_wmb/P_fig1_umap_subclass.png" width="760">

<img src="figures/allen_wmb/P_fig2_violins.png" width="900">

### Primary motor area (MOp)

<img src="figures/allen_wmb/MOp_fig1_umap_subclass.png" width="760">

<img src="figures/allen_wmb/MOp_fig2_violins.png" width="900">

### Primary somatosensory area (SSp)

<img src="figures/allen_wmb/SSp_fig1_umap_subclass.png" width="760">

<img src="figures/allen_wmb/SSp_fig2_violins.png" width="900">

### Retrohippocampal region (RHP)

<img src="figures/allen_wmb/RHP_fig1_umap_subclass.png" width="760">

<img src="figures/allen_wmb/RHP_fig2_violins.png" width="900">

### Retrosplenial area (RSP)

<img src="figures/allen_wmb/RSP_fig1_umap_subclass.png" width="760">

<img src="figures/allen_wmb/RSP_fig2_violins.png" width="900">

### Somatomotor - Frontal pole (MO-FRP)

<img src="figures/allen_wmb/MO-FRP_fig1_umap_subclass.png" width="760">

<img src="figures/allen_wmb/MO-FRP_fig2_violins.png" width="900">

### Somatosensory/gustatory/visceral areas (SS-GU-VISC)

<img src="figures/allen_wmb/SS-GU-VISC_fig1_umap_subclass.png" width="760">

<img src="figures/allen_wmb/SS-GU-VISC_fig2_violins.png" width="900">

### Temporal/perirhinal/ectorhinal areas  (TEa-PERI-ECT)

<img src="figures/allen_wmb/TEa-PERI-ECT_fig1_umap_subclass.png" width="760">

<img src="figures/allen_wmb/TEa-PERI-ECT_fig2_violins.png" width="900">

### Thalamus (TH)

<img src="figures/allen_wmb/TH_fig1_umap_subclass.png" width="760">

<img src="figures/allen_wmb/TH_fig2_violins.png" width="900">

### Visual areas (VIS)

<img src="figures/allen_wmb/VIS_fig1_umap_subclass.png" width="760">

<img src="figures/allen_wmb/VIS_fig2_violins.png" width="900">

### Visual/posterior parietal  areas (VIS-PTLp)

<img src="figures/allen_wmb/VIS-PTLp_fig1_umap_subclass.png" width="760">

<img src="figures/allen_wmb/VIS-PTLp_fig2_violins.png" width="900">
