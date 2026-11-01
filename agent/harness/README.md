# Harness policies

Operational notes that surround models used by TesoroMap (product agents and coding agents).

## Current policies

- Prefer direct provider APIs + thin orchestration over heavy frameworks until complexity forces otherwise.
- Every tool needs: purpose, inputs schema, when-to-use prose, failure behavior, permission scope.
- Retries: bounded; surface errors to traces; do not infinite-loop on tool failure.
- Secrets never enter prompts or traces; redact before logging.
- Production agents require: eval suite, tracing, cost/latency budgets, scoped tools.

## Checklist before adding a new agent capability

- [ ] Spec + success criteria written
- [ ] Eval cases added (or explicitly deferred with owner/date)
- [ ] Skill or rule updated if behavior is reusable
- [ ] Tool permissions scoped
- [ ] Trace fields defined (inputs, tool calls, outputs, tokens, latency)
- [ ] Rollback / soft-fail UX for nondeterministic errors
