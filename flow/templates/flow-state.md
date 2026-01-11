---
project: PROJECT_NAME
last_updated: YYYY-MM-DD
---

# FLOW State

## In-Progress

<!-- Maximum 1 task per stream -->
<!-- Format: - `ID` Description (Stream) -->

## Queue

### Frontend
<!-- Maximum 2 tasks, ordered by JARVIS priority -->
<!-- Format: 1. `ID` Description -->

### Backend
<!-- Maximum 2 tasks -->

### General
<!-- Maximum 2 tasks -->

## Review

<!-- Tasks implemented, awaiting testing/sign-off -->
<!-- Format: - `ID` Description (Stream) -->

## Done (This Session)

<!-- Completed tasks this session, cleared on new session -->
<!-- Format: - `ID` Description ✓ -->

---

## Column Rules

| Column | Capacity | Notes |
|--------|----------|-------|
| In-Progress | 1 per stream | Focus on one task at a time |
| Queue | 2 per stream | Ready to start when In-Progress clears |
| Review | Unlimited | Awaiting verification |
| Done | Session-based | Cleared on new session |

## Commands Reference

- `flow status` - Show this board
- `flow start [ID]` - Queue → In-Progress
- `flow review [ID]` - In-Progress → Review
- `flow done [ID]` - Review → Done (triggers cascade)
- `flow block [ID] [reason]` - Mark blocked
- `flow unblock [ID]` - Remove block
