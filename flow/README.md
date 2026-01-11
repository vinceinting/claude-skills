# FLOW - Task Movement Engine

**Purpose:** Manages task progression through virtual Kanban-style columns.

---

## Overview

FLOW tracks WHERE tasks are in the development workflow. While JARVIS determines task priority and order, FLOW manages the movement of tasks through stages:

```
Backlog → Queue → In-Progress → Review → Done
```

---

## Virtual Columns

| Column | Description | Capacity |
|--------|-------------|----------|
| Backlog | All tasks in current phase (from JARVIS) | Unlimited |
| Queue | Next tasks ready to work on | 2 per stream |
| In-Progress | Currently being implemented | **1 per stream max** |
| Review | Implemented, awaiting testing/sign-off | Unlimited |
| Done | Completed and verified | Unlimited |

---

## Stream Isolation

Each stream (Frontend, Backend, General) has its own pipeline:

```
Frontend:    Queue[2] → In-Progress[1] → Review → Done
Backend:     Queue[2] → In-Progress[1] → Review → Done
General:     Queue[2] → In-Progress[1] → Review → Done
```

This allows parallel work across streams while enforcing focus within each stream.

---

## State Tracking

FLOW maintains state in a project-specific file: `FLOW_STATE.md`

See [templates/flow-state.md](templates/flow-state.md) for the format.

---

## Commands

| Command | Action |
|---------|--------|
| `flow status` | Display current board state |
| `flow start [ID]` | Queue → In-Progress |
| `flow review [ID]` | In-Progress → Review |
| `flow done [ID]` | Review → Done (triggers cascade) |
| `flow block [ID] [reason]` | Mark as blocked |
| `flow unblock [ID]` | Remove blocked status |
| `flow init` | Initialize FLOW_STATE.md for project |

---

## Workflow

### Starting Work
```
User: "flow start KYLO-B30"
FLOW: Moves KYLO-B30 from Queue → In-Progress
      Updates FLOW_STATE.md
      Displays: "🚀 Started KYLO-B30: Cloudflare Tunnel integration"
```

### Completing Work
```
User: "flow done KYLO-B30"
FLOW: 1. Moves KYLO-B30 from Review → Done
      2. Updates JARVIS master checklist (marks [x])
      3. Invokes ORACLE for documentation
      4. Pulls next Queue task → In-Progress
      5. Pulls next Backlog task → Queue
```

---

## Integration

```
JARVIS (Master Checklist)
    │
    ├── Defines task order
    ├── Populates Backlog
    └── Receives completion updates from FLOW
            │
            ↓
FLOW (Movement Engine)
    │
    ├── Manages column positions
    ├── Enforces capacity limits
    └── Triggers ORACLE on completion
            │
            ↓
ORACLE (Documentation)
    │
    └── Updates docs when tasks complete
```

---

## Files

- `FLOW.md` - Skill prompt (instructions for Claude Code)
- `templates/flow-state.md` - Template for project state file
