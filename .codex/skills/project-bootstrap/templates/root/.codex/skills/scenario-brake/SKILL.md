---
name: scenario-brake
description: Pressure-test whether a plan or spec covers enough realistic scenarios before implementation.
---

# Scenario Brake

reference @./references/review-lenses.md

Use this skill when the happy path looks fine but re-entry, failure, state variation, or path variation might be under-specified.

## Workflow

1. Ground the baseline scenario.
2. Identify the key parameters that make the scenario true.
3. Mutate those parameters.
4. Separate truly different scenarios from the same path.
5. Recommend missing coverage and the appropriate verification layer.

## Verdict

- `[SCENARIOS SUFFICIENT]`
- `[SCENARIOS MISSING]`
- `[PLAN NEEDS REFRAME]`
