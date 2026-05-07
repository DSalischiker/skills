# Skills Repository

A collection of custom agent skills.

## Structure

```
skills/
├── README.md           # This file
├── template/           # Template for creating new skills
│   └── SKILL.md
└── skills/             # Individual skill definitions
    └── <skill-name>/
        └── SKILL.md
```

## Using a Skill

### With any agent (.agents)

Copy the desired skill folder into `.agents/skills/` in your project:

```
your-project/
└── .agents/
    └── skills/
        └── <skill-name>/
            └── SKILL.md
```

### With Claude Code (.claude)

Copy the desired skill folder into `.claude/skills/` in your project:

```
your-project/
└── .claude/
    └── skills/
        └── <skill-name>/
            └── SKILL.md
```

## Creating a Skill

Use the template in `template/SKILL.md` as a starting point. Each skill requires:

- **`name`** — a unique identifier (kebab-case)
- **`description`** — when the agent should invoke the skill
- **Body** — the instructions the agent will follow when the skill is triggered
