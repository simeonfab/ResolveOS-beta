---
type: skill
scope: global
owner: ResolveOS
version: 0.1
status: draft
source_project: ResolvePM
source_files:
  - migration/resolvepm-extraction-audit.md
  - migration/resolvepm-extraction-map.md
related_skills:
  - 03-skills/ticket-writing.md
  - 03-skills/completion-reporting.md
  - 03-skills/user-feedback-processing.md
related_context:
  - 00-system/ai-operating-principles.md
  - 01-context/context-loading-rules.md
  - 01-context/startup-context.md
related_governance:
  - 06-governance/codex-working-rules.md
  - 06-governance/extraction-migration-guardrails.md
  - 06-governance/source-of-truth-rules.md
  - 06-governance/architecture-decisions.md
review_required: true
---

# Purpose

Define how acceptance criteria are written, reviewed, validated, and maintained in ResolveOS-enabled work.

This skill preserves reusable ResolvePM guidance around observable outcomes, scope boundaries, testability, validation, implementation drift, manual testability, and completion honesty. It is not generic Agile guidance.

Source references:

- `migration/resolvepm-extraction-audit.md` > `Global Ticket Writing Rules`
- `migration/resolvepm-extraction-map.md` > `Global Ticket Writing Rules`
- `migration/resolvepm-extraction-map.md` > `Extraction Table`
- `AGENTS.md.backup` > `Core Working Rules`
- `docs/project-context/implementation-workflow.md` > `Tickets`

# When To Use

Use this skill when:

- Writing acceptance criteria for a ticket, task, briefing, implementation plan, or follow-up item.
- Reviewing whether acceptance criteria are clear enough for implementation.
- Checking whether completed work satisfies the agreed scope.
- Handling implementation drift that may affect completion.
- Turning feedback, bugs, blockers, or follow-up work into testable outcomes.

Do not use this skill to invent missing product direction, implementation plans, project-specific verification commands, or roadmap scope.

# Inputs

Before writing or reviewing acceptance criteria, gather:

- ticket or task title
- goal
- background or context
- scope
- out-of-scope items or non-goals
- assumptions
- dependencies or prerequisites
- implementation notes
- user-visible expectations
- relevant data, permission, configuration, error, or empty-state expectations
- manual test steps, when available
- project-specific validation commands, when available

If source-system access is unavailable, ask for the missing ticket description or relevant comments.

Do not guess missing acceptance criteria.

Source references:

- `AGENTS.md.backup` > read title, goal, scope, acceptance criteria, implementation notes, and manual test steps
- `AGENTS.md.backup` > do not guess missing acceptance criteria
- `migration/resolvepm-extraction-map.md` > `Extraction Table` > `Do not guess missing acceptance criteria`

# Acceptance Criteria Principles

Acceptance criteria should describe observable completion conditions.

Acceptance criteria should describe outcomes, not hidden implementation instructions.

Acceptance criteria should make clear what must be true for the work to be accepted.

Acceptance criteria should be testable by an implementer, reviewer, or admin.

Acceptance criteria should preserve ticket scope. They should not smuggle in hidden scope, future roadmap work, speculative architecture, or unrelated features.

Acceptance criteria should cover important functional expectations, and should include non-functional expectations where they affect acceptance.

Acceptance criteria should be specific enough to validate, but not so implementation-prescriptive that they prevent a better implementation path.

If implementation drift affects acceptance criteria, do not mark the ticket complete unless the criteria are still satisfied.

Source references:

- `03-skills/ticket-writing.md` > `Acceptance Criteria Guidance`
- `AGENTS.md.backup` > implementation drift and acceptance criteria completion gate
- `docs/project-context/implementation-workflow.md` > tickets define what is achieved, why it matters, scope, assumptions, dependencies, sequencing notes, and non-goals

# Writing Acceptance Criteria

Write criteria from the agreed outcome and scope.

Good acceptance criteria usually identify:

- starting condition
- action, event, or trigger
- observable result
- important state change
- expected user-visible behaviour
- empty state, when relevant
- error state, when relevant
- permission, security, or configuration constraint, when relevant
- data persistence or retrieval expectation, when relevant
- validation, build, test, or deployment gate, when relevant

