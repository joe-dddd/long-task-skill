# {{PROJECT_NAME}} Architecture

This document is updated continuously as milestones land so it reflects implementation reality.

## Guiding principles

- `{{PRINCIPLE_1}}`
- `{{PRINCIPLE_2}}`
- `{{PRINCIPLE_3}}`

## Runtime overview

- App runtime: `{{APP_RUNTIME}}`
- Service/runtime dependencies: `{{SERVICE_RUNTIME}}`
- Local URLs/ports: `{{LOCAL_ENDPOINTS}}`
- Session/context model: `{{SESSION_MODEL}}`

## System model

Describe the core data model and invariants:
- Main entities: `{{CORE_ENTITIES}}`
- Identity strategy: `{{ID_STRATEGY}}`
- Ordering strategy: `{{ORDERING_STRATEGY}}`
- Serialization/canonicalization strategy: `{{SERIALIZATION_STRATEGY}}`

## State transition model

- Change unit: `{{STATE_CHANGE_UNIT}}`
- Apply path: `{{APPLY_PIPELINE}}`
- Undo/redo/history model: `{{HISTORY_MODEL}}`
- Determinism strategy: `{{DETERMINISM_STRATEGY}}`

## Rendering and interaction pipeline

- Rendering approach: `{{RENDERING_APPROACH}}`
- Input handling path: `{{INPUT_PIPELINE}}`
- Draft/commit strategy: `{{DRAFT_COMMIT_STRATEGY}}`

## Collaboration and authority model

- Sync transport/protocol: `{{SYNC_TRANSPORT}}`
- Authority model: `{{AUTHORITY_MODEL}}`
- Conflict handling/rebase strategy: `{{CONFLICT_STRATEGY}}`
- Presence model: `{{PRESENCE_MODEL}}`

## Persistence and IO flows

- Autosave/persistence path: `{{AUTOSAVE_PATH}}`
- Import/export path: `{{IMPORT_EXPORT_PATH}}`
- Recovery strategy: `{{RECOVERY_STRATEGY}}`

## Export and determinism

- Export targets: `{{EXPORT_TARGETS}}`
- Deterministic output strategy: `{{EXPORT_DETERMINISM_STRATEGY}}`
- Snapshot/regression strategy: `{{SNAPSHOT_STRATEGY}}`

## Performance guardrails

- Critical hot paths: `{{HOT_PATHS}}`
- Caching/memoization strategy: `{{CACHE_STRATEGY}}`
- Performance tests/thresholds: `{{PERF_TEST_STRATEGY}}`

## Security and boundary constraints

- Input boundaries and validation: `{{INPUT_VALIDATION}}`
- Secret/config handling: `{{SECRET_HANDLING}}`
- Safety constraints: `{{SAFETY_CONSTRAINTS}}`

## Decision log

| Date | Decision | Context | Alternatives | Rationale | Impacted Modules |
|---|---|---|---|---|---|
| {{DATE_1}} | {{DECISION_1}} | {{CONTEXT_1}} | {{ALTS_1}} | {{RATIONALE_1}} | {{MODULES_1}} |

## Milestone mapping contract

Each milestone in `plans.md` must list required architecture sections from this file.
Implementation must read those sections before coding starts for that milestone.
