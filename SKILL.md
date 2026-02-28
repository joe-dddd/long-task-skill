---
name: long-task
description: Use when executing multi-hour, multi-milestone engineering work that needs staged scoping, architecture alignment, disciplined implementation, and continuous documentation.
---

# Long Task

## Overview

`long-task` is an orchestration skill. It does not replace domain skills. It routes work through required phases, enforces gates, and keeps project docs synchronized with implementation reality.

Required outputs:
- `docs/prompt.md`
- `docs/architecture.md`
- `plans.md`
- `docs/implement.md`
- `docs/documentation.md`

## Required Superpowers Routing

Use these skills by phase:
- Scoping and requirements: `superpowers:brainstorming`
- Plan authoring: `superpowers:writing-plans`
- Isolated workspace: `superpowers:using-git-worktrees`
- Execution (same session): `superpowers:subagent-driven-development`
- Execution (separate session): `superpowers:executing-plans`
- Parallel-only for independent tasks: `superpowers:dispatching-parallel-agents`
- All implementation changes: `superpowers:test-driven-development`
- Any bug/test failure: `superpowers:systematic-debugging`
- Before success claims: `superpowers:verification-before-completion`
- End-of-branch workflow: `superpowers:finishing-a-development-branch`

## Phase Workflow

### Phase 0: Intake Discovery (hard gate before planning)
Collect and confirm minimum inputs:
1. Primary goal and success criteria
2. Non-goals and out-of-scope boundaries
3. Product/feature scope (what must be built first)
4. Tech/runtime constraints
5. Verification commands (`lint`, `test`, `typecheck`, `build`, integration checks)
6. Execution preferences (same session vs separate session, autonomy level, checkpoint preference)

If any required input is missing:
- MUST invoke `superpowers:brainstorming`
- Ask one question at a time until inputs are complete
- Propose 2-3 options when tradeoffs are non-trivial
- Do not start implementation actions

Forbidden before Gate G0 passes:
- creating final `plans.md`
- creating final `docs/implement.md`
- generating implementation tasks
- writing production code
- starting milestone execution

Gate G0 (required to continue):
- Input completeness is achieved and summarized.
- User confirms the intake summary.

### Phase 1: Environment Baseline
1. Set up an isolated worktree using `superpowers:using-git-worktrees` unless user explicitly opts out.
2. Run baseline verification commands and record status.

### Phase 2: Scope Contract (`docs/prompt.md`)
1. Use `superpowers:brainstorming` to finalize scope and acceptance boundaries.
2. Generate `docs/prompt.md` from template.

Gate G1 (required to continue):
- User confirms `docs/prompt.md`.

### Phase 3: Architecture Baseline (`docs/architecture.md`)
1. Use `superpowers:brainstorming` for architecture decisions that impact data model, execution model, consistency model, performance model, or deployment/runtime topology.
2. Generate initial `docs/architecture.md`.
3. Record architecture decisions with rationale.

Gate G2 (required to continue):
- User confirms architecture baseline.

### Phase 4: Plan Freeze (`plans.md`)
1. Invoke `superpowers:writing-plans`.
2. Generate milestone plan with granular steps and verification commands.
3. For every milestone, map required architecture sections to read before implementation.

Gate G3 (required to continue):
- `plans.md` exists, is coherent, and milestone-to-architecture mapping is complete.

### Phase 5: Execution Runbook (`docs/implement.md`)
1. Generate `docs/implement.md` using fixed execution constraints and project-specific command placeholders.
2. Select execution mode:
   - Same session: `superpowers:subagent-driven-development` (default)
   - Separate session: `superpowers:executing-plans`

Gate G4 (required to continue):
- Execution mode is explicit.
- `docs/implement.md` is complete enough to execute.

### Phase 6: Milestone Execution
For each milestone:
1. Read mapped architecture sections first.
2. Implement using TDD discipline.
3. If failures occur, run systematic debugging before fixes.
4. Run milestone verification commands.
5. Update `plans.md` implementation notes and verification checklist.
6. Update `docs/documentation.md` to match reality.
7. If implementation changes architecture behavior, update `docs/architecture.md` before moving on.

Gate G5 (per milestone):
- Verification passes.
- Docs are synchronized (`plans.md`, `docs/documentation.md`, and `docs/architecture.md` if affected).

### Phase 7: Final Verification and Branch Completion
1. Run full verification gate via `superpowers:verification-before-completion`.
2. Complete branch workflow via `superpowers:finishing-a-development-branch`.

Gate G6 (final):
- All milestones completed and verified.
- Final docs are accurate.

## Architecture Document Must Be Read

`docs/architecture.md` is mandatory runtime input, not passive documentation.

Before each milestone:
- Read the milestone-mapped architecture sections from `plans.md`.
- If code must deviate, update `docs/architecture.md` and `plans.md` before continuing.

Do not implement from `plans.md` alone when architecture mappings exist.

## Parallel Execution Rule

Use `superpowers:dispatching-parallel-agents` only when tasks are independent:
- Different subsystems
- No shared files/state conflicts
- No ordering dependency

Otherwise, execute sequentially.

## Incomplete Brief Handling

If user gives only a high-level goal (example: "build a crypto data center collecting Binance futures data"), treat it as incomplete intake.

Required behavior:
1. Start `superpowers:brainstorming` immediately.
2. Ask focused questions (one at a time) to fill missing required inputs from Gate G0.
3. Do not generate final plan or start implementation until Gate G0 passes.

## Templates

Use files under `templates/`:
- `templates/prompt.md`
- `templates/architecture.md`
- `templates/plans.md`
- `templates/implement.md`
- `templates/documentation.md`

Fill placeholders (`{{...}}`) with project-specific values.
