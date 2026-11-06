<!-- readme-v2 -->
# mglurs-brain-sc-datasets

Dataset catalogs (human, rodent, repositories): [docs/datasets.md](docs/datasets.md)

Goal: mGluR (Grm1-8) expression by fine cell type and brain region in public single-cell data. Brain needs expression levels, not % detected: detection saturates in neurons.

## Module 1: Allen whole mouse brain (10x)

- Data: Allen ABC Atlas WMB, 4.04M cells, 10x v2/v3/Multiome 3' GEX, log2(CPM+1), 29 dissection regions (ROI)
- Labels: class > subclass > supertype > cluster (Allen taxonomy). UMAP: Allen `x`,`y`
- UMAP check: 10 nearest neighbours share subclass 80-99% (shuffled 4-43%)
- Overall % cells detecting: Grm1 52, Grm2 17, Grm3 60, Grm4 24, Grm5 76, Grm6 0.03, Grm7 77, Grm8 43

Run (repo root, after downloading data to the external drive):

```
python mglurs_allen_wmb_download_p009.py --dest <drive>/abc_wmb
python mglurs_allen_regions_p010.py --abc-dir <drive>/abc_wmb --out-dir <drive>/derived
python mglurs_allen_notebooks_p013.py
python mglurs_allen_run_p012.py --rois HIP STRd CB TH --split-chem
```

### Whole atlas: top subclasses by mean log2 expression

| Gene | Top 3 subclasses (mean log2) |
|---|---|
| Grm1 | 313 CBX Purkinje Gaba (11.7); 312 CBX MLI Cdh22 Gaba (10.5); 035 OB Eomes Ms4a15 Glut (10.5) |
| Grm2 | 310 CBX Golgi Gly-Gaba (8.3); 144 MM Foxb1 Glut (5.8); 143 MM-ant Foxb1 Glut (5.4) |
| Grm3 | 319 Astro-TE NN (10.3); 331 Peri NN (10.2); 295 CBN Dmbx1 Gaba (9.6) |
| Grm4 | 314 CB Granule Glut (7.9); 147 AD Serpinb7 Glut (6.8); 151 TH Prkcd Grin2c Glut (6.0) |
| Grm5 | 071 LSX Prdm12 Zeb2 Gaba (11.7); 070 LSX Prdm12 Slit2 Gaba (11.7); 069 LSX Nkx2-1 Gaba (11.7) |
| Grm6 | 204 SC Otx2 Gcnt4 Gaba (0.3); 213 SCsg Gabrr2 Gaba (0.1); 202 PRT Tcf7l2 Gaba (0.0) |
| Grm7 | 257 SPVC Ccdc172 Glut (11.8); 144 MM Foxb1 Glut (11.5); 110 BST-po Iigp1 Glut (11.4) |
| Grm8 | 315 DCO UBC Glut (10.6); 111 TRS-BAC Sln Glut (10.5); 064 STR-PAL Chst9 Gaba (9.8) |

## Regions

Per region: UMAP by class, Grm violins per subclass (blue = neuron, grey = glia), Grm on UMAP, top enriched neuronal subclasses.
Enrichment = (mean CPM in subclass + 1) / (mean CPM in other neurons of region + 1), one-sided rank-sum, BH q < 0.05.
v2/v3 split figures are in `figures/allen_wmb/` (`_v2`, `_v3`).

### CB

<img src="figures/allen_wmb/CB_fig1_umap_subclass.png" width="520">

<img src="figures/allen_wmb/CB_fig3_umap_grm.png" width="860">

<img src="figures/allen_wmb/CB_fig2_violins.png" width="860">

