# Unbiased look at mGluR co-expression (by receptor pair) across the whole ABA dataset

Figures for each step of the all-pairs analysis. Tables: `results/allen_wmb/allpairs/`. Back to the [main README](../../../README.md).

## 1. Stringency

Units (subclass x region) passing as the shared cutoff rises, one line per receptor pair.

<img src="GRM_ALLPAIRS_1_stringency.png" width="800">

## 2. Top hits at the highest cutoff

Cell types with the highest % of cells co-expressing two receptors, with observed/expected and the weaker-receptor median.

<img src="GRM_ALLPAIRS_2_top_hits.png" width="800">

## 3. All 8 x 8 pairs

Best unit per pair (color) and the number of passing units (number).

<img src="GRM_ALLPAIRS_3_pair_heatmap.png" width="800">

## 5. Region discordance

Same subclass, different regions: lowest vs highest % co-expressing.

<img src="GRM_ALLPAIRS_5_region_discordance.png" width="800">

## 6. Threshold sanity check

Where the three cutoffs fall in the distribution of subclass x region mean expression.

<img src="GRM_ALLPAIRS_6_threshold_sanity.png" width="800">

## 7. Receptor 1 vs receptor 2 expression

Every passing cell type x pair; top 15 labeled.

<img src="GRM_ALLPAIRS_7_receptor_expression_scatter.png" width="800">

## 4. Cell type x region dot plots (top pairs)

Rows = subclasses, columns = regions (* = focus), color = % co-expressing, size = cells; last column = regions passing.

<img src="GRM_ALLPAIRS_4_dotplot_Grm1_Grm5.png" width="800">

<img src="GRM_ALLPAIRS_4_dotplot_Grm1_Grm7.png" width="800">

<img src="GRM_ALLPAIRS_4_dotplot_Grm5_Grm7.png" width="800">

<img src="GRM_ALLPAIRS_4_dotplot_Grm5_Grm8.png" width="800">
