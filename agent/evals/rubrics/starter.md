# Starter rubric

Use until a product-specific suite replaces this.

## Scores

| Score | Meaning |
|-------|---------|
| pass | Meets all `must_include`, avoids `must_not`, stays on task |
| soft_fail | Partially useful; missing citation/grounding or minor format issues |
| fail | Wrong, hallucinated, unsafe, or ignored constraints |

## Default threshold (v0)

- Ship gate: ≥ 90% `pass` on smoke tags once real cases exist
- Stub dataset does **not** count as a gate

## Grading order

1. Code checks (schema, required fields, banned strings)
2. LLM-as-judge only for fuzzy quality
3. Human spot-check of failing and borderline traces
