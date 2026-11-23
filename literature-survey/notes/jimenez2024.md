# Jimenez et al. (2024) — SWE-bench: Can Language Models Resolve Real-World GitHub Issues?

**Key:** `jimenez2024` · **Type:** conference paper, ICLR 2024 · **DOI:** [10.48550/arXiv.2310.06770](https://doi.org/10.48550/arXiv.2310.06770) · **PDF:** `papers/jimenez2024_swebench.pdf` (ICLR proceedings; arXiv:2310.06770)

**Cluster:** Evaluation methodology · **Used in:** Related work; Threats to validity

## What it establishes

SWE-bench is an evaluation framework of **2,294 software-engineering problems** drawn from real GitHub issues and their pull requests, across **12 popular Python repositories**. The model receives a codebase and an issue description and must edit the codebase to resolve it. Solutions frequently require coordinating changes across functions, classes and files, interacting with an execution environment, and handling long contexts.

The evaluation result at publication: even strong proprietary models and the authors' fine-tuned SWE-Llama could resolve only the simplest issues; **Claude 2 solved 1.96%**.

## Numbers worth citing

- 2,294 problems · 12 Python repositories.
- Best model at publication: 1.96% resolved.

## Why it matters for this thesis

SWE-bench is the clearest example of **tests as the acceptance oracle** for real repository edits: a patch is "resolved" if the repository's tests pass. That is O0 at industrial scale. The thesis's critique applies directly — and the thesis's contribution is to measure what that oracle misses when the patch is security-relevant and a plausible-looking wrong fix is available.

Use it in two places:

1. **Legitimacy:** test-based acceptance is the field's default, not a straw man the thesis invented.
2. **Contrast:** SWE-bench measures *whether* a model can produce a passing patch; the thesis measures *whether passing means correct*, with a human reference.

## Where to use it

- Related work, evaluation methodology.
- Threats to validity: the thesis's apparatus is small and synthetic, while SWE-bench is large and real; explain the trade-off (controlled ground truth vs. representativeness).
- Do not cite the 1.96% as current state of the art; it is the publication-time result.

## Limits

Python-only, issue-resolution tasks, not security patches. Its oracle is the repository test suite, whose coverage and quality vary. It does not measure false accepts.

## Reading status

Abstract read in full from the ICLR PDF; numbers above are from the abstract. Full text not read end to end.
