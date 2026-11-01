# Evals

Evals separate professional AI work from API wrapping.

## Contract

Every AI-facing behavior that can ship needs:

1. **Dataset** — cases from real failures and real user intents (`agent/evals/datasets/`)
2. **Rubric** — what “pass” means (exact match, citation required, schema, policy)
3. **Grader** — code | LLM-as-judge | human (combine; never trust judges blindly)
4. **Runner** — reproducible command in CI or local harness
5. **Trace habit** — read trajectories before trusting scores

Start with **20–50** cases. Grow with production failures.

## Types

| Layer | Question | Typical method |
|-------|----------|----------------|
| Deterministic product code | Correct for input X? | Unit/integration tests |
| Retrieval | Right chunks? | Recall@k, citation checks |
| Generation | Answer quality / groundedness | Rubric + judge + spot human |
| Agent trajectory | Right tools / safe path? | Trace assertions |
| Ops | Cost, latency, drift | Metrics + budgets |

## Experiment discipline

- One variable at a time.
- Log runs (hypothesis, change, score, cost).
- Ablations: remove a harness piece; keep only measured wins.
- New model/prompt ships only with eval evidence.

## CI expectation

- PR touching prompts, tools, RAG, or agent loops must run the relevant eval suite (or document why blocked).
- Regressions fail the gate the same way unit tests do.
