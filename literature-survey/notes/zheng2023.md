# Zheng et al. (2023) — Judging LLM-as-a-Judge with MT-Bench and Chatbot Arena

**Key:** `zheng2023` · **Type:** conference paper, NeurIPS 2023 · **DOI:** [10.48550/arXiv.2306.05685](https://doi.org/10.48550/arXiv.2306.05685) · **PDF:** `papers/zheng2023_llm-judge.pdf` (arXiv:2306.05685)

**Cluster:** Evaluation methodology · **Used in:** Method §adjudication; Threats to validity

## What it establishes

Using strong LLMs as judges is a scalable way to evaluate open-ended model outputs. The paper examines the known limitations — **position bias, verbosity bias, self-enhancement bias, and limited reasoning ability** — and proposes mitigations. It then measures agreement between LLM judges and human preferences on two benchmarks:

- **MT-bench**: a multi-turn question set;
- **Chatbot Arena**: a crowdsourced battle platform.

The key result: strong judges such as GPT-4 can match both controlled and crowdsourced human preferences, achieving **over 80% agreement — the same level of agreement between humans**.

## Numbers worth citing

- >80% agreement between GPT-4 judge and human preferences.
- Comparable to human–human agreement.

## Why it matters for this thesis

The thesis uses a **human adjudicator** as the reference, not an LLM judge. This paper is still the right citation, for two reasons:

1. **Agreement is the right way to report judgement quality.** The thesis re-judges 20 patches and reports agreement with the primary adjudication. That mirrors the paper's method and gives the number a recognised interpretation: agreement in the 80% range is the human–human baseline, not a perfect score.
2. **Bias is expected, so protocol matters.** Position and verbosity bias have human analogues (order effects, first-impression effects). The thesis's blinding, fixed decision order, random patch order and written rubric are exactly the mitigations this literature recommends.

It also warns against the tempting shortcut of using an LLM as the adjudicator: the thesis's central claim is about trusting a judge, so the reference judge should not be another model with the same failure modes.

## Where to use it

- Method §adjudication: justify the blinding/ordering protocol and the re-judging sample.
- Threats to validity: adjudicator subjectivity, reported as agreement rather than denied.
- Discussion: why not LLM-as-judge for the reference standard.

## Limits

Chat-assistant evaluation, not code or security. The >80% agreement is task-dependent; do not assume the same rate for patch adjudication. The paper's mitigations reduce but do not eliminate bias.

## Reading status

Abstract read in full from the arXiv PDF; numbers above are from the abstract. Full text not read end to end.
