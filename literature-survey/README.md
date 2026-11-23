# Literature survey — verifying LLM-generated security patches

Course assignment: collect the relevant literature, store the sources, explain what each source contributes to the thesis, and provide complete bibliographic data.

**Compiled:** 2026-11-23 · **Review type:** targeted (scoping) review, not an exhaustive systematic review · **Sources:** 26 scholarly works, 21 with full-text PDF.

---

## The thesis this literature serves

> A security fix must do two things at once: close the hole, and leave the legitimate user able to work. Every check you can run is good at one of these and blind to the other, so "the tests pass" cannot be a sufficient acceptance criterion.

The thesis measures **how often the verification gate is wrong** when it accepts an automatically generated patch, and **what each additional check costs**:

| Stage | What it runs | What it is blind to |
|---|---|---|
| **O0** | the application's own test suite | wrong authorization that still returns 200 |
| **O1** | replay of the original exploit | degenerate fixes that block the legitimate user |
| **O2** | end-to-end user flows | subtle authorization errors that still return 200 |
| **O3** | mechanical rules on the patch shape | a small, clean, plausible patch that is wrong |
| **O4** | mutation of accepted patches — measures the gate, not the patch | — |

A human adjudication with a written six-verdict rubric (`corect`, `degenerat`, `sub-reparat`, `parțial`, `regresie`, `croitorit pe test`) is the reference. The main outcomes are **false accepts**, marginal detection gain per stage, and gate sensitivity under mutation. Apparatus: a ~1.5k-line Node/Express application with 15 seeded bugs (IDOR and missing-authorization cases, SQL injection, stored and reflected XSS, command injection, path traversal, SSRF, JWT verification, mass assignment, prototype pollution) and 90 patches (15 bugs × 3 attempts × 2 models).

---

## Repository layout

```
literature-survey/
├── README.md            this file: scope, coverage, how to use
├── references.bib       complete BibTeX for all 26 sources
├── search-log.md        databases, queries, dates, what was screened
├── screening.md         inclusion/exclusion criteria, decisions, exclusions
├── synthesis.md         thematic synthesis and the gap the thesis fills
├── papers/              21 full-text PDFs (open-access versions)
└── notes/
    ├── 00-INDEX.md      one-line relevance and placement for every source
    └── <key>.md         one note per source
```

Each note follows the same shape: **what the source establishes → the numbers worth citing → why it matters for this thesis → where to use it → what it does not let you claim → reading status**. Reading status is stated explicitly; most notes are grounded in the abstract and opening pages, not in a full read. Do not cite a claim in the thesis that the note does not support.

---

## Coverage by theme

| Theme | Sources | Role in the thesis |
|---|---|---|
| **APR foundations** | `leGoues2012`, `gazzola2019`, `monperrus2018` | vocabulary (generate-and-validate, plausible vs. correct patch); the snapshot → patch → verify → rollback lineage |
| **Patch correctness and overfitting** | `qi2015`, `smith2015`, `xiong2018`, `liu2021` | the core precedent: tests used to generate a patch cannot certify it; false accepts are a known, measured failure mode |
| **Test oracles** | `barr2015` | why O0/O1/O2 are different oracles, and why none of them is complete |
| **Mutation testing** | `just2014` | validity of O4: mutants as a proxy for real faults |
| **LLM vulnerability repair** | `pearce2023`, `pearce2022`, `chen2019`, `zhang2024vul`, `bouzenia2025`, `le2024`, `hu2025`, `zhang2024apr` | what current repair systems do, how they are evaluated, and why verification is the bottleneck |
| **LLM agents in security** | `fang2024`, `deng2023` | fixes and attacks are both agentic; tool access and feedback loops dominate capability |
| **Detection and secure generation** | `he2023`, `li2025`, `bhatt2023` | the upstream half (finding/avoiding vulnerabilities); also evidence that detection alone is not enough |
| **Evaluation methodology** | `jimenez2024`, `jain2025`, `zheng2023` | test-based acceptance as a benchmark oracle; contamination; human/LLM judgement and agreement |
| **Benchmarks** | `bui2022` | Vul4J: 79 reproducible Java vulnerabilities with proof-of-vulnerability tests, used for the optional real-CVE extension |

A one-paragraph-per-theme synthesis, including what is missing from the literature, is in [`synthesis.md`](synthesis.md).

---

## PDF availability

21 of 26 scholarly sources have a full-text PDF in `papers/`, downloaded from open-access sources: arXiv versions, one ICLR proceedings copy, the MIT DSpace author report (via the Internet Archive), and author/institutional copies from the University of Washington and the University of Luxembourg.

Five works are **metadata-only** because no open-access copy was found on 2026-11-23:

| Key | Why no PDF |
|---|---|
| `leGoues2012` | IEEE TSE, closed; no repository copy located |
| `gazzola2019` | IEEE TSE, closed; publisher "open" link is bot-blocked |
| `smith2015` | ACM FSE, closed; no repository copy located |
| `barr2015` | IEEE TSE, closed; publisher copy bot-blocked |
| `bui2022` | ACM MSR, closed; the Zenodo record hosts the dataset, not the paper |

They are still fully described in `references.bib` and `notes/`. Get the PDFs through the university library before quoting them at length.

---

## Using the bibliography

```latex
\usepackage[backend=biber,style=numeric]{biblatex}
\addbibresource{references.bib}
```

Keys are `firstauthorYEAR` (with a suffix where two works by the same author collide: `zhang2024vul`, `zhang2024apr`). Metadata was checked against Crossref, arXiv and OpenAlex records; arXiv preprints that later appeared at a venue carry the venue in a `note`, so the entry never claims more than was verified.

---

## Scope limits (state these in the thesis)

- This is a **targeted** review: 26 curated works, not a PRISMA-style systematic review. No claim of exhaustive coverage.
- It covers APR, LLM-based vulnerability repair, and evaluation methodology. It does **not** cover symbolic execution, fuzzing, or program analysis in depth; those are out of scope for a thesis about the acceptance gate.
- The thesis's own apparatus (synthetic app, 15 bugs) is deliberately not represented in this literature; no published work measures gate sensitivity on exactly this setup, which is the gap argued in `synthesis.md`.
- PDFs are redistributed only where the source is open access. Rights remain with the authors and publishers.

---

## Note on the thesis direction

The direction moved from "how contaminated is the benchmark" to "how much can you trust the verification". The survey is selected for the second question. Because the apparatus is built by the author, the survey cites no external benchmark or standards document: the 15 bugs are described by class, and the only benchmark entry (`bui2022`) is there for the optional real-CVE extension.
