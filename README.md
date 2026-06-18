# Glioma Multi-Task & Multi-Modal Survival Engine

A deep learning framework engineered to predict prognostic risk trajectories for Glioma patients by mapping high-dimensional, multi-modal genomic data directly to clinically validated biological knowledge graphs. 

This project charts the evolution from flat feature-level concatenation to structurally-informed, graph-fused clinical prediction.

---

## 🎯 Project Overview & Evolutionary Milestones

Biomedical datasets suffer from extreme feature noise and high dimensionality. This engine solves those bottlenecks across distinct development phases:

1. **Unsupervised Latent Embeddings (Phase 2):** Trained a custom Denoising Autoencoder (DAE) to extract clean, compressed molecular features without relying on survival labels.
2. **Tabular Benchmarking Baseline (Phase 3 Tabular):** Designed a regularized Deep vs. Shallow supervised framework utilizing a Cox Partial Likelihood objective head.
3. **Advanced Pathway Graph Fusion (Phase 3 Advanced - Staging):** Implementing a custom PyTorch collation engine that dynamically slices flat patient feature matrices into functional biological pathways and directed signal cross-talk maps.

---

## 📂 Repository Architecture

```text
📁 Glioma-MultiTask-Survival/
│
├── 📝 README.md                         <-- You are here (Project Homepage)
│
└── 📁 v3_pathway_graph_fusion/          <-- Main Phase 3 Workspace
    ├── 📝 v3_tabular_experiments.md     <-- Deep benchmarking report & math details
    │
    ├── 📁 notebooks/
    │   └── v3_1_Universal_Graph_Engine.ipynb <-- Master code execution engine
    │
    └── 📁 survival_plots/               <-- Generated predictive visual assets
        └── architectural_comparison_dashboard.png
        return predicted_hazards.cpu().numpy()
