# Awesome Token-Level Uncertainty

A curated collection of research papers, datasets, tools, implementations, and learning resources related to **token-level uncertainty and hallucination detection in Large Language Models (LLMs)**.

This repository connects an AI-assisted research paper and citation-integrity audit with verified scholarly resources to provide a reusable research resource for students and researchers.

## Contents

* [Overview](#overview)
* [AI-Assisted Research Paper](#ai-assisted-research-paper)
* [Citation Integrity Audit](#citation-integrity-audit)
* [Survey and Review Papers](#survey-and-review-papers)
* [Foundational Research](#foundational-research)
* [Token-Level Uncertainty](#token-level-uncertainty)
* [Hallucination Detection](#hallucination-detection)
* [Semantic Uncertainty](#semantic-uncertainty)
* [Recent Research](#recent-research)
* [Datasets](#datasets)
* [Tools and Libraries](#tools-and-libraries)
* [GitHub Implementations](#github-implementations)
* [Tutorials and Learning Resources](#tutorials-and-learning-resources)
* [License](#license)

---

## Overview

Large Language Models (LLMs) are capable of generating fluent and informative text, but they can also produce hallucinations: statements that are incorrect, unsupported, or inconsistent with the available context. Detecting these hallucinations is an important research problem because fluent language can make incorrect information difficult to identify.

One promising approach is to examine **uncertainty at the token level**. Instead of treating an entire generated response as simply reliable or unreliable, token-level uncertainty examines the model's confidence associated with individual generated tokens. High uncertainty may indicate that the model is less confident about particular parts of its output.

Research in this area includes token probability methods, uncertainty quantification, semantic uncertainty, calibration, internal model representations, and specialized hallucination-detection systems. These approaches can help identify unreliable content and provide more fine-grained information about where hallucinations may occur.

This repository collects research papers, datasets, software tools, implementations, and learning resources related to this research area. The goal is to provide an organized starting point for understanding and investigating the relationship between model uncertainty and hallucination in LLMs.

---

## AI-Assisted Research Paper

### Token-Level Uncertainty as a Predictor of Hallucination in Large Language Models

This research paper was generated as part of the earlier AI Tools for Research laboratory activity. The paper examines the relationship between uncertainty in language-model predictions and hallucination detection.

**AI Tool Used:** Claude

**Topic ID:** T_3

[View AI-Assisted Research Paper](paper/AI_Assisted_Research_Paper.pdf)

---

## Citation Integrity Audit

The AI-generated research paper contained 21 references. A systematic sample of 10 references was selected according to the prescribed sampling procedure and checked for publication existence, metadata, and identifiers.

The audited sample contained 10 verified references, with no wrong-metadata, Frankenstein, fabricated, or identifier-mismatch classifications in the completed audit.

**Authenticity Score:** 100/100

[View Citation Integrity Audit](citation-audit/Citation_Integrity_Audit.pdf)

---

## Survey and Review Papers

* Huang et al. — *A Survey on Hallucination in Large Language Models: Principles, Taxonomy, Challenges, and Open Questions*
* Ji et al. — *Survey of Hallucination in Natural Language Generation*

These papers provide broad background on hallucination, its causes, classifications, detection methods, and open research problems.

---

## Foundational Research

* Guo et al. — *On Calibration of Modern Neural Networks*
* Malinin & Gales — *Uncertainty Estimation in Autoregressive Structured Prediction*
* Kadavath et al. — *Language Models (Mostly) Know What They Know*

These works provide important background for understanding model confidence, uncertainty estimation, calibration, and the relationship between model knowledge and uncertainty.

---

## Token-Level Uncertainty

This section focuses specifically on research examining uncertainty at the token or fine-grained generation level.

* Fadeeva et al. — *Fact-Checking the Output of Large Language Models via Token-Level Uncertainty Quantification*
* Duan et al. — *Shifting Attention to Relevance: Towards the Predictive Uncertainty Quantification of Free-Form Large Language Models*
* Min et al. — *Scalable Token-Level Hallucination Detection in Large Language Models*
* *TokUR: Token-Level Uncertainty Estimation for Large Language Model Reasoning*
* *Token-Level Density-Based Uncertainty Quantification Methods for Eliciting Truthfulness of Large Language Models*

---

## Hallucination Detection

* Azaria & Mitchell — *The Internal State of an LLM Knows When It's Lying*
* Chen et al. — *INSIDE: LLMs' Internal States Retain the Power of Hallucination Detection*
* Farquhar et al. — *Detecting Hallucinations in Large Language Models Using Semantic Entropy*
* Manakul et al. — *SelfCheckGPT: Zero-Resource Black-Box Hallucination Detection for Generative Large Language Models*
* Xiao & Wang — *On Hallucination and Predictive Uncertainty in Conditional Language Generation*

---

## Semantic Uncertainty

Semantic uncertainty methods examine whether multiple possible model outputs express different underlying meanings. This provides another way to estimate whether a model is uncertain about the factual content it is generating.

Important research includes:

* Kuhn, Gal & Farquhar — *Semantic Uncertainty: Linguistic Invariances for Uncertainty Estimation in Natural Language Generation*
* Kossen et al. — *Semantic Entropy Probes: Robust and Cheap Hallucination Detection in LLMs*
* Farquhar et al. — *Detecting Hallucinations in Large Language Models Using Semantic Entropy*

---

## Recent Research

This section contains recent work investigating new methods for token-level uncertainty, hallucination detection, and uncertainty-based evaluation.

* *Scalable Token-Level Hallucination Detection in Large Language Models*
* *TokUR: Token-Level Uncertainty Estimation for Large Language Model Reasoning*
* *Token-Level Density-Based Uncertainty Quantification Methods for Eliciting Truthfulness of Large Language Models*
* *Dynamic Attention-Guided Context Decoding for Mitigating Context Faithfulness Hallucinations in Large Language Models*
* *Detecting Token-Level Hallucinations Using Variance Signals: A Reference-Free Approach*

---

## Datasets

See [datasets.md](datasets/datasets.md) for datasets useful for hallucination detection and uncertainty research.

---

## Tools and Libraries

See [tools.md](tools/tools.md) for software libraries and frameworks relevant to uncertainty quantification and hallucination detection.

---

## GitHub Implementations

See [github-repositories.md](implementations/github-repositories.md) for open-source implementations related to hallucination detection and uncertainty estimation.

---

## Tutorials and Learning Resources

Research papers, official documentation, tutorials, and other learning resources are collected here to help students understand uncertainty estimation, language-model evaluation, and hallucination detection.

---

## License

This repository is intended as an academic research-curation resource. Research papers and external resources remain the property of their respective authors and publishers. This repository links to external resources rather than redistributing copyrighted research papers.
