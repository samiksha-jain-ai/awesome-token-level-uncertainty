# research_decisions.md — Research Workspace & Decision Log

**Topic:** Token-level uncertainty as a predictor of hallucination in large language models
**Stage:** Literature review → implementation-based research paper
**Status legend:** VERIFIED = directly checkable in the attached review text · INFERRED = my reasoning from the review, not stated in it · UNKNOWN = not in the review; needs your input or a source file

---

## 0. Working rules (agreed protocol)

1. Every statement is tagged VERIFIED / INFERRED / UNKNOWN.
2. No invented papers, datasets, repository links, code execution, experiments or metrics. Anything not in the attached review or in a file you supply is marked UNKNOWN until you provide it.
3. Novelty is never claimed without a separate literature search (see D-03).
4. Stages: (1) evidence-based gaps → (2) literature-to-experiment mapping → (3) feasibility → (4) research questions → (5) verified baseline → (6) coding → (7) experimental evaluation → (8) manuscript → (9) reproducibility.
5. Every decision below records: decision, reason, source/evidence, next action.

**Current stage:** 1 (gap identification) — complete as a first pass; see `gap_matrix.md`.

---

## 1. Review scope summary

| Item | Content | Status |
|---|---|---|
| Title | "Token-Level Uncertainty as a Predictor of Hallucination in Large Language Models" | VERIFIED |
| Type | Survey / literature review, 7 sections + 21 references, ~15 pages | VERIFIED |
| Core question | Can hallucinations be flagged from signals internal to generation (token probability, entropy, perplexity) instead of post hoc external checking? | VERIFIED (§1) |
| Measures covered | Token NLL, sequence log-probability, perplexity, predictive entropy (Eqs. 1–4); semantic entropy (Eq. 5) | VERIFIED (§3.1, §3.3) |
| Method families | (a) basic token signals; (b) informativeness-weighted aggregation (Zhang et al. 2023; SAR, Duan et al. 2024); (c) semantic entropy, SEPs, Kernel Language Entropy; (d) consistency/variance (SelfCheckGPT, variance-signal token detector); (e) internal-state/hybrid (Azaria & Mitchell; INSIDE; attention-guided decoding) | VERIFIED (§3) |
| Systems | Fadeeva et al. 2024 fact-checking; TOKENHD; density-based UQ; TokUR; calibration/abstention training (Table 2) | VERIFIED (§4) |
| Stated challenges | Miscalibration/overconfidence; epistemic vs aleatoric confound; lexical variation vs semantic agreement; compute overhead; black-box inaccessibility; token→claim aggregation; task/domain generalization | VERIFIED (§5) |
| Stated future directions | Causal (not only correlational) evaluation; epistemic–aleatoric decomposition for LLMs; efficient semantic uncertainty; standardized benchmarks; incentive-aware training/evaluation; uncertainty-aware decoding/retrieval; reasoning/agentic settings | VERIFIED (§6) |
| Datasets named | **None named explicitly.** Only task types (QA, summarization, image captioning, MT) are mentioned. | VERIFIED (absence) |
| Original experiments / code / metrics | **None.** Figure 1 is explicitly schematic ("not derived from a specific model run"). | VERIFIED (§3.1, Fig. 1) |
| Venue/course requirements, deadline, word limit, compute available | Not in the review | UNKNOWN |

---

## 2. Decision log

| ID | Decision | Reason | Source / evidence | Next action |
|---|---|---|---|---|
| D-01 | Topic fixed as token-level uncertainty → hallucination prediction. | Matches the completed review. | Review title, §1 | None |
| D-02 | Use `research_decisions.md` (this file) + `gap_matrix.md` as the portable workspace. | Prompt 01 requires a portable log; keeps decisions auditable. | Prompts 01–02 | Append to this log after every stage |
| D-03 | No novelty claims until a separate literature search is run on each shortlisted gap. | Review is a survey and states several items as "open"/"understudied" without a systematic search. | §5, §6 wording ("comparatively understudied", "remains an open problem") | Run dedicated searches per top gap (Stage 2) |
| D-04 | Shortlist three gaps for further work: **G1** token→claim aggregation, **G5** uncertainty-triggered abstention/retrieval (causal test), **G3** base vs instruction-tuned calibration. | Best combined fit of significance, feasibility, and low compute. Ranking rationale in `gap_matrix.md`. | `gap_matrix.md` §3 | Confirm or change after you answer the questions in §4 below |
| D-05 | Treat the review's citations as *unverified secondary claims* until checked against original papers. | Several attribution irregularities were found in the review (see §3). | §3 below | Check each flagged item against the original publication |
| D-06 | Do not select datasets, models, or metrics yet. | The review names no datasets, and none were supplied by you. Choosing now would require inventing/assuming. | §1 table | Provide constraints (see §4); dataset candidates will be proposed and marked INFERRED |

