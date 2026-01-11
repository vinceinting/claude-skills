# Claude Skills

Portable, project-agnostic skills for Claude Code CLI.

These skills are designed to work across any project - they must NEVER be hardcoded to a specific codebase.

---

## Available Skills

| Skill | Purpose | Status |
|-------|---------|--------|
| [JARVIS](jarvis/) | Master Task Coordinator | Active |
| [FLOW](flow/) | Task Movement Engine | Active |
| [ORACLE](oracle/) | Documentation Guardian | Planned |
| [PALADIN](paladin/) | Security Auditor | Planned |

---

## Usage

Add as git submodule to your project:

```bash
git submodule add https://github.com/vinceinting/claude-skills.git skills
```

Update to latest:

```bash
git submodule update --remote skills
```

---

## Design Principles

1. **Portable** - Works across any project without modification
2. **Markdown-based** - Human-readable state, git-diffable
3. **Explicit** - No hidden state or magic, everything visible
4. **Composable** - Skills can invoke each other (JARVIS → FLOW → ORACLE)

---

## Skill Interactions

```
JARVIS (Task Coordinator)
    │
    ├── Maintains master checklist
    ├── Determines task order
    └── Feeds queue to FLOW
            │
            ├── Manages virtual columns
            ├── Moves tasks through workflow
            └── Invokes ORACLE on completion
                    │
                    └── Updates documentation

PALADIN (Security)
    │
    └── Invoked at phase gates for security audit
```

---

## License

MIT
