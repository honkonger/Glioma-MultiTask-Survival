# Phase 3: Pathway-Aware Graph Fusion Survival Engine

A deep learning framework designed to predict patient survival risk by integrating multi-modal genomic data (Transcriptomics, CNV, Methylation) with biological knowledge graphs. 

This engine transitions from generic feature concatenation to structurally-informed clinical prediction.

## 🚀 Key Project Milestones
* **Unsupervised Latent Space (V2 Base):** Leveraged a Denoising Autoencoder (DAE) to extract clean, low-dimensional molecular embeddings from noisy data.
* **Deep Tabular Benchmarking (V3 Baseline):** Evaluated deep vs. shallow architectures to establish a regularized baseline performance (Top C-Index: `0.56`).
* **Graph-Aware Slicing Matrix (Staging Advanced):** Engineered a custom PyTorch dataset to dynamically slice patient vectors into functional biological pathways.

---

## 📂 Repository Architecture & Reports
To make this framework highly reproducible, the engineering journey is broken down into structured reports:

* 🔬 **[Deep Tabular Performance & Slicing Report](v3_tabular_experiments.md)**: Look here for a full analysis of the deep vs. shallow baseline comparison, performance tables, and the technical breakdown of our structural pathway slicing code (Cells 2-4).
* 🧪 **`notebooks/v3_1_Universal_Graph_Engine.ipynb`**: The master execution notebook containing data preparation, neural network construction, training loops, and evaluation metrics.
* 📊 **`survival_plots/`**: Directory containing generated validation and clinical testing Kaplan-Meier curves mapping cohort risk separation over time.

---

## 🛠️ Local Installation & Quickstart
Ensure you have `torch`, `lifelines`, and standard plotting libraries installed on your PC:

```bash
pip install torch lifelines matplotlib numpy