---

## 3. Items in the review that need verification before reuse

These are flagged because they affect whether claims can be carried into the implementation paper.

| # | Location in review | Issue | Status |
|---|---|---|---|
| V1 | §3.1, sequence log-probability bullet | Attributes the idea to "Guerreiro et al." through "Alkaissi & Lee's survey lineage cited in Huang et al., 2025". Guerreiro et al. is **not in the reference list**, and the Alkaissi & Lee attribution is confusing. Cite the original Guerreiro et al. paper directly after checking it. | UNKNOWN (needs original) |
| V2 | §3.1 | "Chuang et al." and "Das et al." are cited for entropy–factual-hallucination correlation, but **Das et al. is not in the references**; Chuang appears only as "Chuang et al., 2024" in §3.5 with no reference entry. The claim is routed via arXiv:2501.01059. | UNKNOWN |
| V3 | §3.3 | "Kernel Language Entropy (Nikitin et al.)" has no reference entry and is "cited in Kossen et al., 2024" (a 2024 paper). Verify the original paper and the claim about it. | UNKNOWN |
| V4 | §5, Miscalibration | Says instruction tuning/RLHF degrade calibration, citing Kadavath et al. (2022) and Guo et al. (2017). Guo et al. (2017) predates RLHF-era LLMs, so it cannot support the RLHF part. Verify what Kadavath et al. actually report. | INFERRED misattribution |
| V5 | §3.3, §5 | The "five- to ten-times" inference overhead is attributed to Kossen et al. (2024) and Manakul et al. (2023). Confirm the exact figure and context in those papers. | UNKNOWN |
| V6 | §1 | Farquhar et al. (2024) is cited for legal-citation fabrication, false news and medical risk. Verify this is what that paper says. | UNKNOWN |
| V7 | §2.2 | Claim that epistemic uncertainty is "the more informative" of the two components (Xiao & Wang, 2021). Verify against the paper and its tasks (captioning, data-to-text only). | UNKNOWN |
| V8 | §4, ref. 15 | TOKENHD (arXiv:2605.12384, listed as 2026) and the "0.6B outperforms larger reasoning models" claim. I cannot independently confirm this paper. Open the arXiv page and check. | UNKNOWN |
| V9 | Refs 18–21 | Four references have no author list (variance signals, attention-guided decoding, TokUR, density-based UQ). Add authors from the arXiv pages before submission. | VERIFIED (absence in review) |
| V10 | §3.5 | "Zhang and colleagues have proposed detection frameworks classifying..." is vague (no citation year/title). Identify the exact source. | UNKNOWN |

**Net effect:** the review's *structure and overall argument* are consistent, but its citations should not be copied into the implementation paper without these checks.

---

## 4. Information I need from you (UNKNOWN items)

1. **Deadline, venue/classroom format and length limit** for the implementation paper.
2. **Compute available:** GPU type/VRAM or free-tier only (decides model size and whether sampling-based methods like semantic entropy are feasible).
3. **Model access:** open-weight models you can run (for logits/hidden states) vs API-only.
4. **Programming comfort:** Python/PyTorch/Hugging Face level.
5. **Instructor constraints:** must the contribution be novel, or is a faithful reproduction + extension acceptable?
6. **Source files:** PDFs of the original papers for the top-gap citations (Kuhn 2023, Farquhar 2024, Kossen 2024, Xiao & Wang 2021, Kadavath 2022, Fadeeva 2024, Zhang 2023, Duan 2024). Attach them and I will check the flagged claims against the originals.

---

## 5. Next actions

| # | Action | Owner | Stage |
|---|---|---|---|
| 1 | Answer §4 questions | You | 1→2 |
| 2 | Attach original papers for V1–V10 checks | You | 1 |
| 3 | Run separate novelty searches for G1, G5, G3 | Claude (with web search) + you review | 2 |
| 4 | Convert top gap(s) into 2–3 research questions with hypotheses | Claude + you | 4 |
| 5 | Propose candidate datasets/models (marked INFERRED) and feasibility table | Claude | 3 |
| 6 | Reproduce one verified baseline before any new method | You (with Claude pair-programming) | 5 |

---
*Log started 2026-10-21. Append new entries; do not overwrite earlier decisions — mark superseded ones instead.*
