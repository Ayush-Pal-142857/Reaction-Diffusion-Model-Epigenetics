# 🧬 Reaction–Diffusion Modeling of H3K9me2 Spreading in *S. pombe*

This repository implements a biologically motivated reaction–diffusion model to study the spatial propagation of the repressive histone modification H3K9me2 in *Schizosaccharomyces pombe* (fission yeast). The model quantitatively tests how nucleation sites, feedback-driven spreading, and turnover dynamics shape the steady-state methylation landscape, especially in wild-type (WT) and *leo1*Δ mutant backgrounds.

---

## 🧪 **Biological context**

- **H3K9me2** is a hallmark of heterochromatin, restricting gene expression in specific genomic regions.
- In *leo1*Δ mutants, impaired turnover of H3K9me2 leads to ectopic spreading into normally euchromatic domains.
- We integrate:
  - ChIP-seq data from Sadeghi et al. (2015): genome-wide H3K9me2 profiles.
  - Hi-C data from Mizuguchi et al. (2014): 3D chromatin globules that act as boundaries.

This computational framework models how local nucleation, reader–writer feedback, and turnover jointly explain observed methylation patterns.

---

## ⚙ **Model overview**

We simulate the evolution of methylation density \( m(x,t) \) over genomic position \( x \) using the PDE:

dm/dt = D * d²m/dx² + α(x) + β * m^n / (K^n + m^n) - γ * m
Where:

- D : effective diffusion coefficient (spreading)
- α(x) : spatially localized nucleation sources (triangular peaks + baseline)
- β, K, n : parameters of the feedback-driven Hill function
- γ : turnover rate, representing removal of H3K9me2

---

## 📊 **Data & parameters**

| Dataset | Genomic region modeled | Reference |
|-------|------------------------|-----------|
| ChIP-seq (WT and *leo1*Δ) | Chr II, 1.15–1.20 Mb | Sadeghi et al. (2015) |
| Hi-C globule | Chr II, 1.15–1.20 Mb | Mizuguchi et al. (2014) |

- Baseline nucleation rates and peak positions/strengths are extracted directly from ChIP-seq `.wig` files.
- See `peaks_info` in the code for precise peak locations and heights.

---

## 🚀 **How to run**

```bash
python reaction_diffusion_fit.py
