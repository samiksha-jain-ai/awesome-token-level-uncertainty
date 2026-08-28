# Research Papers

A curated collection of research papers related to token-level uncertainty, uncertainty quantification, hallucination detection, semantic uncertainty, calibration, and reliability of Large Language Models.

---

## 1. Token-Level Uncertainty

### 1.1 Fact-Checking the Output of Large Language Models via Token-Level Uncertainty Quantification

**Authors:** Ekaterina Fadeeva, Aleksandr Rubashevskii, Artem Shelmanov, Sergey Petrakov, Haonan Li, Hamdy Mubarak, Evgenii Tsymbalov, Gleb Kuzmin, Alexander Panchenko, Timothy Baldwin, Preslav Nakov, Maxim Panov
**Year:** 2024
**Venue:** Findings of the Association for Computational Linguistics: ACL 2024
**DOI:** 10.18653/v1/2024.findings-acl.558

This paper directly studies token-level uncertainty for detecting hallucinated claims in LLM outputs. It proposes Claim Conditioned Probability (CCP) to separate uncertainty about the claim from uncertainty about its surface form.

[Paper](https://aclanthology.org/2024.findings-acl.558/)

---

### 1.2 A Token-level Reference-free Hallucination Detection Benchmark for Free-form Text Generation

**Authors:** Tianyu Liu, Yizhe Zhang, Chris Brockett, Yi Mao, Zhifang Sui, Weizhu Chen, Bill Dolan
**Year:** 2022
**Venue:** ACL 2022

This work introduces a token-level, reference-free hallucination detection task and the HaDeS dataset, providing fine-grained annotations for detecting hallucinated content.

[Paper](https://aclanthology.org/2022.acl-long.464/)

---

### 1.3 Shifting Attention to Relevance: Towards the Predictive Uncertainty Quantification of Free-form Large Language Models

**Authors:** J. Duan, H. Cheng, S. Wang, A. Zavalny, C. Wang, R. Xu, B. Kailkhura, K. Xu
**Year:** 2024
**Source:** arXiv

This work investigates predictive uncertainty in free-form LLM generation and studies how uncertainty can be used to identify unreliable model outputs.

[Paper](https://arxiv.org/abs/2307.01379)

---

### 1.4 Scalable Token-Level Hallucination Detection in Large Language Models (TOKENHD)

**Authors:** R. Min, T. Pang, C. Du, M. Cheng, Y. R. Fung
**Year:** 2026
**Source:** arXiv

This recent work focuses on scalable token-level hallucination detection in large language models.

[Paper](https://arxiv.org/abs/2605.12384)

---

### 1.5 TokUR: Token-Level Uncertainty Estimation for Large Language Model Reasoning

**Year:** 2025
**Source:** arXiv

TokUR investigates token-level uncertainty estimation for reasoning processes in large language models.

[Paper](https://arxiv.org/abs/2505.11737)

---

### 1.6 Token-Level Density-Based Uncertainty Quantification Methods for Eliciting Truthfulness of Large Language Models

**Year:** 2025
**Source:** arXiv

This work investigates density-based approaches for quantifying token-level uncertainty and using uncertainty information to study truthfulness in LLMs.

[Paper](https://arxiv.org/abs/2502.14427)

---

## 2. Hallucination Detection

### 2.1 The Internal State of an LLM Knows When It's Lying

**Authors:** A. Azaria, T. Mitchell
**Year:** 2023
**Source:** arXiv

This paper investigates whether internal representations of language models contain information that can help identify when an LLM is generating false information.

[Paper](https://arxiv.org/abs/2304.13734)

---

### 2.2 INSIDE: LLMs' Internal States Retain the Power of Hallucination Detection

**Authors:** C. Chen, K. Liu, Z. Chen, Y. Gu, Y. Wu, M. Tao, Z. Fu, J. Ye
**Year:** 2024
**Source:** arXiv

INSIDE investigates whether information contained within the internal states of LLMs can be used to detect hallucinations.

[Paper](https://arxiv.org/abs/2402.03744)

---

### 2.3 SelfCheckGPT: Zero-Resource Black-Box Hallucination Detection for Generative Large Language Models

**Authors:** P. Manakul, A. Liusie, M. Gales
**Year:** 2023
**Venue:** EMNLP 2023

SelfCheckGPT proposes a black-box hallucination detection approach that uses consistency among multiple generated responses without requiring external knowledge or model probabilities.

[Paper](https://aclanthology.org/2023.emnlp-main.557/)

---

### 2.4 Detecting Token-Level Hallucinations Using Variance Signals: A Reference-Free Approach

**Year:** 2025
**Source:** arXiv

This work investigates variance-based signals for detecting hallucinations at the token level without relying on reference answers.

[Paper](https://arxiv.org/abs/2507.04137)

---

### 2.5 Dynamic Attention-Guided Context Decoding for Mitigating Context Faithfulness Hallucinations in Large Language Models

**Year:** 2025
**Source:** arXiv

This work investigates attention-guided decoding techniques for reducing context-faithfulness hallucinations in large language models.

[Paper](https://arxiv.org/abs/2501.01059)

---

## 3. Semantic Uncertainty

### 3.1 Detecting Hallucinations in Large Language Models Using Semantic Entropy

**Authors:** Sebastian Farquhar, Jannik Kossen, Lorenz Kuhn, Yarin Gal
**Year:** 2024
**Venue:** Nature

This influential work introduces semantic entropy for measuring uncertainty over the meanings of generated answers rather than simply measuring variation in the exact token sequences. It demonstrates that semantic uncertainty can be useful for detecting confabulations.

[Paper](https://www.nature.com/articles/s41586-024-07421-0)

---

### 3.2 Semantic Uncertainty: Linguistic Invariances for Uncertainty Estimation in Natural Language Generation

**Authors:** Lorenz Kuhn, Yarin Gal, Sebastian Farquhar
**Year:** 2023
**Venue:** ICLR 2023

This work develops semantic uncertainty methods that account for different linguistic expressions that convey the same underlying meaning.

[Paper](https://openreview.net/forum?id=VD-AYtP0dve)

---

### 3.3 Semantic Entropy Probes: Robust and Cheap Hallucination Detection in LLMs

**Authors:** J. Kossen, J. Han, M. Razzak, L. Schut, S. Malik, Y. Gal
**Year:** 2024
**Source:** arXiv

This paper investigates semantic entropy probes as a relatively efficient approach to hallucination detection.

[Paper](https://arxiv.org/abs/2406.15927)

---

## 4. Uncertainty Estimation and Calibration

### 4.1 Uncertainty Estimation in Autoregressive Structured Prediction

**Authors:** Andrey Malinin, Mark Gales
**Year:** 2021
**Venue:** ICLR 2021

This work studies uncertainty estimation for autoregressive structured prediction and provides important foundations for understanding uncertainty in sequential generation.

[Paper](https://openreview.net/forum?id=jN5y-zb5Q7m)

---

### 4.2 On Calibration of Modern Neural Networks

**Authors:** Chuan Guo, Geoff Pleiss, Yu Sun, Kilian Q. Weinberger
**Year:** 2017
**Venue:** ICML 2017

This foundational paper studies calibration of neural-network confidence estimates and introduces widely used methods for evaluating and improving calibration.

[Paper](https://proceedings.mlr.press/v70/guo17a.html)

---

### 4.3 Language Models (Mostly) Know What They Know

**Authors:** S. Kadavath et al.
**Year:** 2022
**Source:** arXiv

This study examines whether language models can recognize when they know or do not know information, connecting model confidence with factual reliability.

[Paper](https://arxiv.org/abs/2207.05221)

---

### 4.4 On Hallucination and Predictive Uncertainty in Conditional Language Generation

**Authors:** Y. Xiao, W. Y. Wang
**Year:** 2021
**Venue:** EACL 2021

This work studies the relationship between predictive uncertainty and hallucination in conditional language generation.

[Paper](https://doi.org/10.18653/v1/2021.eacl-main.236)

---

## 5. Hallucination Surveys

### 5.1 Survey of Hallucination in Natural Language Generation

**Authors:** Ziwei Ji et al.
**Year:** 2023
**Venue:** ACM Computing Surveys

This survey provides a broad overview of hallucination in natural language generation, including definitions, causes, detection methods, and mitigation strategies.

[Paper](https://doi.org/10.1145/3571730)

---

### 5.2 A Survey on Hallucination in Large Language Models: Principles, Taxonomy, Challenges, and Open Questions

**Authors:** Lei Huang et al.
**Year:** 2025
**Venue:** ACM Transactions on Information Systems

This survey presents a taxonomy of hallucinations in LLMs and reviews major detection, evaluation, and mitigation approaches.

[Paper](https://doi.org/10.1145/3703155)

---

## 6. Additional Uncertainty and Hallucination Research

### 6.1 Uncertainty Quantification for Hallucination Detection in Large Language Models: Foundations, Methodology, and Future Directions

**Authors:** Sungmin Kang, Yavuz Faruk Bakman, Duygu Nur Yaldiz, Baturalp Buyukates, Salman Avestimehr
**Year:** 2025
**Source:** arXiv

This survey studies uncertainty quantification methods for hallucination detection and organizes approaches according to different uncertainty-estimation strategies.

[Paper](https://arxiv.org/abs/2510.12040)

---

### 6.2 Why Language Models Hallucinate

**Authors:** Adam Tauman Kalai, Ofir Nachum, Santosh S. Vempala, Eric Zhang
**Year:** 2025
**Source:** arXiv

This work investigates the underlying reasons language models can produce hallucinated information and contributes to the theoretical understanding of LLM hallucination.

[Paper](https://arxiv.org/abs/2509.04664)

---

### 6.3 Enhancing Uncertainty-Based Hallucination Detection with Stronger Focus

**Authors:** T. Zhang et al.
**Year:** 2023
**Source:** arXiv

This research investigates methods for improving uncertainty-based hallucination detection by focusing more strongly on informative signals.

[Paper](https://arxiv.org/abs/2311.13230)

---

## Quick Reference

| #  | Paper                                                          | Main Area                |
| -- | -------------------------------------------------------------- | ------------------------ |
| 1  | Fact-Checking LLM Output via Token-Level UQ                    | Token-level uncertainty  |
| 2  | Token-level Reference-free Hallucination Detection             | Token-level detection    |
| 3  | Shifting Attention to Relevance                                | Predictive uncertainty   |
| 4  | TOKENHD                                                        | Token-level detection    |
| 5  | TokUR                                                          | Token-level uncertainty  |
| 6  | Token-Level Density-Based UQ                                   | Token uncertainty        |
| 7  | Internal State of an LLM Knows When It's Lying                 | Internal-state detection |
| 8  | INSIDE                                                         | Internal-state detection |
| 9  | SelfCheckGPT                                                   | Hallucination detection  |
| 10 | Variance Signals for Token-Level Hallucinations                | Token-level detection    |
| 11 | Dynamic Attention-Guided Context Decoding                      | Hallucination mitigation |
| 12 | Semantic Entropy                                               | Semantic uncertainty     |
| 13 | Semantic Uncertainty                                           | Semantic uncertainty     |
| 14 | Semantic Entropy Probes                                        | Semantic uncertainty     |
| 15 | Uncertainty Estimation in Autoregressive Structured Prediction | UQ                       |
| 16 | On Calibration of Modern Neural Networks                       | Calibration              |
| 17 | Language Models Mostly Know What They Know                     | Model confidence         |
| 18 | Hallucination and Predictive Uncertainty                       | Predictive uncertainty   |
| 19 | Survey of Hallucination in NLG                                 | Survey                   |
| 20 | Survey on Hallucination in LLMs                                | Survey                   |
| 21 | UQ for Hallucination Detection                                 | UQ survey                |
| 22 | Why Language Models Hallucinate                                | Hallucination theory     |
| 23 | Enhancing Uncertainty-Based Hallucination Detection            | UQ detection             |

---

## Selection Note

The papers in this collection were selected because they are directly or indirectly relevant to understanding uncertainty, token-level confidence, hallucination detection, semantic uncertainty, calibration, or reliability in large language models.

Priority was given to scholarly publications and publicly accessible research records from sources such as ACL Anthology, Nature, OpenReview, and arXiv.
