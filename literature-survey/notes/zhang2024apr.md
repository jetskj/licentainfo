# Zhang et al. (2024) — A Systematic Literature Review on Large Language Models for Automated Program Repair

**Key:** `zhang2024apr` · **Type:** systematic literature review (arXiv:2405.01466); accepted to *ACM TOSEM* · **DOI:** [10.48550/arXiv.2405.01466](https://doi.org/10.48550/arXiv.2405.01466) · **PDF:** `papers/zhang2024_slr-llm-apr.pdf`

**Cluster:** LLM repair · **Used in:** Related work; gap statement

## What it establishes

The first systematic literature review of LLM applications in automated program repair, covering **2020–2025** and analysing **189 papers**. It:

- categorises popular LLMs used for APR and outlines **four types of utilisation strategies**;
- details repair scenarios that benefit from LLMs, including **semantic bugs and security vulnerabilities**;
- discusses critical integration aspects such as **input forms** and **open science**;
- lists open challenges and guidelines for future research.

## Numbers worth citing

- 189 papers, 2020–2025.
- Four utilisation strategies.

## Why it matters for this thesis

It is the broadest map of the space and it explicitly includes security vulnerabilities as a repair scenario. Two uses:

1. **Positioning.** The thesis can say that LLM-based APR is a mature-enough field for a systematic review (189 papers), and that security vulnerabilities are one of its recognised scenarios — so the thesis is not inventing a niche.
2. **The gap is acknowledged by the field.** The review's "challenges" section covers input forms, evaluation and open science. The thesis's question — reliability of the acceptance decision — sits inside that space but is not answered by any of the 189 papers as a measured quantity. State this carefully: the review does not say "nobody measured this"; the thesis argues it after reading the validation-related work.

## Where to use it

- Related work, first paragraph of the LLM-APR subsection.
- Introduction, one sentence establishing the size of the field.
- Do not use it as evidence for a specific technical claim; it is a map.

## Limits

A review, not an experiment. Its coverage stops in 2025 and its categories may not match the thesis's stages. Cite it for scope and trends, not for rates. The TOSEM version may differ from the arXiv version used here; the entry is keyed to the arXiv version with the acceptance noted.

## Reading status

Abstract read in full from the arXiv version; 56 pages verified. Full text not read end to end.
