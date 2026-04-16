# Fallback Approval Protocol

Use this protocol only after `project_manager/spec_loop.py` stops without approval, typically because `max_rounds` was exhausted.

## Inputs

Read all of the following before editing:

- the latest `project_manager/specs/[feature_name]/spec.md`
- the latest `project_manager/specs/[feature_name]/contracts.md`
- the latest evaluator review artifact from the spec loop
- the latest generator artifact from the spec loop, if present
- the loop final summary or resume state when it contains unresolved findings context
- `.codex/skills/spec-reviewer/SKILL.md`

## Goal

Convert a nearly-approved package into a dispute-resistant approved package without cloning the loop logic.

This pass is not another freeform brainstorm. It is a targeted hardening pass that closes the specific ambiguity, acceptance, and evidence gaps left after the loop.

## Final Pass Rules

1. Start from the latest unresolved findings.
   Treat the most recent evaluator output as the default defect list unless the documents themselves reveal a stricter blocker.
2. Apply the `spec-reviewer` standard directly.
   Reuse its approval gate, dispute-prevention checklist, and hardening rules as the acceptance bar for this pass.
3. Harden both documents together.
   Fix mismatched terminology, missing proof requirements, vague success criteria, and spec-contract drift in the same pass.
4. Prefer explicit evidence over prose.
   Replace subjective or implied language with commands, artifacts, matrices, rubrics, or named proof requirements.
5. Close shallow-worker loopholes.
   If a requirement still allows multiple plausible implementations or test strategies, tighten it before approval.
6. Keep scope inside the package.
   Do not widen the feature or rewrite unrelated docs while hardening.

## Approval Sequence

1. List the remaining blocker and major findings from the latest loop artifacts.
2. Edit `spec.md` and `contracts.md` until those findings are closed in writing.
3. Re-read both documents as:
   - a task planner
   - an implementer
   - a strict reviewer
4. If any requirement still depends on unwritten author intent, keep editing.
5. When blocker findings are closed and pass/fail can be judged from the written documents alone, set `spec.md` to `**Status**: Approved`.
6. Summarize:
   - that loop rounds were exhausted
   - which findings were closed in fallback
   - why the package now meets the `spec-reviewer` approval bar

## Guardrail

Do not approve a package that still requires missing product intent that cannot be derived from the repo, loop artifacts, or the written documents. In that case, stop and surface the precise unresolved decision instead of fabricating closure.
