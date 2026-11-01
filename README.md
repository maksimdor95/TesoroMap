# TesoroMap

Карта для инвестора: область → участки/торги/местность → досье → (позже) совет ИИ.

**Стек v0:** Vite + React + MapLibre · FastAPI · PostgreSQL/PostGIS (локально docker, облако Neon).

Scaffolded for **agentic engineering**: intent → harness → implementation → tests/evals → observability.

## How we work with code & systems

| Layer | What it is |
|-------|------------|
| `AGENTS.md` + `.cursor/rules/` | Static contract for coding agents (always on) |
| `docs/architecture/` | Principles, SDLC, harness, evals, context/skills |
| `docs/product/` | Product intent (fill `vision.md` first) |
| `agent/skills/` | Dynamic procedures (Agent Skills) |
| `agent/evals/` | Quality instrument for AI behavior |
| `agent/harness/` | Policies around models/tools/gates |

**Vibe coding** is allowed for spikes. **Shipping** requires specs, tests/evals, and human judgment on architecture and risk.

## Start here

1. [`docs/product/roadmap.md`](docs/product/roadmap.md) — дорожная карта с чекбоксами (отжимай по мере готовности)
2. [`docs/product/vision.md`](docs/product/vision.md) — для кого продукт и как в него входят
3. [`docs/architecture/ARCHITECTURE.md`](docs/architecture/ARCHITECTURE.md) — канон системы
4. [`docs/product/analysis-loop.md`](docs/product/analysis-loop.md) — карта, слои, честные цифры
5. Качество рекомендаций — [`agent/evals/`](agent/evals/)

## Sources baked in

- Under the Hood — AI Engineer guide 2026 (API plane, harness, RAG→evals→agents, MCP/skills)
- Osmani / Saboo / Kartakis — *The New SDLC With Vibe Coding* (factory model, context engineering, conductor/orchestrator)
