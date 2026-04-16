# Fix Handoff To `tdd-workflow`

Turn each accepted implementation finding into one observable behavior.

## Steps

1. Restate the finding as one target behavior.
2. Write the smallest failing test that proves the gap.
3. Observe red.
4. Apply the minimum production fix.
5. Re-run the targeted test and the nearest relevant broader suite.
6. Confirm the original finding is actually closed.

## Non-Negotiables

- No production fix without a failing reproduction first.
- Do not bundle multiple findings into one broad patch.
- Refactor only after green.