Keep criteria clear and direct.

Use criteria to define acceptance, not to narrate every implementation step.

If an implementation detail is required because it is a real constraint, include it carefully and explain why it is acceptance-critical.

If the criterion is really an implementation note, move it to implementation notes.

If the criterion is really a test step, move it to validation or manual test steps.

If the criterion is really future scope, move it to follow-up work.

Source references:

- `03-skills/ticket-writing.md` > ticket structure and acceptance criteria guidance
- `migration/resolvepm-extraction-audit.md` > tickets should include acceptance criteria and manual test steps
- `docs/codex-briefings/CP-5-roadmap.md` and `docs/codex-briefings/CP-6-work-tracker.md` > repeated outcome-focused Given/When/Then examples

# Given / When / Then Guidance

Given / When / Then is recommended, not mandatory.

Use it where it improves clarity.

Do not force it into tickets where simpler criteria are clearer.

Recommended form:

```text
Given [starting condition],
When [user action, system action, event, or validation step happens],
Then [observable result is true].
```

Shorter variants are acceptable when they are clearer:

```text
Given [condition], then [observable result].
```

Use Given / When / Then especially for:

- user-facing workflow behaviour
- persistence after save, update, delete, refresh, or reload
- filters and search behaviour
- empty states
- error states
- permission or visibility rules
- validation requirements
- build, test, or deployment gates

Source references:

- `docs/codex-briefings/CP-5-roadmap.md` > repeated Given/When/Then acceptance criteria
- `docs/codex-briefings/CP-6-work-tracker.md` > repeated Given/When/Then acceptance criteria
- ADR-011 instruction from Batch 2B: Given / When / Then is recommended, not mandatory

# Validation Guidance

Acceptance criteria must be capable of validation.

Validation may be:

- manual
- automated
- command-based
- inspection-based
- review-based
- admin-confirmed

For every completed ticket, provide simple manual test steps the admin can follow as a non-technical user.

Manual test steps should include:

- what to run
- what page or surface to open
- what to click or type
- what the admin should see
- what confirms success

If project-specific commands are required, keep them project-specific. Do not make one project's lint, build, test, smoke, deployment, or migration commands global ResolveOS requirements.

If a check fails and the failure is related to the ticket, the ticket should not be called complete until the failure is resolved or admin accepts the limitation.

Source references:

- `AGENTS.md.backup` > `Check your work`
- `AGENTS.md.backup` > `Manual testing must be possible`
- `03-skills/completion-reporting.md` > reporting validation
- ADR-013 instruction from Batch 2B: project verification commands remain project-specific

# Definition Of Done Considerations

Definition of done is broader than acceptance criteria.

Acceptance criteria define what must be true for this work to be accepted.

Definition of done may also include:

- criteria satisfied
- implementation complete for the scoped ticket
- relevant checks run or clearly reported as not run
- manual testing possible
- documentation updated where relevant
- blockers reported
- drift reported
- no fake functionality
- no hidden scope
- no unreported failed state
- follow-up work separated from current completion

Do not claim work is done unless the scoped acceptance criteria and required validation have actually been satisfied or the limitation is explicitly reported.

Source references:

- `AGENTS.md.backup` > completion response format
- `AGENTS.md.backup` > do not claim ticket complete if build/lint/test fails
- `03-skills/completion-reporting.md` > completion honesty and partial work reporting
- `00-system/ai-operating-principles.md` > implementation honesty

# Review Expectations

When reviewing acceptance criteria, check:

- Is the expected outcome observable?
- Is the criterion testable?
- Is the criterion in scope?
- Is anything important missing?
- Is any hidden scope being introduced?
- Is any implementation instruction disguised as acceptance criteria?
- Are empty, error, permission, configuration, or data states needed?
- Are manual test steps possible?
- Are dependencies or blockers explicit?
- Does implementation drift affect whether the criteria are still met?

If the answer is unclear, flag it for admin review rather than guessing.

Source references:

- `migration/resolvepm-extraction-map.md` > acceptance criteria and manual test skill
- `06-governance/extraction-migration-guardrails.md` > preserve ticket-writing rules
- `00-system/ai-operating-principles.md` > explicit uncertainty

# Traceability Expectations

