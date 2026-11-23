# Bhatt et al. (2023) — Purple Llama CyberSecEval: A Secure Coding Benchmark for Language Models

**Key:** `bhatt2023` · **Type:** preprint (arXiv:2312.04724) · **DOI:** [10.48550/arXiv.2312.04724](https://doi.org/10.48550/arXiv.2312.04724) · **PDF:** `papers/bhatt2023_cyberseceval.pdf`

**Cluster:** Security benchmarks · **Used in:** Related work; evaluation design

## What it establishes

CyberSecEval is a benchmark for the cybersecurity of LLMs used as coding assistants. It evaluates two domains:

1. the model's **propensity to generate insecure code**;
2. its **compliance when asked to assist in cyberattacks**.

The case study covers **seven models** from the Llama 2, Code Llama and OpenAI GPT families. A notable observation: **more advanced models tended to suggest insecure code**, which the authors read as a need to integrate security into model development. The benchmark includes an automated test-case generation and evaluation pipeline.

## Numbers worth citing

- Seven models evaluated.
- Two evaluation domains.

## Why it matters for this thesis

It shows the community's standard response to "LLMs write insecure code": build a benchmark and measure the model. That is a **generator-side** measurement. The thesis measures the **judge side** — whether an acceptance procedure can tell a good patch from a bad one. The distinction is clean and worth one sentence in related work.

CyberSecEval also illustrates a general evaluation risk the thesis must avoid: automated test-case generation can encode the benchmark author's assumptions. The thesis's controlled apparatus and human rubric are a deliberate alternative.

## Where to use it

- Related work, security benchmarks.
- Method §evaluation: contrast generator-side benchmarking with gate-side measurement.
- Do not cite it as evidence about repair.

## Limits

A benchmark paper; the results are model-specific and 2023-era. It does not evaluate patches, gates, or human adjudication.

## Reading status

Abstract read in full from the arXiv record; PDF downloaded and page count verified (extraction of the first page failed with the PDF library, so the note relies on the arXiv abstract). Full text not read.
