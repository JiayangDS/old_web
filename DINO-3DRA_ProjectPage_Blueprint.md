# DINO-3DRA Project Page Blueprint

**MICCAI 2026**

## DINO-3DRA
### Leveraging 2D Foundation Model Semantics for 3D Cerebral Aneurysm Segmentation

Author A, Author B, Author C  
Anonymized Affiliations

[📄 Paper] [💻 GitHub] [📦 arXiv]

---

> We transfer **frozen 2D VFM semantics** into a 3D U-Net via slice-level embeddings, depth-coherence restoration, and calibrated residual fusion — achieving **+13% Dice** over nnU-Net with only **116K extra parameters** and **zero catastrophic failures** on cross-dataset evaluation.

---

**[Fig. 1 — Architecture overview: place `dino3dra_fig1.png` here]**

> **Fig. 1.** (a) Frozen DINOv3-Small extracts per-slice semantic embeddings. (b) Multi-scale features are refined by Room-Lite Mixers and fused into U-Net skip connections via Calibrated Fusion.

Automated detection in 3D rotational angiography is extremely challenging. 2D VFMs know what anatomical structures look like but can't work in 3D; we build two cheap modules that safely bridge that knowledge into a 3D U-Net — the first framework where frozen 2D features genuinely improve volumetric medical segmentation instead of degrading it.

---

## The Challenge

**Ambiguity:** On a single 2D slice, vessels and aneurysms look identical — both are white parts on black. Only tracking shape across depth separates them.

**The 2D–3D gap:** 2D VFMs encode rich priors from 1.7B images. No 3D equivalent exists. But naïvely injecting 2D features into 3D models makes performance *worse* than no 2D features at all.

**Prior approaches fail:** Inflating 2D kernels destroys inter-slice continuity. Late concatenation ignores the distribution gap. Full spatial token propagation is memory prohibitive. No existing method addresses all three.

**[Fig. 2 — 3D rotational angiography rotation `sample.gif`. Left: label / Right: sample image]**

---

## Method

A frozen 2D VFM provides *what* each slice contains. A trainable 3D U-Net provides *where* structures are. Two lightweight modules bridge the gap:

### 1 — Slice-Level Semantic Extraction

Each axial slice processed by frozen DINOv3-Small. 196 patch tokens mean-pooled to one 384-dim embedding per slice. Per-slice embeddings projected via 1×1 convolutions, reshaped into 3D volumes at three U-Net skip scales.

### 2 — Room-Lite Depth Coherence

Learnable depth bias `B(z)` + depthwise-separable 3D conv restore inter-slice continuity. **21K params total.**

```
Y = X + GELU(GN(Conv₁₁(Conv₃₃(X + B(z)))))
```

### 3 — Calibrated Residual Fusion

GroupNorm aligns DINO to U-Net statistics. Residual bypass: if DINO is unhelpful, W → 0 and output is pure U-Net.

```
F_fused = F_U + GELU(GN(W[F_U; GN(F_D)]))
```

---

## Key Results

Four of five DINO variants fall *below* the plain U-Net baseline. Only the full pipeline surpasses it.

**[Fig. 3 — Interactive visualization in ablation study group: `dino3dra_fig3.html`]**

---

## Cross-Dataset Generalisation

Evaluated on two external datasets without fine-tuning. DINO-3DRA eliminates all catastrophic failures (Dice < 0.5).

| **11.1% → 0%** FAILURES ON CADA | **3.3% → 0%** FAILURES ON SHINY-ICARUS | **75.8%** HD95 REDUCTION (SI) |
|----------------------------------|----------------------------------------|-------------------------------|

| **Dataset** | **Model**       | **Dice**         | **Jaccard**      | **Vol. Sim.**    | **HD95** | **Failures** |
|-------------|-----------------|------------------|------------------|------------------|----------|--------------|
| CADA        | Baseline        | 0.711 ± 0.186    | 0.577 ± 0.186    | 0.813 ± 0.128    | 5.16     | 11.1%        |
| CADA        | **DINO-3DRA**   | **0.739 ± 0.093**| **0.594 ± 0.118**| 0.807 ± 0.109    | **3.58** | **0%**       |
| SI          | Baseline        | 0.718 ± 0.147    | 0.574 ± 0.129    | 0.808 ± 0.089    | 15.52    | 3.3%         |
| SI          | **DINO-3DRA**   | **0.793 ± 0.049**| **0.660 ± 0.065**| 0.812 ± 0.056    | **3.76** | **0%**       |

**[Fig. 4 — Cross-dataset visual comparison. CADA (left), SHINY-ICARUS (right). Blue: vessel, Red: aneurysm.]**

---

## Limitations & Future Work

> ⚠️ **KNOWN LIMITATIONS** — DINO-3DRA under-segments large or atypical aneurysms due to:
> 1. Training data bias toward saccular morphologies — fusiform or multilobular shapes are partially classified as vessel extensions.
> 2. Patch boundary effects — aneurysms exceeding the 64³ input span multiple patches, producing discontinuities at edges.
>
> **Future work:** knowledge distillation for deployment, diverse morphology training, and multi-centre validation at scale.

> 📄 **FOR DETAILS** — See the full paper for complete ablation analysis, per-case breakdowns, training protocol, and implementation details.

---

## BibTeX

```bibtex
@inproceedings{dino3dra2026,
  title     = {DINO-3DRA: Leveraging 2D Foundation Model
               Semantics for 3D Cerebral Aneurysm Segmentation},
  author    = {Anonymized Authors},
  booktitle = {MICCAI},
  year      = {2026}
}
```

---

*Built using the Academic Project Page Template.*
