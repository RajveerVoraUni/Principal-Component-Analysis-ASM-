# Principal Component Analysis (PCA) - Project Report

**A comprehensive exploration of Principal Component Analysis for dimensionality reduction, visualisation, and image compression.**

![PCA Cover](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTpDt1Lpeh_CDFi60ODxRE3Tx4sVuuNpzVtllGWwccN-5JAJEkcYVQVL-0&s=10) <!-- Replace with actual screenshot if available -->

## 📋 Overview

This project presents a **self-contained treatment** of Principal Component Analysis (PCA), one of the most fundamental techniques in multivariate statistics and machine learning. The report covers the mathematical foundations, practical implementation considerations, and real-world applications on two classic datasets:

- **Fisher Iris Dataset**: Dimensionality reduction and species visualisation.
- **ZIP Handwritten-Digit Dataset** ("3"s): High-dimensional image compression and reconstruction.

The work demonstrates PCA's power in addressing the **curse of dimensionality**, variance maximisation, orthogonal transformations, and its dual role in data compression and denoising.

**Date**: 30 April 2026  
**Authors**: 
- Aklanta Borah (BSD-CC-2404)
- Amartya Amritanshu (BSD-CC-2405)
- Rajveer Vora (BSD-CC-2416)
- Somesh Biswas (BSD-CC-2420)

---

## Key Features

- Rigorous mathematical derivation from first principles (variance maximisation → eigenvalue problem).
- Geometric interpretation as an orthogonal rotation.
- Practical guidance on scaling, choosing number of components, and diagnostics (scree plot, correlation circle).
- Two complete worked examples with interpretation.
- Image reconstruction using low-rank approximation (Eckart–Young–Mirsky theorem).
- Clean R implementation with reproducible code.

---

## Introduction

Modern datasets are increasingly high-dimensional. PCA addresses key challenges:
- **Redundancy** from correlated variables
- **Noise** in high-dimensional spaces
- **Computational inefficiency** and visualisation difficulties

PCA constructs uncorrelated principal components ordered by captured variance, enabling effective dimensionality reduction while preserving as much information as possible.

---

## Mathematical Derivation

The report derives PCA step-by-step:

- **First Principal Component**: Maximise `Var(δᵀX)` subject to `||δ|| = 1`
- Solution via Lagrange multipliers leads to the **eigenvalue equation** `Σδ = λδ`
- Subsequent components are orthogonal eigenvectors
- Full transformation: `Y = Γᵀ(X - μ)`
- Properties: Uncorrelated components, total variance preserved, variance ordering

**Geometric View**: Rigid rotation aligning axes with directions of maximum spread.

---

## Practical Implementation

- Sample covariance matrix estimation
- Importance of **standardisation** (correlation vs covariance matrix)
- Choosing `q` components:
  - Cumulative variance threshold (80-95%)
  - Scree plot "elbow"
  - Kaiser rule

---

## Fisher Iris Dataset

**Dataset**: 150 samples, 4 features (sepal/petal length & width), 3 species.

**Results**:
- PC1 explains **92%** variance (overall size, dominated by petal measurements)
- First two PCs explain **97%** variance
- Clear species separation in 2D projection
- Detailed loadings and correlation circle analysis

---

## ZIP Handwritten-Digit Dataset (Image Compression)

**Dataset**: 650 images of handwritten "3" (16×16 pixels → 256 dimensions).

**Key Achievements**:

| Components (q) | Variance Explained | Compression Ratio |
|----------------|--------------------|-------------------|
| 1              | ~40%               | 256:1             |
| 5              | ~70%               | 51:1              |
| **10**         | **~83%**           | **26:1**          |
| 20             | ~92%               | 13:1              |
| 50             | ~98%               | 5:1               |

**Reconstruction**:
- Uses low-rank approximation: `X̂(q) = 1μᵀ + Y(q)G(q)ᵀ`
- Eigendigits visualise dominant stroke patterns
- Excellent reconstruction quality with only ~4% of original features

**Figure 1**: Side-by-side comparison of original vs reconstructed digits (highly legible after denoising).

---

## R Implementation

Reproducible code is included in the report