| Gene | Most enriched neuronal subclasses (fold; mean CPM; n cells) |
|---|---|
| Grm1 | 312 CBX MLI Cdh22 Gaba (1.9x; 41745; 12.8k); 315 DCO UBC Glut (1.3x; 31336; 486); 311 CBX MLI Megf11 Gaba (1.3x; 29259; 30.8k) |
| Grm2 | 310 CBX Golgi Gly-Gaba (882.8x; 8976; 242); 315 DCO UBC Glut (13.2x; 294; 486); 250 CBN Neurod2 Pvalb Glut (4.2x; 96; 259) |
| Grm3 | 295 CBN Dmbx1 Gaba (22.4x; 17877; 3.6k); 310 CBX Golgi Gly-Gaba (11.9x; 13649; 242); 311 CBX MLI Megf11 Gaba (4.9x; 3324; 30.8k) |
| Grm4 | 314 CB Granule Glut (162.8x; 13956; 113.8k) |
| Grm5 | 309 CB PLI Gly-Gaba (61.1x; 40518; 4.2k); 250 CBN Neurod2 Pvalb Glut (25.4x; 40897; 259); 295 CBN Dmbx1 Gaba (12.4x; 16625; 3.6k) |
| Grm7 | 295 CBN Dmbx1 Gaba (86.8x; 35887; 3.6k); 310 CBX Golgi Gly-Gaba (13.3x; 15358; 242); 250 CBN Neurod2 Pvalb Glut (5.5x; 6462; 259) |
| Grm8 | 315 DCO UBC Glut (44.5x; 42232; 486); 310 CBX Golgi Gly-Gaba (24.5x; 25381; 242); 311 CBX MLI Megf11 Gaba (15.6x; 4511; 30.8k) |

### HIP

<img src="figures/allen_wmb/HIP_fig1_umap_subclass.png" width="520">

<img src="figures/allen_wmb/HIP_fig3_umap_grm.png" width="860">

<img src="figures/allen_wmb/HIP_fig2_violins.png" width="860">

| Gene | Most enriched neuronal subclasses (fold; mean CPM; n cells) |
|---|---|
| Grm1 | 037 DG Glut (3.6x; 10649; 80.3k); 053 Sst Gaba (1.7x; 12972; 1.3k) |
| Grm2 | 037 DG Glut (27.2x; 933; 80.3k) |
| Grm3 | 023 SUB-ProS Glut (2.1x; 687; 384); 053 Sst Gaba (1.3x; 424; 1.3k); 016 CA1-ProS Glut (1.1x; 359; 24.9k) |
| Grm4 | 046 Vip Gaba (7.3x; 163; 4.1k); 047 Sncg Gaba (5.7x; 147; 1.1k); 048 RHP-COA Ndnf Gaba (5.7x; 142; 2.1k) |
| Grm5 | 051 Pvalb chandelier Gaba (2.4x; 88217; 281); 023 SUB-ProS Glut (2.2x; 82444; 384); 053 Sst Gaba (1.7x; 64667; 1.3k) |
| Grm6 | 047 Sncg Gaba (1.2x; 0; 1.1k); 023 SUB-ProS Glut (1.1x; 0; 384); 017 CA3 Glut (1.0x; 0; 4.8k) |
| Grm7 | 037 DG Glut (2.1x; 33985; 80.3k); 046 Vip Gaba (1.4x; 37984; 4.1k) |
| Grm8 | 046 Vip Gaba (72.3x; 22144; 4.1k); 023 SUB-ProS Glut (5.8x; 5705; 384); 053 Sst Gaba (3.4x; 3277; 1.3k) |

### STRd

<img src="figures/allen_wmb/STRd_fig1_umap_subclass.png" width="520">

<img src="figures/allen_wmb/STRd_fig3_umap_grm.png" width="860">

<img src="figures/allen_wmb/STRd_fig2_violins.png" width="860">

