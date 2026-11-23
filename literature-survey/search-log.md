# Search log

**Date of all searches:** 2026-11-23 (UTC)
**Review type:** targeted/scoping review of the literature needed to position a thesis on *verification gates for LLM-generated security patches*.
**Protocol:** metadata-driven search through scholarly indexes, followed by manual screening of titles/abstracts and open-access PDF retrieval.

This is not a PRISMA systematic review. The log exists so the search can be re-run and so the reader can see on what basis each source entered.

## Databases and services

| Service | Use | Notes |
|---|---|---|
| **OpenAlex** (`api.openalex.org`) | primary discovery; titles, venues, years, OA locations, citation counts | 26 queries, top 4 hits each screened by title/abstract |
| **Crossref** (`api.crossref.org`) | authoritative DOI metadata (authors, venue, volume, pages) | used to build `references.bib` |
| **arXiv** (`arxiv.org/abs/...`) | preprint metadata and full text | `export.arxiv.org` API was unresponsive on the day; abstract pages were used instead |
| **Semantic Scholar Graph API** | cross-check of identifiers and open-access PDF links | rate-limited (HTTP 429) on first attempts; batch endpoint retried successfully |
| **Unpaywall** | attempted OA lookup | returned HTTP 422 for the DOI list; abandoned, OpenAlex/Crossref used instead |
| **DBLP** | attempted cross-check of volume/pages | returned non-JSON; abandoned, not used for metadata |
| **Internet Archive Wayback Machine** | retrieved the MIT CSAIL author version of `qi2015` after dspace.mit.edu rate-limited (HTTP 429) | one archived PDF, verified against the report title |

## Query log (OpenAlex)

Filters: none by date or language at query time; English-language, peer-reviewed or arXiv works were preferred at screening. For each query the top 4 results by OpenAlex relevance were inspected.

| # | Query | Included from this query |
|---:|---|---|
| 1 | GenProg generic method automatic software repair | `leGoues2012` |
| 2 | Automatic Software Repair A Survey Gazzola Micucci Mariani | `gazzola2019`, `monperrus2018` |
| 3 | An Analysis of Patch Plausibility and Correctness for Generate-and-Validate Patch Generation Systems | `qi2015` |
| 4 | Is the Cure Worse Than the Disease Overfitting in Automated Program Repair | `smith2015` |
| 5 | Are Mutants a Valid Substitute for Real Faults in Software Testing | `just2014` |
| 6 | The Oracle Problem in Software Testing A Survey | `barr2015` |
| 7 | Identifying Patch Correctness in Test-Based Program Repair | `xiong2018` |
| 8 | Anti-patterns in Search-Based Program Repair | considered, excluded (no open copy; superseded by `qi2015`/`smith2015` for this argument) |
| 9 | Examining Zero-Shot Vulnerability Repair with Large Language Models | `pearce2023` |
| 10 | Asleep at the Keyboard Assessing the Security of GitHub Copilot Code Contributions | `pearce2022` |
| 11 | RepairAgent autonomous LLM-based agent program repair | `bouzenia2025` |
| 12 | IRIS LLM-assisted static analysis detecting security vulnerabilities | `li2025` |
| 13 | SequenceR sequence-to-sequence learning end-to-end program repair | `chen2019` |
| 14 | TFix learning to fix coding errors text-to-text transformer | none (TFix is a bug-fix model, not vulnerability-specific; superseded by `chen2019`, `zhang2024vul`) |
| 15 | InferFix end-to-end program repair with large language models | considered, excluded (ACM-only, no OA copy; role covered by `bouzenia2025`) |
| 16 | Vul4J dataset reproducible Java vulnerabilities program repair | `bui2022` |
| 17 | SWE-bench can language models resolve real-world github issues | `jimenez2024` |
| 18 | LiveCodeBench holistic contamination free evaluation of LLMs for code | `jain2025` |
| 19 | Judging LLM-as-a-Judge with MT-Bench and Chatbot Arena | `zheng2023` |
| 20 | CyberSecEval secure coding benchmark for language models | `bhatt2023` |
| 21 | LLM agents can autonomously hack websites | `fang2024` |
| 22 | PentestGPT LLM-empowered automatic penetration testing tool | `deng2023` |
| 23 | Large Language Models for Code Security Hardening and Adversarial Testing | `he2023` |
| 24 | VulRepair T5-based automated software vulnerability repair | considered, excluded (ACM-only, no OA copy; role covered by `zhang2024vul` and `hu2025`) |
| 25 | large language models vulnerability repair survey | `hu2025`, `zhang2024apr`, `le2024` |
| 26 | patch correctness large language models evaluation | none new (returned recent patch-correctness work already covered by `xiong2018`/`liu2021`; candidates were closed access) |

## Supplementary targeted lookups

| Lookup | Result |
|---|---|
| Crossref DOI resolution for every DOI-bearing entry | authors, venue, volume, issue, pages verified; `chen2019` has incomplete Crossref volume data (early access), so it is cited as the arXiv version with a note about the TSE publication |
| arXiv abstract pages for `1807.00515`, `1901.01808`, `2302.05319`, `2308.06782`, `2308.12533`, `2310.06770`, `2312.04724`, `2402.06664`, `2403.07974`, `2403.13193`, `2403.17134`, `2405.01466`, `2405.17238`, `2506.11697`, `2112.02125`, `2108.09293`, `1706.09120`, `2306.05685` | titles, author lists, years and abstracts verified |
| OpenAlex `abstract_inverted_index` for `leGoues2012`, `gazzola2019`, `smith2015`, `qi2015` | abstracts recovered for sources whose publishers do not expose them |
| Semantic Scholar batch endpoint | abstracts for `barr2015` and `bui2022`; OA links cross-checked |

## Retrieval failures and how they were handled

| Target | Problem | Resolution |
|---|---|---|
| `export.arxiv.org/api/query` | request timed out (30 s) | switched to `arxiv.org/abs/<id>` HTML metadata |
| `api.semanticscholar.org` single search | HTTP 429 | batch endpoint with retries; used only for cross-checks |
| `dl.acm.org/doi/pdf/...` | HTTP 403 (bot protection) | used arXiv/author versions instead |
| `ieeexplore.ieee.org/ielx7/...` | HTTP 418 (bot protection) | marked entry as metadata-only |
| `dspace.mit.edu` | HTTP 429 on repeated attempts | retrieved the same MIT-CSAIL-TR-2015-020 PDF from the Wayback Machine; verified title and authors on page 1 |
| `discovery.ucl.ac.uk` | HTTP 403 | metadata-only for `barr2015`/`smith2015` |
| `api.unpaywall.org` | HTTP 422 | abandoned |

## Reproducing the PDF set

Any PDF in `papers/` can be re-fetched from the URL recorded in the corresponding note (`notes/<key>.md`). Files are the open-access versions, not publisher PDFs, except where the publisher makes the version open (ICLR proceedings, ACM OpenTOC where the download succeeded).
