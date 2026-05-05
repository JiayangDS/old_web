---
layout: page
title: DINO-3DRA
description: >
  Leveraging 2D Foundation Model Semantics for 3D Cerebral Aneurysm Segmentation.
  MICCAI 2026 (Under Review) · +13% Dice over nnU-Net · 0% catastrophic failures.
img: assets/img/dino3dra_thumb.png
importance: 1
category: academic
# Uncomment and set once you have a dedicated project page deployed:
# redirect: /projects/dino-3dra-page/
---

## Overview

DINO-3DRA bridges frozen 2D Vision Foundation Model (DINOv3) semantics into a 3D U-Net
for cerebral aneurysm segmentation in 3D Rotational Angiography. Two lightweight modules
(Room-Lite Mixer + Calibrated Residual Fusion) add only **116K extra parameters** while
delivering **+13% Dice** and eliminating catastrophic failures on cross-dataset evaluation.

**Status:** Under review at MICCAI 2026.

## Key Results

| Dataset | Baseline Failures | DINO-3DRA Failures | Dice Improvement |
|---------|-------------------|--------------------|-----------------|
| CADA | 11.1% | **0%** | +3.9% |
| SHINY-ICARUS | 3.3% | **0%** | +7.5% |

## Links

- Paper: available after acceptance
- Code: [GitHub](https://github.com/JiayangDS/Dino3DRA)
- arXiv: available after submission
