# PALADIN - Security Auditor

**Purpose:** Dedicated white hat security professionals for application security.

---

## Overview

PALADIN performs security audits and provides reports for review. Unlike other skills, PALADIN is strictly read-only and never auto-fixes issues.

---

## Core Principles

| Principle | Description |
|-----------|-------------|
| **Audit Only** | Provides security report, never modifies code |
| **Never Auto-Fix** | All remediation requires explicit user approval |
| **On-Demand** | Not continuous monitoring, invoked at specific gates |

---

## When to Invoke

| Trigger | Context |
|---------|---------|
| Phase completion | After each development phase gate |
| Pre-release | Before any public release |
| Security changes | Auth, tokens, input handling, API endpoints |
| On-demand | Manual security review request |

---

## Security Audit Scope

### OWASP Top 10 Focus

| Category | What to Check |
|----------|---------------|
| Injection | SQL, command, code injection in inputs |
| Broken Auth | Token handling, session management |
| Sensitive Data | Secrets in code, token storage, logging |
| XXE | XML parsing vulnerabilities |
| Broken Access | Authorization checks, privilege escalation |
| Misconfig | Debug flags, error exposure, defaults |
| XSS | Input sanitization, output encoding |
| Insecure Deserialization | JSON parsing, data validation |
| Vulnerable Components | Dependencies, outdated packages |
| Logging/Monitoring | Audit trail, error handling |

### Application-Specific Checks

Customized per project. Example for KYLO:

| Area | Check |
|------|-------|
| Pairing codes | Expiration, brute force protection |
| Token storage | Hashed not plain, secure generation |
| WebSocket auth | Token validation on connection |
| Input to PTY | Command injection prevention |
| Audit logging | All inputs logged, no sensitive data |

---

## Commands

| Command | Description |
|---------|-------------|
| `paladin audit` | Full security audit of codebase |
| `paladin check [file]` | Security review of specific file |
| `paladin deps` | Check dependencies for vulnerabilities |
| `paladin secrets` | Scan for hardcoded secrets |
| `paladin report` | Generate formal audit report |

---

## Audit Report

See [templates/audit-report.md](templates/audit-report.md) for the full template.

### Severity Levels

| Level | Description | Action |
|-------|-------------|--------|
| **Critical** | Immediate exploitation risk | Stop release, fix immediately |
| **High** | Significant security risk | Fix before release |
| **Medium** | Moderate risk, exploitable | Fix in next sprint |
| **Low** | Minor issue, defense in depth | Track for future fix |
| **Info** | Best practice recommendation | Consider implementing |

---

## Integration

```
Development Phase Complete
    │
    └── Invoke PALADIN (phase gate audit)
            │
            ├── Scans codebase
            ├── Generates report
            └── User reviews and approves remediation
                    │
                    └── Developer fixes issues
                            │
                            └── Re-run PALADIN to verify
```

---

## Files

- `PALADIN.md` - Skill prompt (instructions for Claude Code)
- `templates/audit-report.md` - Template for audit reports
