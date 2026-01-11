# Claude Skills & Agents

Portable, project-agnostic skills and agents for Claude Code CLI.

These are designed to work across any project - they must NEVER be hardcoded to a specific codebase.

---

## Skills vs Agents

| Type | Context | Best For |
|------|---------|----------|
| **Skill** | Shared with main conversation | Conversational coordination, quick operations |
| **Agent** | Isolated subprocess | Deep analysis, background tasks, read-only audits |

---

## Available Skills

Skills run in the main conversation context and are invoked with `/skillname`.

| Skill | Purpose | Invocation |
|-------|---------|------------|
| [JARVIS](jarvis/) | Master Task Coordinator | `/jarvis` |
| [FLOW](flow/) | Task Movement Engine | `/flow` |

---

## Available Agents

Agents run in isolated context and are invoked with "Use the X agent to...".

| Agent | Purpose | Invocation |
|-------|---------|------------|
| [ORACLE](oracle/) | Documentation Guardian | "Use oracle agent..." |
| [PALADIN](paladin/) | Security Auditor | "Use paladin agent..." |
| [CYLINDERS](cylinders/) | Intelligent Code Optimizer | "Use cylinders agent..." |

**Note:** Agents are registered in `.claude/agents/` (project-level). The markdown files in this submodule serve as reference documentation.

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

## Interactions

```
SKILLS (Main Conversation)
├── JARVIS (Task Coordinator)
│   ├── Maintains master checklist
│   ├── Determines task order
│   └── Feeds queue to FLOW
│
└── FLOW (Task Movement)
    ├── Manages virtual columns
    └── Moves tasks through workflow

AGENTS (Isolated Context)
├── ORACLE (Documentation Guardian)
│   └── Audits docs, reports what needs updating
│
├── PALADIN (Security Auditor)
│   └── Invoked at phase gates for security audit
│
└── CYLINDERS (Code Optimizer)
    ├── Analyzes codebase for patterns
    └── Suggests refactors (user adds to JARVIS)
```

**Workflow:** Skills coordinate → Agents analyze → User acts on findings

---

## License

MIT
