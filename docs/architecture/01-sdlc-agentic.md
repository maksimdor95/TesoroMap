# Agentic SDLC (factory model)

We do not ship a faster waterfall. We ship a **factory**: the system that produces software.

```
intent / specs  →  agents implement  →  tests + evals gate  →  observe / feedback
        ↑________________________________________________________|
```

## Spectrum (pick by stakes)

| | Vibe | Structured assist | Agentic engineering |
|--|------|-------------------|---------------------|
| Intent | Casual prompts | Detailed prompts | Specs, ADRs, memory files |
| Verify | “Seems fine” | Manual spot-check | CI tests + evals + hooks |
| Scope | Spikes, scripts | Features in known patterns | Production / team scale |
| Risk | High OK if disposable | Moderate | Low via systematic gates |

## Phase map

### Requirements & planning
- Conversation with AI produces draft specs + edge cases + schemas.
- Success criteria must be eval-able or testable before implementation expands.

### Design & architecture
- Humans decide trade-offs (consistency, cost, privacy, build/buy).
- Agents scaffold and conform once decisions are written down (`docs/`, rules, skills).

### Implementation
- Conductor for ambiguous/critical work; orchestrator for well-bounded tickets.
- Prefer small diffs with clear acceptance; avoid dumping whole-repo context.

### Testing & QA
- **Output** checks: compile, unit/integration tests.
- **Trajectory** checks for agents: right tools, right order, no unsafe calls.
- Quality flywheel: eval → cluster failures → fix harness/prompt/tools → regress → monitor.

### Review, deploy, maintain
- AI first-pass review; humans for design/security/strategy.
- Hooks block secrets and policy violations.
- Traces + cost/latency meters feed the next iteration.

## Roles

- **Conductor** — real-time direction in the IDE; high control.
- **Orchestrator** — async delegation with PR + eval delta review.

Skills that matter: specification, decomposition, evaluation, system design of constraints.
