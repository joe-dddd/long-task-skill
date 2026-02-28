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

### Phase 0: Environment Baseline
1. Set up an isolated worktree using `superpowers:using-git-worktrees` unless user explicitly opts out.
2. Run baseline verification commands and record status.

### Phase 1: Scope Contract (`docs/prompt.md`)
1. Invoke `superpowers:brainstorming`.
2. Confirm goals, non-goals, constraints, success criteria.
3. Generate `docs/prompt.md` from template.

Gate G1 (required to continue):
- User confirms `docs/prompt.md`.

### Phase 2: Architecture Baseline (`docs/architecture.md`)
1. Use `superpowers:brainstorming` for architecture decisions that impact data model, execution model, consistency model, performance model, or deployment/runtime topology.
2. Generate initial `docs/architecture.md`.
3. Record architecture decisions with rationale.

Gate G2 (required to continue):
- User confirms architecture baseline.

### Phase 3: Plan Freeze (`plans.md`)
1. Invoke `superpowers:writing-plans`.
2. Generate milestone plan with granular steps and verification commands.
3. For every milestone, map required architecture sections to read before implementation.

Gate G3 (required to continue):
- `plans.md` exists, is coherent, and milestone-to-architecture mapping is complete.

### Phase 4: Execution Runbook (`docs/implement.md`)
1. Generate `docs/implement.md` using fixed execution constraints and project-specific command placeholders.
2. Select execution mode:
   - Same session: `superpowers:subagent-driven-development` (default)
   - Separate session: `superpowers:executing-plans`

### Phase 5: Milestone Execution
For each milestone:
1. Read mapped architecture sections first.
2. Implement using TDD discipline.
3. If failures occur, run systematic debugging before fixes.
4. Run milestone verification commands.
5. Update `plans.md` implementation notes and verification checklist.
6. Update `docs/documentation.md` to match reality.
7. If implementation changes architecture behavior, update `docs/architecture.md` before moving on.

Gate G4 (per milestone):
- Verification passes.
- Docs are synchronized (`plans.md`, `docs/documentation.md`, and `docs/architecture.md` if affected).

### Phase 6: Final Verification and Branch Completion
1. Run full verification gate via `superpowers:verification-before-completion`.
2. Complete branch workflow via `superpowers:finishing-a-development-branch`.

Gate G5 (final):
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

## Templates

Use files under `templates/`:
- `templates/prompt.md`
- `templates/architecture.md`
- `templates/plans.md`
- `templates/implement.md`
- `templates/documentation.md`

Fill placeholders (`{{...}}`) with project-specific values.
