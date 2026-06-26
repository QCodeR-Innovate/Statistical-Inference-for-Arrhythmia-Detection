# Statistical Inference for Arrhythmia Detection: Fundamental Limits of Univariate Representations

[![Author](https://img.shields.io/badge/Author-Pushkar%20Chaturvedy-blue.svg)](https://github.com/QCodeR-Innovate)
[![Institution](https://img.shields.io/badge/Institution-IIT%20Kharagpur-gray.svg)]()
[![Dataset](https://img.shields.io/badge/Dataset-MIT--BIH%20Arrhythmia-green.svg)](https://www.kaggle.com/datasets/shayanfazeli/heartbeat)

**TL;DR:** Consumer smartwatches rely on computationally expensive deep learning models for continuous cardiac monitoring. This project asks a fundamental engineering question: *Can a computationally trivial scalar summary of an ECG waveform (total signal energy) serve as a reliable "tripwire" for severe arrhythmias?* Through a complete classical statistical inference pipeline, this repository provides a mathematically rigorous **negative answer**, formally proving why high-dimensional representations are an information-theoretic necessity for edge-device diagnostics.

---

## 📊 The Core Concept

Instead of processing a full 187-dimensional ECG amplitude vector $a_i$, we reduce the data to a single scalar representing total signal energy via Parseval's theorem:

$$X_i = \|a_i\|_2^2 = \sum_{j=1}^{187} a_{ij}^2$$

Using the **MIT-BIH Arrhythmia Dataset**, we model this scalar energy under two hypotheses using a Regular Exponential Family (the Gamma distribution):
* **$H_0$:** Normal Sinus Rhythm
* **$H_1$:** Premature Ventricular Contraction (PVC) Arrhythmia

We establish joint sufficiency, compute Maximum Likelihood Estimates (MLE) via Newton-Raphson, and verify the Cramér-Rao Lower Bound (CRLB). Finally, we derive the **Uniformly Most Powerful (UMP) threshold test** using the Neyman-Pearson Lemma.

---

## 🔬 Key Findings

Even when operating at the absolute theoretical limit of statistical efficiency, the scalar energy feature fails clinically:

* **Optimal Threshold ($k^*$):** $32.82$ energy units (at a strict hardware false-alarm constraint of $\alpha = 0.05$).
* **Statistical Power:** **$22.99\%$** * **Type II Error (Miss Rate):** **$77.01\%$**
* **KL Divergence:** $KL(H_1 \parallel H_0) = 0.3919$ nats.

**Conclusion:** The optimal test misses $\approx 77\%$ of genuine PVC events. By the **Data Processing Inequality**, the mapping $a \to \|a\|_2^2$ irreversibly destroys vital morphological data (phase, QRS width). This mathematically justifies the computational cost of higher-dimensional neural architectures in modern wearable tech.

---

## 📂 Repository Files

This project is contained entirely within two main files. No complex environments or nested directories required.

1. 📄 **[Project Document / Research Report](./Project_Report.pdf)**
   * Read this for the full theoretical breakdown, including mathematical proofs for Sufficiency, the Monotone Likelihood Ratio (MLR), and the exact closed-form KL divergence.
   
2. 💻 **[Python Inference Notebook](./Inference_Pipeline.ipynb)**
   * The complete, reproducible codebase. It handles Kaggle data ingestion, numerical MLE optimization, Fisher Information Matrix calculation, and hypothesis testing visualizations.
