# Notes index

One note per source. Columns: what it is, whether the PDF is in `papers/`, the one thing it contributes to this thesis, and where it is likely to be cited.

| Key | Year | Short title | Type | PDF | Contribution to this thesis | Likely placement |
|---|---:|---|---|:--:|---|---|
| [leGoues2012](leGoues2012.md) | 2012 | GenProg | journal | — | origin of the generate-and-validate loop the gate inherits | Related work; Introduction |
| [gazzola2019](gazzola2019.md) | 2019 | APR survey | survey | — | field map and vocabulary (plausible/correct) | Related work §APR |
| [monperrus2018](monperrus2018.md) | 2018 | APR bibliography | survey | ✓ | broader map, including runtime repair and oracles | Related work §APR |
| [qi2015](qi2015.md) | 2015 | Patch plausibility | conference | ✓ | most reported patches were not even plausible; functionality deletion | Related work; O1/O2 rationale |
| [smith2015](smith2015.md) | 2015 | Overfitting in APR | conference | — | same-suite evaluation overfits; independent tests expose it | Motivation; H1 |
| [xiong2018](xiong2018.md) | 2018 | Patch correctness | conference | ✓ | automatic correctness assessment; 56.3% of bad patches blocked | Related work; Discussion |
| [liu2021](liu2021.md) | 2021 | Critical review of APR evaluation | journal | ✓ | evaluation practices inflate repair rates | Threats to validity |
| [barr2015](barr2015.md) | 2015 | Oracle problem | survey | — | O0/O1/O2 are different oracles, none complete | Method §definitions |
| [just2014](just2014.md) | 2014 | Mutants vs. real faults | conference | ✓ | mutants are a valid fault proxy — warrant for O4 | Method O4 |
| [pearce2023](pearce2023.md) | 2023 | Zero-shot vulnerability repair | conference | ✓ | LLMs repair synthetic cases but fail functionally on real ones | Related work; H2 |
| [pearce2022](pearce2022.md) | 2022 | Copilot security | conference | ✓ | ~40% of generated programs vulnerable | Introduction |
| [chen2019](chen2019.md) | 2019 | SequenceR | preprint/TSE | ✓ | learned repair at scale; "correct patch" measurement problem | Related work |
| [zhang2024vul](zhang2024vul.md) | 2024 | Pre-trained vulnerability repair | journal | ✓ | 32.94–44.96% accuracy; what SOTA repair looks like | Related work; state of the art |
| [bouzenia2025](bouzenia2025.md) | 2025 | RepairAgent | conference | ✓ | autonomous agent, 164 bugs; engineering ancestor | Related work; agent design |
| [le2024](le2024.md) | 2024 | JavaScript vulnerability repair | conference | ✓ | prompt context determines correctness in JS | Related work; stack choice |
| [hu2025](hu2025.md) | 2025 | SoK automated vulnerability repair | SoK | ✓ | names patch validation as a phase; heterogeneous evaluation | Related work; gap statement |
| [zhang2024apr](zhang2024apr.md) | 2024 | SLR LLMs for APR | SLR | ✓ | 189 papers; evaluation is an open challenge | Related work; gap statement |
| [fang2024](fang2024.md) | 2024 | LLM agents hack websites | preprint | ✓ | tool loops drive offensive capability | Related work; motivation |
| [deng2023](deng2023.md) | 2023 | PentestGPT | preprint | ✓ | context loss limits agentic security work | Related work; agent design |
| [he2023](he2023.md) | 2023 | SVEN | conference | ✓ | hardening vs. adversarial testing as an alternative | Related work; discussion |
| [li2025](li2025.md) | 2025 | IRIS | conference | ✓ | detection improves with LLM + static analysis (55/120 vs 27/120) | Related work; upstream half |
| [bhatt2023](bhatt2023.md) | 2023 | CyberSecEval | preprint | ✓ | insecure-code benchmark and its limits | Related work; evaluation |
| [jimenez2024](jimenez2024.md) | 2024 | SWE-bench | conference | ✓ | tests as acceptance oracle for real edits | Related work; threats to validity |
| [jain2025](jain2025.md) | 2025 | LiveCodeBench | conference | ✓ | contamination-free evaluation; leakage argument | Related work; threats |
| [zheng2023](zheng2023.md) | 2023 | LLM-as-a-judge | conference | ✓ | >80% judge–human agreement; adjudication methodology | Method §adjudication |
| [bui2022](bui2022.md) | 2022 | Vul4J | conference | — | 79 reproducible Java vulns with PoV tests; optional extension | Future work |

## How to read a note

Each note is structured as:

1. **What it establishes** — the claims the source actually supports.
2. **Numbers worth citing** — only figures verified in the abstract or the pages read.
3. **Why it matters here** — the mapping to this thesis's stages, hypotheses, or design choices.
4. **Where to use it** — a concrete placement, not just a topic.
5. **Limits** — what the source does *not* license you to claim.
6. **Reading status** — what was actually read (abstract, opening pages, or more).

If the thesis needs a stronger claim than the note supports, open the PDF and revise the note first.
