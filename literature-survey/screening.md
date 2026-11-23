# Screening and selection

**Screening date:** 2026-11-23 · **Records inspected:** 104 top-ranked hits across 26 OpenAlex queries, plus targeted DOI/arXiv lookups · **Included:** 26 scholarly works · **Full text available:** 21.

## Review question used for screening

> Which published work bears on **whether a check that accepts an automatically generated security patch can be trusted**, and on how such checks are built, measured, or shown to fail?

Sub-questions used to classify a candidate:

1. Does it define or measure the difference between a *plausible* patch and a *correct* patch?
2. Does it show a verification method failing in a specific, attributable way (overfitting, weak oracle, degenerate fix, gate insensitivity)?
3. Does it describe the current capability of LLM-based repair/attack agents, so the thesis can position itself against the state of the art?
4. Does it provide a benchmark or evaluation practice the thesis reuses (Vul4J, test-based acceptance, human agreement)?

A source was included if it answered at least one sub-question *and* passed the quality gates below.

## Inclusion criteria

- Peer-reviewed paper, or a preprint with a verifiable arXiv/DOI record and substantial citation impact.
- English.
- Directly relevant to automated repair, vulnerability repair, patch correctness, test oracles, mutation testing, LLM security agents, or evaluation validity.
- Publication window 2012–2025. The lower bound is GenProg, the origin of the generate-and-validate loop the thesis inherits.
- Open-access full text preferred. A closed-access work was admitted only when it is a canonical reference that could not be replaced (five cases; listed in the README).

## Exclusion criteria

- Detection-only work with no repair or verification angle, unless needed to explain the upstream pipeline (`li2025`, `he2023` are the two deliberate exceptions).
- Fuzzing, symbolic execution, and program-analysis techniques not used by the thesis's gate.
- Benchmarks or leaderboards that duplicate a source already included (e.g., CyberSecEval 2/3, LiveCodeBench Pro).
- Works whose bibliographic record could not be verified from Crossref, arXiv, or OpenAlex.
- Non-English publications; opinion pieces; blog posts.
- Duplicate versions of an included work (merged to the version of record, with the preprint noted).

## Deduplication

Ten published/preprint pairs were merged by DOI or arXiv ID, keeping the version of record and noting the preprint in the BibTeX entry:

`pearce2023` (arXiv 2112.02125 / IEEE S&P), `pearce2022` (arXiv 2108.09293 / IEEE S&P), `chen2019` (arXiv 1901.01808 / IEEE TSE), `zhang2024vul` (arXiv 2308.12533 / IEEE TDSC), `bouzenia2025` (arXiv 2403.17134 / ICSE), `li2025` (arXiv 2405.17238 / ICLR), `jimenez2024` (arXiv 2310.06770 / ICLR), `jain2025` (arXiv 2403.07974 / ICLR), `hu2025` (arXiv 2506.11697 / USENIX Security), `zhang2024apr` (arXiv 2405.01466 / TOSEM).

`bui2022` was matched across the MSR paper, the Zenodo artifact, and the ACM record; only the paper is cited, with the artifact in a `note`.

## Included sources and decision basis

