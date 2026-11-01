# TesoroMap — Agent Operating Contract

This repo practices **agentic engineering**, not ad-hoc vibe coding for anything that ships.

Human role: intent, architecture, judgment, verification.  
Agent role: implementation inside a harness of specs, tests, evals, and guardrails.

## Product stance

- We **consume** models via API (plane 2). We do not train or fine-tune by default.
- Advantage lives in the **harness** (context, tools, gates, evals, observability), not in model choice.
- Prototype freely (vibe). Ship only with agentic discipline (specs → implement → test+eval → observe).

## Stack defaults (until product docs override)

- Prefer simple composable patterns and direct API calls over heavy agent frameworks.
- Prefer RAG + prompting over fine-tuning.
- Prefer MCP for tool/data connectors; treat Agent Skills as portable procedural knowledge.
- Prefer model routing: cheap/fast for classification & extraction; strong models for hard reasoning.

## Static context (always on)

1. This file (`AGENTS.md`)
2. `.cursor/rules/*.mdc`
3. `docs/architecture/*` and `docs/product/*` when relevant

Keep static context short and high-signal. Put deep procedures in `agent/skills/*/SKILL.md` (dynamic).

## Working modes

| Mode | When | Expectation |
|------|------|-------------|
| Conductor | Ambiguous logic, architecture, debugging | Real-time guidance; human reviews each critical change |
| Orchestrator | Well-specified tasks with tests/evals | Agent executes; human reviews PR + eval deltas |

## Factory loop (every feature that matters)

1. Spec intent and success criteria (what “correct” means)
2. Add/extend tests (deterministic) and evals (non-deterministic)
3. Implement inside harness constraints
4. Run tests + eval suite; read traces on failures
5. Ablate: change one variable at a time; keep only measured wins
6. Ship with observability (traces, cost, latency, quality)

## Hard rules

- Do not ship AI behavior without an eval path (even a 20–50 case starter set).
- Do not dump entire repos into prompts; retrieve/load skills on demand.
- Do not treat “it seems to work” as verification for production paths.
- Humans own architecture trade-offs, security boundaries, and release judgment.
- When the agent fails, fix the **harness** (rules, tools, context, gates) before blaming the model.

## Where things live

| Concern | Path |
|---------|------|
| Architecture principles | `docs/architecture/` |
| Product intent | `docs/product/` |
| Agent skills (dynamic) | `agent/skills/` |
| Eval datasets & runners | `agent/evals/` |
| Harness notes / policies | `agent/harness/` |
| Traces / run artifacts | `agent/traces/` (local; do not commit secrets) |
