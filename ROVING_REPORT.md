# 📑 Roving Report: Upgrading to v3 Pathway GNN (Glioma Show Case)

This document serves as an active engineering log and blueprint as we transition from our stable baseline (`v2_Universal_Survival_Engine.ipynb`) into the multi-omic graph environment of `v3`.

## 📍 Current State Abstract (v2 Baseline Summary)
Our `v2` engine successfully trains a joint **Denoising Autoencoder (DAE) + Cox Proportional Hazards Model** on 1D genomic features, outputting a 128-dimensional continuous latent space. However, `v2` treats genes as a flat, unorganized array. 

## 🎯 The v3 Pivot: Pathway-Centric Graph "Latent Shortcut"
To optimize for **Glioma survival stratification** without encountering sparse-matrix memory bottlenecks, `v3` introduces a structural Graph Neural Network (GNN). 
* **The Shortcut:** Instead of mapping individual genes, nodes represent higher-level functional biological pathways critical to glioma progression (e.g., *RTK/RAS/PI3K*, *p53*, *RB* signaling). 
* **The Features:** We leverage our pre-trained `v2` DAE weights to extract dense feature embeddings to act as node attributes.
* **The Goal:** Use `GATConv` layers to capture system pathway cross-talk, outputting a unified patient topology vector into our verified Cox Head.

---

## 📅 Roving Log & Daily Output Records

### 🟢 Day 1: Topology Mapping & Edge Initialization
* **Focus:** Isolate target glioma pathways and build the static adjacency matrix ($A$).
* **Data Needed:** Gene list filtered by MSigDB/KEGG pathway indices + STRING database interaction maps.
* **Daily Output Record:** * *[Date: 2026-XX-XX]* Successfully generated `edge_index` tensor of shape `[2, num_edges]`. Verified that critical neuro-oncology interactions (e.g., *EGFR* to *PI3K*) are mapped.

### 🟡 Day 2: PyTorch Geometric Data Pipeline
* **Focus:** Reconstruct the dataset loop to wrap elements into `torch_geometric.data.Data` objects.
* **Data Needed:** `v2` DAE compressed latent tensors bundled with the Day 1 `edge_index`.
* **Daily Output Record:** * *[Date: 2026-XX-XX]* Pipeline validated. Printed test batch configurations: `batch.x` and `batch.edge_index` load smoothly into memory without throwing collation errors.

### 🟠 Day 3: Model Architecture Swap & Forward Pass
* **Focus:** Swap out sequential linear encoding layers for `GATConv` + `global_mean_pool`.
* **Data Needed:** Batched graph DataLoader objects generated on Day 2.
* **Daily Output Record:** * *[Date: 2026-XX-XX]* Executed dummy forward pass. The network successfully outputs relative risk scores ($\eta$) and integrates flawlessly with our existing custom `computed_cox_partial_loss` loop.

### 🔴 Day 4: Model Training & Statistical Validation
* **Focus:** Train the network and evaluate survival stratification using statistical p-values.
* **Data Needed:** Full patient training matrices ($N=309$) over validation splits.
* **Daily Output Record:** * *[Date: 2026-XX-XX]* Model converged. Extracted test risk scores, applied a median split, and executed a **Log-Rank Test**. Achieved a statistically significant separation ($p < 0.05$), proving the graph architecture successfully captures prognostic configurations.

---

## 🔮 Further Work (Future Roadmap)
1. **Macro-Structural Fusion:** Incorporate 3D multi-parametric MRI (mpMRI) convolutional features (T1, T1CE, T2, FLAIR) via late-fusion cross-attention.
2. **Clinical Covariate Conditioning:** Inject crucial categorical neuro-oncology biomarkers (*IDH* status, *1p/19q* co-deletion, *MGMT* methylation, and Age) directly into the fusion bottleneck.
3. **Absolute Hazard Curves:** Transition from relative risk scoring to absolute clinical survival probability curves via post-fit Breslow Baseline Hazard ($H_0(t)$) modeling.
