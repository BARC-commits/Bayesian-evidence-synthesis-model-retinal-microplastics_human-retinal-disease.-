# Bayesian-evidence-synthesis-model-retinal-microplastics_human-retinal-disease.-
Bayesian evidence synthesis model assessing whether retinal microplastics cause human retinal disease. Includes Monte Carlo uncertainty propagation, sensitivity analyses, and publication-ready figures.

# Bayesian Evidence Synthesis: Retinal Microplastics and Disease Causality

[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![DOI](https://img.shields.io/badge/DOI-10.1016%2Fj.biosystems.2025.105502-blue)](https://doi.org/10.1016/j.biosystems.2025.105502)

Companion code for the paper:

> **"From Detection to Disease: A Bayesian Evidence Synthesis Assessing the Causal Role of Retinal Microplastics in Human Retinal Pathology"**

---

## Overview

The recent confirmation of microplastics (MPs) in human retinal tissue at a mean concentration of 49.21 μg/g (Zhang et al., 2025) answers the question "are they there?" but leaves open the clinically urgent question: **"do they cause disease?"**

This repository implements a **Bayesian evidence synthesis model** that formally quantifies the probability that retinal microplastics are a contributing cause of retinal pathology. Starting from a deliberately skeptical prior of 10%, the model sequentially updates this probability using four independent streams of evidence:

| Evidence Node | Description | Likelihood Ratio |
|---------------|-------------|------------------|
| E₁ | MPs detected in human retina | 1.19 |
| E₂ | Convergent mechanistic toxicology (in vitro/in vivo) | 3.60 |
| E₃ | Absence of direct human epidemiological data | 0.74 |
| E₄ | Hyperreflective foci (HRF) are established biomarkers of retinal disease | 1.12 |

The model demonstrates that current evidence raises the probability of causality from 10% to approximately **28%** (95% credible interval: 12–51%), with mechanistic toxicology as the dominant driver.

---

## Key Features

- **Full Bayesian model** with sequential evidence updating in odds form
- **Monte Carlo uncertainty propagation** (100,000 simulations) using Beta-distributed conditional probabilities
- **Comprehensive sensitivity analyses:**
  - Prior probability variation (1%–50%)
  - Mechanistic LR variation (1.0–10.0)
  - Evidence dependence adjustment
  - Tornado plot with empirical LR ranges from Monte Carlo
- **Four publication-quality figures:**
  1. Stepwise posterior update (waterfall bar chart)
  2. Tornado plot (empirical LR ranges, 2.5th–97.5th percentiles)
  3. Sensitivity heatmap (prior × mechanistic LR)
  4. Monte Carlo posterior distribution (histogram, CDF, LR boxplots, total LR)
- **CSV export** of all results for downstream analysis

---

## Background

### Scientific Context

- **Kah (2025)** first hypothesized that retinal hyperreflective foci might contain micro(nano)plastics, proposing a Bayesian framework for detection.
- **Zhang et al. (2025)** confirmed MPs in 12/12 post-mortem human retinal samples, identifying PS, PE, PP, PMMA, and PVC.
- **This work** extends the Bayesian approach from detection to *causation*, integrating toxicology, clinical imaging biomarkers, and the absence of epidemiological data.

### Why Bayesian?

Traditional null-hypothesis significance testing cannot integrate fragmented, multi-source evidence of the kind available for emerging environmental health questions. Bayesian inference:
- Quantifies *degree of belief* on a continuous probability scale
- Makes all assumptions explicit and debatable
- Naturally updates as new evidence emerges
- Identifies which future studies would most efficiently resolve remaining uncertainty

---

## Installation & Requirements

### Dependencies

The code requires only standard scientific Python libraries:

```bash
numpy>=1.21.0
pandas>=1.3.0
matplotlib>=3.5.0
seaborn>=0.11.0
scipy>=1.7.0
