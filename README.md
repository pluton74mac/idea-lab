# Idea Lab

A methodology for accelerated idea development with AI agentic workflows.

Idea Lab provides a skill pack + project template that teaches your AI agent how to collaboratively shape, research, and develop ideas — from first thought to realized artifact. No phase boundaries, no promotion gates, no central workspace. Each idea is a standalone project from creation.

## Philosophy

**Ideas are projects from creation.** Not subfolders in a parent workspace. Not phases to graduate through. When you start an idea, you create a project — and research, design, and building happen in parallel within it.

**Research and building are parallel.** Spikes, prototypes, and code are valid research tools. There's no "research phase" vs "build phase" — build to learn.

**The forge methodology.** When an idea is fuzzy, you don't jump to implementation and you don't passively interview. You **forge** — a collaborative thinking process where the agent asks relentless questions one at a time, pushes back on weak assumptions, suggests alternatives, and crystallizes understanding progressively.

**Files appear as understanding firms up.** A new project starts with minimal files (IDEA.md, README.md, LOG.md, AGENTS.md, llm_wiki/). As technical decisions solidify, AGENTS.md grows, DECISIONS.md gets ADRs, PRD.md defines scope, code appears. The files ARE the status — no status field needed.

**LOG.md is agent-written.** The agent appends a date-stamped entry after every session, research run, or decision. This is the chronicle — the durable record that prevents starting from zero each session.

## What's Included

```
idea-lab/
├── skills/
│   ├── forge/                          # Collaborative thinking methodology
│   │   └── SKILL.md
│   └── idea-lab-workflow/              # Project conventions & file progression
│       ├── SKILL.md
│       └── references/
│           └── evaluating-existing-projects.md
├── template/                           # Clone this to start a new idea
│   ├── AGENTS.md                       # Auto-loaded conventions (references skills)
│   ├── IDEA.md                         # Problem, audience, solution, status
│   ├── README.md                      # Public overview
│   ├── LOG.md                          # Chronicle (agent-written)
│   ├── DECISIONS.md                   # ADR format
│   └── llm_wiki/.gitkeep              # Research KB (llm-wiki skill format)
└── README.md                           # You are here
```

## Skills

### `forge` — Collaborative Thinking

A general methodology for shaping fuzzy ideas, plans, and decisions through relentless questioning, pushback, and incremental crystallization. Not an interview — the agent is a co-builder that brings its own knowledge, challenges assumptions, and crystallizes understanding as it firms up.

**Core mechanics:**
- Every question goes through `clarify()` — one at a time, never questionnaires
- `todo` tool as a visible question buffer — the user sees the queue
- Five modes: inquire, push back, suggest, crystallize, challenge premise
- File-agnostic — crystallizes into whatever artifact fits the context
- 11 pitfalls encoding lessons from real use

**Inspired by:** Matt Pocock's `grilling` skill (the 6-line primitive) — `forge` is the evolved, opinionated version with co-builder modes (push back, suggest, challenge premise) that distinguish it from interviewer-only approaches.

### `idea-lab-workflow` — Project Conventions

Teaches the agent how to run an Idea Lab project: research methodology (llm-wiki integration), progressive file appearance, LOG.md chronicle format, evaluating existing projects, and operational pitfalls.

## Dependencies

- **`llm-wiki`** — Karpathy's LLM Wiki pattern for building interlinked markdown knowledge bases. Used for research in `llm_wiki/` directories. Install separately (it's a standard Hermes skill).

## Installation

### 1. Copy skills into your Hermes skills directory

```bash
# Clone this repo
git clone https://github.com/pluton74mac/idea-lab.git

# Copy skills
cp -r idea-lab/skills/forge ~/.hermes/skills/productivity/forge
cp -r idea-lab/skills/idea-lab-workflow ~/.hermes/skills/productivity/idea-lab-workflow
```

### 2. Ensure llm-wiki is installed

```bash
# If you don't already have it
# Install the llm-wiki skill into your Hermes skills directory
```

### 3. Start a new idea

```bash
# Copy the template
cp -r idea-lab/template ~/Documents/<my-idea-slug>

# Create a Hermes project (if using Hermes Agent)
hermes project create "<My Idea>" --path "~/Documents/<my-idea-slug>"
```

## Usage Flow

1. **Start a session** in the new project. The `AGENTS.md` auto-loads — the agent knows this is an Idea Lab project and which skills to use.

2. **Forge the idea.** The agent loads `forge` and begins collaborative shaping — asking questions one at a time via `clarify()`, pushing back on assumptions, suggesting approaches, and crystallizing understanding into `IDEA.md`.

3. **Research.** The agent uses `llm-wiki` to build an interlinked knowledge base in `llm_wiki/`. Research runs are recurrent — each picks up where the last left off.

4. **Crystallize as you go.** As decisions solidify, files appear: `DECISIONS.md` gets ADRs, `AGENTS.md` grows with technical conventions, `PRD.md` defines scope when ready.

5. **Build to learn.** Spikes and prototypes are valid research tools. There's no "research is done" gate — building IS research.

6. **LOG.md grows automatically.** The agent appends after every session, research run, or decision. This is the durable record.

## File Progression

```
Creation:    IDEA.md, README.md, LOG.md, AGENTS.md, llm_wiki/
                                    ↓
Research:    llm_wiki/ fills up (recurrent runs, interlinked pages)
                                    ↓
Design:      DECISIONS.md (ADRs), AGENTS.md grows, PRD.md (when scoped)
                                    ↓
Build:       Code, prototypes, spikes (parallel with continued research)
```

## License

MIT — use it, fork it, share it.

## Credits

- **`forge`** inspired by [Matt Pocock's](https://github.com/mattpocock/skills) `grilling` / `grill-me` skills — the relentless interview primitive. `forge` extends it with co-builder modes (push back, suggest, challenge premise).
- **`llm-wiki`** based on [Andrej Karpathy's LLM Wiki pattern](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f).
- Built and tested with [Hermes Agent](https://hermes-agent.nousresearch.com).
