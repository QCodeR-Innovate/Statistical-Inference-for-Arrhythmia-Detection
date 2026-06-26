# Statistical Inference for Arrhythmia Detection: Fundamental Limits of Univariate Representations

[![Author](https://img.shields.io/badge/Author-Pushkar%20Chaturvedy-blue.svg)](https://github.com/QCodeR-Innovate)
[![Institution](https://img.shields.io/badge/Institution-IIT%20Kharagpur-gray.svg)]()
[![Dataset](https://img.shields.io/badge/Dataset-MIT--BIH%20Arrhythmia-green.svg)](https://www.kaggle.com/datasets/shayanfazeli/heartbeat)

---

A rigorous statistical inference study of scalar ECG representations for arrhythmia detection. This project investigates the fundamental informational limits of using **total signal energy** as a univariate representation, employing Gamma-family parametric modeling, Maximum Likelihood Estimation, Neyman-Pearson optimal hypothesis testing, and information-theoretic analysis to determine whether computationally inexpensive scalar statistics can reliably detect cardiac abnormalities.

---

# Project Overview

Consumer smartwatches and wearable cardiac monitors often operate under severe computational and power constraints, motivating the search for lightweight screening algorithms. This project investigates a fundamental engineering question:

> **Can a computationally trivial scalar summary of an ECG waveform (total signal energy) serve as a reliable "tripwire" for severe arrhythmias?**

Rather than proposing another machine learning classifier, this work studies the problem from the perspective of **classical statistical inference**. By constructing a complete inference pipeline—from probabilistic modeling and parameter estimation to optimal hypothesis testing and information-theoretic analysis—it demonstrates that scalar energy statistics are fundamentally insufficient for clinical-grade ECG monitoring.

The resulting conclusion is not merely empirical, but mathematical: compressing an ECG waveform into a single energy value irreversibly discards the morphological and temporal information required for reliable arrhythmia detection, thereby justifying the need for higher-dimensional signal representations in embedded healthcare systems.

---

# Background

The **electrocardiogram (ECG)** is a non-invasive recording of the heart's electrical activity and remains one of the primary diagnostic tools used to detect cardiac abnormalities. Every heartbeat generates a characteristic electrical waveform whose morphology reflects the coordinated contraction of different regions of the heart.

An **arrhythmia** is any abnormality in the heart's rhythm or electrical conduction. While some arrhythmias are benign, others can indicate serious cardiovascular conditions requiring immediate medical attention. Automatic arrhythmia detection therefore forms the foundation of many modern wearable healthcare devices, including smartwatches and portable cardiac monitors.

One common abnormal rhythm is the **Premature Ventricular Contraction (PVC)**, where the ventricles contract earlier than expected, producing a distinctive alteration in the ECG waveform. Reliable detection of PVCs is clinically important because frequent occurrences may indicate underlying cardiac dysfunction and often serve as an early warning sign for more severe rhythm disorders.

Traditional arrhythmia detection algorithms—and, more recently, deep learning models—analyze the complete ECG waveform, leveraging its temporal structure, morphology, and frequency content. However, these approaches are computationally demanding and may not always be suitable for ultra-low-power embedded devices that continuously monitor physiological signals.

A natural engineering question therefore arises:

> **How much information can be retained if the ECG waveform is compressed into an extremely simple representation?**

One of the simplest possible representations is the **total signal energy**, a single scalar obtained from the waveform. Such a feature is computationally inexpensive and attractive for battery-powered wearable devices, but its statistical discriminative power remains largely unexplored.

This repository investigates that question from the perspective of **classical statistical inference**, asking whether a single scalar energy statistic contains sufficient information to reliably distinguish normal heartbeats from premature ventricular contractions.

---

# Methodology

The study develops a complete statistical inference pipeline beginning with probabilistic modeling of ECG energy and culminating in optimal hypothesis testing and information-theoretic analysis.

### 1. Parametric Modeling

Each heartbeat is represented by its total signal energy

[
X_i=|a_i|_2^2
]

The distribution of these scalar observations is modeled using a **Gamma Distribution**, a member of the **Regular Exponential Family**.

---

### 2. Parameter Estimation

The Gamma parameters ((\alpha,\beta)) are estimated using **Maximum Likelihood Estimation (MLE)** through numerical optimization.

The estimation procedure is validated using:

* Fisher Information Matrix
* **Cramér-Rao Lower Bound (CRLB)**

to verify estimator efficiency.

---

### 3. Optimal Hypothesis Testing

The binary detection problem is formulated within the framework of **classical hypothesis testing**.

Using the:

* **Neyman-Pearson Lemma**
* **Monotone Likelihood Ratio (MLR)** property

the **Uniformly Most Powerful (UMP)** detector is derived and evaluated.

---

### 4. Information-Theoretic Analysis

Finally, the statistical separability of the two heartbeat classes is quantified using

* **Kullback-Leibler (KL) Divergence**

whose interpretation through the **Data Processing Inequality** establishes the theoretical limitations imposed by compressing an ECG waveform into a single scalar statistic.

---

# Key Findings

The statistically optimal detector exhibits the following performance:

| Metric                            | Value                  |
| --------------------------------- | ---------------------- |
| **Optimal Threshold ((k^*))**     | **32.82** energy units |
| **Significance Level ((\alpha))** | **0.05**               |
| **Statistical Power**             | **22.99%**             |
| **Type II Error (Miss Rate)**     | **77.01%**             |
| **KL Divergence**                 | **0.3919 nats**        |

---

# Conclusion

Even under the statistically optimal **Neyman-Pearson detector**, a scalar-energy classifier fails to identify approximately **77% of genuine PVC events**.

This is not merely a limitation of a particular model or dataset—it is a structural consequence of dimensionality reduction.

Mapping an ECG waveform to a single scalar norm irreversibly destroys the phase and morphological signatures necessary for robust arrhythmia classification. Consequently, clinically reliable detection requires richer feature representations or higher-dimensional inference architectures.

---

# Repository Structure

```
.
├── Statistical_Inference_PROJECT.pdf      # Complete research report
├── Statistical_Inference_PROJECT.ipynb    # End-to-end inference pipeline
└── README.md
```

---

# Repository Contents

## 📄 Project Report

**`Statistical_Inference_PROJECT.pdf`**

A complete research report containing:

* Mathematical derivations
* Statistical proofs
* Theoretical background
* Literature review
* Experimental methodology
* Discussion of results

---

## 💻 Python Inference Pipeline

**`Statistical_Inference_PROJECT.ipynb`**

A fully reproducible implementation including:

* MIT-BIH dataset ingestion
* Signal preprocessing
* Scalar energy computation
* Numerical MLE optimization
* Fisher Information computation
* CRLB verification
* Neyman-Pearson hypothesis testing
* ROC analysis
* Decision-threshold visualization
* Information-theoretic analysis

---

# Repository Philosophy

This repository is intended to serve both as a **reproducible implementation** and as a **self-contained technical document**.

The accompanying report develops the theoretical foundations, while the notebook provides an end-to-end computational realization of every major statistical result.

Together, they demonstrate not only **how** the inference pipeline is implemented, but also **why** the resulting performance limitations arise from fundamental principles of statistical decision theory and information theory.

Rather than introducing another predictive model, this work establishes the **fundamental statistical limits** of an intentionally minimal ECG representation. In doing so, it provides a rigorous justification for why practical arrhythmia detection systems must ultimately rely on richer signal representations that preserve the temporal and morphological characteristics of the underlying cardiac waveform.

---

# Citation

If you find this work useful in your research, please cite the accompanying report.

```text
Pushkar Chaturvedy.
Statistical Inference for Arrhythmia Detection:
Fundamental Limits of Univariate Representations.
Indian Institute of Technology Kharagpur.
```

---

# Author

**Pushkar Chaturvedy**

Indian Institute of Technology Kharagpur
