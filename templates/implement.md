Now implement the entire project end-to-end.

## Execution mode

- Default mode: same-session execution with `superpowers:subagent-driven-development`.
- Alternate mode: separate-session execution with `superpowers:executing-plans`.
- Choose mode based on user preference and task coupling.

## Non-negotiable constraints

- Unless the user explicitly asks for milestone checkpoints, do not stop after each milestone to ask for confirmation.
- Proceed through every milestone in `plans.md` until the project is complete and fully validated.

## Execution rules (follow strictly)

- Treat `plans.md` as the source of truth for scope and milestone sequencing.
- Treat `docs/architecture.md` as mandatory runtime input:
  - before each milestone, read mapped architecture sections from `plans.md`
  - if implementation must deviate, update `docs/architecture.md` and `plans.md` before coding
- If anything is ambiguous, make a reasonable decision and record it in `plans.md` before coding.
- Implement deliberately with small, reviewable commits. Avoid bundling unrelated changes.
- After every milestone:
  - run verification commands from `plans.md` (`{{LINT_CMD}}`, `{{TYPECHECK_CMD}}`, `{{TEST_CMD}}`, `{{INTEGRATION_CMD}}`, `{{BUILD_CMD}}`)
  - fix all failures immediately
  - add or update tests that cover the milestone core behavior
  - commit with a clear message referencing the milestone name
  - update `docs/documentation.md` to match implementation reality
- If a bug is discovered at any point:
  - invoke `superpowers:systematic-debugging` before proposing fixes
  - write a failing test that reproduces it
  - fix the bug
  - confirm the test now passes
  - record a short note in `plans.md` under "Implementation Notes"

## Validation requirements

- Maintain a "verification checklist" section in `plans.md` and keep it accurate.
- Use `superpowers:verification-before-completion` before any completion claims.
- Enforce deterministic behavior for `{{DETERMINISM_SURFACES}}` where relevant, with stable ordering and snapshot/regression tests.

## Documentation requirements

- Create `docs/documentation.md` and keep it concise and useful.
- Update it continuously so it matches the current repo state.
- At minimum, include:
  - what the project is
  - local setup and one-command dev start
  - how to run tests, lint, typecheck, and build
  - how to run key workflows/CLI with examples
  - demo flow(s)
  - repo structure overview
  - architecture and data format overview
  - troubleshooting section (top issues and fixes)

## Completion criteria (do not stop until all are true)

- All milestones in `plans.md` are implemented and checked off.
- `{{DEV_CMD}}` works and default demo/starter state loads as expected.
- Feature acceptance criteria are met:
  - `{{FEATURE_ACCEPTANCE_1}}`
  - `{{FEATURE_ACCEPTANCE_2}}`
  - `{{FEATURE_ACCEPTANCE_3}}`
- Verification commands all pass:
  - `{{TEST_CMD}}`
  - `{{LINT_CMD}}`
  - `{{TYPECHECK_CMD}}`
  - `{{BUILD_CMD}}`
- `docs/documentation.md` is accurate and complete.

Start now by reading `plans.md` and `docs/architecture.md`, then begin Milestone 1.
