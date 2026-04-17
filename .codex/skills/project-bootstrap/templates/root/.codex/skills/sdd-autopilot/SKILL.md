---
name: sdd-autopilot
description: Fully automated Spec-Driven Development (SDD) pipeline. Advances a feature specification from its initial draft (`spec.md` and `contracts.md`) through clarification, auditing, research, planning, design, task generation, contract finalization, consistency analysis, and readiness checks without human intervention.
---

# SDD Autopilot Workflow

This skill automatically guides the Spec-Driven Development (SDD) lifecycle without human intervention.
**Prerequisite:** Either the user provides an initial `spec.md` and `contracts.md`, or `project_manager` has already created them inside the target `specs/[spec-name]/` directory for the current worktree.
Your goal is to act as an autonomous orchestrator, utilizing specialized agents (specifically `product-builder` for product/UX decisions and `architect` for technical decisions) to drive the specification through rigorous validation and design steps, perfectly preparing it for implementation.

## Core Principle: Autonomous Execution & Agent Delegation
You must execute the following commands and steps in sequence.
- **NO HUMAN INTERVENTION**: Do NOT ask the user for input, clarification, or decisions during the interactive steps (`clarify`, `spec-audit`, `analyze`). 
- **AGENT DELEGATION**: Whenever a command requires a decision, clarification, or review, you MUST consult the `product-builder` agent (for product, requirements, and UX) or the `architect` agent (for technical, architecture, and system design) to resolve it autonomously.
- **AUTOPILOT SUB-SKILL MODE**: Whenever you invoke a question-oriented or review-oriented Speckit sub-skill (`clarify`, `checklist`, `task-details`, `analyze`), you MUST pass explicit autopilot/non-interactive instructions in the command input so the sub-skill resolves decisions through agents instead of waiting for the user.
- **ARTIFACT AUTHORITY**: Treat `plan.md` as the canonical implementation index, `data-model.md` as the authoritative data model, `contracts/` as the authoritative interface contract set, and `design.md` as the authoritative behavioral/architectural design.
- Communicate and document primarily in **Korean (한국어)**.
- Guide the execution focusing on:
  - High performance, scalability, and security.
  - Bulletproof edge-case handling.
  - Clear, measurable acceptance criteria.
  - Maintaining the product vision while hardening the engineering strategy.

## Execution Sequence

Execute the following steps one by one. Read the output of each command and perform the necessary follow-up actions autonomously before moving to the next step.

### Step 0: Initialization
1. Identify the `[spec-name]` from the user's request.
2. Resolve the feature directory from the current context in this priority order:
   - existing `specs/[spec-name]/`
   - a `project_manager`-prepared spec directory already present in the current `task-*` worktree
   - `.specify` helper scripts via current branch, `SPECIFY_FEATURE`, or `SPECIFY_FEATURE_DIR`
3. **Create the `specs/[spec-name]/` directory only if it does not already exist.**
4. If the user provided the content for the specification and contract in the prompt, **write them as `spec.md` and `contracts.md`** inside the resolved feature directory. If `project_manager` already created them, validate and adopt those files instead of overwriting them.
5. **Create or update `specs/[spec-name]/spec-progress.md`** based on the template below to track the SDD pipeline progress.
6. All subsequent commands and file modifications must occur within this directory to maintain strict context isolation.

#### `spec-progress.md` Template
```markdown
# SDD Autopilot Progress: [spec-name]

- [x] Step 0: Initialization / Artifact Adoption
- [ ] Step 1: Clarification Loop (`/speckit:clarify`)
- [ ] Step 2: Checklist Generation (`/speckit:checklist`)
- [ ] Step 3: First Strategic Audit Loop (`speckit-audit`)
- [ ] Step 4: Research (`/speckit:research`)
- [ ] Step 5: Planning (`/speckit:plan`)
- [ ] Step 6: Technical Design (`speckit-design`)
- [ ] Step 7: Task Breakdown (`/speckit:tasks`)
- [ ] Step 8: Task Details Injection (`/speckit:task-details`)
- [ ] Step 9: Subtask Decomposition (`/speckit:subtasks`)
- [ ] Step 10: Contract Finalization (`/speckit:contract`)
- [ ] Step 11: Consistency Analysis (`/speckit:analyze`)
- [ ] Step 12: Final Strategic Audit Loop (`speckit-audit`)
- [ ] Step 13: Readiness Gate (`/speckit:readiness`)
```

#### Step 0 validation notes
- `project_manager`-created `spec.md` and `contracts.md` are first-class inputs. Do not recreate them if they already exist.
- `task-015-something` style worktree branches are valid when they resolve to a single `specs/015-*` directory.
- If helper scripts cannot resolve the feature path automatically, use `SPECIFY_FEATURE` or `SPECIFY_FEATURE_DIR` explicitly rather than abandoning the pipeline.

### Step 1: Clarification Loop (`/speckit:clarify`)
1. Run the `/speckit:clarify` command in explicit autopilot/non-interactive mode.
2. Read the multiple-choice or short-answer questions presented by the command.
3. **Consult the `product-builder` agent** to answer all product, UX, and requirement-related questions. Consult the `architect` agent for purely technical questions.
4. Apply the agents' answers to the spec as instructed by the `clarify` command output.
5. Repeat `/speckit:clarify` until the command reports "No critical ambiguities detected" or that all categories are Clear.
6. **Update `spec-progress.md`**: Mark Step 1 as completed `[x]`.

### Step 2: Checklist Generation (`/speckit:checklist`)
1. Run the `/speckit:checklist` command in explicit autopilot/non-interactive mode.
2. **Consult the `product-builder` agent** to identify the most critical focus areas (e.g., Security, UX, Edge Cases) based on the core product values.
3. Ensure the checklist remains focused on requirement quality, clarity, completeness, and edge-case coverage rather than implementation testing.
4. **Update `spec-progress.md`**: Mark Step 2 as completed `[x]`.

