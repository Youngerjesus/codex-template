---
name: implementation-brake
description: Review completed implementation for correctness, regression risk, missing tests, and unnecessary complexity before shipping.
---

# Implementation Brake

reference @./references/review-lenses.md
reference @./references/fix-handoff.md

Use this skill after code exists and before calling it done.

## Workflow

1. Ground the implementation and test surface.
2. Produce findings first.
3. Separate must-fix issues from deferrable cleanup.
4. Convert accepted findings into the next TDD step.
5. Re-review after fixes.

## Output

1. Implementation under review
2. Findings
3. What must be fixed now
4. What can be deferred
5. Fix plan
6. Verification result

Verdict must be one of:
- `[SHIP]`
- `[FIX BEFORE SHIP]`
- `[NEEDS REWORK]`
