# JARVIS - Master Task Coordinator

**Purpose:** Maintains the single source of truth for project progress via a markdown-based master checklist.

---

## Overview

JARVIS is responsible for:
- Maintaining a structured master checklist
- Analyzing task priorities and dependencies
- Determining intelligent task ordering per stream
- Tracking completion status across phases
- Feeding task queues to FLOW skill

---

## Task Attributes

| Attribute | Values | Description |
|-----------|--------|-------------|
| Priority | P0, P1, P2 | P0 = critical, P1 = important, P2 = nice-to-have |
| Stream | Frontend, Backend, General | Routes work to correct worktree/team |
| Effort | Low, Medium, High | Complexity estimate |
| Type | Feature, Update, Bug, Chore | Categorizes the work |

---

## Master Checklist Format

JARVIS reads and writes a structured markdown file. See [templates/master-checklist.md](templates/master-checklist.md) for the full template.

### Task Line Format

```markdown
- [ ] `PROJECT-ID` [Priority/Effort] Description - Type
```

Examples:
```markdown
- [ ] `KYLO-F01` [P0/Medium] Reconnection UI indicator - Feature
- [ ] `KYLO-B02` [P1/Low] Add rate limiting - Update
- [x] `KYLO-G01` [P0/High] Initial project setup - Feature
```

---

## Intelligent Ordering

Within each stream, JARVIS orders tasks by:

1. **Priority first** - P0 before P1 before P2
2. **Dependencies** - Blocked tasks wait for blockers
3. **Effort balance** - Mix quick wins with larger efforts
4. **Quick wins** - Low-effort P1 can jump ahead if P0 is blocked

---

## Usage

When JARVIS is invoked:

1. Read the master checklist file (location defined by project)
2. Parse current phase and all tasks
3. Analyze dependencies and priorities
4. Generate ordered task queue per stream
5. Report current status and next actions

---

## Integration

- **With FLOW:** JARVIS feeds the ordered queue → FLOW manages column movement
- **With ORACLE:** After task completion, ORACLE updates documentation
- **With PALADIN:** At phase gates, PALADIN runs security audit

---

## Files

- `JARVIS.md` - Skill prompt (instructions for Claude Code)
- `templates/master-checklist.md` - Template for new projects
