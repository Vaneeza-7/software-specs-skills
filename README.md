# software-specs-skills

Claude skills for speccing software and projects.

## Skills

| Skill | What it does |
|---|---|
| [`diagrams`](plugins/software-specs/skills/diagrams/SKILL.md) | Draws architecture, data flow (DFD) and process flow diagrams in a consistent, spec-ready style. |
| [`technical-proposal`](plugins/software-specs/skills/technical-proposal/SKILL.md) | Writes technical proposals and implementation plans: modules, tech stack, architecture, milestone timeline with acceptance criteria, scope boundary, open questions and assumptions. |

### Technical proposal

- Asks first: internal or client version, and a per-day or per-week plan.
- Settles scope in chat and writes only after sign-off.
- Order: overview, modules, tech stack, requested diagrams, milestones at a glance, Week 1 blockers, milestone tables, final acceptance, scope boundary, open questions, assumptions.
- Client version never shows buffer or person-days.

### Diagrams

- **Architecture**: the deployed system only. Dashed provider zones, named service boxes, labelled connections.
- **Data flow diagram**: one universal diagram with swimlanes split by system and arrows labelled with data.
- **Process flow**: end to end with decision diamonds, no swimlanes, person icons wherever someone interacts.
- **Everywhere**: person icons for people, DB icons for data stores, labelled arrows, one concrete choice per box, one accent colour.

## Install

### Claude Code

Run these inside a Claude Code session:

```
/plugin marketplace add Vaneeza-7/software-specs-skills
/plugin install software-specs@software-specs-skills
```

### Claude chat (claude.ai, desktop and mobile apps)

1. Download the skills you want from the latest release: [`diagrams.zip`](https://github.com/Vaneeza-7/software-specs-skills/releases/latest/download/diagrams.zip), [`technical-proposal.zip`](https://github.com/Vaneeza-7/software-specs-skills/releases/latest/download/technical-proposal.zip).
2. In Claude, open **Settings > Capabilities**, find **Skills**, and upload each zip.
3. Turn the skills on. Claude uses them automatically when your request matches.

### Claude API / Agent SDK

Copy the skill folders from `plugins/software-specs/skills/` into your project's `.claude/skills/` directory, or upload them through the Skills API.

## Usage

Ask Claude while speccing, for example:

- "Draw the architecture diagram for this system."
- "Make a data flow diagram covering all flows."
- "Create a process flow for how a deal gets analysed."
- "Write a client technical proposal for this build."

Claude picks the matching skill, applies its conventions, and checks the result before delivering.

## Repository layout

```
.claude-plugin/marketplace.json          # marketplace entry for Claude Code
plugins/software-specs/
  .claude-plugin/plugin.json             # plugin manifest
  skills/diagrams/SKILL.md               # the diagrams skill
  skills/technical-proposal/SKILL.md     # the technical proposal skill
  skills/<next-skill>/SKILL.md           # future skills go alongside
LICENSE                                  # MIT
```

## Contributing

All skills (diagrams, docs and more) live in the single `software-specs` plugin, so one install gets everything. Add a new skill as `plugins/software-specs/skills/<skill-name>/SKILL.md` with `name` and `description` frontmatter, and list it in the table above. Bump `version` in `plugin.json` and `marketplace.json`, then publish a GitHub release with a zip of each skill folder so Claude chat users can download it.

## License

[MIT](LICENSE)
