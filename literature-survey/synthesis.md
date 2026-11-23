# Synthesis — what the literature already establishes, and what it leaves open

The thesis is not "LLMs can fix vulnerabilities" and not "a scanner plus an LLM works". It is a claim about an instrument: **the verification gate that decides whether a generated patch is acceptable**. The literature below is read through that lens.

## 1. A gate is an oracle, and the oracle problem is not new

`barr2015` defines the oracle problem: deciding whether observed behaviour is correct is a separate, expensive problem from producing the behaviour. Applied here, O0, O1 and O2 are three different oracles over the same patch: the developer's test suite, the attacker's replay, and the legitimate user's flow. None of them observes "the hole is closed *and* the application still works". That is not an implementation detail; it is the structural reason a single green check cannot be sufficient.

`gazzola2019` and `monperrus2018` give the field's vocabulary and show that repair research has always treated the test suite as the oracle of record. The consequence — that the oracle is part of the object being evaluated — is the opening the thesis exploits.

## 2. Plausible is not correct, and the gap has been measured before

Four works establish the core empirical fact:

- `qi2015` re-analysed reported patches from GenProg, RSRepair and AE and found that, because of errors in the evaluation infrastructure, **the majority were not even plausible**, and that most plausible patches were equivalent to deleting functionality. Their Kali system, which only deletes code, performed comparably to the repair tools.
- `smith2015` repaired with one test suite and evaluated with an independent one. GenProg and TrpAutoRepair did not improve the proportion of independent tests passed, and patch quality tracked the coverage of the suite used for repair.
- `xiong2018` built an automatic correctness assessor on runtime behaviour similarity and prevented **56.3% of incorrect patches** from being accepted without blocking correct ones — evidence that the gap is partly closable, but also that it needs machinery beyond the test suite.
- `liu2021` reviews APR evaluation practices and argues that reported repair rates are inflated by weak suites and inconsistent metrics.

This is the strongest part of the literature and it is also the reason the thesis must be precise about its contribution. "Tests can be fooled" is not new. What is not measured in these works is the **error profile of a composed gate** — per stage, false accepts versus false rejections, with the cost of each stage — on security patches, where the degenerate fix (deny everyone) is a realistic and attractive failure mode.

## 3. Mutation testing is the precedent for judging the judge

`just2014` is the methodological warrant for O4. Across 357 real faults in five projects, mutant detection correlated with real-fault detection independently of code coverage. If mutants are a defensible proxy for faults, then mutating an **accepted patch** is a defensible probe of whether the gate would have noticed a worse patch. The innovation in the thesis is not mutation testing; it is pointing mutation at the gate rather than at the test suite, and reporting **sensitivity per stage**.

## 4. LLM repair works often enough to make verification the bottleneck

The repair literature has moved from templates and learned bug-fixers (`chen2019`) to vulnerability-specific models (`zhang2024vul`, 32.94–44.96% prediction accuracy) to agents that plan and use tools (`bouzenia2025`, 164 Defects4J bugs fixed autonomously, 39 not fixed by prior techniques, ~270k tokens / 14 cents per bug). `pearce2023` shows zero-shot repair succeeds on synthetic and hand-crafted cases but struggles to produce functionally correct code on historical real-world examples. `le2024` finds the same for JavaScript: context in the prompt materially changes whether the fix is correct.

Two consequences for this thesis:

1. The capability exists, so a gate is needed; arguing "LLMs cannot fix code" would be false.
2. The failure mode is **functional correctness and side effects**, not inability to produce a security-looking diff. That is exactly what O0 is weak at and O2 is meant to catch.

`hu2025` (SoK) is the closest framing: it systematises automated vulnerability repair as analysis → patch generation → **patch validation**, and notes that tools are evaluated on heterogeneous, small datasets. It names validation as a phase but does not quantify how often validation accepts a bad patch. `zhang2024apr` (189 papers, 2020–2025) likewise lists evaluation as an open challenge. The thesis turns that open challenge into a measured quantity.

## 5. Agents and evaluation validity: two adjacent literatures that supply method, not answers

`fang2024` and `deng2023` show that agent capability is driven by tool access and by whether the loop preserves context. This supports the thesis's decision to restrict what the repair agent sees (vulnerable function plus one caller level) and to log the trajectory: the restriction is both a realism choice and a way to avoid a ceiling effect where every patch is correct.

On the evaluation side, `jimenez2024` makes tests the acceptance oracle for real repository edits, and `jain2025` shows why benchmarks must be contamination-free. The thesis inherits the test-as-oracle design and the contamination concern, but its apparatus is built rather than scraped, so the ground truth is controlled. `zheng2023` supplies the methodological anchor for adjudication: strong LLM judges reach **over 80% agreement** with human preferences, the same order as human–human agreement. That is relevant in reverse — it justifies reporting **human agreement** on a sample of re-judged patches, rather than pretending a single adjudicator is objective.

## 6. Secure generation and detection are the upstream half

`he2023` (SVEN) and `pearce2022` (~40% of 1,689 Copilot programs vulnerable) show that security can be pushed into generation. `li2025` (IRIS) shows that LLM-assisted static analysis detects more than CodeQL alone (55/120 vs. 27/120 on CWE-Bench-Java). These works explain why the input to the gate is a plausible-looking patch rather than obvious garbage. They do not evaluate acceptance.

## The gap

Put together, the literature contains:

- proof that test-based acceptance overfits (`smith2015`, `qi2015`),
- proposals for better correctness assessment (`xiong2018`),
- validation named as a phase of vulnerability repair (`hu2025`),
- mutation testing validated as a fault proxy (`just2014`),
- and evaluation-validity methods (`jimenez2024`, `jain2025`, `zheng2023`).

It does **not** contain a study that (a) composes a gate from heterogeneous checks, (b) measures **false accepts and false rejections per stage** against a written human rubric, (c) includes **degenerate fixes** as a first-class failure class, and (d) measures the **sensitivity of the gate itself** by mutating accepted patches — on security patches, in a setting where the ground truth is controlled.

That is the thesis's contribution: not a better repair system, but a measurement of how much the acceptance decision can be trusted, and at what cost.

## Hypotheses this reading makes defensible

| Hypothesis | Grounded in |
|---|---|
| O0 alone has a high false-accept rate on authorization bugs | `smith2015`, `qi2015`, `xiong2018` |
| O1 catches under-repair but is structurally blind to degenerate fixes | `qi2015` (functionality deletion), `barr2015` (oracle specificity) |
| O2 catches degenerate fixes but misses subtle authorization errors that still return 200 | `barr2015`, `smith2015` |
| O3 catches test-tampering and hardcoding that O1/O2 cannot see | `qi2015` (evaluation-infrastructure errors), `liu2021` |
| Gate sensitivity under mutation is well below 100% even when all stages pass | `just2014`, `jain2025` (benchmark validity) |

## One paragraph for the related-work section

> Automated repair has always been validated by tests, and the field has known for a decade that this overestimates correctness: patches that pass the generating suite may delete functionality (`qi2015`) or fail independent tests (`smith2015`). LLM-based vulnerability repair has made the generator stronger — agents now fix hundreds of real bugs (`bouzenia2025`) and repair benchmarks report tens of percent accuracy (`zhang2024vul`) — and systematisations name patch validation as a distinct phase (`hu2025`). What has not been measured is the reliability of that phase: how often a composed acceptance gate says "good" for a patch a human judge calls wrong, which stage is responsible, what each stage costs, and whether the gate would notice a deliberately worsened patch. This thesis measures exactly that.
