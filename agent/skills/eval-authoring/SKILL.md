---
name: eval-authoring
description: Create or extend eval datasets and rubrics for TesoroMap AI surfaces. Use when adding LLM/RAG/agent behavior or when quality regressions appear.
---

# Eval authoring skill

## When to use

- New AI feature or prompt change
- Production failure / hallucination to lock in
- Model or retrieval experiment

## Procedure

1. Collect 20–50 real inputs (user questions, tickets, logs) — not synthetic-only.
2. For each case write expected signal: gold answer, must_include, citations, or trajectory constraints.
3. Tag cases (`smoke`, `rag`, `tools`, `safety`).
4. Prefer code graders for schema/citations; use LLM-judge only where fuzzy.
5. Add a short rubric in `agent/evals/rubrics/`.
6. Run baseline; save score. Change one variable; compare.
7. Promote failing prod traces into the dataset after redaction.

## Anti-patterns

- Only happy-path demos
- Huge suites before a working smoke set
- Shipping prompt edits with no score delta
