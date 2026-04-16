---
name: spec-hardening-loop
description: Use this skill to harden `project_manager/specs/[feature_name]` packages by running the existing `project_manager/spec_loop.py` generator-evaluator loop, then falling back to a final `spec-reviewer`-guided approval pass when max rounds are exhausted.
---

# Spec Hardening Loop

reference @./references/fallback-approval-protocol.md

Use this skill when the user wants a spec package strengthened through the existing spec loop and expects the workflow to push the package to an approval-ready state instead of stopping at the first non-terminal loop result.

## Use When

- Hardening an existing `project_manager/specs/[feature_name]/` package
- Running the generator-evaluator loop on `spec.md` and `contracts.md`
- Resuming a partially completed spec loop run
- Closing the last blocker findings after the loop stalls at the round limit

## Do Not Use

- Creating a brand-new spec package from scratch
- Breaking approved specs into tasks
- Implementing product code
- Approving a spec without reading the current `spec.md`, `contracts.md`, and latest loop artifacts

## Operating Rules

1. Treat `project_manager/spec_loop.py` as the authoritative loop engine.
   Do not copy its logic into the skill folder and do not create a shadow implementation.
2. Limit document edits to the target package unless the user explicitly expands scope.
3. Treat `project_manager/specs/[feature_name]/spec.md` and `project_manager/specs/[feature_name]/contracts.md` as the only approval boundary.
4. Reuse `spec-reviewer` as the final approval standard.
   The fallback pass must close ambiguity, evidence gaps, and contract drift to that standard before approval.
5. Do not mark a spec `Approved` by assertion alone.
   The documents must be hardened enough that a task planner, implementer, and reviewer can all reach the same conclusion from the written files.

## Workflow

1. Ground in the target package.
   Read `spec.md`, `contracts.md`, and the current `**Status**:` line. Confirm the package lives under `project_manager/specs/[feature_name]/`.
2. Exit early for terminal packages.
   If `spec.md` is already in a terminal status such as `Approved` or `Completed`, stop after summarizing the current state.
3. Run the authoritative loop.
   Use `project_manager/spec_loop.py --spec-dir <target> --max-rounds 10` as the default path unless the user explicitly requests a different model or round cap.
4. Accept clean loop approval.
   If the loop leaves the package in a terminal approved state, summarize what changed and stop.
5. Fallback on `max_rounds_exhausted`.
   If the loop stops without approval, switch to the final protocol in [fallback-approval-protocol.md](./references/fallback-approval-protocol.md).
6. Finish with a strict re-read.
   Re-read `spec.md` and `contracts.md` after fallback edits. Only then set `spec.md` to `Approved` and summarize whether approval came from the loop or the fallback pass.

## Defaults

- Target path: `project_manager/specs/[feature_name]/`
- Primary engine: `project_manager/spec_loop.py`
- Default rounds: `10`
- Required documents: `spec.md`, `contracts.md`
- Final standard: `spec-reviewer`

