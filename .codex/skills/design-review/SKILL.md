---
name: design-review
description: Audit and polish the rendered UI of this project. Use when the user asks for visual QA, design polish, UI consistency review, or to check whether a live page actually looks good. This skill inspects the rendered app first, aligns findings to the repo's Toss-like trust baseline, then applies minimal source fixes and re-verifies them.
---

# Design Review

Use this skill when the user wants rendered UI critique plus concrete fixes, not just a static design opinion.

## What This Skill Produces

- A rendered-design audit grounded in the current app, not guesswork
- A prioritized list of visual, hierarchy, spacing, interaction, and consistency issues
- Minimal source changes for fixable issues, followed by re-verification
- A short audit artifact or summary the user can act on

When this skill is used inside a loop or audit workflow, store the canonical review artifact under `project_manager/contexts/...` or the orchestrator-provided output path.

## Operating Rules

1. Start from the live UI.
   Inspect the rendered page first. Do not begin with source-only critique.
2. Calibrate against repo truth.
   Read `AGENTS.md`, `DESIGN.md` if present, the Toss-like design-system spec, and relevant frontend token files before judging severity.
3. Treat this project as app UI first.
   The baseline is a trustworthy, analytical, mobile-first app surface, not a generic landing page or decorative brand site.
4. Fix narrowly.
   Prefer small styling or structure changes that resolve a specific finding. Do not use design review as a pretext for broad refactors.
5. Re-verify every fix.
   After editing code, re-check the affected page in a real browser flow before closing the finding.

## Workflow

### 1. Ground in Repo Context

Read these first:

- `AGENTS.md`
- `DESIGN.md` if it exists
- `specs/008-toss-design-system/spec.md`
- `specs/008-toss-design-system/design.md`
- relevant frontend style files such as `frontend/src/styles/globals.css`, `frontend/tailwind.config.ts`, and root layout/font setup

Then read [project-alignment.md](./references/project-alignment.md).

### 2. Choose the Review Mode

Pick one mode explicitly:

- **Live Audit**: the user gives a URL or wants a running local page checked
- **Diff-Aware Audit**: no URL is given and the current branch changed specific UI files
- **Targeted Polish**: one page, component, or flow needs review
- **Regression Audit**: compare current UI against a known baseline, prior artifact, or recent change

### 3. Establish a Browser Verification Path

Use the local browser-testing workflow when the page must be rendered locally.

- Prefer the helpers in `main/.codex/skills/browser-testing/` to start and stop the dev environment safely.
- Use browser automation or browser MCP tools to inspect the page, capture screenshots, and verify fixes.
- If a stable local URL already exists, use it directly.

Do not rely on gstack browse or design binaries.

### 4. Audit the Rendered Experience

Use the checklist in [audit-checklist.md](./references/audit-checklist.md).

Audit in this order:

- first impression and hierarchy
- design-system consistency
- spacing, typography, and color discipline
- mobile behavior and touch ergonomics
- interaction states and perceived responsiveness
- AI-slop patterns or generic template artifacts

Every finding should include:

- what is wrong
- why it matters for user trust or comprehension
- severity: high, medium, or polish
- the likely source area to inspect

### 5. Fix Only What Is Safe and Verifiable

Use the guidance in [fix-loop.md](./references/fix-loop.md).

Default fix style:

- CSS and token fixes first
- component-level markup adjustments second
- behavior changes only when the issue is truly interaction-related

When the worktree is already dirty, do not overwrite unrelated user changes. Work around them carefully or stop if the same files conflict.

### 6. Verify and Summarize

Before finishing:

- re-open the affected page
- confirm the specific issue is actually resolved
- check mobile and desktop if the fix changes layout
- note anything deferred because it needs larger design or product input

If the user asked for review only, stop at findings. If they asked for polish or fixes, carry through implementation and verification.
If an orchestration workflow explicitly says `artifacts-only`, do not modify production UI code and only emit findings plus evidence.

## Constraints and Anti-Patterns

- Do not import gstack telemetry, review logs, home-directory artifact storage, or CLAUDE routing behavior.
- Do not treat this as source-only code review unless the rendered UI is unavailable.
- Do not score marketing-page aesthetics ahead of app trust and usability for this repo.
- Do not refactor broad frontend architecture under the banner of "design polish."
- Do not claim a fix is complete without re-checking the affected UI.

## References

- [project-alignment.md](./references/project-alignment.md)
- [audit-checklist.md](./references/audit-checklist.md)
- [fix-loop.md](./references/fix-loop.md)