| Gene | Most enriched neuronal subclasses (fold; mean CPM; n cells) |
|---|---|
| Grm1 | 061 STR D1 Gaba (1.4x; 11819; 16.7k); 062 STR D2 Gaba (1.0x; 9984; 18.1k) |
| Grm2 | 063 STR D1 Sema5a Gaba (6.1x; 26; 780); 064 STR-PAL Chst9 Gaba (2.2x; 9; 437); 056 Sst Chodl Gaba (2.1x; 9; 230) |
| Grm3 | 062 STR D2 Gaba (1.2x; 7407; 18.1k); 061 STR D1 Gaba (1.1x; 7053; 16.7k) |
| Grm4 | 063 STR D1 Sema5a Gaba (1.2x; 719; 780); 062 STR D2 Gaba (1.1x; 650; 18.1k); 061 STR D1 Gaba (1.1x; 651; 16.7k) |
| Grm5 | 062 STR D2 Gaba (1.2x; 96031; 18.1k); 061 STR D1 Gaba (1.1x; 92927; 16.7k) |
| Grm7 | 063 STR D1 Sema5a Gaba (1.3x; 67417; 780); 062 STR D2 Gaba (1.2x; 55500; 18.1k); 061 STR D1 Gaba (1.1x; 52365; 16.7k) |
| Grm8 | 064 STR-PAL Chst9 Gaba (10.9x; 22023; 437); 061 STR D1 Gaba (1.0x; 2266; 16.7k) |

### TH

<img src="figures/allen_wmb/TH_fig1_umap_subclass.png" width="520">

<img src="figures/allen_wmb/TH_fig3_umap_grm.png" width="860">

<img src="figures/allen_wmb/TH_fig2_violins.png" width="860">

| Gene | Most enriched neuronal subclasses (fold; mean CPM; n cells) |
|---|---|
| Grm1 | 151 TH Prkcd Grin2c Glut (4.9x; 30050; 68.1k) |
| Grm2 | 150 CM-IAD-CL-PCN Sema5b Glut (3.2x; 666; 13.6k); 149 PVT-PT Ntrk1 Glut (2.9x; 647; 9.9k); 147 AD Serpinb7 Glut (2.0x; 487; 716) |
| Grm3 | 093 RT-ZI Gnb3 Gaba (15.3x; 10651; 7.5k); 213 SCsg Gabrr2 Gaba (7.5x; 7940; 2.1k); 203 LGv-SPFp-SPFm Nkx2-2 Tcf7l2 Gaba (2.3x; 2481; 5.6k) |
| Grm4 | 151 TH Prkcd Grin2c Glut (2.4x; 1260; 68.1k); 147 AD Serpinb7 Glut (2.1x; 1752; 716); 150 CM-IAD-CL-PCN Sema5b Glut (1.7x; 1337; 13.6k) |
| Grm5 | 213 SCsg Gabrr2 Gaba (4.3x; 78209; 2.1k); 203 LGv-SPFp-SPFm Nkx2-2 Tcf7l2 Gaba (3.7x; 63571; 5.6k); 109 LGv-ZI Otx2 Gaba (2.1x; 38075; 4.4k) |
| Grm6 | 213 SCsg Gabrr2 Gaba (5.5x; 5; 2.1k) |
| Grm7 | 153 MG-POL-SGN Nts Glut (1.7x; 55423; 2.0k); 152 RE-Xi Nox4 Glut (1.7x; 52762; 5.5k); 150 CM-IAD-CL-PCN Sema5b Glut (1.6x; 48879; 13.6k) |
| Grm8 | 109 LGv-ZI Otx2 Gaba (3.9x; 12117; 4.4k); 150 CM-IAD-CL-PCN Sema5b Glut (3.4x; 9525; 13.6k); 168 SPA-SPFm-SPFp-POL-PIL-PoT Sp9 Glut (3.3x; 9628; 10.8k) |

## Caveats

- Dissection region (ROI) is coarse; fine identity comes from subclass/supertype/cluster
- `mean_log2` averages logs; table columns `mean_expm1_log2` / `mean_cpm` are linear
- Ambient RNA: single-digit % detection is not expression (e.g. Plp1 in 30-50% of neurons)
- Allen data is mouse 10x only, CC BY-NC 4.0. Plate-based, spatial, rat, human: not yet

## Next

- Independent 10x 3' datasets per region (CELLxGENE Census, literature) to replicate Allen patterns
