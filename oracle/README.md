# ORACLE - Documentation Guardian

**Purpose:** Maintains all documentation accuracy at all times.

---

## Overview

ORACLE ensures documentation stays in sync with implementation. It operates in two modes and is typically invoked by FLOW when tasks complete, or on-demand for comprehensive audits.

---

## Modes

| Mode | Trigger | Scope |
|------|---------|-------|
| **Full Audit** | On-demand | Comprehensive review/update of all docs |
| **Spot Update** | Invoked by FLOW | Targeted update when task completes |

---

## Full Audit Mode

Triggered by: `oracle audit`

Performs comprehensive documentation review:

1. **Inventory** - List all markdown files in docs/
2. **Cross-reference** - Check for broken internal links
3. **Accuracy** - Verify docs match current implementation
4. **Completeness** - Identify undocumented features
5. **Archival** - Move obsolete docs to archive/

### Audit Report Format

```markdown
# ORACLE Audit Report - YYYY-MM-DD

## Summary
- Files scanned: X
- Issues found: Y
- Auto-fixed: Z

## Issues

### Broken Links
- [file.md:15] Link to `missing.md` not found

### Outdated Content
- [architecture.md] References Beta 2 but we're on Beta 3

### Missing Documentation
- No docs found for: rate limiting, error handling

## Actions Taken
- Updated phase references in development-phases.md
- Archived deprecated-feature.md → archive/

## Recommendations
- [ ] Document rate limiting implementation
- [ ] Update architecture diagrams
```

---

## Spot Update Mode

Triggered by: `oracle update [task-id]` or automatically by FLOW

Performs targeted update for completed task:

1. **Identify scope** - What docs might this task affect?
2. **Check accuracy** - Do existing docs need updates?
3. **Add content** - Document new features if needed
4. **Archive** - Move outdated content if needed

### Spot Update Output

```
ORACLE Spot Update: KYLO-B30 (Cloudflare Tunnel integration)

Checked:
✓ docs/architecture/unison/tier-1-core/SYNC.md - OK
✓ docs/product/design-decisions.md - OK
⚠ docs/roadmap/development-phases.md - Updated Beta 3 status

Actions:
- Marked "Cloudflare Tunnel integration" as complete in development-phases.md
- No new documentation required

Done.
```

---

## Documentation Structure

ORACLE understands and maintains this structure:

```
docs/
├── architecture/     # System design, UNISON modules
├── archive/          # Completed/deprecated docs
├── brand/            # Brand guidelines, assets
├── operations/       # Operational procedures
├── plans/            # Implementation plans
├── product/          # Product specs, requirements
└── roadmap/          # Milestone planning
```

---

## Commands

| Command | Mode | Description |
|---------|------|-------------|
| `oracle audit` | Full | Comprehensive docs review |
| `oracle update [ID]` | Spot | Update docs for completed task |
| `oracle check [file]` | Spot | Verify single file accuracy |
| `oracle links` | Full | Check all internal links |
| `oracle archive [file]` | Spot | Move file to archive/ |

---

## Integration

```
FLOW (on task completion)
    │
    └── Invokes ORACLE (spot update)
            │
            ├── Checks affected documentation
            ├── Updates if needed
            └── Reports changes

User (on-demand)
    │
    └── Invokes ORACLE (full audit)
            │
            ├── Scans all docs
            ├── Reports issues
            └── Fixes what it can
```

---

## Files

- `ORACLE.md` - Skill prompt (instructions for Claude Code)
