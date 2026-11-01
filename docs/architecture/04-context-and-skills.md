# Context engineering & Agent Skills

Prompt wording helps. **Context selection** decides quality and cost.

## Six context types

1. **Instructions** — role, goals, boundaries  
2. **Knowledge** — docs, domain data, architecture  
3. **Memory** — session + durable project state  
4. **Examples** — few-shot and golden patterns  
5. **Tools** — precise APIs the agent may call  
6. **Guardrails** — hard constraints and validators  

## Static vs dynamic

| Static (always loaded) | Dynamic (on demand) |
|------------------------|----------------------|
| `AGENTS.md`, core rules | Matching `agent/skills/*` |
| Hard security invariants | RAG hits / tool results |
| Product non‑negotiables | Windowed history / deep refs |

Too much static → context rot and token burn.  
Too little → forgotten rules. Treat the boundary as versioned architecture.

## Agent Skills pattern

Each skill is a folder:

```
agent/skills/<skill-name>/
  SKILL.md          # when to use + procedure
  scripts/          # optional helpers
  references/       # deep material loaded only if needed
```

Progressive disclosure:

1. Agent sees short skill metadata  
2. Loads full `SKILL.md` when task matches  
3. Pulls references/scripts only if required  

Skills are portable procedural memory — prefer them over stuffing the system prompt.

## Coding-agent interaction

- Put always-true project law in rules / `AGENTS.md`.
- Put “how we do X” procedures in skills.
- Prefer MCP for external systems instead of one-off brittle integrations.
- Review skills and eval datasets in PRs like production code.
