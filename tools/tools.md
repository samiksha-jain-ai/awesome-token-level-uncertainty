# Tools and Libraries

This section contains software tools and libraries that can be used for working with Large Language Models, token probabilities, uncertainty estimation, hallucination detection, and model evaluation.

---

## 1. Hugging Face Transformers

**Type:** Python library / Deep Learning

**Description:**
Hugging Face Transformers provides implementations and pretrained models for many transformer-based language models. It can be used to load models, generate text, and access token-level model outputs such as logits and probabilities.

**Why it is relevant:**
Token-level logits and probabilities are important inputs for calculating predictive uncertainty at the token level.

**Official Website:**
https://huggingface.co/docs/transformers/

**GitHub:**
https://github.com/huggingface/transformers

---

## 2. PyTorch

**Type:** Deep Learning Framework

**Description:**
PyTorch is a widely used open-source machine-learning framework for building and evaluating neural-network models.

**Why it is relevant:**
PyTorch can be used to process model logits, calculate probability distributions, and implement uncertainty metrics for language-model outputs.

**Official Website:**
https://pytorch.org/

**GitHub:**
https://github.com/pytorch/pytorch

---

## 3. UQLM

**Type:** Python Library / Uncertainty Quantification

**Description:**
UQLM is a Python package designed for uncertainty quantification and hallucination detection in large language models. It provides different uncertainty scorers, including approaches that use model probabilities.

**Why it is relevant:**
UQLM directly connects uncertainty estimation with LLM hallucination detection and therefore closely matches the focus of this repository.

**GitHub:**
https://github.com/cvs-health/uqlm

---

## 4. vLLM

**Type:** LLM Inference and Serving Framework

**Description:**
vLLM is an open-source framework designed for efficient inference and serving of large language models.

**Why it is relevant:**
Efficient LLM inference is useful when conducting experiments involving multiple generations, token probabilities, uncertainty estimation, and hallucination detection.

**Official Website:**
https://vllm.ai/

**GitHub:**
https://github.com/vllm-project/vllm

---

## 5. lm-evaluation-harness

**Type:** LLM Evaluation Framework

**Description:**
EleutherAI's Language Model Evaluation Harness is an open-source framework for evaluating language models across a large collection of standardized tasks and benchmarks.

**Why it is relevant:**
A standardized evaluation framework can help researchers compare model behavior and evaluate reliability-related methods across different models and datasets.

**GitHub:**
https://github.com/EleutherAI/lm-evaluation-harness

---

## Tool Comparison

| Tool                      | Main Use                                | Relevance |
| ------------------------- | --------------------------------------- | --------- |
| Hugging Face Transformers | LLMs and token outputs                  | Very High |
| PyTorch                   | Model computation                       | High      |
| UQLM                      | Uncertainty and hallucination detection | Very High |
| vLLM                      | Efficient LLM inference                 | High      |
| lm-evaluation-harness     | LLM evaluation                          | High      |

---

## How These Tools Can Be Used Together

A possible experimental workflow is:

**LLM → Token Probabilities → Uncertainty Calculation → Hallucination Detection → Evaluation**

For example, Hugging Face Transformers can be used to obtain model outputs and token-level information. PyTorch can process the model probabilities and calculate numerical quantities. UQLM can provide uncertainty-based hallucination detection methods, while vLLM can support efficient generation for larger experiments. The evaluation harness can then be used to compare model performance on standardized tasks.

## Selection Note

The tools were selected because they provide functionality relevant to LLM inference, token-level model information, uncertainty quantification, hallucination detection, or systematic model evaluation. The strongest direct connection to this repository is UQLM because it specifically focuses on uncertainty quantification for LLM hallucination detection.
