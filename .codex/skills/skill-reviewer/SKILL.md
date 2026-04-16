---
name: skill-reviewer
description: Review a Codex skill for trigger quality, context economy, workflow completeness, safety, and benchmark overfitting risk. Use this skill as the approval gate for skill hardening.
---

# Skill Reviewer

Use this skill to review an existing skill before approving it as hardened.

## Review Focus

- trigger precision and over-invocation risk
- missing trigger coverage for realistic requests
- unnecessary context loading or deep reference chains
- unclear workflow steps that still leave implementer discretion
- unsafe or overly broad tool guidance
- benchmark leakage or brittle overfitting

## Output Standard

Return:
- verdict
- concise summary
- blocker, major, and minor findings with location and required fix

Do not approve while a blocker remains.
