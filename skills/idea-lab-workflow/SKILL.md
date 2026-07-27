---
name: idea-lab-workflow
description: "Run an Idea Lab project — conventions for research, progressive files, LOG.md chronicle, and evaluation methodology."
version: 2.0.0
author: Franco + Hermes
license: MIT
metadata:
  hermes:
    tags: [idea-lab, ideas, projects, workflow, research, incubation]
    category: productivity
    related_skills: [forge, llm-wiki]
---

# Idea Lab Workflow

Conventions for running an Idea Lab project. This skill encodes how to work within a project that uses the Idea Lab methodology — research, file progression, logging, and evaluation.

## What an Idea Lab Project Is

An Idea Lab project is a standalone Hermes project where an idea is developed from first thought to realized artifact. Ideas are projects from creation — no promotion gate, no phase boundaries, no central workspace. Research, spikes, and building happen in parallel.

Each project follows a standard file structure (provided in the `template/` directory of the Idea Lab repo) and uses three skills:

- **`forge`** — collaborative thinking methodology for shaping the idea
- **`idea-lab-workflow`** (this skill) — conventions and file progression
- **`llm-wiki`** — research knowledge base (dependency)

## Starting a New Idea Project

1. Clone or copy the `template/` directory to a new location
2. Rename the folder to `<idea-slug>` (kebab-case, descriptive, short)
3. Create a Hermes project: `hermes project create "<name>" --path "<path>"`
4. Start a session in the new project and begin forging the idea

The template's `AGENTS.md` auto-loads and tells the agent what conventions to follow.

## Research

Use the **`llm-wiki` skill** for research. Key rules:

- Build interlinked markdown in `llm_wiki/`
- Research runs are **recurrent** — each run stacks on prior findings
- Visualize in Obsidian (graph view) if desired
- Research and building are parallel — spikes and prototypes are valid research tools. Build to learn.

### Populating a Wiki from Original Research

When doing original research (not ingesting existing sources), the efficient pattern:

1. **Batch web research** — fire all `web_search` calls in one turn. Follow up with `web_extract` on the best URLs.
2. **Synthesize** — read all results, extract key facts, frameworks, effect sizes. Write original pages, not copies.
3. **Delegate page writing** — for batches of 10+ pages, use `delegate_task` to write files. Pass ALL research content as context. The subagent writes pages, then creates index.md and log.md.
4. **Verify** — spot-check 2-3 pages for frontmatter compliance and wikilink integrity.
5. **Update LOG.md** — append a research entry to the project's LOG.md.

## Progressive Files

Files appear as the idea matures (NOT at creation — only IDEA.md, README.md, LOG.md, and `llm_wiki/` exist at creation):

**`AGENTS.md`** — when technical decisions are made:
- Architecture, tech stack, conventions
- Paths, ports, "never do X" rules
- This file already exists from the template — it grows as decisions solidify

**`PRD.md`** — when scope is defined:
- Features, constraints, users, success criteria

**`DECISIONS.md`** — when non-trivial choices need ADRs:
- Format: `## ADR #NNN — Title` with date, decision, rationale, alternatives

## LOG.md Format

Agent-written. Append after EVERY session, research run, or decision. The user never writes to it.

```markdown
# Chronicle — <Idea Name>

## YYYY-MM-DD — Type: Brief title
- **Discussed:** Key topics (sessions only)
- **Decisions:** What and why
- **Findings:** Results (research runs)
- **Next steps:** Concrete actions
- **Files touched:** New or updated files
```

Concise. Bullet points only. No narrative.

## Evaluating Existing Projects

When the user brings an existing project (with documentation, blueprints, or live code) for evaluation, follow the methodology in `references/evaluating-existing-projects.md` before starting the Idea Lab workflow. The goal is to understand what exists, what's obsolete, what gaps remain, and where the value lies.

## Anti-Patterns

- Don't create a project from a single offhand comment — wait for sustained signal
- Don't skip `clarify()` before creating a project — this is a joint decision
- Don't treat research and building as sequential phases — they're parallel
- Don't create AGENTS.md content for an idea with no technical decisions yet (the template's placeholder is enough)

## Pitfalls

### Verifying Platform Capabilities

When assessing whether your platform has a feature, **check the live docs before claiming it doesn't exist.** Skills cover known features, but platforms evolve fast. Run `hermes --help`, check docs, or use `web_extract` on the relevant docs page before giving a negative answer. Absence in a skill file is not evidence the feature doesn't exist.

### Compare Before Redesigning

When the user proposes a structural change, **compare the current and proposed systems side by side before executing.** Don't jump straight to building the new version. Present a comparison table so the user can evaluate trade-offs. The comparison itself is part of the decision process.

### Forge Each Doc Change Individually

When patching multiple sections of a document, forge each change one at a time — read the current text, propose the change, let the user push back or adjust, lock it, then move to the next. Don't batch-apply multiple changes without forging each one.

### Stale Skills from Abandoned Design Paths

When a design exploration produces a skill that describes a system you later decided NOT to build, that skill becomes stale and contradicts the final decision. Flag it for cleanup. Don't leave contradictory skills — future sessions will get confused about which model is active.

### Build Complete ≠ Validated

When a project reaches "build complete" (all tasks executed, files created, tests passed), that does NOT mean it's validated. The build proves the system *can* work — not that it *does* work over time.

Before declaring success:
1. Check what's actually running — are cronjobs enabled? Are foundation files filled with real content or still templates?
2. Check open design questions — were all deferred questions resolved?
3. Check success criteria — if the plan defined validation criteria, has ANY of the validation period elapsed?
4. A system built but never used is not validated.

**Pattern:** "Built but not used" is the most common false-positive for success.
