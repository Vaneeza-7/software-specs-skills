---
name: technical-proposal
description: Write technical proposal and implementation plan documents that combine a technical spec (modules, tech stack, architecture) with a milestone timeline, acceptance criteria, scope boundary, open questions and assumptions. Use this skill whenever the user wants a technical proposal, project proposal, implementation plan, delivery plan, project timeline, milestone plan, statement of work or build plan for software, for a client or internal team, even if they only say "plan the build" or "how long will this take".
---

# Technical Proposal

A technical proposal tells the reader what will be built, with what, in what order, and how each step is proven done. Readers skim for scope, timeline and acceptance, so the document stays concise, keeps every fact in one place, and uses tables only where they help comparison.

## Workflow

### 1. Ask two questions first

Ask these before planning, unless the user has already answered them:

- **Audience: internal or client?** The versions share the same scope but differ in what they reveal (see "Audience versions").
- **Plan granularity: per day or per week?** Per day suits short projects measured in days or a few weeks. Per week suits longer projects. Suggest one based on the likely size, and let the user decide.

### 2. Settle the content in chat

Propose the modules, tech stack, milestones and their durations in chat, and resolve every point with the user before writing. Writing the full document before scope is agreed wastes a draft and buries decisions in prose. Write the document only after the user signs off.

### 3. Write the document

Follow the structure below in order. Leave out any section the project genuinely has nothing for, rather than filling it with placeholders.

### 4. Revise against the previous version

When revising, compare line by line against the exact version the user provides, and justify every change from it. Unexplained changes erode trust in a document the client may already have read.

## Document structure

1. **Title**, with a subtitle such as "N-Week Implementation Plan" or "N-Day Implementation Plan". Use relative weeks or days, never calendar dates, because start dates move.
2. **Overview**: a short paragraph, not bullets, stating what is being built and the outcome.
3. **Modules**: a table of Module | What it does. State plainly what each module does, in one line.
4. **Tech stack**: a table of Layer | Technology. Name one concrete technology per layer, with no "or" alternatives.
5. **Diagrams**: include only the diagrams the user asks for (architecture, data flow, process flow, ERD). Draw them with the `diagrams` skill so they follow the same conventions as the rest of the spec.
6. **Milestones at a glance**: a table of Milestone | Duration | Expected working state. The working state describes what can be demonstrated at the end of the milestone.
7. **Week 1 technical blockers**: what must be resolved or provided before or during the first week (access, credentials, data, decisions), so it is surfaced early rather than discovered late.
8. **Milestone detail** (see "Timeline").
9. **Final acceptance**: a table of the criteria the whole project must meet, ending with a one-line end-to-end flow showing the complete system working.
10. **Scope boundary**: one section listing what is not covered or is deferred to a later phase. Keep it to one list so exclusions are never repeated elsewhere.
11. **Open questions**: only items that are genuinely pending or block development. Leave out decisions that are obvious or already made.
12. **Assumptions**: flat single-line bullets, last.

## Timeline

### Milestone tables

Both modes use these columns:

| Day or Milestone | Implementation | Dependencies | Tests | Acceptance criteria |

- **Implementation** is numbered steps in the order the work happens, written as clear actions, not keyword lists.
- **Acceptance criteria** live only in this table. Do not repeat them in a separate section, apart from the whole-project criteria in "Final acceptance".

Under each milestone, add a short **milestone block** in bullets covering the deliverables and the dependency for the next milestone (or the release dependency for the final one). Keeping deliverables here holds the table to five columns.

### Per-day mode

Give each milestone its own section: a one-line goal, then a table with one row per day (Day 1 to Day N), so the whole table represents that milestone. Follow it with the milestone block.

### Per-week mode

Decide the layout by content:

- If each milestone fits in a few short rows, use one combined table with one row per milestone.
- If the Implementation cells get long, give each milestone (or week) its own section with a one-line goal and its own table, because a single wide table becomes unreadable.

Follow each milestone with its milestone block.

### Estimating

- Keep timelines realistic. Push back on durations that cannot hold, rather than agreeing to an unrealistic plan.
- Count weeks as 5 working days, and land deliveries at the end of a week, not mid-week.
- Keep person-days tight. Rounding up to the week end should give each milestone at most about 2 days of slack.
- Describe what gets built, not who builds it or how the team is organised.

## Audience versions

Both versions have the same scope, modules, milestones and acceptance criteria.

- **Internal**: adds person-days per milestone and the buffer.
- **Client**: weeks and milestones only. Never show buffer or person-days.

## Writing style

- Be concise and plain. Cut anything redundant, and state each fact once.
- Use tables only where they aid comparison, and bullets otherwise.
- Prefer comma-separated lists to nested sub-bullets.
- Leave out-of-scope material out of the document entirely, rather than describing that it is omitted.

## Check before delivering

- Were the audience and granularity confirmed, and was the content signed off in chat?
- Are the sections in order, with modules, stack and diagrams before the timeline?
- Does each milestone have a table with numbered implementation steps and acceptance criteria, followed by a milestone block?
- Are acceptance criteria, exclusions and assumptions each stated once?
- Do open questions contain only pending or blocking items?
- Client version: no buffer, no person-days, no calendar dates?
- Revision: is every change from the previous version justified?
