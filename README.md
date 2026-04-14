# Macrophage Innate Immune Memory – RNA-seq Analysis

Exploratory RNA-seq analysis investigating innate immune memory in macrophages,
comparing PBS-trained (y0) and IFNy-trained (y100) cells across an LPS stimulation timecourse.

## Experiment
Macrophages were pre-trained with either PBS (control) or IFNy (mimicking prior infection),
then all cells were challenged with LPS as a secondary stimulus and sampled at 0, 1, 3, 6,
and 12 hours post-stimulation.

## Analysis Pipeline
- **Preprocessing** – count filtering (median percentile + minimum count thresholds) and
  CPM normalization via edgeR
- **Gene ID Mapping** – Ensembl → HGNC symbol conversion with biomaRt
- **PCA** – dimensionality reduction across all genes and top 5,000 most variable genes
- **Timecourse Visualization** – per-gene CPM lineplots across LPS timepoints for y0 vs y100
- **Potentiated Gene Identification** – three methods for defining genes with stronger
  response in IFNy-trained cells:
  1. ≥2x CPM in at least one timepoint
  2. ≥2x CPM at each condition's peak timepoint
  3. ≥2x CPM in at least 2 consecutive timepoints

## Key Packages
`edgeR` · `biomaRt` · `ggplot2` · `ggrepel`

## Data
Input: `gene_counts.tsv` — raw gene-level counts (featureCounts output, Ensembl gene IDs)

## Authors
Vyas Koduvayur · Libby Li
