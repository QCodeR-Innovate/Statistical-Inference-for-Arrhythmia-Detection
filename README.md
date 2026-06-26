
# Statistical Inference for Arrhythmia Detection: Fundamental Limits of Univariate Representations

[![Author](https://img.shields.io/badge/Author-Pushkar%20Chaturvedy-blue.svg)](https://github.com/QCodeR-Innovate)
[![Institution](https://img.shields.io/badge/Institution-IIT%20Kharagpur-gray.svg)]()
[![Dataset](https://img.shields.io/badge/Dataset-MIT--BIH%20Arrhythmia-green.svg)](https://www.kaggle.com/datasets/shayanfazeli/heartbeat)

---

A rigorous statistical inference study of scalar ECG representations for arrhythmia detection. This project investigates the fundamental informational limits of using total signal energy as a univariate representation, employing Gamma-family parametric modeling, Maximum Likelihood Estimation, Neyman-Pearson optimal hypothesis testing, and information-theoretic analysis to determine whether computationally inexpensive scalar statistics can reliably detect cardiac abnormalities.

---

## Project Overview

Consumer smartwatches and wearable cardiac monitors often operate under severe computational and power constraints, motivating the search for lightweight screening algorithms. This project investigates a fundamental engineering question:

> **Can a computationally trivial scalar summary of an ECG waveform (total signal energy) serve as a reliable "tripwire" for severe arrhythmias?**

Rather than proposing another machine learning classifier, this work studies the problem from the perspective of **classical statistical inference**. By constructing a complete inference pipeline—from probabilistic modeling and parameter estimation to optimal hypothesis testing and information-theoretic analysis—it demonstrates that scalar energy statistics are fundamentally insufficient for clinical-grade ECG monitoring.

The resulting conclusion is not merely empirical, but mathematical: compressing an ECG waveform into a single energy value irreversibly discards the morphological and temporal information required for reliable arrhythmia detection, thereby justifying the need for higher-dimensional signal representations in embedded healthcare systems.

---

## Methodology

- **Parametric Modeling:** Model the scalar energy
  \[
  X_i = \|a_i\|_2^2
  \]
  using a Regular Exponential Family (**Gamma Distribution**).

- **Estimation:** Numerical Maximum Likelihood Estimation (MLE) of the Gamma parameters \((\alpha,\beta)\), verified using the Fisher Information Matrix and the **Cramér-Rao Lower Bound (CRLB)**.

- **Optimal Hypothesis Testing:** Derivation of the **Uniformly Most Powerful (UMP)** detector through the **Neyman-Pearson Lemma**, with verification of the Monotone Likelihood Ratio (MLR) property.

- **Information-Theoretic Analysis:** Quantification of discriminative power using **Kullback-Leibler Divergence**, interpreted through the **Data Processing Inequality** to establish the theoretical limits of scalar representations.

---

## Key Findings

- **Optimal Threshold (\(k^*\))**: **32.82** energy units (\(\alpha = 0.05\))
- **Statistical Power:** **22.99%**
- **Type II Error (Miss Rate):** **77.01%**
- **KL Divergence:** **0.3919 nats**

### Conclusion

Even under the statistically optimal Neyman-Pearson detector, a scalar-energy classifier fails to identify approximately **77% of genuine PVC events**.

This is not merely a limitation of a particular model or dataset—it is a structural consequence of dimensionality reduction. Mapping an ECG waveform to a single scalar norm irreversibly destroys the phase and morphological signatures necessary for robust arrhythmia classification. Consequently, clinically reliable detection requires richer feature representations or higher-dimensional inference architectures.

---

## Repository Access

### 📄 Project Report

**[`Project_Report.pdf`](./Statistical_Inference_PROJECT.pdf)**

A complete research report containing:

- Mathematical derivations
- Statistical proofs
- Theoretical background
- Experimental methodology
- Discussion of results
- Literature review

---

### 💻 Python Inference Pipeline

**[`Inference_Pipeline.ipynb`](./Statistical_Inference_PROJECT.ipynb)**

A fully reproducible implementation including:

- MIT-BIH dataset ingestion
- Signal preprocessing
- Numerical MLE optimization
- Fisher Information computation
- CRLB verification
- Neyman-Pearson hypothesis testing
- ROC and decision-threshold visualization
- Information-theoretic analysis

---

## Repository Philosophy

This repository is intended to serve both as a reproducible implementation and as a self-contained technical document. The accompanying report develops the theoretical foundations, while the notebook provides an end-to-end computational realization of every major statistical result.

Together, they demonstrate not only *how* the inference pipeline is implemented, but also *why* the resulting performance limitations arise from fundamental principles of statistical decision theory and information theory.

