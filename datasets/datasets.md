# Datasets for Token-Level Uncertainty and Hallucination Detection

This collection contains datasets and benchmarks useful for studying hallucination detection, factuality, uncertainty, and reliability in Large Language Models.

---

## 1. HaDeS — Hallucination Detection Dataset

**Source:** Microsoft Research / GitHub

**Description:**
HaDeS is a dataset designed for token-level, reference-free hallucination detection. It provides fine-grained annotations that identify hallucinated content in generated text.

**Why it is relevant:**
This dataset is highly relevant to token-level uncertainty research because hallucinations can be studied at the level of individual generated tokens rather than only at the level of an entire response.

**Link:**
https://github.com/microsoft/HaDes

---

## 2. HaluEval

**Source:** GitHub / Research benchmark

**Description:**
HaluEval is a large-scale benchmark designed to evaluate the ability of models to recognize hallucinations in generated text. It contains hallucinated and non-hallucinated examples across different tasks.

**Why it is relevant:**
HaluEval can be used to evaluate whether uncertainty-based methods can distinguish reliable model outputs from hallucinated outputs.

**Link:**
https://github.com/RUCAIBox/HaluEval

---

## 3. TruthfulQA

**Source:** Center for AI Safety / GitHub

**Description:**
TruthfulQA is a benchmark designed to measure whether language models generate truthful answers to questions that are likely to produce false or misleading responses.

**Why it is relevant:**
Truthfulness is closely related to hallucination detection. Token-level uncertainty or other confidence measures can be investigated using truthful and untruthful model responses.

**Link:**
https://github.com/sylinrl/TruthfulQA

---

## Dataset Comparison

| Dataset    | Main Purpose                        | Relevance to Topic |
| ---------- | ----------------------------------- | ------------------ |
| HaDeS      | Token-level hallucination detection | Very High          |
| HaluEval   | Hallucination evaluation            | High               |
| TruthfulQA | Truthfulness evaluation             | High               |

---

## How These Datasets Can Be Used

These datasets can support experiments involving:

1. **Token-level uncertainty** — examining whether token probabilities or uncertainty scores identify hallucinated tokens.
2. **Hallucination detection** — testing whether uncertainty measures distinguish hallucinated from reliable outputs.
3. **Truthfulness evaluation** — investigating the relationship between model confidence and factual correctness.
4. **Benchmarking** — comparing different uncertainty-based hallucination detection methods.
5. **Model evaluation** — studying whether uncertainty estimates remain useful across different models and tasks.

## Selection Note

The datasets were selected because they provide data or evaluation settings relevant to hallucination, factuality, truthfulness, or fine-grained hallucination detection. HaDeS has the strongest direct connection to the token-level focus of this repository, while HaluEval and TruthfulQA provide broader hallucination and truthfulness evaluation settings.
