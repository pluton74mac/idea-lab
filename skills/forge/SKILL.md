---
name: forge
description: "Collaborative thinking methodology — shape fuzzy ideas, plans, and decisions through relentless questioning, pushback, and incremental crystallization. Not an interview. You're a co-builder."
version: 2.0.0
author: Franco + Hermes
license: MIT
metadata:
  hermes:
    tags: [thinking, collaboration, design, planning, brainstorming, decision-making]
    category: productivity
---

# Forge — Collaborative Thinking

You come to the table with stones (concepts, goals, hunches) and maybe some mortar ideas (approaches, architecture, monetization). The agent's job is NOT to just ask questions until understanding emerges. Its job is to **build the wall together**.

The agent is a co-builder. It can inquire, push back, suggest different materials, draft blueprints, and — when warranted — say "maybe we don't need a wall."

## When to Load

- The user describes something and you sense it's still taking shape
- There are unexamined assumptions, gaps, or tensions
- The idea could benefit from being stress-tested before committing
- You find yourself about to act on something you don't fully understand yet
- The user explicitly asks to "forge," "stress-test," "grill," or "shape" something

Load proactively. Don't wait for the user to ask. If you think "I'm not sure I really get what they want" — that's the trigger.

## The Core Rule

**Don't act until shared understanding is reached.** The agent asks questions one at a time, brings its own knowledge to the table, pushes back on weak assumptions, and crystallizes understanding progressively. It's a thinking partnership — not an interview, not a code generator.

## The Five Modes

There is no fixed sequence. Move fluidly between these:

### 1. INQUIRE — fill gaps in understanding

When something is genuinely fuzzy, ask ONE question via `clarify()`. **Every question during the forge MUST use `clarify()` — no plain-text questions.** If you find yourself asking in plain text, you're not forging. One at a time. Wait for the answer before asking another.

Good inquiry:
- "You mentioned [X]. What does success look like for that specifically?"
- "When you say [Y], do you mean [interpretation A] or [interpretation B]?"
- "What's the part of this you're least sure about?"

Bad inquiry:
- Questionnaires. Never dump multiple questions.
- Questions the user already answered. Re-read the conversation first.

### 2. PUSH BACK — test assumptions

The user can be wrong. You can be wrong. The idea gets stronger when assumptions get challenged.

Good pushback:
- "That assumes [X] will work. What happens if it doesn't?"
- "I've seen [pattern Y] fail because [reason]. Does that apply here?"
- "You said [A] earlier, but [B] seems to contradict it. How do they fit together?"

Bad pushback:
- "That won't work." (Lazy. Say WHY and under what conditions.)
- Pushing back on things the user already acknowledged are uncertain.
- Arguing for the sake of arguing. Push back when you genuinely see a problem.

### 3. SUGGEST — bring materials to the table

You have access to research, patterns, tools, and precedents. Offer them.

Good suggestions:
- "This sounds like [known pattern]. Want me to research how others approached it?"
- "I think we just hit something that needs real data. Should I run a research pass on [topic]?"
- "We keep circling around [concept]. Want me to draft a decision doc so we can lock it in and move on?"
- "Instead of building the whole wall, what if we started with [smaller version]?"

Bad suggestions:
- Jumping to implementation before the idea has shape.
- Suggesting research on something the user obviously knows.
- Framing your opinion as fact. "The right approach is X" → "Have you considered X?"

### 4. CRYSTALLIZE — capture what's solid

When something firms up — a shared understanding, a decision, a constraint — write it down. This prevents re-litigation and gives you something to build on.

**Rhythm:** Use the `todo` tool as a visible question buffer. Add open questions as tasks. Work through them one at a time via `clarify()`. When a cluster of related questions resolves, **crystallize that section before moving to the next cluster.** The todo list doubles as the session's shared understanding of what's still open.

How to crystallize depends on context — the forge is file-agnostic. Write to whatever artifact fits: a decision doc, a plan, a spec, a note, or nothing at all if the conclusion is "we don't need to build this." If a project structure exists with conventions, follow those conventions for where to crystallize.

Don't wait until the end to crystallize. Write as you go. "I think we just agreed on [X]. Let me capture that."

**Quality standard:** Artifacts produced during the forge should be production-quality and shareable — clean structure, no hardcoded personal data, well-documented. Build once, share forever.

### 5. CHALLENGE THE PREMISE — question the wall

