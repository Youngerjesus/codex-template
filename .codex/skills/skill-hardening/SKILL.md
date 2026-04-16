---
name: skill-hardening
description: Use this skill to harden an existing project skill under `.codex/skills/*` by running the `project_manager/skill_loop.py` benchmark-and-review loop, accepting only revisions that improve benchmark performance and pass `skill-reviewer`.
---

# Skill Hardening

Use this skill when the user wants to strengthen an already-created project skill instead of writing a brand-new one.

## Use When

- Hardening an existing project-local skill under `.codex/skills/<skill-name>/`
- Running a repeatable benchmark-and-review loop after `skill-creator`
- Resuming a prior skill loop run under `project_manager/contexts/skill-loop/...`

## Do Not Use

- Creating a new skill from scratch
- Hardening `$CODEX_HOME/skills` or other external skill directories by default
- Treating vague prose edits as success without benchmark evidence

## Operating Rules

1. Treat `project_manager/skill_loop.py` as the authoritative loop engine.
2. Default scope is the target skill directory only.
3. The loop may patch the target skill directly, but must restore the best accepted snapshot if a round regresses.
4. Approval requires both benchmark improvement and a blocker-free `skill-reviewer` verdict.
5. Keep all loop artifacts under `project_manager/contexts/skill-loop/...`.

## Workflow

1. Confirm the target skill lives under `.codex/skills/<skill-name>/`.
2. Run `project_manager/skill_loop.py --skill-dir <path> --max-rounds 3` unless the user requests a different cap.
3. Review `scoreboard.json` and `final.md`.
4. Treat the best accepted snapshot as canonical.
