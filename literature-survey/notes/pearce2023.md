# Pearce et al. (2023) — Examining Zero-Shot Vulnerability Repair with Large Language Models

**Key:** `pearce2023` · **Type:** conference paper, IEEE S&P 2023, pp. 2339–2356 · **DOI:** [10.1109/SP46215.2023.10179324](https://doi.org/10.1109/SP46215.2023.10179324) · **PDF:** `papers/pearce2023_zero-shot-vuln-repair.pdf` (arXiv:2112.02125)

**Cluster:** LLM vulnerability repair · **Used in:** Related work; hypotheses H2/H3; motivation

## What it establishes

The paper studies whether LLMs can repair insecure code **zero-shot**, and what makes prompting work. It examines five commercially available black-box LLMs, an open-source model, and a locally trained model, on a mix of:

- synthetically generated vulnerabilities,
- hand-crafted scenarios,
- historical real-world vulnerabilities.

The headline result is deliberately split:

- the models **could collectively repair 100% of the synthetically generated and hand-crafted scenarios**;
- a **qualitative evaluation on historical real-world examples highlights challenges in generating functionally correct code**.

The paper also documents that prompt design — how the vulnerability is described, semantically and syntactically — materially affects whether a repair is produced.

## Numbers worth citing

- Five commercial LLMs + one open-source + one locally trained model.
- 100% collective repair on synthetic and hand-crafted scenarios.
- Functional correctness is the failure point on real-world examples.

## Why it matters for this thesis

This is the best single justification for the thesis's shift from "can it repair?" to "can you trust the acceptance?". If models can produce a security-looking patch for a synthetic case, then a benchmark built from synthetic cases will report high repair rates while the patches may still be functionally wrong. The thesis's apparatus is synthetic by design — so it must not repeat that mistake: hence O2 (legitimate flows) and the human `degenerat` verdict.

The synthetic-vs-real split also supports the thesis's decision to build its own application and report the choice as a limitation, rather than pretending synthetic bugs are representative.

## Where to use it

- Related work, LLM vulnerability repair: the canonical zero-shot reference.
- Introduction: "repair is not the bottleneck; verified repair is".
- Threats to validity: synthetic scenarios inflate success; the thesis compensates with controlled ground truth and explicit functional checks.

## Limits

Pre-agent, pre-2023 models; not a security-patch acceptance study. The 100% figure is on synthetic/hand-crafted scenarios and **must not** be quoted as a general repair rate. The paper does not measure false accepts against a human rubric.

## Reading status

Abstract read in full from the arXiv version; numbers above are from the abstract. Full text not read end to end.
