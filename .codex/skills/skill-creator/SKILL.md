---
name: skill-creator
description: Guide for creating or updating Codex skills that package specialized workflows, references, templates, or helper scripts.
---

# Skill Creator

This skill provides guidance for creating effective Codex skills.

reference @./extend_codex_with_skills.md

## Core Principles

### Concise is Key

Assume the model is already strong. Add only context that the model would not reliably infer on its own.

### Match Degrees of Freedom to Risk

- Use freeform instructions when multiple approaches are valid.
- Use templates or pseudocode when a preferred pattern exists.
- Use scripts or assets when consistency and reliability matter.

### Keep the Skill Modular

Every skill should have:

- a focused trigger description
- a lean `SKILL.md`
- optional references, assets, or scripts only when they materially help

## Workflow

1. Define the skill's exact job and trigger conditions.
2. Choose the minimum files needed.
3. Create `SKILL.md` with explicit routing guidance.
4. Add references/templates/scripts only when the body would otherwise become bloated.
5. Verify all relative references are one hop away from `SKILL.md`.