| Key | Year | Venue | Type | PDF | Cluster | Why it was kept |
|---|---|---:|---|---|---|---|
| `leGoues2012` | 2012 | IEEE TSE | journal | — | APR foundations | origin of generate-and-validate repair; the snapshot → verify → rollback lineage |
| `gazzola2019` | 2019 | IEEE TSE | survey | — | APR foundations | 108-paper map of repair; supplies the field's vocabulary |
| `monperrus2018` | 2018 | ACM CSUR | survey/bibliography | ✓ | APR foundations | broader map including runtime repair and oracles |
| `qi2015` | 2015 | ISSTA | conference | ✓ | Patch correctness | shows reported patches are often not even plausible; isolates evaluation-infrastructure error |
| `smith2015` | 2015 | ESEC/FSE | conference | — | Patch correctness | independent tests reveal overfitting; the direct ancestor of the thesis's O0 critique |
| `xiong2018` | 2018 | ICSE | conference | ✓ | Patch correctness | automatic correctness assessment; 56.3% of incorrect patches filtered without blocking correct ones |
| `liu2021` | 2021 | JSS | journal | ✓ | Patch correctness | critical review of APR evaluation practices and metrics |
| `barr2015` | 2015 | IEEE TSE | survey | — | Test oracles | defines the oracle problem; justifies treating O0/O1/O2 as different oracles |
| `just2014` | 2014 | FSE | conference | ✓ | Mutation testing | validates mutants as proxies for real faults (357 faults, 5 projects) — the basis for O4 |
| `pearce2023` | 2023 | IEEE S&P | conference | ✓ | LLM vuln repair | zero-shot LLM vulnerability repair; shows functional correctness is the weak point |
| `pearce2022` | 2022 | IEEE S&P | conference | ✓ | Secure generation | ~40% of 1,689 Copilot programs vulnerable — motivation for downstream verification |
| `chen2019` | 2019 | arXiv / IEEE TSE | preprint | ✓ | LLM repair | sequence-to-sequence repair; establishes the "correct patch" measurement problem at scale |
| `zhang2024vul` | 2024 | IEEE TDSC | journal | ✓ | LLM vuln repair | systematic comparison of pre-trained vulnerability repair; 32.94–44.96% accuracy |
| `bouzenia2025` | 2025 | ICSE | conference | ✓ | LLM repair agents | autonomous repair agent, 164 Defects4J bugs; closest engineering ancestor of the thesis's agent |
| `le2024` | 2024 | WWW Companion | conference | ✓ | LLM vuln repair | JavaScript-specific repair; context in the prompt changes correctness |
| `hu2025` | 2025 | USENIX Security | SoK | ✓ | LLM vuln repair | systematises AVR into analysis → generation → **validation**; directly frames the thesis's stage |
| `zhang2024apr` | 2024 | arXiv / TOSEM | SLR | ✓ | LLM repair | 189 papers, 2020–2025; confirms evaluation is an open problem |
| `fang2024` | 2024 | arXiv | preprint | ✓ | LLM security agents | autonomous web hacking without prior knowledge; shows tool loops are the capability driver |
| `deng2023` | 2023 | arXiv | preprint | ✓ | LLM security agents | PentestGPT; context loss as the limiting factor in agentic security work |
| `he2023` | 2023 | ACM CCS | conference | ✓ | Secure generation | SVEN: hardening vs. adversarial testing; the "train it to be safe" alternative to verification |
| `li2025` | 2025 | ICLR | conference | ✓ | Detection | IRIS: LLM + static analysis detects 55/120 vs. CodeQL's 27 — the upstream half |
| `bhatt2023` | 2023 | arXiv | preprint | ✓ | Security benchmarks | CyberSecEval; automated insecure-code benchmark, and its limits |
| `jimenez2024` | 2024 | ICLR | conference | ✓ | Evaluation methodology | SWE-bench: tests as the acceptance oracle for real repository edits |
| `jain2025` | 2025 | ICLR | conference | ✓ | Evaluation methodology | LiveCodeBench: contamination-free evaluation; the leakage argument |
| `zheng2023` | 2023 | NeurIPS | conference | ✓ | Evaluation methodology | LLM/human judge agreement (>80%); supports the adjudication protocol design |
| `bui2022` | 2022 | MSR | conference | — | Benchmarks | Vul4J: 79 reproducible Java vulnerabilities with proof-of-vulnerability tests — the optional real-CVE extension |

## Considered and excluded

| Candidate | Reason |
|---|---|
| Tan et al., *Anti-patterns in Search-Based Program Repair* (FSE 2016) | No open copy; its "plausible but wrong" argument is covered by `qi2015`, `smith2015`, `xiong2018`. |
| *VulRepair: a T5-based automated software vulnerability repair* (ESEC/FSE 2022) | No open copy; its role is covered by `zhang2024vul` (which benchmarks against it) and `hu2025`. |
| *InferFix: End-to-End Program Repair with LLMs* (ESEC/FSE 2023) | No open copy; agentic repair covered by `bouzenia2025`. |
| *PatchAgent* (USENIX Security 2025, as cited in the internal notes) | Could not verify a bibliographic record in OpenAlex, Crossref, or arXiv on the search date; excluded rather than cited second-hand. |
| *TFix: Learning to Fix Coding Errors with a Text-to-Text Transformer* (ICML 2021) | Bug-fix model, not security-specific; superseded for this argument by `chen2019` and `zhang2024vul`. |
| CyberSecEval 2 / 3 | Extensions of `bhatt2023`; no additional argument needed for this thesis. |
| LiveCodeBench Pro, SWE-bench+, SWE-bench-java | Variants of included benchmarks; add no new methodological point. |
| Detection surveys and fuzzing/symbolic-execution work | Out of scope: the thesis measures the acceptance gate, not discovery. |
| Blog posts, vendor reports, and tool documentation | Not peer-reviewed; not usable as scholarly support. |

## Screening limitations

- Screening was done by one person on titles and abstracts, with full text consulted only to disambiguate. No dual screening, no kappa.
- OpenAlex relevance ranking is not a systematic search; relevant work outside the top 4 per query may exist.
- Citation counts were used as a quality signal at discovery time but are not reported as evidence.
- Closed-access works were admitted on canonical status; their content is summarised at abstract level only.
