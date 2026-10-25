---
name: diagrams
description: Draw architecture diagrams, data flow diagrams (DFDs) and process flow diagrams in a consistent, spec-ready style. Use this skill whenever the user is speccing software or a project and asks for a system diagram, architecture diagram, deployment diagram, DFD, data flow, process flow, flowchart or workflow diagram, or wants to show how a system is built, how data moves through it, or how work gets done, even if they don't name the diagram type.
---

# Diagrams

Spec diagrams fail when they try to answer several questions at once. This skill keeps each diagram to one question by separating three types, each with its own conventions, plus a small set of shared rules that keep them visually consistent across a spec.

## Choose the diagram type

Identify the question the diagram should answer before drawing anything:

| Question | Type | Arrows mean |
|---|---|---|
| What is deployed, where, and how does it connect? | Architecture | "connects to / calls" |
| What data moves between which systems? | Data flow diagram (DFD) | "this data goes here" |
| How does work get done, step by step, with decisions? | Process flow | "then" |

If the request could be more than one type, ask the user which question they want answered. Keep types separate: process steps in an architecture diagram, or decision diamonds in a DFD, blur what the reader is looking at.

A quick test: if a decision diamond fits, it is a process flow; if every arrow is labelled with a piece of data, it is a DFD; if it shows hosted components and their connections, it is architecture.

## Shared rules

Apply these to every type so diagrams in the same spec read as one set:

- Draw people as person icons and databases or data stores as DB (cylinder) icons. Recognisable icons let readers spot actors and storage at a glance.
- Label every arrow with exactly what it carries or means. Unlabelled arrows force the reader to guess.
- Name one concrete technology per element (e.g. "Postgres", not "Postgres or MySQL"). A spec should describe a decision, not a menu.
- Keep styling restrained: muted colours, with one accent colour reserved for the single most important link or path, so emphasis stays meaningful.
- Use as few arrows as possible. Prefer a trunk with a junction over many parallel arrows.
- Keep one reading direction (top-to-bottom or left-to-right) and make every zone or lane label visible.

## Architecture diagrams

Show the finished product as it looks deployed: what runs where and how it connects.

- Use cloud-architecture style, like GCP or AWS reference diagrams.
- Group services into dashed zones, one per hosting provider or boundary (e.g. Vercel, Cloud VM · Docker Compose, Supabase, External API, Data import).
- Draw each service as a named box with a short one-line role.
- Draw arrows that show exactly how services connect, labelled with the protocol or purpose.
- Include only the runtime system. Leave out process flow and development steps such as training, MLflow, data generation, CI or experimentation, because they are not part of what gets deployed and they clutter the picture.

## Data flow diagrams

Show what data moves where across the whole system.

- Use swimlanes split by system, one lane per system, component or provider (e.g. Client · Backend · Orchestrator · Database · External APIs). Match the lanes to the architecture diagram's provider zones where possible so the two diagrams line up.
- Produce one universal diagram that covers every flow, internal and external. A single view shows how flows interact; splitting them hides that.
- Label arrows with the data itself (e.g. "pitch deck PDF", "scores JSON"), not with steps.
- Use the standard DFD elements: external entities, processes that transform data, data stores (DB icons) and labelled flows.
- Leave out decision diamonds, sequencing, and start or end points. Those belong in a process flow.

Classic DFD notation does not use swimlanes; system lanes are a deliberate hybrid chosen here because they make data crossing system boundaries obvious.

## Process flow diagrams

Show the end-to-end process: how work gets done.

- Run the flow from start to finish, with decision diamonds that have labelled yes/no branches.
- Do not use swimlanes. Most of the work is done by the system, so lanes would add structure without adding information.
- Mark each point where a person interacts with a person icon: at the start as the trigger, and mid-flow wherever someone acts (e.g. an analyst approval). Continue the system's process onward from each interaction. This keeps the "who" visible without lanes.
- Show the overall system flow, not internal implementation detail.

## Check before delivering

Review the diagram against the rules for its type:

- Does it answer one question, with nothing from another type mixed in?
- Are person and DB icons used consistently, and is every arrow labelled?
- Is every element a single concrete choice?
- Architecture: runtime system only, grouped into provider zones?
- DFD: system lanes, one universal diagram, data-labelled arrows, no decisions?
- Process flow: no lanes, decision diamonds present, person icons wherever people act, including mid-flow?
