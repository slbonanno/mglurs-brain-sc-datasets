# Allen whole-mouse-brain Grm summary (module 1)

Built 2026-11-05. 4,042,976 cells from 24 expression files (10x v2, v3, Multiome). Expression is Allen's log2 files; detection means log2 value > 0 (equivalent to a raw count of at least 1 if the normalization is log2(CPM+1); check `normalization` in `wmb_extraction_log.csv`). `mean_expm1_log2` = mean of 2^x - 1 (CPM-like) and assumes that normalization.

Tables (`.csv.gz`, one row per group x gene): `wmb_grm_summary_{neurotransmitter,class,subclass,supertype,cluster,region}`. Columns `roi` (dissection region) and `chem` (10Xv2/10Xv3/10XMulti) are `ALL` for pooled rows; class/subclass/supertype also have per-roi and per-chem rows.

Gene groups: grm (Grm1-8), marker (cell-class markers), housekeeping, gpcr_control (other neuronal GPCRs), long_neuronal (long-gene detection control).

`wmb_grm_top_hits.csv`: top 25 subclasses and supertypes per Grm by mean log2(CPM+1) (min cells 100), with long-gene and housekeeping medians for comparison.

## Top subclasses per Grm (pooled, by mean log2 expression)

**Grm1**: 313 CBX Purkinje Gaba (mean log2 11.70, 100% detected, n=380); 312 CBX MLI Cdh22 Gaba (mean log2 10.46, 100% detected, n=13,098); 035 OB Eomes Ms4a15 Glut (mean log2 10.46, 100% detected, n=1,651); 311 CBX MLI Megf11 Gaba (mean log2 10.05, 100% detected, n=31,619); 151 TH Prkcd Grin2c Glut (mean log2 10.01, 100% detected, n=68,480); 308 DCO Il22 Gly-Gaba (mean log2 9.90, 100% detected, n=1,367); 144 MM Foxb1 Glut (mean log2 9.71, 100% detected, n=8,279); 197 SNr Six3 Gaba (mean log2 9.62, 100% detected, n=1,421)

**Grm2**: 310 CBX Golgi Gly-Gaba (mean log2 8.25, 96% detected, n=291); 144 MM Foxb1 Glut (mean log2 5.80, 83% detected, n=8,279); 143 MM-ant Foxb1 Glut (mean log2 5.40, 76% detected, n=5,451); 008 L2/3 IT ENT Glut (mean log2 4.86, 71% detected, n=21,111); 149 PVT-PT Ntrk1 Glut (mean log2 4.85, 76% detected, n=10,258); 043 OB-mi Frmd7 Gaba (mean log2 4.75, 64% detected, n=611); 150 CM-IAD-CL-PCN Sema5b Glut (mean log2 4.68, 72% detected, n=13,604); 021 L4 RSP-ACA Glut (mean log2 4.60, 75% detected, n=6,615)

**Grm3**: 319 Astro-TE NN (mean log2 10.34, 98% detected, n=154,311); 331 Peri NN (mean log2 10.20, 94% detected, n=24,907); 295 CBN Dmbx1 Gaba (mean log2 9.56, 100% detected, n=3,641); 310 CBX Golgi Gly-Gaba (mean log2 9.33, 100% detected, n=291); 327 Oligo NN (mean log2 8.87, 92% detected, n=422,574); 061 STR D1 Gaba (mean log2 8.38, 97% detected, n=36,287); 062 STR D2 Gaba (mean log2 8.33, 96% detected, n=36,963); 212 SCs Lef1 Gli3 Gaba (mean log2 8.29, 92% detected, n=2,140)

**Grm4**: 314 CB Granule Glut (mean log2 7.89, 86% detected, n=133,778); 147 AD Serpinb7 Glut (mean log2 6.80, 93% detected, n=720); 151 TH Prkcd Grin2c Glut (mean log2 6.01, 86% detected, n=68,480); 150 CM-IAD-CL-PCN Sema5b Glut (mean log2 6.00, 85% detected, n=13,604); 021 L4 RSP-ACA Glut (mean log2 5.54, 83% detected, n=6,615); 148 AV Col27a1 Glut (mean log2 5.31, 80% detected, n=7,531); 144 MM Foxb1 Glut (mean log2 5.30, 79% detected, n=8,279); 061 STR D1 Gaba (mean log2 5.05, 81% detected, n=36,287)

**Grm5**: 071 LSX Prdm12 Zeb2 Gaba (mean log2 11.74, 100% detected, n=6,587); 070 LSX Prdm12 Slit2 Gaba (mean log2 11.70, 100% detected, n=7,843); 069 LSX Nkx2-1 Gaba (mean log2 11.68, 100% detected, n=7,877); 258 SPVC Nmu Glut (mean log2 11.42, 100% detected, n=960); 062 STR D2 Gaba (mean log2 11.38, 100% detected, n=36,963); 061 STR D1 Gaba (mean log2 11.37, 100% detected, n=36,287); 068 LSX Otx2 Gaba (mean log2 11.36, 100% detected, n=4,379); 023 SUB-ProS Glut (mean log2 11.30, 100% detected, n=6,844)

**Grm6**: 204 SC Otx2 Gcnt4 Gaba (mean log2 0.30, 5% detected, n=1,036); 213 SCsg Gabrr2 Gaba (mean log2 0.14, 3% detected, n=15,799); 202 PRT Tcf7l2 Gaba (mean log2 0.03, 1% detected, n=5,714); 207 SCs Dmbx1 Gaba (mean log2 0.02, 0% detected, n=5,612); 214 IPN Otp Crisp1 Gaba (mean log2 0.02, 0% detected, n=3,087); 338 Lymphoid NN (mean log2 0.02, 0% detected, n=404); 296 RPA Pax6 Hoxb5 Gly-Gaba (mean log2 0.01, 0% detected, n=336); 252 DMX VII Tbx20 Chol (mean log2 0.01, 0% detected, n=339)

**Grm7**: 257 SPVC Ccdc172 Glut (mean log2 11.82, 100% detected, n=593); 144 MM Foxb1 Glut (mean log2 11.52, 100% detected, n=8,279); 110 BST-po Iigp1 Glut (mean log2 11.42, 100% detected, n=155); 269 LDT Fgf7 Gaba (mean log2 11.38, 100% detected, n=522); 258 SPVC Nmu Glut (mean log2 11.38, 100% detected, n=960); 067 LSX Sall3 Pax6 Gaba (mean log2 11.25, 100% detected, n=1,114); 207 SCs Dmbx1 Gaba (mean log2 11.16, 100% detected, n=5,612); 313 CBX Purkinje Gaba (mean log2 11.12, 100% detected, n=380)

**Grm8**: 315 DCO UBC Glut (mean log2 10.55, 100% detected, n=7,328); 111 TRS-BAC Sln Glut (mean log2 10.49, 98% detected, n=1,194); 064 STR-PAL Chst9 Gaba (mean log2 9.82, 98% detected, n=18,689); 235 PG-TRN-LRN Fat2 Glut (mean log2 9.76, 100% detected, n=3,894); 191 PAG-MRN Rln3 Gaba (mean log2 9.59, 99% detected, n=228); 110 BST-po Iigp1 Glut (mean log2 9.53, 99% detected, n=155); 188 SCop Sln Glut (mean log2 9.44, 99% detected, n=3,096); 269 LDT Fgf7 Gaba (mean log2 9.32, 98% detected, n=522)
