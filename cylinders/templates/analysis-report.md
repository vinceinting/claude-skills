# CYLINDERS Analysis Report

**Project:** PROJECT_NAME
**Date:** YYYY-MM-DD
**Mode:** Ultrathink (Extended Analysis)
**Analyst:** CYLINDERS

---

## Executive Summary

| Metric | Count |
|--------|-------|
| Patterns Identified | 0 |
| Refactor Opportunities | 0 |
| Estimated Code Reduction | ~0% |

| Priority | Count |
|----------|-------|
| High | 0 |
| Medium | 0 |
| Low | 0 |

---

## Patterns Found

### High Priority

<!--
### [HIGH] PAT-001: Pattern Name
**Locations:**
- `file/path.ts:123`
- `another/file.ts:456`
- `third/file.ts:789`

**Current State:**
Description of the duplicated/similar code and why it's problematic.

**Suggested Refactor:**
```typescript
// Proposed abstraction or utility
export function unifiedSolution() {
  // Implementation
}
```

**Usage After Refactor:**
```typescript
// How to use the new abstraction
import { unifiedSolution } from './utils';
unifiedSolution();
```

**Impact:**
- Files affected: X
- Lines reduced: ~X
- Maintenance: Single point of change
- Risk: Low/Medium (describe any risks)
-->

### Medium Priority

<!-- Medium priority patterns -->

### Low Priority

<!-- Low priority patterns -->

---

## CLAUDE.md Violations

<!-- List any violations of the reusable systems requirement -->

| File | Line | Violation | Recommendation |
|------|------|-----------|----------------|
| | | | |

---

## Existing Abstractions Underutilized

<!-- Abstractions that exist but aren't being used consistently -->

| Abstraction | Location | Should Be Used In |
|-------------|----------|-------------------|
| | | |

---

## Recommendations

### Immediate (High Impact, Low Effort)
1.

### Short-term (Medium Impact)
1.

### Long-term (Architectural)
1.

---

## Files Analyzed

### Source Files
- `packages/server/src/**/*.ts`
- `packages/android/src/**/*.ts`
- `packages/android/src/**/*.tsx`

### Configuration
- `package.json`
- `tsconfig.json`

### Excluded
- `node_modules/`
- `build/`
- `dist/`

---

## Metrics

| Category | Before | After (Estimated) |
|----------|--------|-------------------|
| Total Files | X | X |
| Total Lines | X | X (-Y%) |
| Duplicated Blocks | X | X |
| Utility Functions | X | X (+Y) |
| Shared Components | X | X (+Y) |

---

## Next Steps

1. Review this report with the team
2. Prioritize refactors to implement
3. Add approved refactors to JARVIS master checklist
4. Implement through normal FLOW workflow
5. Re-run CYLINDERS after refactors to verify improvement

---

**Report Generated:** YYYY-MM-DD HH:MM
**Next Analysis Recommended:** After significant feature additions or refactor completion
