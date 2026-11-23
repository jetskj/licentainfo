# Smith et al. (2015) — Is the Cure Worse Than the Disease? Overfitting in Automated Program Repair

**Key:** `smith2015` · **Type:** conference paper, ESEC/FSE 2015, pp. 532–543 · **DOI:** [10.1145/2786805.2786825](https://doi.org/10.1145/2786805.2786825) · **PDF:** not available (closed access)

**Cluster:** Patch correctness · **Used in:** Motivation; hypothesis H1; Threats to validity

## What it establishes

The paper targets a specific defect in how repair tools were evaluated: **repairing with one set of tests and judging correctness with the same set**. Because tests are an imperfect metric of correctness, this cannot distinguish a correct patch from one that overfits the suite and breaks untested but desired behaviour.

They evaluate GenProg and TrpAutoRepair on a public benchmark where each bug has a human-written patch, and judge the generated patches with **tests independent from those used during repair**. Findings:

- the tools are **unlikely to improve the proportion of independent tests passed**;
- patch quality is **proportional to the coverage** of the suite used during repair;
- for programs that already pass most tests, the tools are **as likely to break tests as to fix them**;
- novice developers overfit too, and automated repair performs **no worse than these developers**.

## Numbers worth citing

- Two tools: GenProg and TrpAutoRepair.
- The qualitative claims above; the abstract does not give a single headline percentage, so do not invent one.

## Why it matters for this thesis

This is the direct ancestor of the thesis's central complaint. O0 is exactly the "same suite" evaluation Smith et al. criticise, applied to LLM-generated security patches. Their result supports hypothesis H1 (O0 has a high false-accept rate) without proving it for this setting.

Two nuances the thesis should keep:

1. **Automated repair is not uniquely bad.** Smith et al. show novice developers overfit at similar rates. The thesis should not frame the problem as "LLMs are worse than humans"; it is a property of test-based acceptance.
2. **Coverage matters.** The thesis's test suite is deliberately written like a normal project's suite — happy paths, no adversarial authorization cases. That is the condition under which Smith et al. predict overfitting, and it is a design choice the thesis must defend as realistic rather than as sabotage.

## Where to use it

- Introduction: one paragraph on why "tests pass" is not a correctness certificate.
- Method §O0: the design of the application's suite is justified by this result.
- Threats to validity: the suite is weak by construction, and that is the point — real project suites look like this.

## Limits

Pre-LLM, pre-security: the bugs are general-purpose defects, not access-control or injection vulnerabilities. The paper does not measure per-stage false accepts or cost. Cite it for the mechanism (overfitting to the validating suite), not for a rate.

## Reading status

Abstract read in full (OpenAlex abstract; Crossref record). Full text not read — no open-access copy.
