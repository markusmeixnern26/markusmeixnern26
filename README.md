# Claude Code Workspace Setup

A personal AI workspace built on [Claude Code](https://claude.ai/code), configured for product, data, and design workflows.
by Markus Meixner
---

## Agents

Six specialized agents installed globally (`~/.claude/agents/`) inspired by Akash Kedia

| Agent | Purpose | Triggers |
|---|---|---|
| **Router** | Detects workflow type, routes to the right agent | Every request |
| **Supervisor** | Session recovery + token limit continuity | Session start |
| **Skills Loader** | Loads specialized agents on demand | When a skill is needed |
| **PRD Agent** | Product discovery, feature planning, PRD creation | PRD / feature work |
| **Data Query Agent** | SQL queries, data analysis via Data Catalog + Sheets MCP | Data questions |
| **FigJam Agent** | User flows and diagrams via Mermaid + FigJam MCP | Visual flows |

### How it works

```
Request → Router detects intent
        → Skills Loader picks the right agent
        → Specialized agent executes
```

### Outputs

- PRDs, user flows, research → `~/ai/projects/product-planning/`
- SQL queries, analysis → `~/DataQueries/<question-slug>/`
- FigJam boards → returned as board URLs

---

## Status Line

Every session displays context usage and cost in real time:

```
[███░░░░░░░] 30%  cost: $0.0312
```

Pricing adjusts automatically per model (Opus / Sonnet / Haiku).
