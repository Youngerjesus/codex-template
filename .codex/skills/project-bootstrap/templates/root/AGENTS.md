# AGENTS

This file is the repository-wide operating contract for agents and human collaborators.

## Project North Star

- Core Value: `[Describe the primary value this project must deliver.]`
- Core Hypothesis: `[Describe the belief the team is testing.]`
- Anti-Goals:
  - `[What this project must not become]`
  - `[What type of complexity or UX must be avoided]`
  - `[What kind of maintenance burden or process waste must be rejected]`
- Success Metrics:
  - `[Primary business or product metric]`
  - `[Secondary quality or retention metric]`

## Critical Rules

1. Plan non-trivial work before implementation.
2. Do not mark work complete without verification evidence.
3. Prefer root-cause fixes over temporary workarounds.
4. Keep documentation aligned when assumptions change.
5. Treat the approved spec and contract as the source of truth.
6. Prefer subtraction over additive complexity.

## Coding Agent Operation

### Plan First

- Use planning for any change with multiple steps, architectural choices, or meaningful regression risk.
- Re-plan when implementation assumptions break.
- Verification steps must be planned too, not improvised at the end.

### Review Before Ship

- Never assume the code is done because it compiles.
- Prove changed behavior with tests, commands, screenshots, or runtime evidence as appropriate.
- Treat unverified behavior as unfinished behavior.

### Context Discipline

- Gather only the context needed to reduce uncertainty.
- Read the direct SSOT first, then inspect the changed code and tests, then expand to long-lived docs only if needed.
- If sources conflict, the currently approved direct SSOT wins.

### Simplicity

- Choose the smallest change that actually closes the problem.
- Avoid fallback-heavy compatibility logic unless stability or migration truly requires it.
- If a fix feels brittle, pause and simplify the design before expanding the code.

## Core Interaction Principles

- Truth over agreement.
- Challenge weak plans or bad tradeoffs directly.
- Prefer reuse over parallel implementation.
- Surface hidden assumptions before writing code.
- Keep recommendations concrete and testable.

## Spec-Driven Development

- No spec, no code.
- Minimal mode is allowed: `spec.md` and `contracts.md` are enough to begin.
- Add `plan.md`, `tasks.md`, `design.md`, `research.md`, or review artifacts only when complexity requires them.
- Requirements should be explicit and verifiable. Use EARS-style statements when that improves clarity.

## Testing Rules

- Use tests to prove changed behavior and guard regressions.
- Start from the smallest useful proof, then expand to the nearest higher-risk suite when the change warrants it.
- If broader verification was skipped, document the remaining risk explicitly.
- Keep test ownership clear:
  - unit tests prove local behavior and contracts
  - integration tests prove subsystem interaction
  - end-to-end tests prove critical user or operator flows

## Code Organization

- Prefer explicit boundaries and clear ownership.
- Keep files and functions small enough to review quickly.
- Validate external data at boundaries before passing it inward.
- Separate types, configuration, providers, persistence, domain logic, runtime entrypoints, and UI when the project is large enough to benefit from layering.
- Enforce architectural rules with tooling when possible, not only with prose.

## Context Gathering Principle

- Check the direct SSOT for the current task first.
- Inspect the actual implementation and tests next.
- Use long-lived docs, history, or git archaeology only when they materially reduce ambiguity.
- Do not over-collect context just to feel safe.

## Document Map

- Root `README.md`: project entrypoint and onboarding
- Root `AGENTS.md`: operating rules and execution contract
- Root `DESIGN.md`: optional design-system and UI SSOT for UI-bearing projects
- `main/docs/project_overview.md`: business, product, and strategy SSOT seed
- `main/docs/tech_stack.md`: chosen runtime, tooling, and delivery stack
- `main/specs/`: feature-level specs and contracts
- `main/work_queue/progress.md`: project progress index
- `main/contexts/`: temporary task artifacts

## Local Dev And Verification

- Define the real local development commands in `README.md` or `main/docs/tech_stack.md`.
- Automation-friendly verification commands should be non-interactive when possible.
- Do not recommend environment or workflow patterns that cannot return control cleanly to the caller.
