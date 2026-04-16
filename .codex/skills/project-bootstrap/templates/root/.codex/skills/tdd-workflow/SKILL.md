---
name: tdd-workflow
description: Default workflow for bounded implementation, bugfix, or behavior changes driven by automated verification.
---

# Test-Driven Development Workflow

reference @./references/tdd-rules.md
reference @./references/verification-checklist.md

## Workflow

1. State the target behavior.
2. Write one minimal test for one behavior.
3. Run it and observe red.
4. Write the minimum production code to reach green.
5. Re-run the targeted test and the relevant broader suite.
6. Refactor only after green.

## Non-Negotiables

- No production code before a failing test.
- If the test passes immediately, the test is wrong or already-covered behavior.
- Do not expand scope beyond the current failing behavior.
