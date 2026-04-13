# Claude Code Workspace Setup

A personal AI workspace built on [Claude Code](https://claude.ai/code), configured for product, data, and design workflows.

by Markus Meixner

---

## Directory Structure

```
~/.claude/
├── CLAUDE.md               ← Tier 1: always loaded (this file)
├── agents/                 ← Specialized agents
│   ├── router-agent.md
│   ├── supervisor-agent.md
│   ├── skills-loader.md
│   ├── prd-agent.md
│   ├── data-query-agent.md
│   └── figjam-agent.md
├── skills/                 ← Reusable prompt patterns
│   └── daily-improvement.md
└── commands/               ← Slash-command automations

~/ai/projects/product-planning/   ← PRDs, user flows, research
~/DataQueries/                    ← SQL queries & analysis
~/ai/sessions/index.md            ← Session recovery index
```

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

### Routing pipeline

```
Request → Router detects intent (discovery / research / analysis /
          strategy / communication / automation)
        → Skills Loader picks the right agent
        → Specialized agent executes
```

### Outputs

- PRDs, user flows, research → `~/ai/projects/product-planning/`
- SQL queries, analysis → `~/DataQueries/<question-slug>/`
- FigJam boards → returned as board URLs

---

## Skills

| Skill | Description | Usage |
|---|---|---|
| **daily-improvement** | Researches latest Claude updates, audits current setup, produces prioritised improvement list | `"Run the daily improvement skill"` |

---

## MCP Servers

| Server | Tools |
|---|---|
| **Atlassian** | Jira (create/edit issues, transitions, worklogs) + Confluence (pages, comments, search) |
| **GitHub** | Repository access & authentication |
| **Figma** | Read designs, generate code, Code Connect mappings, FigJam diagrams |
| **OpenMetadata** | Data catalog access for SQL/data analysis workflows |

---

## Token Efficiency

Three-tier loading strategy keeps context lean:

| Tier | What | When loaded |
|---|---|---|
| 1 | `~/.claude/CLAUDE.md` | Always (every session) |
| 2 | Folder-level `CLAUDE.md` files | On query |
| 3 | Actual content files | On demand |

---

## Status Line

Every session displays context usage and cost in real time:

```
[███░░░░░░░] 30%  cost: $0.0312
```

Pricing adjusts automatically per model (Opus / Sonnet / Haiku).
