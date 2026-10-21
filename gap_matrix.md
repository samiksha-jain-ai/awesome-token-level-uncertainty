# gap_matrix.md — Evidence-Based Research Gap Matrix

**Source analysed:** attached review, "Token-Level Uncertainty as a Predictor of Hallucination in Large Language Models"
**Tags:** VERIFIED = stated in the review · INFERRED = my reasoning · UNKNOWN = needs verification or your input
**Important:** no novelty is claimed for any gap. Each requires a separate literature search (D-03 in `research_decisions.md`).

---

## 1. Extraction summary

**Central methods (VERIFIED):** token NLL, sequence log-probability, perplexity, predictive entropy (§3.1); informativeness-weighted aggregation, Zhang 2023 and SAR (§3.2); semantic entropy, Semantic Entropy Probes, Kernel Language Entropy (§3.3); SelfCheckGPT and variance-signal token detection (§3.4); hidden-state probing, INSIDE, attention-guided decoding (§3.5); TOKENHD, TokUR, density-based UQ, Fadeeva fact-checking (§4).

**Datasets (VERIFIED):** none named. Only task families appear: question answering, summarization, image captioning, data-to-text, machine translation (§2.2, §5).

**Measured findings (VERIFIED, but secondary and unverified against originals):**
- Higher predictive uncertainty correlates with more hallucination; epistemic is the more informative component (Xiao & Wang 2021, §2.2).
- Semantic entropy is a reliable unsupervised confabulation detector (Farquhar 2024, §3.3).
- SEPs approximate semantic entropy from hidden states in one pass (Kossen 2024, §3.3).
- Token entropy correlates with context-unfaithful output in RAG (arXiv:2501.01059, §3.5).
- A compact 0.6B detector outperforms much larger reasoning models at token localization (TOKENHD, §4). See V8 in the decision log.

**Author-reported limitations (VERIFIED, §5):** miscalibration; epistemic–aleatoric confound; lexical variation masking semantic agreement; 5–10× sampling overhead; black-box inaccessibility; no settled token→claim aggregation; limited generalization to long-form, dialogue and reasoning.

**Unresolved questions (VERIFIED, §6):** causal vs correlational evidence; cheap epistemic/aleatoric split; cheap semantic uncertainty; standard benchmarks; incentive-aware evaluation; uncertainty-triggered retrieval; reasoning/agentic settings.

**Important absence (VERIFIED):** the review reports no original experiments, so every "finding" is borrowed.

---

## 2. Gap matrix: source evidence → candidate question → possible experiment

Notation: **[R]** = limitation or gap stated in the review. **[I]** = my inference, not stated in the review.

### G1. Token-to-claim aggregation
- **Source evidence:** §5 "Aggregation from token to claim": "no settled, theoretically justified method"; mean/min/max each have different failure modes (citing Huang 2025). §3.2: averaging dilutes signal because function words are confident; Zhang 2023 and SAR reweight tokens. **[R]**
- **Inferred extension:** a systematic head-to-head of aggregators on one fixed claim-labelled set has not been shown in the review. **[I]**
- **Candidate question:** Which aggregator (mean, min, max, entropy-weighted, keyword-weighted, learned) best separates hallucinated from correct claims, and does the ranking change across claim types (entities, dates, numbers)?
- **Possible experiment:** fix one open-weight LLM; generate answers; split into atomic claims; label claims; compute per-token NLL/entropy; apply each aggregator; compare AUROC/AUPRC and risk–coverage per claim type.
- **Evidence that would test it:** AUROC differences with bootstrap CIs across aggregators; per-claim-type breakdown.
- **Needs from you:** dataset with claim-level labels (UNKNOWN; see D-06), GPU for inference only.

### G2. Cheap token-level epistemic vs aleatoric separation
- **Source evidence:** §5 "Epistemic versus aleatoric confound"; §6 "Unified epistemic-aleatoric decomposition for LLMs … remains an open problem." Malinin & Gales 2021 formalize the decomposition via ensembles. **[R]**
- **Inferred extension:** test whether multi-sample or lightweight proxies (e.g., entropy across a few samples/prompt perturbations) approximate the epistemic part. **[I]**
- **Candidate question:** On questions with single-answer vs multiple-valid-phrasing targets, does a cheap proxy for mutual information predict hallucination better than raw entropy?
- **Possible experiment:** build two question subsets (unambiguous fact vs paraphrase-rich); compute raw entropy and a K-sample proxy; compare detection AUROC and sensitivity to paraphrase.
- **Evidence that would test it:** interaction effect (subset × measure) in detection performance.
- **Risk:** defining "epistemic proxy" rigorously is hard; ground truth for the decomposition is UNKNOWN.

