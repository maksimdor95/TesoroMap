---
name: repo-workflow
description: How to change TesoroMap safely under agentic engineering. Use when starting a feature, fixing AI behavior, or preparing a PR.
---

# Repo workflow skill

## When to use

Starting any non-trivial change, especially prompts, RAG, tools, or agents.

## Procedure

1. Read `AGENTS.md` and relevant `docs/architecture/*` / `docs/product/*`.
2. State success criteria in the PR/description (testable or evalable).
3. If AI behavior changes: add/update cases under `agent/evals/datasets/` and note rubric.
4. Prefer smallest harness change that evals can measure.
5. Implement; run tests + relevant evals; attach score delta.
6. On failure: inspect traces, fix context/tools/gates, re-run.
7. Do not expand scope into unrelated refactors.

## Output expectations

- Clear intent
- Measured verification
- No secrets in logs/traces
