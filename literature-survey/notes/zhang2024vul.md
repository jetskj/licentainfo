# Zhang et al. (2024) — Pre-Trained Model-Based Automated Software Vulnerability Repair: How Far Are We?

**Key:** `zhang2024vul` · **Type:** journal article, *IEEE Transactions on Dependable and Secure Computing* 21(4):2507–2525 · **DOI:** [10.1109/TDSC.2023.3308897](https://doi.org/10.1109/TDSC.2023.3308897) · **PDF:** `papers/zhang2024_pretrained-vuln-repair.pdf` (arXiv:2308.12533)

**Cluster:** LLM vulnerability repair · **Used in:** Related work; state of the art; H5

## What it establishes

The first extensive comparison of pre-trained models for **automated vulnerability repair**. On two vulnerability datasets:

- all studied pre-trained models **consistently outperform VRepair**, the prior state of the art, with prediction accuracy of **32.94%–44.96%**;
- the authors analyse three phases of the workflow — data pre-processing, model training, repair inference;
- a "simplistic" approach that transfers learning from **bug fixing** improves prediction accuracy by **9.40% on average**;
- additional discussion covers code representation and a preliminary study with ChatGPT, and the paper ends with practical guidelines for fine-tuning.

## Numbers worth citing

- 32.94%–44.96% prediction accuracy across pre-trained models.
- +9.40% average from transfer learning on bug-fix data.
- Two vulnerability datasets.

## Why it matters for this thesis

Two things:

1. **Calibration of the state of the art.** Even the best pre-trained repair models get roughly a third to a half of predictions right. That is the regime in which the thesis operates: a generator that is often right and sometimes wrong, which is exactly when the acceptance gate matters.
2. **The metric is prediction accuracy, not verified repair.** The paper measures whether the model predicts the right fix, not whether a downstream check would accept a wrong one. That is the gap the thesis addresses, and it should be stated without implying the authors missed something obvious — they are measuring the generator.

It also supports hypothesis H5 indirectly: if repair accuracy varies with vulnerability type and difficulty, the gate's false-accept rate should too.

## Where to use it

- Related work, state of the art in vulnerability repair.
- Method, justification for using two models rather than one: accuracy is model-dependent, so gate reliability may be too.
- Discussion: compare the thesis's `sub-reparat` rate with the ~33–45% repair accuracy reported here, while noting the metrics are not the same.

## Limits

Prediction-accuracy evaluation on curated vulnerability datasets, not end-to-end verified repair. The datasets are Java/C-centric and the models are pre-2024. Do not convert 32.94%–44.96% into a false-accept rate; the units differ.

## Reading status

Abstract read in full from the arXiv version; numbers above are from the abstract. Full text not read end to end.