### G3. Calibration of token probabilities: base vs instruction-tuned models
- **Source evidence:** §5 "Miscalibration and overconfidence": instruction tuning and RLHF degrade calibration relative to base models (cited to Kadavath 2022; Guo 2017). §2.3 and §2.1 (Kalai 2025: confident wrongness). **[R]**
- **Verification flag:** V4 — Guo 2017 predates RLHF and cannot support the RLHF part; Kadavath's exact finding must be checked. **[I]**
- **Candidate question:** For matched base/instruct model pairs, how do ECE and hallucination-detection AUROC of token-level probability and entropy differ, and does temperature scaling recover the gap?
- **Possible experiment:** choose open-weight pairs from the same family; run identical prompts; compute ECE/reliability diagrams and AUROC before/after temperature scaling (Guo 2017).
- **Evidence that would test it:** significant ECE/AUROC difference between base and instruct; recovery after scaling.
- **Needs from you:** model pairs you can run (UNKNOWN). Very low implementation cost.

### G4. Accuracy–efficiency trade-off of semantic uncertainty
- **Source evidence:** §3.3 (5–10× overhead; SEPs cheaper); §5 "Computational overhead": "the extent of this trade-off is not yet fully characterized across domains and model families"; §6 "Efficient semantic uncertainty at scale". **[R]**
- **Candidate question:** How does detection quality of semantic entropy vary with number of samples M, compared with token entropy and a probe-based approximation, per unit of compute?
- **Possible experiment:** vary M (e.g., small set of values you choose), compute SE via an NLI clustering model; compare to single-pass entropy and (if feasible) a linear probe; plot AUROC vs GPU-seconds.
- **Evidence that would test it:** a Pareto frontier of AUROC against compute across methods.
- **Risk:** highest compute; probe training needs hidden states and labels (UNKNOWN resources). Checks of V5 first.

### G5. Causal test: uncertainty-triggered abstention / retrieval
- **Source evidence:** §6 "Causal, not merely correlational, evaluation" (only Xiao & Wang 2021 intervene) and "Uncertainty-aware decoding and retrieval integration" (uncertainty-triggered retrieval named as promising); §4 abstention training. **[R]**
- **Candidate question:** If generation abstains (or triggers retrieval) when token-level uncertainty exceeds a threshold, does the hallucination rate fall at an acceptable coverage cost, and is the effect larger for entropy than for a calibration-matched baseline?
- **Possible experiment:** generate with and without an uncertainty gate; compare hallucination rate vs answer coverage (risk–coverage curves) for several thresholds and signals; include a random-abstention control at matched coverage.
- **Evidence that would test it:** significant reduction vs random-abstention control at equal coverage. This isolates the signal's causal usefulness from mere correlation.
- **Needs from you:** a labelled QA setup and, optionally, a retrieval corpus (UNKNOWN; retrieval is optional for a first paper).

---

## 3. Ranking (top three)

Criteria: research significance (S), available resources (R: assumes modest GPU, open-weight model; UNKNOWN until you confirm), implementation feasibility (F). Scores 1–5 are my INFERRED judgements, not measurements.

| Rank | Gap | S | R | F | Rationale |
|---|---|---|---|---|---|
| 1 | **G1** Token→claim aggregation | 4 | 5 | 5 | Directly stated as unsettled in §5; inference-only compute; clean comparative design with clear metrics. |
| 2 | **G5** Uncertainty-triggered abstention (causal) | 5 | 4 | 3 | Addresses the review's top-listed gap (causal evaluation); control condition is simple; retrieval variant can be deferred. |
| 3 | **G3** Base vs instruct calibration | 4 | 5 | 5 | Cheap and fast; also tests a claim in the review whose citation is shaky (V4), so it adds verification value. |
| 4 | G4 Semantic uncertainty trade-off | 4 | 2 | 3 | Strong topic but sampling plus NLI cost is large. |
| 5 | G2 Epistemic/aleatoric proxy | 5 | 3 | 2 | High significance, but no clear ground truth for the decomposition. |

**Suggested combined framing (INFERRED, to confirm in Stage 4):** G3 supplies the calibration baseline, G1 the best claim-level score, and G5 the intervention test, forming one coherent paper: *"From token uncertainty to calibrated abstention."*

---

## 4. Claims in the review requiring verification against originals

See the full list V1–V10 in `research_decisions.md` §3. Highest priority for this matrix:
- **V4** (RLHF → miscalibration citation) — affects G3.
- **V5** (5–10× overhead) — affects G4.
- **V8** (TOKENHD claims) — affects any comparison involving learned detectors.
- **V1/V2** (missing or confusing references for sequence log-probability and entropy-correlation claims) — affects G1 baselines.

---

## 5. Items not claimed / limitations of this matrix
- Novelty of G1–G5 is **UNKNOWN**; no separate literature search has been done.
- Datasets, models, metrics values and baselines are **UNKNOWN**; none have been run or invented.
- Feasibility scores assume modest compute and are INFERRED until you answer the questions in `research_decisions.md` §4.
