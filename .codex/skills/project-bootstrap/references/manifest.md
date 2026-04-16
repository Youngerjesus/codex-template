# Bootstrap Manifest

This manifest is the file-level source of truth for `project-bootstrap`.

Every template-managed file under `templates/root/` that bootstrap may create, preserve, or update must be declared here.

| Path | Required | Condition | Overwrite | Upgrade Sync | Notes |
| --- | --- | --- | --- | --- | --- |
| `.codex/config.toml` | Yes | all modes | safe in `upgrade-sync` | Yes | installs shared agents |
| `.codex/agents/document-writer.toml` | Yes | all modes | safe in `upgrade-sync` | Yes | template-managed |
| `.codex/agents/product-builder.toml` | Yes | all modes | safe in `upgrade-sync` | Yes | template-managed |
| `.codex/agents/project-reviewer.toml` | Yes | all modes | safe in `upgrade-sync` | Yes | template-managed |
| `.codex/agents/decision-brake-reviewer.toml` | Yes | all modes | safe in `upgrade-sync` | Yes | template-managed |
| `.codex/agents/implementation-brake-reviewer.toml` | Yes | all modes | safe in `upgrade-sync` | Yes | template-managed |
| `.codex/agents/task-master.toml` | Yes | all modes | safe in `upgrade-sync` | Yes | template-managed |
| `.codex/agents/task-reviewer.toml` | Yes | all modes | safe in `upgrade-sync` | Yes | template-managed |
| `.codex/agents/code-reviewer.toml` | Yes | all modes | safe in `upgrade-sync` | Yes | template-managed |
| `.codex/agents/testing-reviewer.toml` | Yes | all modes | safe in `upgrade-sync` | Yes | template-managed |
| `.codex/agents/security-reviewer.toml` | Yes | all modes | safe in `upgrade-sync` | Yes | template-managed |
| `.codex/agents/verifier.toml` | Yes | all modes | safe in `upgrade-sync` | Yes | minimal spec mode aware |
| `.codex/agents/context-synchronizer.toml` | Yes | all modes | safe in `upgrade-sync` | Yes | template-managed |
| `.codex/agents/staff-engineer.toml` | Yes | all modes | safe in `upgrade-sync` | Yes | template-managed |
| `.codex/docs/template_customization.md` | Yes | all modes | safe in `upgrade-sync` | Yes | includes bootstrap marker |
| `.codex/skills/context-sync/SKILL.md` | Yes | all modes | preserve | No | installed runtime skill |
| `.codex/skills/decision-brake/SKILL.md` | Yes | all modes | preserve | No | installed runtime skill |
| `.codex/skills/decision-brake/references/review-lenses.md` | Yes | all modes | preserve | No | direct skill reference |
| `.codex/skills/implementation-brake/SKILL.md` | Yes | all modes | preserve | No | installed runtime skill |
| `.codex/skills/implementation-brake/references/fix-handoff.md` | Yes | all modes | preserve | No | direct skill reference |
| `.codex/skills/implementation-brake/references/review-lenses.md` | Yes | all modes | preserve | No | direct skill reference |
| `.codex/skills/requirement-clarifier/SKILL.md` | Yes | all modes | preserve | No | installed runtime skill |
| `.codex/skills/scenario-brake/SKILL.md` | Yes | all modes | preserve | No | installed runtime skill |
| `.codex/skills/scenario-brake/references/review-lenses.md` | Yes | all modes | preserve | No | direct skill reference |
| `.codex/skills/plan-eng-review/SKILL.md` | Yes | all modes | preserve | No | installed runtime skill |
| `.codex/skills/spec-creator/SKILL.md` | Yes | all modes | preserve | No | installed runtime skill |
| `.codex/skills/spec-creator/SPEC_TEMPLATE.md` | Yes | all modes | preserve | No | direct skill asset |
| `.codex/skills/spec-creator/CONTRACT_TEMPLATE.md` | Yes | all modes | preserve | No | direct skill asset |
| `.codex/skills/spec-reviewer/SKILL.md` | Yes | all modes | preserve | No | installed runtime skill |
| `.codex/skills/task-master-planning/SKILL.md` | Yes | all modes | preserve | No | installed runtime skill |
| `.codex/skills/tdd-workflow/SKILL.md` | Yes | all modes | preserve | No | installed runtime skill |
| `.codex/skills/tdd-workflow/references/tdd-rules.md` | Yes | all modes | preserve | No | direct skill reference |
| `.codex/skills/tdd-workflow/references/verification-checklist.md` | Yes | all modes | preserve | No | direct skill reference |
| `.codex/skills/systematic-debugging/SKILL.md` | Yes | all modes | preserve | No | installed runtime skill |
| `.codex/skills/systematic-debugging/references/phase-gates.md` | Yes | all modes | preserve | No | direct skill reference |
| `.codex/skills/systematic-debugging/references/test-layer-selection.md` | Yes | all modes | preserve | No | direct skill reference |
| `.codex/skills/systematic-debugging/references/debug-report-template.md` | Yes | all modes | preserve | No | direct skill reference |
| `.codex/skills/systematic-debugging/root-cause-tracing.md` | Yes | all modes | preserve | No | direct skill reference |
| `.codex/skills/systematic-debugging/defense-in-depth.md` | Yes | all modes | preserve | No | direct skill reference |
| `.codex/skills/systematic-debugging/condition-based-waiting.md` | Yes | all modes | preserve | No | direct skill reference |
| `AGENTS.md` | Yes | all modes | never | No | strategic project doc |
| `README.md` | Yes | all modes | never | No | strategic project doc |
| `DESIGN.md` | Optional | UI-bearing projects only | never | No | root design SSOT |
| `main/README.md` | Yes | all modes | preserve | No | workspace intro |
| `main/.gitignore` | Yes | all modes | preserve | No | generic ignores |
| `main/.env.example` | Yes | all modes | preserve | No | placeholder only |
| `main/docs/project_overview.md` | Yes | all modes | never | No | project SSOT seed |
| `main/docs/tech_stack.md` | Yes | all modes | preserve | No | stack decisions |
| `main/docs/history_archives/history.md` | Yes | all modes | preserve | No | history seed |
| `main/specs/_template/spec.md` | Yes | all modes | never | No | minimal spec mode |
| `main/specs/_template/contracts.md` | Yes | all modes | never | No | minimal completion contract |
| `main/work_queue/progress.md` | Yes | all modes | preserve | No | project progress seed |
| `main/src/.gitkeep` | Yes | all modes | preserve | No | workspace seed |
| `main/tests/.gitkeep` | Yes | all modes | preserve | No | workspace seed |
| `main/contexts/.gitkeep` | Yes | all modes | preserve | No | context artifacts |
| `main/temp/todo.md` | Yes | all modes | preserve | No | scratchpad |
| `main/temp/temp.md` | Yes | all modes | preserve | No | scratchpad |
