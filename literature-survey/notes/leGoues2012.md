# Le Goues et al. (2012) — GenProg: A Generic Method for Automatic Software Repair

**Key:** `leGoues2012` · **Type:** journal article, *IEEE Transactions on Software Engineering* 38(1):54–72 · **DOI:** [10.1109/TSE.2011.104](https://doi.org/10.1109/TSE.2011.104) · **PDF:** not available (closed access)

**Cluster:** APR foundations · **Used in:** Related work; Method (the snapshot → verify → rollback lineage)

## What it establishes

GenProg repairs defects in off-the-shelf C programs without formal specifications or annotations. It uses an extended form of genetic programming to evolve a program variant that keeps the required functionality while avoiding the defect, with the **existing test suite encoding both** the defect and the required functionality. Structural differencing and delta debugging then reduce the variant to a minimal repair.

This is the canonical statement of *generate-and-validate* repair: a candidate is accepted because it passes the tests you have, not because it is known to be correct. Every later gate, including the one this thesis measures, is a descendant of that acceptance rule.

## Numbers worth citing

- 16 programs, 1.25 M lines of C plus 120 K lines of module code.
- Eight classes of defects.
- Average repair time: 357 seconds.

## Why it matters for this thesis

Two uses, both defensive:

1. **Lineage.** The thesis's agent loop (snapshot → patch → judge → rollback) is an agentic version of GenProg's evolve-and-test loop. Claiming novelty for the loop would be wrong; the novelty is in measuring the *acceptance decision*.
2. **The oracle is inside the technique.** GenProg's acceptance criterion is the test suite it was given. The thesis's O0 is the same criterion, modernised. The critique that follows (`smith2015`, `qi2015`) applies to the whole lineage, not just to GenProg.

It also supports the decision to report *cost per patch*: GenProg already reported runtime as a first-class result, and the thesis reports time per gate stage.

## Where to use it

- Related work, first paragraph of the APR subsection: "automated repair begins with generate-and-validate".
- Method, when justifying rollback: the loop must restore state when validation fails, because a rejected candidate must not contaminate the next attempt.
- Introduction, one clause: the thesis inherits a 13-year-old loop and asks a different question about it.

## Limits

GenProg predates LLMs and has nothing to say about semantic plausibility, security properties, or human adjudication. Its success rates were later shown to depend heavily on the evaluation infrastructure (`qi2015`). Do **not** cite GenProg as evidence that automated repair works; cite it as the origin of the acceptance rule.

## Reading status

Abstract and bibliographic metadata read (publisher abstract via OpenAlex; Crossref record). Full text not read — no open-access copy.
