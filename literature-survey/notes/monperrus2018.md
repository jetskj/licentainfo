# Monperrus (2018) — Automatic Software Repair: A Bibliography

**Key:** `monperrus2018` · **Type:** journal article (survey/bibliography), *ACM Computing Surveys* 51(1):1–24 · **DOI:** [10.1145/3105906](https://doi.org/10.1145/3105906) · **PDF:** `papers/monperrus2018_bibliography.pdf` (arXiv:1807.00515)

**Cluster:** APR foundations · **Used in:** Related work §APR; definition of the oracle

## What it establishes

A structured survey of automatic software repair that spans several research communities (software engineering, dependability, operating systems, programming languages, security). It separates:

- **behavioural repair**, where test suites, contracts, models, or crashing inputs are taken as the oracle;
- **state repair** (runtime repair/recovery), e.g. checkpoint-and-restart, reconfiguration, invariant restoration.

The taxonomy is the useful part. It makes explicit that in behavioural repair the oracle is not a neutral observer: it is whatever artefact the technique was handed. Test-suite-based repair is therefore *defined* by the weakness of its oracle.

## Numbers worth citing

- None in the abstract; cite the taxonomy and the scope (multi-community survey), not statistics.

## Why it matters for this thesis

The thesis's O0 is behavioural repair's oracle in its purest form: the application's own tests. Monperrus's taxonomy lets the thesis say precisely what it is measuring — not "repair quality" in general, but the reliability of one oracle and of the checks added around it.

It also justifies treating runtime rollback as part of repair rather than as an implementation detail: state repair is a recognised category, and the thesis's snapshot/rollback mechanism belongs to it.

## Where to use it

- Related work, alongside `gazzola2019`: two complementary maps (one algorithm-oriented, one taxonomy-oriented).
- Method §definitions: "oracle" and "plausible patch" are used in the sense established by this literature.
- Introduction: one sentence locating the work in behavioural repair.

## Limits

A 2018 bibliography; it cannot support claims about LLM repair. It is a map, not evidence about error rates. Do not cite it for the claim that tests are insufficient — that claim needs `smith2015`, `qi2015`, or `xiong2018`.

## Reading status

Abstract and first pages read from the arXiv author version; taxonomy taken from the abstract and section structure. Not read end to end.
