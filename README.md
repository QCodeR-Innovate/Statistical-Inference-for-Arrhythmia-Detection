# Statistical Inference for Arrhythmia Detection: Fundamental Limits of Univariate Representations

[![Author](https://img.shields.io/badge/Author-Pushkar%20Chaturvedy-blue.svg)](https://github.com/QCodeR-Innovate)
[![Institution](https://img.shields.io/badge/Institution-IIT%20Kharagpur-gray.svg)]()
[![Dataset](https://img.shields.io/badge/Dataset-MIT--BIH%20Arrhythmia-green.svg)](https://www.kaggle.com/datasets/shayanfazeli/heartbeat)

### Project Overview
Consumer smartwatches rely on computationally expensive deep learning models for continuous cardiac monitoring. This project addresses a fundamental engineering question: **Can a computationally trivial scalar summary of an ECG waveform (total signal energy) serve as a reliable "tripwire" for severe arrhythmias?** 

Through a rigorous statistical inference pipeline, this project demonstrates that scalar energy statistics are fundamentally insufficient for clinical-grade ECG monitoring. It provides a mathematical justification for the necessity of higher-dimensional signal processing architectures in low-power embedded devices, moving beyond empirical observation into formal informational theory.

---

### Methodology
* **Parametric Modeling:** We model the scalar energy $X_i = \|a_i\|_2^2$ using a Regular Exponential Family (**Gamma Distribution**).
* **Estimation:** Implementation of numerical Maximum Likelihood Estimation (MLE) for $(\alpha, \beta)$, verified by the Fisher Information Matrix and the **Cramér-Rao Lower Bound (CRLB)**.
* **Optimal Testing:** Derivation of the **Uniformly Most Powerful (UMP)** threshold test via the **Neyman-Pearson Lemma** and verification of the Monotone Likelihood Ratio (MLR) property.
* **Information Limits:** Certification of discriminative power via **Kullback-Leibler Divergence** and the **Data Processing Inequality**.

---

### Key Findings
* **Optimal Threshold ($k^*$):** $32.82$ energy units (at $\alpha = 0.05$).
* **Statistical Power:** **$22.99\%$** | **Type II Error (Miss Rate):** **$77.01\%$**.
* **Divergence:** $KL(H_1 \parallel H_0) = 0.3919$ nats.

**Conclusion:** The optimal scalar-energy detector misses $\approx 77\%$ of genuine PVC events. This failure is a structural theorem: the mapping to a scalar norm irreversibly destroys the phase and morphological signatures essential for reliable arrhythmia classification.

---

### Repository Access
* 📄 **[Project Document / Research Report](./Project_Report.pdf)**
  * Full theoretical breakdown, mathematical proofs, and literature context.
* 💻 **[Python Inference Notebook](./Inference_Pipeline.ipynb)**
  * Reproducible code: Kaggle ingestion, numerical MLE optimization, Fisher Information calculation, and hypothesis testing visualizations.
