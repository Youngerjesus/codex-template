---
name: systematic-debugging
description: Use when encountering any bug, test failure, or unexpected behavior, before proposing fixes.
---

# Systematic Debugging

reference @./references/phase-gates.md
reference @./references/test-layer-selection.md
reference @./references/debug-report-template.md
reference @./root-cause-tracing.md
reference @./defense-in-depth.md
reference @./condition-based-waiting.md

## Iron Law

`NO FIXES WITHOUT ROOT CAUSE INVESTIGATION FIRST`

## Workflow

1. Investigate the root cause.
2. Analyze the pattern.
3. Form one explicit hypothesis and test it.
4. Implement the root-cause fix and verify it.

## Output Contract

- `Symptom`
- `Expected`
- `Reproduced`
- `Evidence`
- `Current hypothesis`
- `Next step`
- `Fix gate`
