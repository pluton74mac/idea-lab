# Evaluating Existing Projects

When the user brings a project that already has artifacts (blueprints, design docs, running code, reference implementations) for evaluation. This is a distinct workflow from "fuzzy idea conversation" — the artifacts exist, the question is what they mean and what's next.

## When to Use

- The user says "evaluate this project" and points to a folder with documentation
- A project exists with designs + code that needs assessment
- An MCP server, library, or tool was built from blueprints and needs architectural review

## Methodology

### Step 1: Read Everything

Read the entire archive. Every document. Don't skim. The evaluation is only as good as your understanding.

- Start with the README or index to understand structure
- Read in the recommended order if one exists
- Read large documents fully — use `read_file` with offset/limit, not truncation

### Step 2: Map Design → Reality

If there's a live implementation (MCP server, codebase, running system), do a systematic mapping:

1. **List what the designs proposed** — every tool, feature, script, data flow
2. **Check what the implementation actually provides** — tool lists, API surfaces, capabilities
3. **Assess each item:** Covered? Superset? Subset? Not covered? Obsolete?
4. **Use a coverage table** — it forces rigor and reveals patterns

Example coverage assessment:

| Blueprint Feature | Implementation Reality | Verdict |
|---|---|---|
| Data fetcher (sleep, HRV, BB) | get_sleep_data, get_hrv_data, get_body_battery | **Covered** |
| HTML dashboards | Not implemented | **Gap** |
| 6 safety rules | 7 safety rules via run_safety_check() | **Superset** |

### Step 3: Quantify Impact

Don't just say "it covers most of it." Put numbers on it:

- Scripts proposed vs tools available
- Multi-call workflows collapsed into single calls
- Lines of code eliminated
- New capabilities not in the original design

This turns a subjective "it's good" into an objective "85% of proposed scripts are obsolete, and the implementation adds 10+ capabilities not designed."

### Step 4: Identify Remaining Gaps

The gap analysis is the most valuable output — it tells you what work remains:

- What did the blueprints propose that's still not built?
- What new gaps did the implementation reveal?
- What needs to change in the original design to accommodate the implementation?

### Step 5: Deliver the Verdict

Answer these questions explicitly:
- Does the architecture still hold up? (yes/no + why)
- What's obsolete from the original design?
- What's the remaining work?
- What's the first thing to build?

## Pitfalls

- **Don't skip reading.** Evaluating from summaries or partial reads leads to wrong assessments.
- **Don't accept "it covers it" without checking.** "Has a sleep tool" ≠ "returns the fields the design needed." Check the data contracts.
- **Don't assume the implementation is a strict subset.** It may be a superset — the implementation may add capabilities not in the design. Note these explicitly.
- **Don't evaluate without context.** Understand what problem the project solves before assessing technical fit.
