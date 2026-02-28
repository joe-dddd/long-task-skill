# {{PROJECT_NAME}} Implementation Plan

> **For Codex:** REQUIRED SUB-SKILL: Use `superpowers:subagent-driven-development` (same session) or `superpowers:executing-plans` (separate session) to implement this plan task-by-task.

**Goal:** {{GOAL}}

**Architecture baseline:** `docs/architecture.md`

**Execution runbook:** `docs/implement.md`

---

## Scope and non-goals

- In scope: {{IN_SCOPE}}
- Out of scope: {{OUT_OF_SCOPE}}

## Verification commands

- Lint: `{{LINT_CMD}}`
- Typecheck: `{{TYPECHECK_CMD}}`
- Unit tests: `{{UNIT_TEST_CMD}}`
- Integration/E2E: `{{INTEGRATION_CMD}}`
- Build/package: `{{BUILD_CMD}}`

## Verification checklist (keep updated)

- [ ] Lint passes
- [ ] Typecheck passes
- [ ] Unit tests pass
- [ ] Integration/E2E checks pass
- [ ] Build/package passes
- [ ] Milestone docs updated

## Risk register

| Risk | Impact | Likelihood | Mitigation | Owner | Status |
|---|---|---|---|---|---|
| {{RISK_1}} | {{RISK_1_IMPACT}} | {{RISK_1_LIKELIHOOD}} | {{RISK_1_MITIGATION}} | {{RISK_1_OWNER}} | Open |

## Demo script ({{DEMO_DURATION}})

1. {{DEMO_STEP_1}}
2. {{DEMO_STEP_2}}
3. {{DEMO_STEP_3}}

## Milestone index

| ID | Milestone | Scope | Architecture sections required before coding | Verification commands | Status |
|---|---|---|---|---|---|
| M01 | {{M01_NAME}} | {{M01_SCOPE}} | {{M01_ARCH_SECTIONS}} | `{{M01_VERIFY}}` | Planned |
| M02 | {{M02_NAME}} | {{M02_SCOPE}} | {{M02_ARCH_SECTIONS}} | `{{M02_VERIFY}}` | Planned |
| M03 | {{M03_NAME}} | {{M03_SCOPE}} | {{M03_ARCH_SECTIONS}} | `{{M03_VERIFY}}` | Planned |

## Milestones

### Milestone {{MID}}: {{MILESTONE_NAME}}

**Architecture sections to read first:**
- `{{ARCH_SECTION_1}}`
- `{{ARCH_SECTION_2}}`

**Files:**
- Create: `{{CREATE_PATHS}}`
- Modify: `{{MODIFY_PATHS}}`
- Test: `{{TEST_PATHS}}`

**Step 1: Write the failing test**

```{{TEST_LANGUAGE}}
{{FAILING_TEST_SNIPPET}}
```

**Step 2: Run to confirm failure**

Run: `{{RED_COMMAND}}`  
Expected: `{{RED_EXPECTED}}`

**Step 3: Write minimal implementation**

```{{IMPL_LANGUAGE}}
{{MINIMAL_IMPL_SNIPPET}}
```

**Step 4: Run verification**

Run: `{{GREEN_COMMAND}}`  
Expected: `{{GREEN_EXPECTED}}`

**Step 5: Commit**

```bash
{{COMMIT_COMMANDS}}
```

## Implementation Notes

- {{IMPLEMENTATION_NOTE_1}}

## Decisions made during implementation

- {{DECISION_NOTE_1}}
