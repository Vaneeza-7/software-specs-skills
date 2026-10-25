# software-specs-skills

Claude skills for speccing software and projects.

## Skills

| Skill | What it does |
|---|---|
| [`diagrams`](plugins/software-specs/skills/diagrams/SKILL.md) | Draws architecture, data flow (DFD) and process flow diagrams in a consistent, spec-ready style. |

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

1. Download [`diagrams.zip`](https://github.com/Vaneeza-7/software-specs-skills/releases/latest/download/diagrams.zip) from the latest release.
2. In Claude, open **Settings > Capabilities**, find **Skills**, and upload the zip.
3. Turn the skill on. Claude uses it automatically when you ask for a diagram.

### Claude API / Agent SDK

Copy `plugins/software-specs/skills/diagrams` into your project's `.claude/skills/` directory, or upload it through the Skills API.

## Usage

Ask Claude for a diagram while speccing, for example:

- "Draw the architecture diagram for this system."
- "Make a data flow diagram covering all flows."
- "Create a process flow for how a deal gets analysed."

The skill picks the right type, applies its conventions, and checks the result before delivering.

## Repository layout

```
.claude-plugin/marketplace.json          # marketplace entry for Claude Code
plugins/software-specs/
  .claude-plugin/plugin.json             # plugin manifest
  skills/diagrams/SKILL.md               # the diagrams skill
  skills/<next-skill>/SKILL.md           # future skills go alongside
LICENSE                                  # MIT
```

## Contributing

All skills (diagrams, docs and more) live in the single `software-specs` plugin, so one install gets everything. Add a new skill as `plugins/software-specs/skills/<skill-name>/SKILL.md` with `name` and `description` frontmatter, and list it in the table above. Bump `version` in `plugin.json` and `marketplace.json`, then publish a GitHub release with a zip of each skill folder so Claude chat users can download it.

## License

[MIT](LICENSE)
