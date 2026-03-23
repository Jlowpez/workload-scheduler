# workload-scheduler

> Constraint-based workload scheduling agent with what-if scenario analysis for operations planning.

![Phase](https://img.shields.io/badge/phase-4_in_development-f59e0b)
![CI](https://github.com/Jlowpez/workload-scheduler/actions/workflows/ci.yml/badge.svg)

## Status

Active development begins **Week 25**. This scaffold establishes the repository structure, documentation standards, and evaluation targets that will guide the Phase 4 build.

## What This Will Build

`workload-scheduler` is a Planner-Executor agent that generates and optimizes work schedules under real-world operational constraints — technician availability, equipment due dates, instrument capacity, and regulatory priorities. It supports what-if scenario analysis so planners can evaluate "what happens if I add three urgent jobs this week" without committing to the change.

## Agentic Pattern: Planner-Executor + Optimization

The agent first **plans** — generating a candidate schedule that satisfies all hard constraints. It then **executes** iterative optimization passes, evaluating alternatives and selecting the highest-scoring schedule. What-if queries run the same pipeline against a modified constraint set without touching the live schedule.

## Evaluation Targets

| Metric | Target |
|--------|--------|
| Constraint Satisfaction | 100% (no violations in generated schedules) |
| Due Date Coverage | ≥90% of overdue and near-due jobs scheduled |
| Resource Load | No resource exceeds 110% capacity |
| What-If Query Time | <15s per scenario |

## Part of a Larger System

| Agent | Pattern | Repo |
|-------|---------|------|
| knowledge-navigator | RAG Agent | [link](https://github.com/Jlowpez/knowledge-navigator) |
| intake-agent | Structured Output + Tool Use | [link](https://github.com/Jlowpez/intake-agent) |
| compliance-checker | Multi-Agent Pipeline | [link](https://github.com/Jlowpez/compliance-checker) |
| workload-scheduler | Planner-Executor | **this repo** |
| ops-orchestrator | Orchestrator / Router | [link](https://github.com/Jlowpez/ops-orchestrator) |

## Quick Start

> Active development begins Week 25. Full demo available at Phase 4 completion.

```bash
git clone https://github.com/Jlowpez/workload-scheduler
cd workload-scheduler
pip install uv && uv pip install -e ".[dev]"
pytest tests/ -v
```

## Production Path

Replace the constraint data in `data/synthetic/` with your organization's resource calendars, job queues, and capacity limits. The scheduling engine and optimization logic are unchanged — only the data source differs.

## See Also

- [ARCHITECTURE.md](ARCHITECTURE.md) — System design and component breakdown
- [TOOLS.md](TOOLS.md) — Tool and library selection rationale
- [ops-orchestrator](https://github.com/Jlowpez/ops-orchestrator) — full platform view
