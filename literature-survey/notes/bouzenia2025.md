# Bouzenia, Devanbu & Pradel (2025) — RepairAgent: An Autonomous, LLM-Based Agent for Program Repair

**Key:** `bouzenia2025` · **Type:** conference paper, ICSE 2025, pp. 2188–2200 · **DOI:** [10.1109/ICSE55347.2025.00157](https://doi.org/10.1109/ICSE55347.2025.00157) · **PDF:** `papers/bouzenia2025_repairagent.pdf` (arXiv:2403.17134)

**Cluster:** LLM repair agents · **Used in:** Related work; agent design; cost reporting

## What it establishes

RepairAgent is an autonomous LLM agent for program repair. Instead of a fixed prompt or a fixed feedback loop, the LLM **plans and invokes tools**, interleaving:

- gathering information about the bug,
- gathering repair ingredients,
- validating fixes,

and deciding which tool to call next based on what it has learned. The enablers are a tool set for repair, a dynamically updated prompt format, and a finite-state machine that constrains tool invocation.

## Numbers worth citing

- **164 Defects4J bugs** repaired autonomously, including **39** not fixed by prior techniques.
- Average **270,000 tokens per bug**; about **14 cents per bug** at GPT-3.5 prices.

## Why it matters for this thesis

This is the closest engineering ancestor of the thesis's repair agent, and it establishes three design facts the thesis can rely on:

1. **An agent with tools is a credible generator** — the thesis does not need to justify using an agent loop.
2. **Cost is reportable and non-trivial** — token cost per patch is a real quantity, supporting the thesis's decision to log LLM cost alongside gate cost.
3. **Validation is part of the agent's own loop** — RepairAgent validates fixes while searching. That is precisely the conflation the thesis wants to break: the generator's self-check is not an independent gate. The thesis should keep the repairer's internal validation and the external acceptance gate separate, and say why.

It also supports the context-restriction design: RepairAgent shows that what the agent can inspect determines what it can do, so restricting the view is a meaningful experimental variable.

## Where to use it

- Related work, agentic repair.
- Method §agent: justify the snapshot → patch → judge → rollback loop and the tool set.
- Method §cost: precedent for reporting tokens and currency per patch.

## Limits

Defects4J (Java, general bugs), not security vulnerabilities. The 164-bug result is with the authors' tool set and a specific model/price point; do not generalise the cost. It does not measure false accepts against a human rubric.

## Reading status

Abstract read in full from the arXiv version; numbers above are from the abstract. Full text not read end to end.