### Step 3: First Strategic Audit Loop (`speckit-audit`)
1. Run the `speckit-audit` skill or command.
2. Review the Markdown report detailing 🔴 Critical Flaws and 🟡 Strategic Refinements.
3. If flaws are found:
   - **Delegate to the `product-builder` and `architect` agents** to resolve the critical flaws and incorporate strategic refinements. Propose specific rewrites or updates for `spec.md` to them and apply their approved modifications.
   - Update `spec.md` autonomously to resolve the critical flaws.
   - Run `speckit-audit` again.
4. Repeat this loop until `speckit-audit` yields a clean bill of health (no critical flaws).
5. **Update `spec-progress.md`**: Mark Step 3 as completed `[x]`.

### Step 4: Research (`/speckit:research`)
1. Run the `/speckit:research` command to investigate technical unknowns and architecture choices, producing `research.md`.
2. **Consult the `architect` agent** to review the research findings and make final decisions on trade-offs.
3. Once the architect decides, ensure `research.md` is finalized.
4. **Update `spec-progress.md`**: Mark Step 4 as completed `[x]`.

### Step 5: Planning (`/speckit:plan`)
1. Run the `/speckit:plan` command to generate the technical implementation plan (`plan.md`) based on the completed `research.md`.
2. Verify `plan.md` is successfully generated and that it references any newly created `data-model.md`, `contracts/`, and `quickstart.md` artifacts as downstream authorities.
3. **Update `spec-progress.md`**: Mark Step 5 as completed `[x]`.

### Step 6: Technical Design (`speckit-design`)
1. Run the `speckit-design` skill or command to generate the detailed technical design document (`design.md` or similar).
2. Verify the design document is successfully generated.
3. **Update `spec-progress.md`**: Mark Step 6 as completed `[x]`.

### Step 7: Task Breakdown (`/speckit:tasks`)
1. Run the `/speckit:tasks` command to generate the parallelized execution tasks (`tasks.md`).
2. Verify `tasks.md` is successfully generated.
3. **Update `spec-progress.md`**: Mark Step 7 as completed `[x]`.

### Step 8: Task Details Injection (`/speckit:task-details`)
1. Run the `/speckit:task-details` command in explicit autopilot/non-interactive mode to enrich tasks in `tasks.md` with precise technical details.
2. If ambiguities or questions are generated, **consult the `architect` agent** to resolve them autonomously.
3. Update `tasks.md` (or rerun clarification/details if necessary) until all task details are explicitly clear.
4. **Update `spec-progress.md`**: Mark Step 8 as completed `[x]`.

### Step 9: Subtask Decomposition (`/speckit:subtasks`)
1. Run the `/speckit:subtasks` command to expand complex monolithic tasks in `tasks.md` into granular config/state/execution subtasks.
2. Verify `tasks.md` is successfully updated with the indented subtasks.
3. **Update `spec-progress.md`**: Mark Step 9 as completed `[x]`.

### Step 10: Contract Finalization (`/speckit:contract`)
1. Run the `/speckit:contract` command after `design.md`, `tasks.md`, and the task refinements are finalized.
2. **Delegate to the `architect` agent** to ensure the API endpoints, data schemas, system boundaries, and completion gates reflect the latest technical decisions.
3. If `contracts.md` does not exist, create it; if it exists, enhance it with detailed validation rules and edge-case handling.
4. Do not create or update a parallel singular contract file; `contracts.md` is the canonical contract artifact.
5. **Update `spec-progress.md`**: Mark Step 10 as completed `[x]`.

### Step 11: Consistency Analysis (`/speckit:analyze`)
1. Run the `/speckit:analyze` command in explicit autopilot/non-interactive mode to perform a cross-artifact scan.
2. Review the resulting Analysis Report.
3. If inconsistencies, missing coverage, or constitution violations are found:
   - **Consult the relevant agents (`product-builder` or `architect`)** to determine how to resolve the issues in the offending artifacts (`spec.md`, `contracts.md`, `research.md`, `plan.md`, `design.md`, or `tasks.md`).
   - Edit the artifacts autonomously based on the agents' guidance. `speckit:analyze` itself remains read-only; the remediation work is performed by the orchestrator after reading the report.
   - Run `/speckit:analyze` again to confirm all artifacts are perfectly aligned.
4. **Update `spec-progress.md`**: Mark Step 11 as completed `[x]`.

### Step 12: Final Strategic Audit Loop (`speckit-audit`)
1. Run `speckit-audit` one final time to ensure the sweeping architectural decisions, contract definitions, and task breakdowns have not introduced new logical gaps.
2. **Consult the `architect` agent** to fix any new issues in `spec.md`, `plan.md`, `design.md`, or `contracts.md`.
3. **Update `spec-progress.md`**: Mark Step 12 as completed `[x]`.

### Step 13: Readiness Gate (`/speckit:readiness`)
1. Run the `/speckit:readiness` command.
2. Review the Readiness Report.
3. If the verdict is **NO-GO** due to critical blockers (e.g., TBD items, missing environment configs):
   - **STOP IMMEDIATELY**.
   - Do not attempt to resolve the blockers autonomously.
   - Provide a detailed explanation to the user about why the implementation cannot proceed and what specific blockers were found.
4. If the verdict is **GO**, **Update `spec-progress.md`**: Mark Step 13 as completed `[x]`.

## Completion
Once `/speckit:readiness` returns a **GO** verdict, print a concise summary of the major architectural decisions made and confirm that the project is completely ready for the Phase 2 implementation loop via `sdd-implement-loop`. Mention `speckit-implement` only as an optional targeted implementation path for a single task.