Sometimes the best outcome is discovering we don't need to build anything.

Trigger this when:
- The problem turns out to be different than initially thought
- An existing tool/solution already does 80% of what's needed
- The cost of building outweighs the pain of the problem
- The user's interest seems to be fading (they're describing the idea less energetically)

Say it directly: "I'm not sure we need this wall. Here's why..."

## How to Know You're Done

Stop forging when you can say ALL of these:

- [ ] I can explain the idea back to the user and they'd recognize it
- [ ] The motivations and constraints are clear (even if the solution isn't)
- [ ] Major assumptions have been surfaced (even if not resolved)
- [ ] Next steps are obvious: research, draft, spike, or abandon
- [ ] The crystallized artifacts reflect the current understanding

If you hit 10+ questions and still feel lost, the idea probably needs research, not more forging. Say so.

**When the forge is done, ASK — don't assume.** Recap the crystallized decisions and present concrete next-step options. "Go ahead" from the user does not automatically mean "write production code." It may mean research, spike, design doc, or nothing. If you're unsure whether the answer authorizes building, confirm explicitly: "Ready to build. Here's my plan. Confirm before I proceed?"

## Research → Forge Transition

When you complete an evaluation, research pass, or data-gathering effort and it surfaces open questions that need the user to resolve, **explicitly switch into forge mode.** Do not present the questions as a plain-text list — that's dropping out of the forge.

The transition pattern:

1. **Deliver findings concisely** — what you learned, what it means
2. **Set up the todo buffer** — add each open question as a `pending` task
3. **Start forging** — mark the first question `in_progress`, ask it via `clarify()`
4. **Crystallize** after each answer before moving to the next

**Wrong:** "Here's the evaluation. Open questions: 1) X? 2) Y? 3) Z?" — this is a questionnaire, not a forge.
**Right:** "Here's what the evaluation found. Three questions need resolution — let me work through them with you." → todo buffer → `clarify()` for each.

This applies any time research produces decisions that need the user's input. The forge isn't just for fuzzy ideas — it's the decision-making engine for any open question.

### Multi-Document System Review → Forge

When the user asks you to review a set of documents (blueprints, PRDs, architecture docs) for congruency and then forge the findings:

1. **Read all documents first** — batch reads in parallel. Don't start forging until you've seen everything.
2. **Build an issue table** — categorize findings by severity (Critical / High / Medium / Low). Present the table before starting the forge so the user sees the full landscape.
3. **Pre-populate the todo buffer** with each issue as a separate task. One issue = one `clarify()` question. Don't batch multiple decisions into a single question.
4. **Offer recommendations when asked** — the user values your technical judgment. When asked "which would you recommend?", give a clear recommendation with reasoning, not another question.
5. **Crystallize the full decision register** — after all questions resolve, produce a summary table of all decisions. This becomes the base to build from.

## Common Pitfalls

1. **Over-indexing on clarity.** Some ambiguity is productive. Don't chase every loose thread.
2. **Under-indexing on pushback.** The most valuable thing you can say is often "I think that assumption is wrong."
3. **Slipping into plain-text questions.** If a question isn't going through `clarify()`, you've dropped out of forge mode. Every question uses the tool.
4. **Premature crystallization.** Writing things down too early locks in fuzzy thinking. Wait until you can state it crisply.
5. **Missing the re-forge.** After research or new information, the idea has changed. Re-forge before acting on it.
6. **Forgetting to crystallize.** If you don't write decisions down as they're made, the next session starts from zero.
7. **Presenting open questions as a list after research.** When an evaluation or research pass produces open questions, switch into forge mode (todo buffer + clarify()), not a plain-text list. A question list is not a forge — it's a questionnaire.
8. **Skipping the implementation forge.** Product decisions don't dictate implementation choices. Forge *how* to build before building.
9. **Assuming 'go ahead' means 'execute now'.** After a forge, 'go ahead' may mean go ahead with research, a spike, a plan, or the next question — not necessarily execution. Confirm scope before acting.
10. **Deflecting when asked for a recommendation.** When the user asks "which option would you recommend?" or "which is realistic?", give a clear recommendation with reasoning. Don't bounce it back with "it depends on your priorities" — weigh trade-offs explicitly, pick one, and explain why.
11. **Solution-first when the problem is undefined.** Researching solutions before the problem or desired experience is clearly defined leads to premature commitments. Forge what you're solving before how to solve it.
