# 🧬 WIG Peak Detection and Methylation Profiling (ChIP-seq)

Python script to analyze ChIP-seq methylation data stored in WIG (Wiggle) files for wild type (WT) and leo1Δ mutants.
The script detects genomic peak regions, computes baselines, identifies the exact WT peak inside the triangular domain, and visualizes the profiles.

> ⚠ **Note:** This workflow is tailored for genome-wide ChIP-seq methylation or histone modification data saved in WIG format.

## 📦 Features
- Parses compressed `.wig.gz` files by chromosome
- Interpolates and normalizes methylation signals
- Computes flat-region baselines for WT and leo1Δ
- Identifies:
  - WT triangular peak region (above baseline + tolerance)
  - Exact WT peak coordinate inside triangle
  - leo1Δ peak regions above baseline + tolerance, and their exact peaks
- Generates publication-ready plots with peaks and shaded regions

## 🧰 Requirements
- Python 3.7+
- numpy
- pandas
- matplotlib
- scipy
- google.colab (if running in Google Colab)

Install dependencies (if needed):
```bash
pip install numpy pandas matplotlib scipy
