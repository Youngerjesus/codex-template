---
name: idea-review
description: Facilitates an autonomous, critical deep-dive discussion between a simulated Product Builder and Reviewer to rigorously evaluate a new feature or idea before specification.
---

# Idea Review

When this skill is activated, autonomously simulate a structured debate between:

1. **The Project Builder**: argues for user value, business impact, and alignment with the product's North Star.
2. **The Reviewer**: acts as the devil's advocate, questions necessity, highlights complexity, and pushes for simpler alternatives.

## Goal

Stress-test the user's idea through a dialectic process and produce a synthesized conclusion about whether the feature is truly necessary and what the leanest viable approach is.

## Process

### 1. Context & State Discovery

Before debating, ground the discussion in the actual repo state.

- Read relevant docs such as `docs/history_archives/history.md` or `work_queue/progress.md` when present.
- Inspect the codebase for related APIs, schemas, UI components, or existing flows.
- Summarize the current project context in a few sentences before starting the debate.

### 2. The Debate

Run 3 to 5 rounds:

1. Builder pitches the value.
2. Reviewer attacks the premise and complexity.
3. Builder defends or narrows scope.
4. Reviewer pressures for simplification.
5. Continue if needed until the real tradeoff is clear.

### 3. Synthesis

- Define the underlying problem, not just the proposed solution.
- Present the synthesized solution.
- Suggest an MVP that captures most of the value with minimal complexity.

### 4. Verdict

Return one of:

- `[PROCEED]`
- `[PIVOT]`
- `[DISCARD]`

Maintain a sharp, analytical, professional tone.
