# Gazzola, Micucci & Mariani (2019) — Automatic Software Repair: A Survey

**Key:** `gazzola2019` · **Type:** journal article (survey), *IEEE Transactions on Software Engineering* 45(1):34–67 · **DOI:** [10.1109/TSE.2017.2755013](https://doi.org/10.1109/TSE.2017.2755013) · **PDF:** not available (closed access)

**Cluster:** APR foundations · **Used in:** Related work §APR; terminology

## What it establishes

A survey of **108 papers** on automatic software repair. It organises the algorithms and approaches, compares them on representative examples, and discusses open challenges and the empirical evidence reported so far. Its stated motivation is that repair techniques have proliferated into a heterogeneous research framework that needs structuring.

## Numbers worth citing

- 108 papers surveyed.

## Why it matters for this thesis

This is the reference to cite for the **field's vocabulary**, so the thesis does not have to invent it:

- *repair* as producing a change that makes a failing behaviour acceptable;
- *generate-and-validate* as the dominant architecture;
- the distinction between a patch that satisfies the available tests and one that is actually correct.

The survey also documents that repair results are reported with heterogeneous benchmarks and metrics — the same problem `liu2021` attacks directly. That gives the thesis a defensible sentence: the evaluation problem is not incidental to the field; it is a recognised open challenge in its main survey.

Do **not** use it for claims about security patches: the surveyed literature is almost entirely general-purpose bug repair, not vulnerability repair.

## Where to use it

- Related work, opening of the APR subsection, together with `monperrus2018`: "two surveys map the field".
- Definitions section: cite it for the standard repair terminology the thesis reuses.
- Do not cite it for the thesis's specific claims about gates; it does not measure gate reliability.

## Limits

Published in 2019, so it predates LLM-based repair entirely. It cannot support statements about modern agents or foundation models. Full text was not read; only the abstract and metadata were available, so no specific page-level claim should be attributed to it.

## Reading status

Abstract and bibliographic metadata read (OpenAlex abstract; Crossref record). Full text not read — no open-access copy.
