# CYLINDERS - Intelligent Code Optimizer

**Purpose:** Recognize patterns across the codebase and suggest refactors for maximum reusability.

*Named after "firing on all cylinders" - ensuring the codebase operates at peak efficiency.*

---

## Overview

CYLINDERS performs deep analysis of the entire codebase to identify:
- Repeated logic that could be abstracted
- Similar UI patterns that could be componentized
- Duplicated data flows that could be centralized
- Hard-coded one-off solutions that should be generalized

---

## Core Principles

| Principle | Description |
|-----------|-------------|
| **Ultrathink Always** | Uses extended thinking for maximum context |
| **Suggest Only** | Never auto-refactors without explicit approval |
| **Manual Invocation** | On-demand analysis, not continuous monitoring |
| **Holistic View** | Analyzes entire codebase, not individual files |

---

## Pattern Categories

### Logical Patterns
- Repeated business logic across files
- Similar validation routines
- Duplicated error handling
- Common data transformations

### UI Patterns
- Similar component structures
- Repeated styling patterns
- Common layout compositions
- Shared interaction patterns

### Navigation Patterns
- Repeated navigation flows
- Similar screen transitions
- Common deep linking patterns
- Shared route guards

### Data Flow Patterns
- Duplicated API calls
- Similar state management
- Repeated data fetching logic
- Common caching patterns

---

## Commands

| Command | Description |
|---------|-------------|
| `cylinders analyze` | Full codebase pattern analysis (ultrathink) |
| `cylinders check [path]` | Analyze specific directory/file |
| `cylinders compare [file1] [file2]` | Compare two files for consolidation |
| `cylinders report` | Generate formal analysis report |

---

## Output

CYLINDERS produces analysis reports with:
- Pattern identification with file:line locations
- Current state description
- Suggested refactor with code examples
- Impact assessment (files affected, code reduction)
- Priority rating (High/Medium/Low)

See [templates/analysis-report.md](templates/analysis-report.md) for the full format.

---

## CLAUDE.md Enforcement

CYLINDERS directly enforces the reusable systems requirement:

> 1. **Integration First**: Check if implementations can integrate with existing modules
> 2. **Native Library Check**: Check if a native library function already serves the purpose
> 3. **Centralized Solutions**: All solutions must be reusable, never hard-coded one-offs

---

## Integration

```
CYLINDERS (identifies patterns)
    │
    ├── Generates refactor suggestions
    ├── User approves specific refactors
    └── Adds tasks to JARVIS master checklist
            │
            └── Tasks flow through normal FLOW workflow
```

---

## Files

- `CYLINDERS.md` - Skill prompt with ultrathink protocol
- `templates/analysis-report.md` - Template for analysis reports
