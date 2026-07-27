# <Idea Name> — Agent Context

This is an Idea Lab project. The Idea Lab is a methodology for accelerated idea development with AI agentic workflows.

## Skills

- **`forge`** — collaborative thinking methodology for shaping ideas, plans, and decisions
- **`idea-lab-workflow`** — conventions for running an Idea Lab project (this project follows these)
- **`llm-wiki`** — research knowledge base (dependency — install separately if not available)

## Conventions

- Use `forge` when shaping the idea, resolving open questions, or stress-testing assumptions
- Use `llm-wiki` for research — recurrent runs that stack on prior findings
- LOG.md is agent-written — append after every session, research run, or decision
- Files appear progressively: IDEA.md → LOG.md → llm_wiki/ → DECISIONS.md → AGENTS.md updates → PRD.md → code
- This file (AGENTS.md) grows as technical decisions solidify

## File Purposes

| File | Purpose | Written by |
|---|---|---|
| IDEA.md | Problem, audience, solution, status | Human + Agent |
| README.md | Public overview — what, status, quick start | Agent |
| LOG.md | Chronicle — every session, research run, decision | Agent only |
| DECISIONS.md | ADRs — date + decision + rationale | Agent |
| llm_wiki/ | Research KB (llm-wiki skill format) | llm-wiki skill |
| PRD.md | Product requirements (when scoped) | Agent |
