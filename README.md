# long-task skill

`long-task` is a Codex skill for long-running engineering execution across many milestones.

It is designed as an orchestration skill: it does not replace implementation skills. It routes work through staged documents, explicit gates, and required workflow skills (planning, TDD, debugging, verification, branch completion).

## Why this skill exists

Long tasks often fail because:
- scope is not locked before coding
- architecture decisions are undocumented or ignored during implementation
- milestones are implemented without repeatable verification gates
- documentation drifts away from code reality

`long-task` solves this by enforcing a document-driven lifecycle:
- `docs/prompt.md` (scope contract)
- `docs/architecture.md` (architecture baseline and decisions)
- `plans.md` (milestones and verification plan)
- `docs/implement.md` (execution runbook)
- `docs/documentation.md` (continuous project documentation)

## Core workflow

1. Scope phase (`prompt.md`) with user alignment.
2. Architecture phase (`architecture.md`) with explicit decisions.
3. Planning phase (`plans.md`) with milestone-level verification steps.
4. Execution phase (`implement.md`) with strict gates.
5. Continuous docs updates (`documentation.md`) during implementation.
6. Final verification before completion claims.

## References

Primary reference:
- OpenAI Cookbook: Long-horizon tasks with Codex  
  https://developers.openai.com/cookbook/examples/codex/long_horizon_tasks/

Reference implementation materials:
- long_horizon_tasks.md  
  https://raw.githubusercontent.com/openai/openai-cookbook/main/examples/codex/long_horizon_tasks.md
- design-desk prompt.md  
  https://raw.githubusercontent.com/derrickchoi-openai/design-desk/main/docs/prompt.md
- design-desk architecture.md  
  https://raw.githubusercontent.com/derrickchoi-openai/design-desk/main/docs/architecture.md
- design-desk plans.md  
  https://raw.githubusercontent.com/derrickchoi-openai/design-desk/main/docs/plans.md
- design-desk implement.md  
  https://raw.githubusercontent.com/derrickchoi-openai/design-desk/main/docs/implement.md
- design-desk documentation.md  
  https://raw.githubusercontent.com/derrickchoi-openai/design-desk/main/docs/documentation.md

## Install into Codex

### Option A: Personal skill (recommended)

```bash
mkdir -p ~/.codex/skills
git clone git@github.com:joe-dddd/long-task-skill.git ~/.codex/skills/long-task
```

Expected structure:

```text
~/.codex/skills/long-task/
  SKILL.md
  templates/
```

### Option B: Project-shared skill

From a project root:

```bash
mkdir -p .codex/skills/long-task
cp -R /path/to/long-task-skill/SKILL.md /path/to/long-task-skill/templates .codex/skills/long-task/
```

Expected structure:

```text
.codex/skills/long-task/
  SKILL.md
  templates/
```

## Usage notes

- `SKILL.md` is the skill entrypoint.
- Template files under `templates/` are copied and filled per long task.
- Keep placeholder substitution explicit (`{{...}}`) and project-specific.
