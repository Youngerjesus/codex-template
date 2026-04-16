# Curated Bundle

`project-bootstrap` installs a curated default bundle. It is intentionally selective.

## Default Agents

- `document-writer`
- `product-builder`
- `project-reviewer`
- `decision-brake-reviewer`
- `implementation-brake-reviewer`
- `task-master`
- `task-reviewer`
- `code-reviewer`
- `testing-reviewer`
- `security-reviewer`
- `verifier`
- `context-synchronizer`
- `staff-engineer`

## Source-Only Bootstrap Skill

- `project-bootstrap`

`project-bootstrap` is the bootstrap source skill that builds the template. It is not copied into generated templates by default because its own nested template payload would recurse.

## Default Installed Skills

- `context-sync`
- `decision-brake`
- `implementation-brake`
- `requirement-clarifier`
- `scenario-brake`
- `plan-eng-review`
- `spec-creator`
- `spec-reviewer`
- `task-master-planning`
- `tdd-workflow`
- `systematic-debugging`

## Selection Rules

- Prefer existing proven assets over inventing new ones.
- Remove domain-specific language, proprietary workflows, and hard stack assumptions.
- Exclude optional specialist assets from the default bundle when they only apply to narrow UI, infra, or domain situations.