Acceptance criteria should remain traceable to the source of scope.

Useful traceability links include:

- ticket or task
- briefing
- feedback item
- blocker note
- implementation note
- decision record
- project context
- manual test step

When feedback becomes work, preserve traceability back to the original feedback and use this skill only after the feedback has been reviewed for conversion into work.

Source references:

- `03-skills/user-feedback-processing.md` > feedback-to-ticket traceability
- `03-skills/ticket-writing.md` > start from current ticket or approved scope
- `06-governance/source-of-truth-rules.md` > source ownership

# Anti-Patterns

Do not:

- guess missing acceptance criteria
- write vague criteria that cannot be validated
- write criteria that do not describe an observable outcome
- hide scope inside acceptance criteria
- use acceptance criteria as a disguised implementation plan
- add future roadmap work to current acceptance criteria
- ignore empty states, error states, permissions, configuration, or data persistence when they affect acceptance
- force Given / When / Then where simpler criteria are clearer
- mark a ticket complete when implementation drift means criteria are no longer satisfied
- claim validation passed unless it actually passed
- replace specific ResolvePM guidance with generic Agile wording

Source references:

- `AGENTS.md.backup` > do not guess missing acceptance criteria
- `AGENTS.md.backup` > if drift affects acceptance criteria, do not mark complete unless criteria are still satisfied
- `06-governance/extraction-migration-guardrails.md` > preserve ticket-writing rules

# Examples

Outcome-focused criteria:

```text
- Given a user saves a valid item, when the page reloads, then the saved item is still visible.
- Given no records exist, when the page loads, then a useful empty state is shown.
- Given data loading fails, then a clear error state is shown.
- Given required fields are missing, then the user sees a clear validation error.
```

Validation-oriented criterion:

```text
- Given the project build command is run, then the build passes.
```

Criterion that should be rewritten:

```text
- Add a new helper function in the data layer.
```

Why it is weak:

```text
This is an implementation instruction, not an observable acceptance condition.
Rewrite it as the outcome the helper must enable, or move the instruction to implementation notes.
```

# Related Skills

- `03-skills/ticket-writing.md`
- `03-skills/completion-reporting.md`
- `03-skills/user-feedback-processing.md`

# Related Governance

- `00-system/ai-operating-principles.md`
- `01-context/context-loading-rules.md`
- `01-context/startup-context.md`
- `06-governance/codex-working-rules.md`
- `06-governance/extraction-migration-guardrails.md`
- `06-governance/source-of-truth-rules.md`
- `06-governance/architecture-decisions.md`

# Source Merge Notes

Multiple source variants were consolidated:

- The strongest explicit caution is `Do not guess missing acceptance criteria`, preserved from `AGENTS.md.backup` and the extraction map.
- The strongest completion gate is `If the drift affects the acceptance criteria, do not mark the ticket complete unless the criteria are still satisfied`, preserved from `AGENTS.md.backup`.
- Given / When / Then guidance is extracted from repeated briefing examples and constrained by ADR-011: recommended, not mandatory.
- Manual validation guidance is extracted from `AGENTS.md.backup` and existing `ticket-writing.md`.
- Project-specific commands and platform details are not migrated into this global skill.

# Deferred Items

Deferred because they are out of scope for Batch 2D or require admin review:

- Project-specific verification commands.
- Full ticket or acceptance-criteria templates.
- Role-specific acceptance-criteria review responsibilities.
- Implementation-review drift template details beyond the acceptance gate.
- Project-specific Definition of Done checklists.

# Ambiguous Items For Admin Review

Admin review is needed for:

- Whether ResolveOS should define a canonical Definition of Done skill or keep it inside ticket-writing, completion-reporting, and acceptance criteria.
- Whether any project should make Given / When / Then mandatory as a local override.
- Which non-functional categories should become canonical rather than project-specific.
- Whether acceptance criteria should include severity or priority labels, or whether those belong only in ticket/feedback workflows.

# What This Skill Must Not Do

This skill must not:

- create templates
- define role responsibilities
- replace project-specific verification commands
- invent missing acceptance criteria
- promote ResolvePM product doctrine into global ResolveOS guidance
- weaken completion gates into vague readiness language
