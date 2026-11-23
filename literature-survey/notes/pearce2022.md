# Pearce et al. (2022) — Asleep at the Keyboard? Assessing the Security of GitHub Copilot's Code Contributions

**Key:** `pearce2022` · **Type:** conference paper, IEEE S&P 2022, pp. 754–768 · **DOI:** [10.1109/SP46214.2022.9833571](https://doi.org/10.1109/SP46214.2022.9833571) · **PDF:** `papers/pearce2022_copilot-security.pdf` (arXiv:2108.09293)

**Cluster:** Secure code generation · **Used in:** Introduction (motivation); Related work

## What it establishes

Copilot is trained on public code, including vulnerable code, so it may reproduce insecure patterns. The authors prompt it with scenarios drawn from high-risk weaknesses (MITRE's "Top 25" CWE list) and analyse the results along three axes: **diversity of weakness, diversity of prompt, diversity of domain**.

## Numbers worth citing

- **89 scenarios**, producing **1,689 programs**.
- Approximately **40%** of the generated programs were vulnerable.

## Why it matters for this thesis

This is the upstream motivation: if a substantial fraction of generated code is insecure, then downstream verification is not optional. It also supports a framing choice — the thesis is not arguing that LLMs are bad at code; it is arguing that **the acceptance decision must be independent of the generator**, because the generator's output is sometimes subtly wrong.

The 40% figure should be used carefully: it is a rate over prompted scenarios, not over all Copilot completions in real use. Say "in their scenario suite, about 40% of 1,689 generated programs were vulnerable", not "40% of Copilot code is vulnerable".

## Where to use it

- Introduction, one paragraph: generated code is often insecure, so verification matters.
- Related work, secure-generation subsection, with `he2023` as the "fix the generator" alternative.
- Do not use it to claim that LLM-generated *patches* are insecure; that is a different measurement.

## Limits

2022, Copilot-only, CWE-scenario prompts. Does not evaluate repair or acceptance. The scenario construction may over-represent security-sensitive prompts relative to ordinary autocomplete.

## Reading status

Abstract read in full from the arXiv version; numbers above are from the abstract. Full text not read end to end.
