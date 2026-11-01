# AI harness

```
Agent = Model + Harness
```

The model is rented. The harness is ours.

## Harness components (product + coding agents)

| Component | Responsibility | Repo home |
|-----------|----------------|-----------|
| Instructions / rules | Who the agent is; hard “never” | `AGENTS.md`, `.cursor/rules/` |
| Skills | On-demand procedures | `agent/skills/*/SKILL.md` |
| Tools / MCP | World actions with scoped permissions | product MCP servers + connectors |
| Context assembly | Static + dynamic retrieval | harness context builders |
| Sandbox | Safe execution boundaries | runtime / CI sandboxes |
| Orchestration | Loops, retries, handoffs, routing | agent runtime |
| Guardrails / hooks | Deterministic lifecycle checks | hooks, CI, pre-commit |
| Evals | Quality instrument | `agent/evals/` |
| Observability | Traces, cost, latency, drift | `agent/traces/` + prod telemetry |

## Product AI surfaces (when TesoroMap adds them)

Default build order (from the AI engineer track):

1. LLM API + structured outputs + prompt/context discipline  
2. RAG over real product/domain documents  
3. Evals (20–50 real cases) + tracing  
4. Tool use / MCP agents only after eval baseline exists  
5. Model routing + prompt caching for cost/latency  

Skip fine-tuning unless evals prove prompting + RAG are not enough.

## Failure default

When quality drops, inspect in order:

1. Missing/noisy context  
2. Missing tool or bad tool description  
3. Weak guardrail / no eval coverage  
4. Orchestration bug  
5. Model choice (last)
