# Evals

## Layout

```
agent/evals/
  README.md
  datasets/           # jsonl / yaml cases
  rubrics/            # scoring definitions
  runners/            # executable eval entrypoints (added with first suite)
```

## Case format (starter)

`datasets/example.jsonl` — one JSON object per line:

```json
{"id":"ex-001","input":{"question":"..."},"expected":{"must_include":["..."],"must_not":["..."]},"tags":["rag","smoke"]}
```

## Rubric minimum

Document per suite:

- What is scored (task success, groundedness, schema, tool trajectory, safety)
- Pass threshold
- Grader type(s)
- How to reproduce locally

## Command convention (when runners exist)

```bash
# example — define with first real suite
pnpm eval --suite <name>
# or
python -m agent.evals.runners.<name>
```

CI should run the suite(s) touched by the PR.
