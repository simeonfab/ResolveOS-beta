---
type: knowledge_bundle
scope: global
owner: ResolveOS
source_repository: https://github.com/simeonfab/ResolveOS
source_commit: c578659caa3766a8efe63e6b5c43cd1dc078eb81
generated: true
generated_date: 2026-06-22
included_paths:
  - 03-skills/acceptance-criteria.md
  - 03-skills/completion-reporting.md
  - 03-skills/dependency-management.md
  - 03-skills/documentation-storage-architecture.md
  - 03-skills/implementation-review.md
  - 03-skills/requirement-traceability.md
  - 03-skills/ticket-writing.md
  - 03-skills/user-feedback-processing.md
  - 05-workflows/feedback-to-ticket.md
  - 05-workflows/implementation-review-loop.md
  - 05-workflows/project-initiation.md
  - 05-workflows/ticket-to-implementation.md
  - 05-workflows/user-guide.md
---

# Source: 03-skills/acceptance-criteria.md

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

---

# Source: 03-skills/completion-reporting.md

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

# Completion Reporting

## Purpose

Define the canonical ResolveOS skill for reporting completed, partial, failed, blocked, or deferred work.

This skill preserves ResolvePM guidance about implementation honesty, blocker reporting, validation reporting, uncertainty, manual steps, changed files, command execution, deployment status, review status, and follow-up work.

This file is a skill, not a template. A future completion report template may be created separately after review.

Source references:

- Extraction map: `High Risk Migrations`
- Extraction map: `Global Working Preferences`
- Extraction map: `Assistant Anti-Patterns`
- Audit: `Risks / Things Not To Lose`
- Inline ADR instruction: ADR-012 says completion reporting consists of a skill and a future template; this batch creates only the skill.

## When To Use

Use this skill whenever an assistant, agent, or Codex reports the state of work.

Use it after:

- implementation
- migration batches
- audit or extraction work
- ticket refinement
- review work
- debugging
- failed or blocked attempts
- validation or testing
- deployment-related work

Use it even when work is partial, blocked, or failed. Completion reporting is not only for successful work.

Source references:

- Extraction table: `AGENTS.md.backup` completion response format
- Extraction table: `docs/ai-roles/implementation-engineer.md` required completion report format
- Extraction map: `Global Working Preferences`

## Inputs

Before reporting, identify:

- requested task, ticket, batch, or scope
- files created, modified, removed, or intentionally left untouched
- commands run
- checks run
- checks not run
- command outcomes
- validation performed
- validation not performed
- blockers encountered
- assumptions made
- deviations from the original plan
- known issues
- deferred work
- follow-up work
- deployment or commit status, if relevant

Do not infer these from memory when direct evidence is available.

Source references:

- Extraction map: `Global Working Preferences`
- Extraction table: `AGENTS.md.backup` completion response format
- ResolveOS: `00-system/ai-operating-principles.md`

## Completion Reporting Principles

### 1. Truthfulness Before Fluency

Do not claim work was done unless it was actually done.

Do not claim files were changed, tests were run, code was committed, a deployment happened, or a ticket was completed unless there is direct evidence.

Source references:

- ResolveOS: `00-system/ai-operating-principles.md`
- Extraction map: `Assistant Anti-Patterns`
- Audit: `Global Assistant Anti-Patterns / Prohibited Behaviours`

### 2. Implementation Honesty

Do not invent implementation claims.

Do not pretend code was committed or pushed. Do not pretend a check passed. Do not claim a ticket, batch, or file is complete if required checks failed or required scope was not finished.

Source references:

- ResolveOS: `00-system/ai-operating-principles.md`
- Extraction table: `AGENTS.md.backup` no direct commit and completion honesty rules
- Extraction map: `Assistant Anti-Patterns`

### 3. Explicit Limitations

Be explicit about limitations.

Report what was not done, what could not be verified, and what remains uncertain.

Do not imply success when status is unknown.

Source references:

- ResolveOS: `00-system/ai-operating-principles.md`
- ResolveOS: `06-governance/codex-working-rules.md`
- Audit: `Global User Working Preferences`

### 4. Preserve Reviewability

Completion reports should make the work reviewable.

They should identify:

- what changed
- why it changed
- where it changed
- what was checked
- what was not checked
- what remains risky, blocked, or deferred

Source references:

- ResolveOS: `06-governance/codex-working-rules.md`
- Extraction table: `docs/ai-roles/implementation-engineer.md` required completion workflow
- Extraction map: `Global Working Preferences`

## Reporting Completed Work

When work is complete, report:

- the task, ticket, or batch
- what was achieved
- why it matters, when useful for review
- files created or changed
- implementation path or extraction path
- validation performed
- result of validation
- known issues, if any
- manual steps for the admin, if any
- follow-up work, if any
- commit, deployment, or review status, if relevant

Do not overstate completion. If the work is complete only for the scoped batch, say that.

Source references:

- Extraction table: `AGENTS.md.backup` completion response format
- Extraction table: `docs/ai-roles/implementation-engineer.md` required completion report format
- Extraction map: `Global Ticket Writing Rules`

## Reporting Partial Work

When work is partially complete, say so directly.

Report:

- what was completed
- what remains incomplete
- why it remains incomplete
- whether acceptance criteria or task requirements are still unmet
- what decision, prerequisite, or follow-up is needed

Do not label partial work as complete.

Source references:

- Extraction table: `AGENTS.md.backup` if blocked or partially complete
- Extraction table: `AGENTS.md.backup` implementation drift reporting
- Audit: `Risks / Things Not To Lose`

## Reporting Failed Work

When work fails, do not silently leave the task in a failed state.

Report:

- what failed
- what command, check, or step failed
- the first clear error or failure reason when available
- what was tried
- what changed before the failure, if anything
- whether the failure is related to the scoped work
- what help, decision, config, or prerequisite is needed

Do not keep making random changes after repeated failure.

Source references:

- Extraction table: `AGENTS.md.backup` stuck-loop and failed-state behaviour
- Extraction map: `Assistant Anti-Patterns`
- Audit: `Global Assistant Anti-Patterns / Prohibited Behaviours`

## Reporting Blockers

If blocked:

- stop
- explain the blocker clearly
- explain why continuing would be unsafe or unsupported
- state what information, credential, config, source file, or admin decision is needed
- suggest the highest-leverage unblocker or follow-up action

Do not silently work around blockers.

Do not work around security or architecture requirements just to continue.

Source references:

- ResolveOS: `00-system/ai-operating-principles.md`
- ResolveOS: `06-governance/codex-working-rules.md`
- Extraction table: `AGENTS.md.backup` blocker handling
- Extraction table: `docs/project-context/implementation-workflow.md` blocker behaviour

## Reporting Validation

Report validation honestly.

For checks or commands that were run, include:

- command or validation method
- outcome
- important failure or warning, if any
- what the check proves, when useful

For checks or commands not run, say:

- not run
- why not run
- residual risk, if any

Project verification commands remain project-specific. Do not make global claims that every project must use the same lint, build, test, smoke, or deployment commands.

Source references:

- Extraction table: `AGENTS.md.backup` checks run and manual test steps
- Extraction map: `Global Working Preferences`
- ResolveOS: `06-governance/codex-working-rules.md`
- Inline ADR instruction: ADR-013 says project verification commands remain project-specific.

## Reporting Risk And Uncertainty

Report uncertainty explicitly.

Use clear labels when needed:

- known
- not verified
- inferred
- blocked
- deferred
- requires admin review

Do not hide uncertainty. Do not imply success when status is unknown.

If implementation differs from the original plan, explain:

- original plan
- what actually happened
- why it changed
- impact
- follow-up needed

Source references:

- Extraction table: `AGENTS.md.backup` implementation drift reporting template
- ResolveOS: `00-system/ai-operating-principles.md`
- Audit: `Risks / Things Not To Lose`

## Reporting Follow-Up Work

Report follow-up work separately from completed scope.

Follow-up work should identify:

- suggested follow-up ticket or task
- why it is separate
- whether it is required or optional
- whether it blocks future work

If useful extra work was noticed, do not imply it was implemented unless it actually was.

Source references:

- Extraction table: `AGENTS.md.backup` suggested follow-up tickets rule
- Extraction map: `Global Working Preferences`
- ResolveOS: `03-skills/ticket-writing.md`

## Reporting Manual Steps

Manual steps should be short and clear.

Explain what the admin is doing, not just what command to run.

If jargon is unavoidable, briefly explain it.

When manual git, deployment, migration, or validation steps are needed, report them as admin actions rather than implying the assistant performed them.

Source references:

- Extraction table: `AGENTS.md.backup` manual step communication rules
- Extraction table: `AGENTS.md.backup` manual git command rules
- Audit: `Risks / Things Not To Lose`

## Reporting Deployment, Commit, And Review Status

Do not pretend code was committed or pushed.

Do not pretend deployment happened.

Do not treat deployment as complete until the real deployment status is known.

When review is expected, report that work is ready for review rather than presenting it as merged, committed, pushed, or deployed.

If manual git commands are provided, make clear they are commands for the admin to run.

Source references:

- Extraction table: `AGENTS.md.backup` no direct commit and git reporting rules
- ResolveOS: `06-governance/codex-working-rules.md`
- Audit: `Global Assistant Anti-Patterns / Prohibited Behaviours`

## Outputs

A completion report should produce a concise, reviewable account of:

- status
- completed work
- partial or failed work, if any
- files changed
- commands or checks run
- commands or checks not run
- validation result
- blockers
- assumptions
- uncertainty
- known issues
- deferred work
- follow-up work
- manual steps
- commit, deployment, or review status, if relevant

The report should be as short as the task allows, but it must not omit important truth, limitations, or blockers.

Source references:

- Extraction table: `AGENTS.md.backup` completion response format
- Extraction map: `Global Working Preferences`
- Audit: `Global Skill Candidates`

## Anti-Patterns

Do not:

- claim work was done unless it was done
- claim files changed unless files actually changed
- pretend code was committed or pushed
- pretend tests, checks, deployment, or validation ran
- imply success when status is unknown
- hide blockers
- hide uncertainty
- hide failed checks
- describe partial work as complete
- silently leave work in a failed state
- keep making random changes after repeated failure
- bury important limitations in vague summaries
- replace specific completion-reporting rules with generic status-report language

Source references:

- Extraction map: `Assistant Anti-Patterns`
- Extraction map: `High Risk Migrations`
- Audit: `Global Assistant Anti-Patterns / Prohibited Behaviours`
- ResolveOS: `06-governance/extraction-migration-guardrails.md`

## Examples

### Completed Work

```text
Status:
Complete for the requested scope.

Files changed:
- [file path]

Validation:
- Ran [command/check]: passed.
- Not run: [command/check]. Reason: [reason].

Known issues:
- None identified / [issue].

Follow-up:
- [follow-up item, or None].
```

### Partial Work

```text
Status:
Partially complete.

Completed:
- [what was completed]

Not completed:
- [what remains]

Reason:
- [blocker, decision, missing context, or failed validation]

Next step:
- [highest-leverage unblocker or follow-up action]
```

### Blocked Work

```text
Status:
Blocked.

Current blocker:
[Specific missing context, credential, configuration, dependency, source file, or admin decision]

Why continuing is unsafe:
[Why proceeding would require guessing, fake functionality, or unsupported assumptions]

Highest-leverage unblocker or follow-up action:
[What is needed next]
```

These examples are guidance for the skill. They are not a canonical completion report template.

Source references:

- Extraction table: `AGENTS.md.backup` completion and blocker report formats
- Inline ADR instruction: ADR-012 says a future template is separate from this skill.

## Related Skills

- `03-skills/ticket-writing.md`

Future related skills or templates may include:

- acceptance criteria
- implementation review
- completion report template

## Related Governance

- `00-system/ai-operating-principles.md`
- `01-context/context-loading-rules.md`
- `01-context/startup-context.md`
- `06-governance/codex-working-rules.md`
- `06-governance/extraction-migration-guardrails.md`
- `06-governance/source-of-truth-rules.md`
- `06-governance/architecture-decisions.md`

## Source Merge Notes

Multiple source variants were consolidated:

- The strongest completion-reporting structure came from `AGENTS.md.backup`.
- The strongest implementation honesty rules came from `AGENTS.md.backup`, Batch 1 `ai-operating-principles.md`, and `codex-working-rules.md`.
- The strongest blocker wording came from `AGENTS.md.backup` and `docs/project-context/implementation-workflow.md`.
- Validation guidance preserves ResolvePM's check-reporting discipline while following ADR-013: project verification commands remain project-specific.
- Template-level report formatting is deferred because ADR-012 says completion reporting consists of a skill and a future template.

## Deferred Items

Deferred because they are out of scope for Batch 2B or require admin review:

- `completion-report-template.md`
- any other template file
- role-specific completion-reporting rules
- project-specific commands such as exact lint, build, smoke, deployment, or migration commands
- dependency ordering rules, because ADR-014 places dependency ordering in governance rather than ticket-writing
- exact ResolvePM Jira comment format as a template
- ResolvePM project-specific deployment status wording

## Ambiguous Items For Admin Review

- Whether the full `AGENTS.md.backup` completion report format should become the future template verbatim.
- Whether manual git command reporting is global or scoped to Codex/Windows projects.
- Whether completion reports should always include "why it matters" or only when useful for review.
- Whether deployment status should have a dedicated future workflow or remain inside completion reporting guidance.

## What This Skill Must Not Do

This skill must not:

- create templates
- define role responsibilities
- replace project-specific verification commands
- claim validation requirements are identical across all projects
- move dependency ordering rules out of governance
- promote ResolvePM project-specific deployment, Jira, Supabase, Vercel, or CP-ticket details into global ResolveOS guidance
- weaken implementation honesty, blocker reporting, or uncertainty reporting into vague status-report language

---

# Source: 03-skills/dependency-management.md

---
type: skill
scope: global
owner: ResolveOS
version: 0.1
status: draft
source_project: ResolvePM
source_files:
  - migration/resolvepm-residual-audit.md
  - migration/resolveos-architecture-review.md
  - migration/template-layer-review.md
related_roles:
  - 02-roles/technical-strategy-lead.md
  - 02-roles/implementation-engineer.md
  - 02-roles/business-analyst.md
related_skills:
  - 03-skills/ticket-writing.md
  - 03-skills/acceptance-criteria.md
  - 03-skills/completion-reporting.md
related_context:
  - 01-context/startup-context.md
  - 01-context/project-loading-rules.md
  - 01-context/running-context.md
related_workflows:
  - 05-workflows/ticket-to-implementation.md
  - 05-workflows/implementation-review-loop.md
related_templates:
  - 04-templates/ticket-context-template.md
  - 04-templates/briefing-template.md
  - 04-templates/blocker-report-template.md
related_governance:
  - 06-governance/source-of-truth-rules.md
  - 06-governance/update-process.md
  - 06-governance/architecture-decisions.md
review_required: true
---

# Purpose

Provide a reusable method for identifying, validating, sequencing, tracking, and communicating dependencies without assuming implementation ownership.

This skill centralises repeated ResolveOS and ResolvePM dependency guidance: current-ticket-first discipline, blocker visibility, sequencing awareness, prerequisite tracking, and explicit approval before creating or expanding dependency work.

This file is a skill. It does not define role authority, approve ticket scope, replace workflow sequence, or create dependency tickets by itself.

Source references:

- `migration/resolvepm-residual-audit.md` > `Future ResolveOS Extraction Candidates` > `dependency-management.md`
- `migration/resolveos-architecture-review.md` > `Missing Skills` > dependency management
- `03-skills/ticket-writing.md` > `Dependency And Sequencing Guidance`
- `05-workflows/ticket-to-implementation.md` > `Implementation Readiness`
- `02-roles/technical-strategy-lead.md` > `Behaviour Rules`

# Dependency Identification

Identify dependencies before implementation, review, migration, or delivery work starts.

Look for dependencies in:

- ticket scope
- acceptance criteria
- implementation notes
- source comments
- project context
- role context
- prior ticket outcomes
- briefing files
- architecture decisions
- validation requirements
- configuration, credentials, schema, data, or environment state

Common dependency types include:

- prerequisite tickets
- previous-ticket outcomes
- schema, model, helper, or migration work
- configuration or credential availability
- source-system access
- acceptance criteria or approval
- architecture decisions
- validation commands or manual test paths
- deployment, build, or release constraints
- paid API, security, or cost constraints

Before editing, identify prerequisites, dependencies, blockers, missing schema, architecture gaps, source-of-truth conflicts, configuration gaps, security constraints, and paid API risks.

Source references:

- `05-workflows/ticket-to-implementation.md` > `Implementation Readiness`
- `04-templates/ticket-context-template.md` > dependency and blocker prompts
- `04-templates/briefing-template.md` > dependency and prerequisite state

# Dependency Classification

Classify each dependency by the effect it has on the current work.

Useful classifications:

- prerequisite: must be completed before the current work can start safely
- blocked-by: currently prevents safe progress
- sequencing: affects order but may not block discovery or planning
- validation: required to prove completion
- context: required to understand scope or intent
- approval: requires admin, project owner, role, or source-owner decision
- follow-up: useful work discovered, but not part of current approved scope
- related: connected work that should be visible but does not affect current execution

Do not treat every related item as a prerequisite.

Do not turn a follow-up dependency into current scope without explicit approval.

Source references:

- `03-skills/ticket-writing.md` > one ticket at a time and follow-up separation
- `05-workflows/feedback-to-ticket.md` > current implementation scope and follow-up work
- `04-templates/ticket-context-template.md` > previous, prerequisite, follow-up, duplicate, and blocked-by relationship notes

# Dependency Validation

Validate dependency state before relying on it.

Where practical, confirm:

- whether the prerequisite was actually completed
- whether related code was committed, pushed, deployed, or otherwise available when that matters
- whether the source system says the dependency is done
- whether the local repository state matches the source context
- whether acceptance criteria, validation evidence, or decision records exist
- whether the dependency is still current

Do not assume a dependency is complete because it was discussed.

Do not assume a previous ticket is available if its implementation is uncommitted, unpushed, failed validation, or missing from the current environment.

If dependency state cannot be validated and safe progress depends on it, report a blocker rather than inventing around it.

Source references:

- `02-roles/technical-strategy-lead.md` > dependency commit/order checks
- `03-skills/completion-reporting.md` > do not pretend commits, pushes, tests, deployment, or completion happened
- `04-templates/blocker-report-template.md` > dependency issue and missing prerequisite reporting

# Dependency Sequencing

Sequence dependencies so the current approved work can proceed safely.

Preserve current-ticket-first discipline:

- Work one ticket, task, or approved batch at a time.
- Do not implement future-ticket work inside the current ticket.
- Do not retry blocked dependent work until the prerequisite is complete.
- Do not silently work around prerequisite gaps.

Where a UI or workflow depends on schema, data helpers, typed models, persisted state, configuration, source records, or architecture direction, sequence those foundations first.

If useful dependency work is identified outside the current approved scope, recommend it as a prerequisite or follow-up item and explain why it should be separate.

Dependency sequencing should inform implementation readiness. It should not become unapproved implementation scope.

Source references:

- `03-skills/ticket-writing.md` > `Work one ticket at a time`
- `03-skills/ticket-writing.md` > `Dependency And Sequencing Guidance`
- `02-roles/technical-strategy-lead.md` > `Maintain implementation sequencing`
- `05-workflows/ticket-to-implementation.md` > current approved scope

# Dependency Risk Assessment

Assess dependency risk before recommending progress.

Dependency risks include:

- false completion because prerequisite work is absent
- implementation drift because source context changed
- validation failure because required setup is missing
- build or deployment risk from uncommitted prerequisite work
- security, cost, or paid API risk
- architecture drift from forcing work around missing foundations
- source-of-truth conflict between ticket state and repository state
- hidden scope expansion through dependency work

If a dependent ticket is completed while its prerequisite remains unavailable, treat this as delivery risk.

If resolving the dependency changes product scope, architecture direction, cost exposure, or project source-of-truth state, escalate to the accountable role or admin rather than deciding silently.

Source references:

- `02-roles/technical-strategy-lead.md` > dependency, architecture, build, deployment, and source-of-truth stop lines
- `05-workflows/ticket-to-implementation.md` > blocker and validation rules
- `06-governance/decision-maker-reporting.md` > impact and risk reporting

# Dependency Communication

Communicate dependencies plainly and early.

A useful dependency note should state:

- what the dependency is
- why it matters
- whether it blocks current work
- what evidence supports the dependency state
- what decision, prerequisite, or validation is needed
- whether the next action is current-scope work, prerequisite work, follow-up work, or admin review

If the dependency is a blocker, use blocker-reporting structure and name the exact missing prerequisite, decision, context, credential, configuration, validation evidence, or source file.

Do not bury dependency problems inside a completion report or make partial, blocked, failed, or not-verified work sound complete.

Source references:

- `04-templates/blocker-report-template.md` > blocker report structure
- `03-skills/completion-reporting.md` > reporting blockers and partial work
- `06-governance/decision-maker-reporting.md` > intent, outcome, impact, risk, recommendation, evidence

# Dependency Tracking

Track dependencies in the source that owns them.

Use the correct source of ownership:

- current running state belongs in running context only when it is current and source-backed
- durable architecture decisions belong in ADRs
- workflow sequence belongs in workflow files
- role authority belongs in role files
- reusable method belongs in skill files
- project tickets, roadmap, commands, project architecture, and source-system details belong in project repositories or source systems

If dependency state changes during implementation, review, planning, or migration, flag which file or source should be updated.

Do not duplicate dependency state across many files just because it is useful. Link or reference the owning source where practical.

Source references:

- `06-governance/source-of-truth-rules.md` > ownership hierarchy
- `06-governance/update-process.md` > update the source of ownership
- `01-context/running-context.md` > current state only

# Anti-Patterns

Do not:

- silently ignore dependencies
- silently work around blockers
- retry blocked dependent work before the prerequisite is complete
- create dependency work without approval
- expand current scope because a dependency was discovered
- treat related future work as current implementation scope
- assume a dependency is complete without evidence
- hide dependency risk inside vague language
- invent schema, configuration, source facts, validation evidence, or project context
- proceed when missing dependency state makes safe work impossible
- move role authority, workflow sequence, or project doctrine into this skill

Source references:

- `03-skills/ticket-writing.md` > blocker and dependency anti-patterns
- `05-workflows/ticket-to-implementation.md` > anti-patterns
- `06-governance/extraction-migration-guardrails.md` > no silent scope expansion and no implementation drift

# Notes

This skill intentionally centralises method only.

Technical Strategy Lead may own sequencing and dependency governance in role context, but this skill does not grant that authority to every assistant.

Implementation Engineer may identify and report blockers while executing scoped work, but this skill does not authorise expanding implementation scope.

Project-specific dependency fields, ticket link types, source-system posting rules, environment commands, deployment order, and release gates remain project-owned unless promoted through ResolveOS governance.

Deferred:

- source-tracker dependency comment formats
- project-specific dependency schemas
- release-management or deployment-order workflows
- exact rules for when dependency blockers require source-system comments

Ambiguous for admin review:

- whether dependency blockers need a dedicated future template
- whether source systems should distinguish previous, prerequisite, follow-up, duplicate, and blocked-by relationships in a richer canonical schema
- whether prerequisite commit/push order should remain role/workflow guidance or become stronger global governance

---

# Source: 03-skills/documentation-storage-architecture.md

---
type: skill
scope: global
owner: ResolveOS
version: 0.1
status: draft
related_skills:
  - 03-skills/user-feedback-processing.md
  - 03-skills/completion-reporting.md
related_context:
  - 01-context/missing-context-behaviour.md
  - 01-context/context-loading-rules.md
related_governance:
  - 06-governance/source-of-truth-rules.md
  - 06-governance/architecture-decisions.md
review_required: true
---

# Documentation Storage Architecture

## Purpose

Govern where information should be stored before ResolveOS writes to any documentation, workspace, knowledge-base, project-management, repository, or local storage tool.

Use this skill before writing to Notion, GitHub markdown, Google Docs, SharePoint, Confluence, local files, Jira, Linear, GitHub Issues, or similar documentation and storage systems.

This skill is about storage architecture. It does not replace source-of-truth governance, project-specific documentation rules, feedback processing, ticket writing, decision logging, or external tool permissions.

## Documentation Storage Principle

ResolveOS should not create unnecessary top-level pages, documents, files, folders, or database structures.

Before writing to any external documentation or workspace tool, ResolveOS must identify the intended information architecture:

- source of truth
- parent location
- storage type
- update existing vs create new
- whether top-level storage is justified

Creating new top-level storage is allowed only when the content represents a new major project, product area, system, database, or durable knowledge domain.

Routine feedback, notes, decisions, risks, meeting outputs, implementation context, and conversation summaries should usually be stored inside the relevant existing structure.

Storage location is part of source-of-truth discipline. Do not create a new storage location when an existing canonical location exists.

## When To Use

Use this skill when the user asks to:

- save something
- store something
- put something in Notion
- capture feedback
- create documentation from a conversation
- preserve a handoff, meeting output, implementation summary, decision, risk, research note, or project context
- write to a documentation, knowledge-base, workspace, project-management, repository, or local file tool

Use it before the storage tool is called or the file is created.

## Decision Tree

1. Identify information type.
2. Identify source-of-truth owner.
3. Search or fetch existing relevant structure where possible.
4. Prefer updating existing pages, sections, databases, tickets, comments, folders, or files.
5. Create child pages only for durable sub-topics.
6. Create top-level pages or files only for new major areas.
7. Use databases for repeatable structured records.
8. Ask the user only if location cannot be inferred safely.
9. Report where it was stored and why.

## Storage Types

Choose the smallest storage shape that preserves context and ownership:

- append to existing page or section
- update existing page
- create child page under existing parent
- create database record
- create file in an existing folder or path
- create ticket or comment
- create a new top-level page or file only when justified
- use fallback or temporary storage if the intended destination is inaccessible

Fallback storage must be labelled as fallback or temporary and should name the intended destination that was unavailable.

## Information Types

Classify the content before storing it.

Common types include:

- feedback
- decision
- risk
- assumption
- validation finding
- implementation handoff
- meeting output
- research note
- operating knowledge
- project context
- technical documentation
- ticket or task context
- completion or blocker report
- conversation summary

If more than one type applies, choose the primary owner first, then preserve secondary labels or links where useful.

## Tool Model Guidance

ResolveOS should not merely recommend tools. It should know how to use them well.

Common ownership patterns:

- Notion: product context, strategy, decisions, risks, validation, feedback, operating knowledge.
- Jira or Linear: execution tracking.
- GitHub: code, technical docs, implementation evidence, repo-owned context.
- Confluence, SharePoint, or Google Docs: organisational documentation where they are the declared source of truth.

These are defaults, not hard rules. Project-specific source-of-truth declarations override generic tool preferences.

When recommending a tool, also recommend the storage model that prevents clutter: hubs, child pages, existing folders, existing docs, existing databases, comments, or records as appropriate.

## Non-Delegation Behaviour

Do not ask the user where to store something if the correct location can be inferred.

Do not ask the user to design the documentation structure unless it materially affects ownership or workflow.

If uncertain, propose the best location and explain the assumption.

Ask only the smallest necessary question.

If a storage issue is surfaced, provide the practical resolution path.

## Notion-Specific Behaviour

Treat Notion as a structured workspace, not a flat page dump.

Before writing to Notion:

- search or fetch the relevant hub, parent page, or database before writing
- do not create top-level Notion pages by default
- use existing pages where appropriate
- append to an existing page when content extends an existing topic
- create a child page under the relevant parent when content is a durable sub-topic
- use databases for repeated structured records such as feedback, risks, decisions, validation findings, tasks, or research notes
- use comments only for review or commentary, not permanent structured storage
- if the intended database or page is inaccessible, report that and use the best fallback
- if creating fallback storage, label it clearly as fallback or temporary

If ResolveOS recommends Notion, it should understand Notion workspace hygiene:

- hubs
- child pages
- databases for repeatable records
- preserved hierarchy
- no root-level clutter

Report back using this shape:

```text
Stored under [location] because [reason].
```

## Reporting After Storage

After storage, report:

- where the content was stored
- what storage type was used
- why that location fit the source-of-truth and information type
- whether an assumption or fallback was used
- any inaccessible intended destination or follow-up needed

Do not claim storage happened unless the write actually succeeded.

## Good / Bad Examples

Bad:

```text
User: "We've just discussed this. Save it somewhere."
AI creates seven new top-level Notion pages.
```

Why bad:

- workspace clutter
- context fragmentation
- user cleanup
- broken source-of-truth discipline
- extra admin

Good:

```text
I found the Resolve Product Hub and stored this under Feedback because it is product feedback. I created one structured child page for the full write-up and grouped the content into sections. I did not create separate top-level pages because this does not represent new product areas.
```

## Anti-Patterns

Do not:

- create random top-level pages, documents, files, folders, or databases
- use Notion as a flat page dump
- create a new source of truth when an existing one exists
- split one routine conversation into many standalone documents
- ask the user to design storage structure when ResolveOS can infer it safely
- treat tool recommendation as enough without explaining how the tool should be used
- use comments as permanent structured storage
- hide fallback or temporary storage
- claim content was stored, linked, ticketed, or documented unless it was

## Related Governance

- `06-governance/source-of-truth-rules.md`
- `06-governance/architecture-decisions.md`

## Related Context

- `01-context/missing-context-behaviour.md`
- `01-context/context-loading-rules.md`

## Related Skills

- `03-skills/user-feedback-processing.md`
- `03-skills/completion-reporting.md`

## Deferred Items

Deferred because they are project-specific or would overbuild this skill:

- tool-specific database schemas
- Notion workspace templates
- Confluence, SharePoint, or Google Docs templates
- automatic workspace cleanup
- project-specific taxonomy
- migration of existing documentation structures

## What This Skill Must Not Do

This skill must not:

- make Notion the only supported model
- create duplicate source-of-truth systems
- replace project-specific documentation rules
- replace feedback processing, ticket writing, or decision logging
- impose a global database schema
- create external tool structures without approval

---

# Source: 03-skills/implementation-review.md

---
type: skill
scope: global
owner: ResolveOS
version: 0.1
status: draft
source_project: ResolvePM
source_files:
  - migration/resolvepm-residual-audit.md
  - migration/resolveos-architecture-review.md
  - migration/template-layer-review.md
related_roles:
  - 02-roles/technical-strategy-lead.md
  - 02-roles/implementation-engineer.md
  - 02-roles/qa-tester.md
  - 02-roles/business-analyst.md
related_skills:
  - 03-skills/completion-reporting.md
  - 03-skills/acceptance-criteria.md
  - 03-skills/ticket-writing.md
  - 03-skills/requirement-traceability.md
  - 03-skills/dependency-management.md
related_context:
  - 01-context/startup-context.md
  - 01-context/project-loading-rules.md
  - 01-context/running-context.md
related_workflows:
  - 05-workflows/ticket-to-implementation.md
  - 05-workflows/implementation-review-loop.md
related_templates:
  - 04-templates/completion-report-template.md
  - 04-templates/blocker-report-template.md
  - 04-templates/ticket-context-template.md
related_governance:
  - 06-governance/decision-maker-reporting.md
  - 06-governance/source-of-truth-rules.md
  - 06-governance/update-process.md
  - 06-governance/architecture-decisions.md
review_required: true
---

# Purpose

Provide a reusable method for reviewing completed or attempted implementation work against approved scope, acceptance criteria, architectural intent, validation requirements, documented decisions, and source context.

This skill preserves ResolvePM's review behaviour around implementation honesty, no fake completion, validation awareness, acceptance criteria alignment, implementation drift detection, architecture alignment, blocker visibility, and follow-up separation.

This file is a skill. It does not replace the implementation-review-loop workflow, QA sign-off, Technical Strategy Lead authority, completion-reporting template, or project-specific verification commands.

Source references:

- `migration/resolvepm-residual-audit.md` > `Future ResolveOS Extraction Candidates` > `implementation-review.md`
- `migration/resolveos-architecture-review.md` > `Missing Skills` > implementation review
- `05-workflows/implementation-review-loop.md` > review of stuck, failed, drifted, blocked, or questionable work
- `03-skills/completion-reporting.md` > implementation honesty and validation reporting
- `06-governance/decision-maker-reporting.md` > reviewable reporting layers

# Review Inputs

Gather the smallest useful set of evidence before reviewing implementation.

Useful review inputs include:

- approved ticket, task, source item, or batch scope
- acceptance criteria
- implementation notes
- comments, blocker notes, and follow-up notes
- completion report
- files changed
- commands run
- checks, tests, builds, linting, or manual validation performed
- checks or validation not run
- known failures
- architecture decisions
- project context
- dependency and prerequisite state
- source-system status
- repository diff or implementation evidence

Do not review from memory when required context files, ticket scope, acceptance criteria, source comments, project context, or repository state are needed for safe review.

Source references:

- `05-workflows/ticket-to-implementation.md` > context loading and completion reporting
- `04-templates/completion-report-template.md` > evidence sections
- `01-context/project-loading-rules.md` > do not use memory as source of truth

# Scope Review

Check whether the implementation stayed inside approved scope.

Ask:

- What was approved?
- What was actually changed?
- Was any future-ticket work implemented?
- Was any unrelated refactor included?
- Was any hidden scope added through dependency work?
- Were non-goals respected?
- Was partial work clearly reported?

Implementation should not expand current scope because related work, feedback, dependency gaps, or useful improvements were discovered.

If useful extra work was found, it should be reported as follow-up or prerequisite work, not as completed current scope unless explicitly approved.

Source references:

- `05-workflows/ticket-to-implementation.md` > implement only current approved scope
- `03-skills/ticket-writing.md` > one ticket at a time and follow-up separation
- `05-workflows/feedback-to-ticket.md` > do not expand current implementation scope

# Acceptance Criteria Review

Check whether the delivered work satisfies the acceptance criteria.

Ask:

- Are the criteria present?
- Are the criteria still valid?
- Are the criteria observable and testable?
- Did implementation drift affect any criterion?
- Are manual test steps or validation expectations addressed?
- Are missing criteria clearly reported rather than guessed?

If the drift affects the acceptance criteria, do not mark the ticket complete unless the criteria are still satisfied.

Do not treat implementation notes, partial behaviour, fake states, or future follow-up recommendations as acceptance evidence.

Source references:

- `03-skills/acceptance-criteria.md` > acceptance criteria principles and implementation drift gate
- `03-skills/completion-reporting.md` > do not overstate completion
- `04-templates/ticket-context-template.md` > missing acceptance criteria handling

# Validation Review

Review validation honestly.

Check:

- which commands, checks, tests, builds, linting, manual steps, or review steps were run
- which validation steps were not run
- whether failures are related to the scoped work
- whether validation proves the approved scope
- whether residual validation risk remains
- whether project-specific verification commands were followed when available

Do not pretend tests, checks, deployment, or validation ran.

Do not claim completion if required build, lint, test, validation, or acceptance criteria fail.

If validation is blocked, missing, skipped, unavailable, or out of scope, say so directly.

Source references:

- `03-skills/completion-reporting.md` > reporting validation
- `05-workflows/ticket-to-implementation.md` > validation expectations
- `04-templates/completion-report-template.md` > validation and residual risk sections

# Architecture Review

Check whether the implementation respects architectural intent and documented decisions.

Review:

- relevant ADRs
- project architecture context
- role or workflow boundary constraints
- source-of-truth rules
- update-process expectations
- dependency sequencing
- security, cost, configuration, or environment constraints
- whether the implementation introduced speculative architecture

If implementation reveals architecture drift, schema gaps, unsafe assumptions, or dependency changes, report the finding and escalate to the accountable role or admin.

Do not approve architecture changes merely because code was written.

Source references:

- `06-governance/architecture-decisions.md` > ADR enforcement
- `06-governance/source-of-truth-rules.md` > source ownership
- `02-roles/technical-strategy-lead.md` > architecture and sequencing review boundaries

# Documentation Review

Check whether implementation changed information that should be reflected in source-owned documentation.

Potential documentation updates include:

- project context
- current focus or running context
- ticket notes
- source-system comments
- ADRs
- decision logs
- workflow or governance files
- role, skill, or template files when their owned behaviour changed

Do not let documentation drift from reality.

Do not update unrelated files merely because review found a possible improvement. Identify the correct source of ownership and report out-of-scope updates as follow-up work.

Source references:

- `06-governance/update-process.md` > update ownership and change propagation
- `01-context/running-context.md` > current state only
- `03-skills/ticket-writing.md` > documentation requirements

# Drift Assessment

Implementation drift is any meaningful difference between approved intent and delivered reality.

Drift may affect:

- product meaning
- requirement meaning
- acceptance criteria
- architecture
- sequencing
- validation
- documentation
- source-of-truth state
- cost, security, or deployment risk

When drift exists, report:

- what changed
- why it changed, if known
- whether the outcome still satisfies the original intent
- whether acceptance criteria remain satisfied
- what risk or decision remains
- whether follow-up work is needed

Do not hide drift inside a positive completion summary.

Source references:

- `06-governance/decision-maker-reporting.md` > drift reporting
- `03-skills/completion-reporting.md` > implementation drift reporting
- `05-workflows/implementation-review-loop.md` > drifted implementation review

# Review Outcomes

An implementation review should produce one clear outcome.

Common outcomes:

- accepted for scoped review
- accepted with clearly separated follow-up
- partially complete
- blocked
- failed validation
- not verified
- requires admin decision
- requires role review
- requires prerequisite work
- requires documentation update
- requires source-system update

The outcome should include:

- status
- evidence reviewed
- acceptance criteria status
- validation status
- scope or drift notes
- risks
- blockers
- highest-leverage follow-up action

Do not imply success when status is unknown.

Source references:

- `04-templates/completion-report-template.md` > status and next action fields
- `04-templates/blocker-report-template.md` > blocked and failed validation outcomes
- `06-governance/decision-maker-reporting.md` > recommendation and evidence layers

# Anti-Patterns

Do not:

- claim work was done unless it was actually done
- pretend tests, checks, deployment, commits, pushes, source-ticket updates, or admin approval happened
- mark work complete when acceptance criteria are missing, failed, or no longer satisfied
- treat fake functionality, fake data, fake integrations, or fake success states as valid implementation
- hide blockers, uncertainty, failed validation, or implementation drift
- treat follow-up recommendations as completed scope
- approve architecture changes just because implementation happened
- use implementation review to expand scope
- move workflow sequence, QA sign-off, role authority, template structure, or project doctrine into this skill

Source references:

- `03-skills/completion-reporting.md` > anti-patterns
- `05-workflows/ticket-to-implementation.md` > anti-patterns
- `06-governance/extraction-migration-guardrails.md` > no fake functionality, no silent scope expansion, no implementation drift

# Notes

Implementation review is a method, not ownership.

QA Tester remains accountable for QA-specific validation and defect review where that role is loaded.

Technical Strategy Lead remains accountable for sequencing, architecture, dependency, and implementation-governance review where that role is loaded.

Implementation Engineer remains accountable for scoped implementation execution and honest reporting where that role is loaded.

Project-specific review checklists, verification commands, release gates, source-system status fields, deployment environments, and sign-off rules remain project-owned.

Deferred:

- source-tracker review comment formats
- project-specific verification command catalogues
- dedicated debugging-support method
- deployment-readiness review workflow
- QA sign-off workflow

Ambiguous for admin review:

- whether implementation review needs a future template separate from completion and blocker templates
- whether repeated failed validation should route to a future debugging-support skill
- whether source-system update checks should be mandatory when source-system access exists

---

# Source: 03-skills/requirement-traceability.md

---
type: skill
scope: global
owner: ResolveOS
version: 0.1
status: draft
source_project: ResolvePM
source_files:
  - migration/resolvepm-residual-audit.md
  - migration/resolveos-architecture-review.md
  - migration/template-layer-review.md
related_roles:
  - 02-roles/product-manager.md
  - 02-roles/business-analyst.md
  - 02-roles/qa-tester.md
  - 02-roles/technical-strategy-lead.md
related_skills:
  - 03-skills/ticket-writing.md
  - 03-skills/acceptance-criteria.md
  - 03-skills/user-feedback-processing.md
  - 03-skills/completion-reporting.md
related_context:
  - 01-context/startup-context.md
  - 01-context/project-loading-rules.md
  - 01-context/running-context.md
related_workflows:
  - 05-workflows/feedback-to-ticket.md
  - 05-workflows/ticket-to-implementation.md
  - 05-workflows/implementation-review-loop.md
related_templates:
  - 04-templates/ticket-context-template.md
  - 04-templates/completion-report-template.md
  - 04-templates/decision-log-template.md
related_governance:
  - 06-governance/source-of-truth-rules.md
  - 06-governance/decision-maker-reporting.md
  - 06-governance/update-process.md
  - 06-governance/architecture-decisions.md
review_required: true
---

# Purpose

Provide a reusable method for preserving links between objectives, requirements, acceptance criteria, implementation, validation, feedback, decisions, blockers, and follow-up work.

This skill preserves ResolvePM's repeated traceability behaviour: do not guess requirements, do not lose original intent, keep acceptance criteria aligned to source scope, preserve feedback traceability, and report drift when delivered work changes meaning.

This file is a skill. It does not approve scope, replace source systems, create tickets automatically, or define role ownership.

Source references:

- `migration/resolvepm-residual-audit.md` > `Future ResolveOS Extraction Candidates` > `requirement-traceability.md`
- `migration/resolveos-architecture-review.md` > `Missing Skills` > requirement traceability
- `02-roles/business-analyst.md` > requirement traceability responsibilities
- `03-skills/user-feedback-processing.md` > feedback traceability
- `03-skills/acceptance-criteria.md` > traceability expectations

# Traceability Principles

Preserve original intent before interpreting, cleaning, ticketing, implementing, or reviewing work.

Do not guess requirements.

Do not infer motivation, priority, severity, acceptance criteria, source facts, or implementation meaning that the available source material does not support.

Keep raw source material separate from interpretation.

Distinguish:

- source facts
- assumptions
- interpretation
- recommendations
- approved decisions
- unresolved questions
- follow-up work

Traceability should make review easier, not create heavy process for its own sake.

If a requirement is unsupported, contradictory, incomplete, or drifting, flag it rather than smoothing over the gap.

Source references:

- `03-skills/user-feedback-processing.md` > preserve raw feedback and separate raw feedback from interpretation
- `02-roles/business-analyst.md` > evidence over invention and no guessed requirements
- `00-system/ai-operating-principles.md` > evidence over invention and explicit uncertainty

# Requirement Sources

Requirement sources may include:

- admin instruction
- ticket or issue
- project context file
- briefing
- feedback item
- source-system comment
- blocker report
- decision log
- ADR
- acceptance criteria
- implementation report
- validation result
- stakeholder note
- repository state

Use the source that owns the requirement.

Project repositories own product vision, roadmaps, tickets, feature decisions, project terminology, project architecture, commands, active implementation constraints, and source-system details.

ResolveOS owns reusable behaviour, methods, roles, workflows, templates, context-loading rules, and governance.

If source-system access is unavailable, use approved fallback context only when the fallback clearly states its limitations.

Source references:

- `06-governance/source-of-truth-rules.md` > project and ResolveOS ownership
- `01-context/project-loading-rules.md` > project context source discipline
- `04-templates/briefing-template.md` > briefings preserve source traceability and limitations

# Traceability Mapping

Map requirements from source to work item before implementation or review.

A useful traceability map identifies:

- source objective
- source requirement or request
- source location
- acceptance criteria
- implementation scope
- exclusions or non-goals
- assumptions
- dependencies or blockers
- validation expectation
- decision or approval state
- follow-up work

When a requirement becomes a ticket, preserve the link back to the original request, feedback, decision, or blocker note.

When an acceptance criterion is created, it should remain traceable to the source of scope and describe an observable outcome.

When implementation changes the path, preserve whether the outcome still matches the original requirement.

Source references:

- `03-skills/ticket-writing.md` > ticket structure and source context
- `03-skills/acceptance-criteria.md` > traceability expectations
- `06-governance/decision-maker-reporting.md` > original intent, outcome, impact, risk, recommendation, evidence

# Validation Traceability

Validation should prove the approved scope, not adjacent future work.

Track which acceptance criteria, requirements, or risks each validation step supports.

Validation traceability should make clear:

- what was checked
- what source requirement or criterion it supports
- whether it passed, failed, was blocked, or was not run
- whether missing validation affects completion
- whether the validation evidence is sufficient for review

Do not claim validation passed unless it actually passed.

Do not call work complete when required validation, acceptance criteria, or source requirements remain unsatisfied unless the limitation is explicit.

Source references:

- `03-skills/completion-reporting.md` > validation reporting
- `03-skills/acceptance-criteria.md` > validation guidance
- `05-workflows/ticket-to-implementation.md` > validation should prove current approved scope

# Feedback Traceability

Feedback must remain traceable from raw input to reviewed work.

When feedback is processed:

- capture raw feedback first
- preserve source and timestamp where available
- separate the user's message from interpretation
- preserve proposed solutions separately from observed problems
- link duplicate or related feedback without discarding the new input
- do not turn ambiguous feedback into acceptance criteria
- do not expand current implementation scope because feedback was found

When feedback becomes a ticket, retain source feedback and timestamp in the ticket background where practical.

Repeated feedback may be evidence of importance, confusion, poor workflow fit, or documentation gaps. Do not infer priority from repetition alone without project context.

Source references:

- `03-skills/user-feedback-processing.md` > feedback preservation, duplicate handling, and conversion into work
- `05-workflows/feedback-to-ticket.md` > source-to-ticket traceability
- ADR-015 and ADR-016 in `06-governance/architecture-decisions.md`

# Change Impact Assessment

When a requirement, implementation path, dependency, validation result, or decision changes, assess the traceability impact.

Ask:

- Does this still satisfy the original intent?
- Does it change product meaning?
- Does it change requirement meaning?
- Does it affect acceptance criteria?
- Does it affect validation needs?
- Does it create follow-up work?
- Does it require a source-of-truth update?
- Does it need admin, role, or source-owner review?

If the drift affects acceptance criteria, do not mark the work complete unless the criteria are still satisfied.

If drift changes product meaning, requirement meaning, sequencing, architecture, validation, or strategy, escalate to the accountable role or admin.

Source references:

- `06-governance/decision-maker-reporting.md` > drift and impact reporting
- `03-skills/acceptance-criteria.md` > implementation drift acceptance gate
- `05-workflows/implementation-review-loop.md` > drifted or questionable implementation work

# Anti-Patterns

Do not:

- guess requirements
- lose original intent
- overwrite raw feedback with cleaned interpretation
- invent source facts, priority, severity, acceptance criteria, validation evidence, or approval
- hide assumptions inside confident wording
- convert every feedback item into a ticket automatically
- expand current scope because related feedback or requirements exist
- detach acceptance criteria from source scope
- report follow-up work as completed scope
- let implementation drift break traceability without reporting it
- duplicate source-of-truth content across files instead of linking to the owner
- move role authority, workflow sequence, template structure, or project doctrine into this skill

Source references:

- `03-skills/user-feedback-processing.md` > anti-patterns
- `03-skills/acceptance-criteria.md` > anti-patterns
- `06-governance/source-of-truth-rules.md` > avoid competing sources of truth

# Notes

This skill supports roles and workflows that need traceability, but it does not decide priority, approve scope, sign off QA, or create implementation authority.

Traceability should be proportionate. A small ticket may need only source, scope, acceptance criteria, and validation notes. Larger or riskier work may need explicit mapping across decisions, feedback, blockers, validation, and follow-up.

Project-specific traceability fields, source-system link formats, ticket schemas, review states, and workflow labels remain project-owned.

Deferred:

- source-tracker handoff/comment formats
- project-specific traceability schemas
- a full traceability matrix template
- automatic feedback-to-ticket linking implementation

Ambiguous for admin review:

- whether ResolveOS should define a richer canonical traceability schema later
- whether source-system comments should be mandatory when traceability changes
- whether decision logs should always be linked from requirements when durable decisions are involved

---

# Source: 03-skills/ticket-writing.md

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
related_context:
  - 00-system/ai-operating-principles.md
  - 01-context/context-loading-rules.md
  - 01-context/startup-context.md
related_governance:
  - 06-governance/codex-working-rules.md
  - 06-governance/extraction-migration-guardrails.md
  - 06-governance/source-of-truth-rules.md
review_required: true
---

# Ticket Writing

## Purpose

Define the canonical ResolveOS skill for writing and refining implementation tickets.

This skill preserves reusable ticket-writing guidance extracted from ResolvePM. It is not generic Agile guidance. It exists to keep ticket work clear, scoped, sequenced, implementation-ready, testable, and honest about blockers, assumptions, non-goals, and production constraints.

Source references:

- Extraction map: `Global Ticket Writing Rules`
- Extraction map: `Proposed ResolveOS File Inventory`
- Audit: `Global Ticket Writing Rules`
- Audit: `Global Skill Candidates`

## When To Use

Use this skill when creating, reviewing, refining, splitting, or preparing tickets for implementation.

Use it for:

- implementation tickets
- prerequisite tickets
- follow-up tickets
- blocker resolution tickets
- ticket sequence planning
- ticket readiness review
- ticket prompts for implementation agents

Do not use this skill to create product roadmap direction, role behaviour, full completion report templates, or project-specific feature decisions unless those inputs already exist in the relevant project context.

Source references:

- Extraction map: `Global Ticket Writing Rules`
- Extraction map: `Global Context Loading Rules`
- ResolveOS: `06-governance/source-of-truth-rules.md`

## Inputs

Before writing or refining a ticket, gather the available source context:

- ticket key or source item identifier, when one exists
- title
- goal
- scope
- acceptance criteria
- implementation notes
- manual test steps
- relevant comments or blocker notes
- related briefing, epic, or current focus
- relevant project context
- known dependencies and prerequisites
- known non-goals
- current repository or implementation constraints, when implementation is near-term

If source-system access is unavailable, ask for the missing ticket description or relevant comments. Do not guess missing acceptance criteria.

Source references:

- Extraction table: `AGENTS.md.backup` read title, goal, scope, acceptance criteria, notes, comments, and manual test steps
- Extraction table: `AGENTS.md.backup` do not guess missing acceptance criteria
- Audit: `Global Ticket Writing Rules`

## Ticket Structure

Tickets should define:

- what is being achieved
- why it matters
- implementation scope
- assumptions
- dependencies
- sequencing notes
- non-goals where useful
- acceptance criteria
- implementation notes
- manual test steps
- documentation expectations, when relevant
- deployment or production considerations, when relevant

At minimum, a well-scoped implementation ticket should contain:

```text
Title:

Goal:

Background / Context:

Scope:

Out of Scope:

Assumptions:

Dependencies / Prerequisites:

Implementation Notes:

Acceptance Criteria:

Testing / Manual Test Steps:

Documentation Notes:

Deployment / Production Notes:
```

Use only the sections needed for the ticket. Do not over-format small tickets into heavy process documents.

Source references:

- Extraction table: `docs/project-context/implementation-workflow.md` tickets define outcome, value, scope, assumptions, dependencies, sequencing notes, non-goals
- Audit: `Global Ticket Writing Rules`
- Extraction map: `Global Ticket Writing Rules`

## Ticket Writing Process

### 1. Start From The Current Ticket Or Approved Scope

Ticket work must start from a ticket/source item or an explicitly approved scope.

Work one ticket at a time.

Do not start future tickets unless explicitly asked.

Do not start implementation from an epic alone if child implementation tickets are missing.

Source references:

- Extraction map: `Global Ticket Writing Rules`
- Extraction table: `AGENTS.md.backup` one ticket at a time
- Extraction table: `docs/codex-briefings/CP-7-knowledge-base.md` do not start implementation from epic alone

### 2. Confirm Understanding Before Writing Or Implementing

Before implementation, the ticket should make clear:

- what the ticket is trying to achieve
- why it matters
- how it fits into the larger project or workflow
- what assumptions are being made
- what dependencies or blockers exist

Ticket prompts and implementation handoffs should summarise this in plain English.

Source references:

- Extraction table: `AGENTS.md.backup` summarise task understanding before implementation
- Extraction map: `Global Communication Rules`
- Audit: `Global User Working Preferences`

### 3. Keep Scope Small, Safe, And Reversible

Prefer:

- small tickets
- clear scope
- reversible changes
- explicit sequencing

Avoid:

- massive implementation tickets
- unclear scope
- speculative implementation
- future scope bundling

If useful extra work is identified, do not add it silently to the current ticket. Add it as suggested follow-up work and explain why it should be separate.

Source references:

- Extraction table: `docs/project-context/implementation-workflow.md` small safe tickets
- Extraction table: `AGENTS.md.backup` useful extra work goes to suggested follow-up tickets
- Extraction map: `Global Working Preferences`

### 4. Define Sequencing And Dependencies

Tickets should identify prerequisites clearly.

If implementation reveals missing schema, architecture gaps, prerequisite work, or unsafe assumptions, suggest follow-up or prerequisite tickets.

If prerequisite work is missing, stop and identify the prerequisite before writing around it.

Do not retry a blocked dependent ticket until the prerequisite is complete.

Source references:

- Extraction table: `docs/project-context/implementation-workflow.md` sequencing matters
- Extraction table: `docs/codex-briefings/CP-5-roadmap.md` do not retry blocked dependent ticket until prerequisite is complete
- Audit: `Global Ticket Writing Rules`

### 5. Keep Prompts Short When Persistent Context Exists

Per-ticket prompts should stay short by default when the ticket and project context already exist.

Do not repeat full persistent context in every ticket prompt. Reference the relevant role, project context, briefing, and ticket instead.

Ask for a longer prompt only when:

- important scope is missing
- comments reveal a blocker that needs clarification
- the ticket contradicts the current repo state
- the ticket is unusually risky
- the admin is asking for work outside the ticket

Source references:

- Extraction table: `AGENTS.md.backup` keep per-ticket prompts short
- Extraction map: `Global Context Loading Rules`
- Audit: `Context Loading Rules Found`

## Acceptance Criteria Guidance

Acceptance criteria should describe observable completion conditions.

Use clear Given / When / Then wording where it improves precision:

```text
Given [starting condition],
When [user or system action happens],
Then [observable result is true].
```

Acceptance criteria should cover:

- expected user-visible behaviour
- important data persistence or state changes
- empty states where relevant
- error states where relevant
- permission, security, or configuration constraints where relevant
- build, test, or deployment gates where relevant

Do not guess missing acceptance criteria. If acceptance criteria are missing or contradicted by implementation reality, flag the gap for admin review or write a draft clearly marked for review.

If implementation drift affects acceptance criteria, the ticket should not be marked complete unless the criteria are still satisfied.

Source references:

- Extraction table: `AGENTS.md.backup` do not guess missing acceptance criteria
- Extraction table: `AGENTS.md.backup` if drift affects acceptance criteria, do not mark complete unless criteria are still satisfied
- Extraction map: `Global Ticket Writing Rules`
- Audit: `Global Ticket Writing Rules`

## Testing Guidance

Every implementation ticket should include test or validation expectations.

Manual test steps should be simple enough for a non-technical admin to follow and should include:

- what to run
- what page or surface to open, if applicable
- what to click, type, inspect, or trigger
- what the admin should see
- what confirms success

Automated or command checks should be listed when relevant, but check names must remain project-overridable.

If a command or test is required for completion, the ticket should say so. If a check is unavailable, out of scope, or blocked, the ticket should make that clear.

Source references:

- Extraction table: `AGENTS.md.backup` manual testing format
- Extraction table: `AGENTS.md.backup` run appropriate checks after implementation
- Extraction map: `Global Ticket Writing Rules`
- ResolveOS: `06-governance/codex-working-rules.md`

## Documentation Guidance

Tickets should include documentation expectations when implementation may affect persistent project context, future tickets, setup, deployment, security posture, or user-facing instructions.

Do not let documentation drift from reality.

Documentation notes should identify:

- which document or context file may need updating
- why it may need updating
- whether the update is required for this ticket or can be follow-up work
- the specific wording or summary to add, when useful

Do not create heavy documentation requirements for small tickets unless the change affects future work, setup, production behaviour, or admin understanding.

Source references:

- Extraction table: `AGENTS.md.backup` do not let documentation drift from reality
- Audit: `Global User Working Preferences`
- Extraction map: `Duplicate Content Consolidation Plan`

## Production Considerations

Ticket-writing should identify production or deployment considerations when relevant.

Include production notes for:

- environment configuration
- paid AI/API usage
- security or privacy constraints
- data migrations
- deployment ordering
- prerequisite commits or pushes
- disabled states when configuration is missing
- real data versus mock/demo data

Do not ask implementers to fake paid API responses, fake integrations, fake data, or fake success states to satisfy a ticket.

For AI/API-backed work, tickets should preserve cost-safe behaviour:

- require explicit configuration before paid calls are enabled
- make paid calls user-triggered by default
- avoid automatic retry or regeneration loops
- provide honest disabled/error states when configuration is missing
- do not fake paid API responses as real output

Source references:

- Extraction table: `docs/ai-roles/implementation-engineer.md` cost-safe external API rules
- Extraction table: `docs/codex-briefings/CP-8-ai-updates.md` cost-safe AI workflow design
- Extraction map: `Global Working Preferences`
- ResolveOS: `00-system/ai-operating-principles.md`

## Blocker Handling

If a ticket is blocked:

- stop
- explain the blocker clearly
- explain why continuing would be unsafe or unsupported
- identify the smallest prerequisite fix
- suggest a new prerequisite ticket if needed

Do not silently work around blockers.

Do not invent schema, fake functionality, fake data, fake integrations, or fake success states to make a ticket appear complete.

If the ticket cannot be completed as written, the ticket should be updated or followed by a prerequisite/follow-up ticket rather than forcing implementation through unsafe assumptions.

Source references:

- Extraction table: `AGENTS.md.backup` blocker handling
- Extraction table: `docs/project-context/implementation-workflow.md` blocker behaviour
- Audit: `Risks / Things Not To Lose`
- ResolveOS: `00-system/ai-operating-principles.md`

## Outputs

This skill should produce tickets or ticket review notes that include:

- clear title
- goal
- background or context
- scoped implementation work
- explicit non-goals
- assumptions
- dependencies and prerequisites
- acceptance criteria
- testing expectations
- documentation expectations, when relevant
- production or deployment notes, when relevant
- blocker notes, when relevant
- suggested follow-up tickets, when useful

Outputs should be practical, implementation-ready, and reviewable.

Source references:

- Extraction map: `Global Ticket Writing Rules`
- Audit: `Global Skill Candidates`

## Anti-Patterns

Do not:

- write tickets from unsupported assumptions
- guess missing acceptance criteria
- hide dependencies
- hide blockers
- bundle unrelated future scope into the current ticket
- start implementation from an epic alone when child tickets are missing
- create massive implementation tickets when smaller safe tickets are possible
- write vague tickets that do not say what is being achieved or why it matters
- rely on fake functionality, fake data, fake integrations, or fake success states
- over-plan distant roadmap work too early
- replace specific admin ticket-writing rules with generic Agile wording
- create project-specific product doctrine in global ResolveOS tickets

Source references:

- Extraction map: `Assistant Anti-Patterns`
- Extraction map: `Global Ticket Writing Rules`
- Audit: `Global Assistant Anti-Patterns / Prohibited Behaviours`
- ResolveOS: `06-governance/extraction-migration-guardrails.md`

## Examples

### Example Ticket Skeleton

```text
Title:
[Short implementation outcome]

Goal:
[What this ticket achieves]

Background / Context:
[Why this is needed and what source context informs it]

Scope:
- [Specific implementation item]
- [Specific implementation item]

Out of Scope:
- [Explicit non-goal]
- [Future work not included]

Assumptions:
- [Assumption, or None]

Dependencies / Prerequisites:
- [Required prior work, schema, config, source, or decision]

Implementation Notes:
- [Relevant implementation guidance]
- [Existing pattern or helper to use, if known]

Acceptance Criteria:
- Given [starting condition], when [action], then [observable result].
- Given [error or empty condition], when [action], then [honest state is shown].

Testing / Manual Test Steps:
1. [What to run/open/do]
   Why: [What this proves]
2. [What to inspect]
   Why: [What this proves]

Documentation Notes:
- [File/context to update, or Not needed]

Deployment / Production Notes:
- [Config, migration, rollout, or disabled-state notes, or Not needed]
```

### Example Blocked Ticket Note

```text
Status:
Blocked

Current blocker:
[Specific missing prerequisite, context, credential, schema, decision, or implementation dependency]

Why continuing is unsafe:
[Why implementation would require guessing, fake functionality, or unsupported assumptions]

Highest-leverage unblocker or follow-up action:
[Prerequisite fix or admin decision needed]

Suggested prerequisite ticket:
[Ticket title or None]
```

Source references:

- Extraction table: `AGENTS.md.backup` ticket startup and blocker formats
- Extraction table: `docs/project-context/implementation-workflow.md` ticket and blocker rules

## Related Context

- `00-system/ai-operating-principles.md`
- `01-context/context-loading-rules.md`
- `01-context/startup-context.md`

## Related Governance

- `06-governance/codex-working-rules.md`
- `06-governance/extraction-migration-guardrails.md`
- `06-governance/source-of-truth-rules.md`

## Source Merge Notes

Multiple source variants were consolidated:

- The ticket structure rule uses the strongest general wording from `docs/project-context/implementation-workflow.md`, expanded with specific fields preserved from `AGENTS.md.backup` and the extraction map.
- One-ticket-at-a-time guidance uses repeated wording from `AGENTS.md.backup`, `implementation-workflow.md`, role prompts, and epic briefings.
- Blocker handling preserves the stronger stop-and-explain wording from `AGENTS.md.backup` and `implementation-workflow.md`.
- Testing guidance preserves `AGENTS.md.backup` manual testing details while keeping project-specific command names project-overridable.
- Production considerations preserve reusable cost-safe and real-state rules without copying ResolvePM-specific Supabase, Vercel, CP ticket, or roadmap details.

## Deferred Items

Deferred because they are out of scope for Batch 2A or require admin review:

- a standalone `acceptance-criteria.md` skill
- a standalone completion-reporting skill or template
- role-specific implementation behaviour
- ResolvePM CP ticket sequences
- ResolvePM product roadmap, product vision, or product terminology
- project-specific deployment commands, Supabase details, and Vercel details
- richer feedback-processing taxonomy
- exact completion report format from `AGENTS.md.backup`

## Ambiguous Items For Admin Review

- Whether completion reporting should become its own skill or template in a later batch.
- Whether Given / When / Then should be mandatory or only recommended when it improves precision.
- Whether check commands should be globally standardised or remain entirely project-overridable.
- Whether dependency commit-order rules belong in ticket writing, Codex governance, or a future implementation workflow.

## What This Skill Must Not Do

This skill must not:

- create or modify tickets automatically without admin instruction
- define role responsibilities
- define full acceptance-criteria or completion-reporting skills
- replace project-specific source-of-truth files
- promote ResolvePM product doctrine into global ResolveOS guidance
- invent ticket rules not supported by the extraction map or audit

---

# Source: 03-skills/user-feedback-processing.md

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

Define how assistants, agents, and Codex capture, preserve, classify, analyse, and convert user feedback into reviewed work.

This skill exists to preserve the reusable ResolvePM feedback-handling behaviour in ResolveOS without turning it into generic product-management process.

Source references:
- `migration/resolvepm-extraction-audit.md` > `Global Feedback Handling Rules`
- `migration/resolvepm-extraction-map.md` > `Global Feedback Handling Rules`
- `migration/resolvepm-extraction-map.md` > `Extraction Table`
- `06-governance/extraction-migration-guardrails.md` > feedback-handling preservation rules

# When To Use

Use this skill when:

- Capturing product, workflow, tester, admin, or user feedback.
- Cleaning feedback without losing the original meaning.
- Classifying feedback before backlog, roadmap, or ticket decisions.
- Reviewing whether feedback should become a follow-up ticket.
- Handling duplicate, ambiguous, partial, or conflicting feedback.
- Preserving traceability from feedback to later work.

Do not use this skill to replace project-specific discovery, strategy, prioritisation, research, ticket-writing, or implementation review processes.

# Inputs

Useful inputs include:

- Raw feedback text.
- Source or user identity where available.
- Timestamp where available.
- Feedback category where available.
- Product, project, workflow, ticket, release, or testing context.
- Existing related feedback, tickets, decisions, or prior analysis.
- Project-specific prioritisation filters from the current project context.

Minimum explicit feedback fields found in ResolvePM are:

- `category`
- `message`
- `user`
- `timestamp`

Source reference:
- `migration/resolvepm-extraction-map.md` > `Global Feedback Handling Rules`
- `migration/resolvepm-extraction-map.md` > `Extraction Table` > `docs/codex-briefings/CP-84-tester-readiness.md`

# Feedback Processing Principles

Keep feedback handling simple by default.

Preserve the original intent before cleaning, classifying, or converting feedback.

Separate raw feedback from interpretation. Do not overwrite the original wording with a cleaned summary.

Distinguish observations, requests, assumptions, proposed solutions, recommendations, and follow-up work.

Prefer evidence over invention. Do not infer motivation, priority, severity, or acceptance criteria that the feedback does not support.

Feedback should become reviewed follow-up tickets, not automatic current-scope expansion.

Do not over-format feedback into a heavy taxonomy unless admin approves.

Use project-specific prioritisation filters only from the active project context. Do not make ResolvePM product doctrine global.

Source references:
- `migration/resolvepm-extraction-audit.md` > `Global Feedback Handling Rules`
- `migration/resolvepm-extraction-audit.md` > `Risks / Things Not To Lose`
- `migration/resolvepm-extraction-map.md` > `Global Feedback Handling Rules`
- `migration/resolvepm-extraction-map.md` > `High Risk Migrations`
- `00-system/ai-operating-principles.md` > `Evidence Over Invention`
- `00-system/ai-operating-principles.md` > `Preserve Admin Intent`

# Capturing Feedback

Capture the raw feedback first.

When structured capture is needed, collect at least:

- `category`
- `message`
- `user`
- `timestamp`

Feedback collection should be simple enough that the user can provide useful feedback without extra operational burden.

Where practical, feedback should be collected without developer intervention.

External testing feedback should validate workflow value, not just technical correctness.

Do not expand feedback capture into workspace, billing, enterprise auth, organisation, or other platform models unless admin explicitly approves that scope.

Source references:
- `migration/resolvepm-extraction-audit.md` > `Global Feedback Handling Rules`
- `migration/resolvepm-extraction-map.md` > `Extraction Table` > `docs/codex-briefings/CP-84-tester-readiness.md`

# Preserving Feedback

Preserve:

- The raw feedback wording.
- The feedback source.
- The timestamp where available.
- The project, ticket, feature, workflow, or test context.
- Any uncertainty, contradiction, or missing detail.
- Links to related feedback, tickets, or decisions where available.

Cleaned feedback may clarify grammar, remove noise, or separate concepts, but it must not change the meaning.

If the feedback contains both a problem and a proposed solution, preserve both separately.

If the assistant is unsure what the user meant, label the uncertainty explicitly instead of resolving it silently.

Source references:
- `06-governance/extraction-migration-guardrails.md` > feedback capture, cleaning, classification, and traceability guardrails
- `00-system/ai-operating-principles.md` > `Explicit Uncertainty`
- `00-system/ai-operating-principles.md` > `Do Not Over-Summarise Important Rules`

# Classifying Feedback

Use lightweight classification unless admin asks for a richer taxonomy.

Recommended lightweight classes:

- Raw feedback.
- Observation.
- Problem or pain point.
- Request.
- Proposed solution.
- Recommendation.
- Question.
- Ambiguous feedback.
- Duplicate or related feedback.
- Follow-up ticket candidate.

Classification should help review. It should not become a substitute for review.

Do not treat every user message as a ticket request. A message may be feedback, a correction, a blocker, an instruction, a question, or a signal that project context needs to be checked.

Source references:
- `migration/resolvepm-extraction-map.md` > `Ambiguous Classifications Requiring Admin Decision`
- `migration/resolvepm-extraction-map.md` > `High Risk Migrations`
- `06-governance/extraction-migration-guardrails.md` > feedback-handling rules

# Converting Feedback Into Work

Convert feedback into work only after review.

Before converting feedback into a ticket:

- Preserve the raw feedback.
- Identify the underlying problem or request.
- Separate observations from recommendations.
- Check for duplicates or related work.
- Confirm whether the work belongs in the current scope or should become follow-up work.
- Use the project context to decide whether the feedback is globally relevant, project-specific, or not actionable yet.

When feedback becomes a ticket, use `03-skills/ticket-writing.md`.

Feedback should suggest follow-up tickets rather than expand the current implementation scope unless admin explicitly changes the scope.

Source references:
- `migration/resolvepm-extraction-audit.md` > `Global Feedback Handling Rules`
- `migration/resolvepm-extraction-audit.md` > `Risks / Things Not To Lose`
- `migration/resolvepm-extraction-map.md` > `Global Feedback Handling Rules`
- `03-skills/ticket-writing.md` > `Ticket Writing Process`

# Duplicate Handling

Duplicates should be consolidated without losing traceability.

When feedback duplicates or overlaps existing feedback:

- Preserve the new raw feedback.
- Link or reference the existing feedback, ticket, or decision where possible.
- Note whether it is an exact duplicate, a related example, or a new variation of the same issue.
- Preserve source and timestamp information.
- Do not discard duplicate feedback merely because the underlying issue is already known.

Repeated feedback can be evidence of importance, confusion, poor workflow fit, or documentation gaps. Do not infer priority from repetition alone without project context.

Source references:
- `06-governance/extraction-migration-guardrails.md` > duplicate and traceability preservation
- `00-system/ai-operating-principles.md` > `Evidence Over Invention`

# Ambiguous Feedback

When feedback is ambiguous:

- Preserve the original wording.
- State what is unclear.
- Avoid inventing intent.
- Avoid turning ambiguity into acceptance criteria.
- Ask for admin review when the ambiguity affects scope, priority, product direction, or implementation.
- Keep the feedback as raw or under review until enough context exists.

If feedback may be project-specific, do not migrate it into global ResolveOS behaviour without admin decision.

Source references:
- `migration/resolvepm-extraction-map.md` > `Ambiguous Classifications Requiring Admin Decision`
- `06-governance/source-of-truth-rules.md` > project repositories own project-specific decisions
- `00-system/ai-operating-principles.md` > `Explicit Uncertainty`

# Prioritisation Guidance

Prioritisation must use the active project context.

Global feedback processing may identify:

- Frequency.
- Severity.
- Workflow impact.
- User impact.
- Evidence strength.
- Scope fit.
- Follow-up readiness.

Global feedback processing must not impose ResolvePM-specific product filters on other projects.

The ResolvePM strategic filter found during extraction is not migrated as a global rule. It should remain project-specific unless admin separately approves a generic version.

Source references:
- `migration/resolvepm-extraction-audit.md` > `Global Feedback Handling Rules`
- `migration/resolvepm-extraction-map.md` > `Project-Specific ResolvePM Content`
- `06-governance/source-of-truth-rules.md` > ResolveOS versus project source ownership

# Outputs

Possible outputs include:

- Preserved raw feedback record.
- Cleaned feedback summary.
- Lightweight feedback classification.
- Duplicate or related-feedback note.
- Ambiguity note.
- Follow-up ticket recommendation.
- Deferred feedback list.
- Admin-review question.
- Source-to-ticket traceability note.

Any output that claims feedback was stored, ticketed, linked, reviewed, tested, deployed, or implemented must only say so if that action actually happened.

Source references:
- `03-skills/completion-reporting.md` > completion honesty and validation reporting
- `06-governance/codex-working-rules.md` > no fake functionality and completion honesty

# Anti-Patterns

Do not:

- Over-format feedback into a heavy taxonomy unless admin approves.
- Convert every feedback item into a ticket automatically.
- Expand current implementation scope because feedback was found.
- Lose the raw wording.
- Replace user intent with assistant interpretation.
- Treat a proposed solution as the underlying problem.
- Treat an observation as a recommendation.
- Discard duplicates without traceability.
- Hide ambiguity.
- Invent priority, severity, source, timestamp, or acceptance criteria.
- Make ResolvePM product doctrine global.
- Claim feedback was stored, reviewed, ticketed, or implemented unless it was.

Source references:
- `migration/resolvepm-extraction-map.md` > `Global Feedback Handling Rules`
- `migration/resolvepm-extraction-map.md` > `High Risk Migrations`
- `06-governance/extraction-migration-guardrails.md` > preservation rules
- `00-system/ai-operating-principles.md` > truthfulness and evidence rules

# Examples

Simple captured feedback:

```text
category: workflow
message: "It is not clear what happens after I submit tester feedback."
user: external tester
timestamp: 2026-06-07 14:30
```

Cleaned classification:

```text
Raw feedback preserved: yes
Classification: observation; possible documentation or workflow clarity issue
Interpretation: user may need clearer post-submit confirmation
Uncertainty: exact expected confirmation is not specified
Recommended handling: review against project context before creating a follow-up ticket
```

Feedback-to-ticket review note:

```text
Feedback should not expand the current implementation scope.
Recommended follow-up: create a reviewed ticket only if admin agrees this is actionable now.
Traceability: retain source feedback and timestamp in the ticket background.
```

# Related Skills

- `03-skills/ticket-writing.md`
- `03-skills/completion-reporting.md`

# Related Governance

- `00-system/ai-operating-principles.md`
- `01-context/context-loading-rules.md`
- `01-context/startup-context.md`
- `06-governance/codex-working-rules.md`
- `06-governance/extraction-migration-guardrails.md`
- `06-governance/source-of-truth-rules.md`
- `06-governance/architecture-decisions.md`

# Deferred Items

Deferred for later batches or admin decision:

- A dedicated `05-workflows/feedback-to-ticket.md` workflow.
- Any feedback capture template.
- A richer feedback triage taxonomy.
- Project-specific prioritisation filters.
- Product-specific tester-readiness workflows.
- Storage implementation details for feedback systems.
- Automatic feedback collection mechanisms.

# Ambiguous Items For Admin Review

Admin review is needed for:

- Whether ResolveOS should keep feedback fields minimal or define a richer canonical taxonomy.
- Whether ordinary user messages should be treated as feedback by default across all projects.
- Whether ResolveOS should define a generic version of ResolvePM's product feedback strategic filter.
- Which storage fields beyond `category`, `message`, `user`, and `timestamp` should become canonical.

---

# Source: 05-workflows/feedback-to-ticket.md

---
type: workflow
scope: global
owner: ResolveOS
version: 0.1
status: draft
source_project: ResolvePM
source_files:
  - migration-review.md
  - migration/resolvepm-extraction-map.md
  - migration/resolvepm-extraction-audit.md
  - AGENTS.md.backup
  - docs/codex-briefings/CP-84-tester-readiness.md
  - docs/project-context/implementation-workflow.md
  - docs/ai-core/operational-clarity-framework.md
  - docs/ai-role-prompts/
related_roles:
  - 02-roles/product-manager.md
  - 02-roles/business-analyst.md
  - 02-roles/technical-strategy-lead.md
  - 02-roles/strategic-product-director.md
  - 02-roles/implementation-engineer.md
  - 02-roles/qa-tester.md
related_skills:
  - 03-skills/user-feedback-processing.md
  - 03-skills/ticket-writing.md
  - 03-skills/acceptance-criteria.md
  - 03-skills/completion-reporting.md
related_workflows:
  - 05-workflows/ticket-to-implementation.md
  - 05-workflows/implementation-review-loop.md
related_context:
  - 01-context/context-loading-rules.md
  - 01-context/startup-context.md
  - 01-context/role-loading-rules.md
  - 01-context/missing-context-behaviour.md
  - 01-context/project-loading-rules.md
related_governance:
  - 00-system/ai-operating-principles.md
  - 06-governance/source-of-truth-rules.md
  - 06-governance/architecture-decisions.md
review_required: true
---

# Purpose

Define the ResolveOS workflow for turning captured feedback into reviewed, scoped, traceable work.

This workflow owns the transition from feedback into ticket-ready scope or follow-up tickets. It does not replace the `user-feedback-processing` skill, which captures, preserves, classifies, and interprets feedback. It does not replace the `ticket-writing` skill, which defines how tickets are written.

Feedback should become reviewed follow-up tickets, not automatic current-scope expansion.

# Trigger

Use this workflow when:

- captured feedback may need to become a ticket
- tester feedback, user feedback, review feedback, or completion-report follow-up needs triage
- raw feedback needs to be separated from interpretation before ticket creation
- feedback duplicates or relates to existing work
- feedback is ambiguous and may require admin clarification
- implementation or review reveals useful work outside the current ticket
- a role needs to decide whether feedback is no action, needs clarification, deferred, a follow-up candidate, or ticket-ready

Do not use this workflow to:

- collect feedback from scratch
- create a feedback storage schema
- define a feedback template
- run product discovery
- impose project-specific prioritisation doctrine
- expand the current implementation scope without explicit admin approval

# Inputs

Use the smallest relevant input set needed for the feedback decision.

Useful inputs include:

- preserved raw feedback
- feedback category, message, user, and timestamp
- source context, such as ticket, feature, workflow, test session, review, comment, or completion report
- cleaned feedback summary, if already created
- feedback classification, if already created
- current ticket or approved implementation scope
- related tickets, feedback items, decisions, blockers, or documentation
- active project context and project-owned prioritisation filters
- relevant role context for Product Manager, Business Analyst, Technical Strategy Lead, Strategic Product Director, QA Tester, or Implementation Engineer
- relevant skills for user feedback processing, ticket writing, acceptance criteria, and completion reporting

If required source context is unavailable, name the missing context and proceed only with an explicit limitation. Do not invent missing requirements, priority, severity, user intent, acceptance criteria, or project strategy.

# Workflow Principles

- Keep feedback handling simple by default.
- Preserve the original feedback before cleaning, classifying, or converting it.
- Preserve raw feedback separately from interpretation.
- Distinguish the problem from the proposed solution.
- Distinguish observations, requests, assumptions, recommendations, and follow-up work.
- Do not treat every user message as a ticket request.
- Do not over-format feedback into a heavy taxonomy unless admin approves.
- Do not discard duplicates.
- Do not infer priority from repetition alone.
- Do not use project-specific prioritisation filters unless they are loaded from active project context.
- Do not make ResolvePM product doctrine global ResolveOS doctrine.
- Do not expand current scope silently.

# Required Context

Before converting feedback into scoped work, load or confirm:

- the active project and current source of truth
- whether the feedback belongs to current scope, future work, no action, or admin review
- whether active project context defines a prioritisation filter
- whether related tickets, feedback items, blocker notes, or decisions already exist
- the role that owns the decision being made

Use `01-context/project-loading-rules.md` when project context or prioritisation ownership matters.

Use `06-governance/source-of-truth-rules.md` when feedback, tickets, comments, documentation, or admin instruction conflict.

# Steps

## 1. Confirm Feedback Context

Identify where the feedback came from and what work it might affect.

Confirm whether the feedback is connected to:

- current implementation scope
- a current ticket
- a completed ticket
- a test session
- a product area
- a workflow
- a project decision
- future work

If the source is unclear, keep the feedback under review instead of converting it into work.

## 2. Preserve The Raw Feedback

Preserve the original feedback before cleaning or interpreting it.

At minimum, preserve:

- category
- message
- user
- timestamp

When available, also preserve:

- source
- project, ticket, feature, workflow, or test context
- related links or references
- uncertainty, contradiction, or missing detail
- related tickets, feedback items, or decisions

Do not overwrite the original wording with a cleaned version.

## 3. Clean Lightly

Clean feedback only enough to make it reviewable.

Cleaning may:

- clarify grammar
- remove noise
- split multiple concepts
- identify obvious references

Cleaning must not:

- change meaning
- hide uncertainty
- add missing requirements
- turn a proposed solution into an accepted product decision
- turn vague feedback into polished fake certainty

## 4. Classify Lightly

Use lightweight classification to support review.

Useful categories include:

- raw feedback
- observation
- problem or pain point
- request
- proposed solution
- recommendation
- question
- ambiguous feedback
- duplicate or related feedback
- follow-up ticket candidate

Classification helps review. It does not substitute for review.

## 5. Separate Problem, Request, And Solution

Identify what the feedback actually says.

Separate:

- observed issue
- user need or pain
- explicit request
- proposed solution
- product interpretation
- implementation implication
- open question

Do not treat the user's proposed solution as the underlying problem.

## 6. Check Existing Work

Check whether the feedback is:

- an exact duplicate
- related to existing feedback
- already covered by a ticket
- already covered by a decision
- a new variation of a known issue
- contradicted by existing source-of-truth material

Preserve the new feedback even when it duplicates existing feedback.

## 7. Decide Review Outcome

Assign one review outcome:

- no action
- preserve for later review
- needs clarification
- duplicate or related item
- follow-up ticket candidate
- ticket-ready scope
- current-scope change, only when admin explicitly approves the scope change

If the decision depends on project strategy, roadmap priority, scope authority, or ambiguous requirements, defer for admin review or the accountable role.

## 8. Apply Project Filters Only When Loaded

If active project context provides prioritisation filters, apply them as project-owned context.

If no project-specific filter is loaded, do not import ResolvePM strategic filters or product doctrine. Record the prioritisation gap and ask for admin or Strategic Product Director review where needed.

## 9. Prepare Ticket-Ready Scope

When feedback is ready to become work, use `03-skills/ticket-writing.md`.

Ticket-ready scope should include:

- source feedback reference
- original feedback or link to preserved feedback
- problem or outcome
- why it matters, when supported by source context
- scope
- non-goals where useful
- assumptions
- dependencies or prerequisites
- acceptance criteria
- manual validation expectations where relevant
- ambiguity, blocker, or admin-review notes

Do not guess missing acceptance criteria.

## 10. Report The Result

Report what happened to the feedback.

Include:

- preserved source
- review outcome
- duplicate or related references
- ticket-ready scope or follow-up recommendation
- deferred items
- admin questions
- role escalations
- whether current scope changed

# Feedback Review

Feedback review should answer:

- What did the original feedback say?
- What is interpretation rather than raw feedback?
- What problem or pain is visible?
- What solution, if any, was proposed?
- What evidence supports action?
- Is this duplicate, related, contradicted, or new?
- Does it belong to current scope or future work?
- Is project-specific prioritisation context available?
- What is missing before this can become a ticket?

Do not let formatting make unresolved feedback look resolved.

# Ticket Readiness

Feedback is ticket-ready only when it can be converted into scoped, testable work without inventing requirements.

Before ticket creation, confirm:

- the source feedback remains traceable
- the problem or outcome is clear
- scope is bounded
- non-goals are clear where needed
- assumptions are explicit
- dependencies or prerequisites are known or flagged
- acceptance criteria are observable and testable
- priority is either supported by project context or explicitly left for review

Creating a ticket does not imply approval authority.

# Duplicate Handling

When feedback duplicates or relates to existing feedback:

- preserve the new raw feedback
- link or reference the existing feedback, ticket, decision, or blocker
- state whether it is an exact duplicate, related item, contradiction, or new variation
- preserve source, user, and timestamp
- do not discard the duplicate

Repeated feedback may signal importance, confusion, workflow friction, or documentation gaps. It does not automatically establish priority.

# Ambiguous Feedback Handling

When feedback is ambiguous:

- preserve the original wording
- state what is unclear
- avoid inventing intent
- avoid creating acceptance criteria from ambiguity
- ask admin or the accountable role when ambiguity affects scope, priority, direction, implementation, or acceptance
- keep the item under review until enough context exists

Ambiguous feedback may become a clarification question, not a ticket.

# Scope Control

Feedback does not automatically change current scope.

If feedback arrives during implementation, review, QA, completion reporting, or a current ticket:

- preserve it
- classify it
- check duplicates or related work
- suggest follow-up tickets when useful
- keep current work inside approved scope

Only treat feedback as a current-scope change when admin explicitly approves the change.

Avoid hidden scope expansion.

# Role Responsibilities

Product Manager owns product-scope alignment, feedback-to-work discipline, and ticket readiness for product work.

Business Analyst owns requirement clarification, ambiguity reduction, assumption identification, and traceability between feedback, requirements, and tickets.

Technical Strategy Lead owns sequencing, dependency, prerequisite, architecture, and implementation-governance review when feedback affects delivery.

Strategic Product Director owns strategy-level prioritisation, roadmap coherence, positioning, and whether the work should exist.

QA Tester owns validation evidence, defect identification, defect ticket creation where appropriate, and quality-risk escalation.

Implementation Engineer may report feedback, blockers, drift, and suggested follow-up work, but should not silently convert adjacent ideas into implementation scope.

# Outputs

This workflow may produce:

- preserved feedback reference
- cleaned feedback summary
- lightweight classification
- duplicate or related-work note
- ambiguity note
- no-action decision
- clarification question
- follow-up ticket recommendation
- ticket-ready scope
- admin-review note
- role escalation note
- traceability note

# Anti-Patterns

Do not:

- convert every feedback item into a ticket automatically
- expand current implementation scope without explicit admin approval
- overwrite original feedback with cleaned wording
- discard duplicates
- infer priority from repetition alone
- guess missing requirements, severity, priority, motivation, business value, or acceptance criteria
- over-format feedback into a heavy taxonomy without admin approval
- impose ResolvePM product doctrine on global ResolveOS workflows
- treat project-specific prioritisation filters as global governance
- treat a proposed solution as the confirmed problem
- make ambiguous feedback look ticket-ready
- create templates, skills, roles, or storage schemas from this workflow

# Examples

Tester feedback:

```text
Raw: "I cannot tell whether the save worked."
Review: Problem or pain point. Possible workflow clarity issue.
Outcome: Follow-up ticket candidate unless current scope explicitly included save-state confirmation.
Traceability: Preserve raw feedback, tester, timestamp, tested page or workflow, and related ticket.
```

Duplicate feedback:

```text
Raw: "The setup page is confusing."
Review: Related to existing feedback about onboarding wording.
Outcome: Preserve as related feedback, link to existing item, and note that repetition may indicate confusion.
Priority: Leave priority to project context or Strategic Product Director review.
```

Ambiguous feedback:

```text
Raw: "This should be smarter."
Review: Ambiguous. Could refer to automation, defaults, recommendations, or error handling.
Outcome: Clarification required. Do not create acceptance criteria yet.
```

# Related Roles

- `02-roles/product-manager.md`
- `02-roles/business-analyst.md`
- `02-roles/technical-strategy-lead.md`
- `02-roles/strategic-product-director.md`
- `02-roles/implementation-engineer.md`
- `02-roles/qa-tester.md`

# Related Skills

- `03-skills/user-feedback-processing.md`
- `03-skills/ticket-writing.md`
- `03-skills/acceptance-criteria.md`
- `03-skills/completion-reporting.md`

# Related Context

- `01-context/context-loading-rules.md`
- `01-context/startup-context.md`
- `01-context/role-loading-rules.md`
- `01-context/missing-context-behaviour.md`
- `01-context/project-loading-rules.md`

# Related Governance

- `00-system/ai-operating-principles.md`
- `06-governance/source-of-truth-rules.md`
- `06-governance/architecture-decisions.md`

---

# Source: 05-workflows/implementation-review-loop.md

---
type: workflow
scope: global
owner: ResolveOS
version: 0.1
status: draft
source_project: ResolvePM
source_files:
  - migration-review.md
  - migration/resolvepm-extraction-map.md
  - migration/resolvepm-extraction-audit.md
  - AGENTS.md.backup
  - DEBUGGING.md
  - docs/project-context/implementation-workflow.md
  - docs/codex-briefings/
related_roles:
  - 02-roles/implementation-engineer.md
  - 02-roles/qa-tester.md
  - 02-roles/technical-strategy-lead.md
  - 02-roles/product-manager.md
  - 02-roles/business-analyst.md
  - 02-roles/strategic-product-director.md
related_skills:
  - 03-skills/completion-reporting.md
  - 03-skills/acceptance-criteria.md
  - 03-skills/ticket-writing.md
related_workflows:
  - 05-workflows/ticket-to-implementation.md
related_context:
  - 01-context/missing-context-behaviour.md
  - 01-context/project-loading-rules.md
  - 01-context/role-loading-rules.md
  - 01-context/context-loading-rules.md
related_governance:
  - 00-system/ai-operating-principles.md
  - 06-governance/codex-working-rules.md
  - 06-governance/source-of-truth-rules.md
  - 06-governance/architecture-decisions.md
review_required: true
---

# Purpose

Define the canonical ResolveOS workflow for reviewing implementation when work is incomplete, repeatedly failing, drifting from scope, blocked, uncertain, or not ready to report as complete.

This workflow is the stop-and-review loop for implementation execution. It prevents false completion, hidden blockers, repeated random changes, fake functionality, future-ticket leakage, documentation drift, and unsupported claims that implementation is done.

This is not a retrospective template, QA sign-off workflow, debugging skill, ticket template, or role definition.

# Trigger

Use this workflow when implementation work shows one or more review triggers:

- repeated implementation failure
- stuck loop
- failed build, lint, test, deployment, runtime check, or validation
- missing context during implementation
- unclear or missing acceptance criteria during implementation
- implementation drift from approved scope
- discovered dependency or prerequisite issue
- schema, architecture, configuration, credential, or source-of-truth blocker
- technical uncertainty that makes continued changes unsafe
- partial completion
- future-ticket leakage
- possible fake functionality or fake state
- documentation drift from implementation reality
- uncertainty about whether work can be reported as complete

Use it before claiming completion when any of these conditions exist.

# Inputs

Use the smallest relevant evidence needed to review the implementation state.

Inputs may include:

- current ticket, task, source item, or approved batch
- approved scope and acceptance criteria
- implementation notes and manual test steps
- ticket comments, blocker notes, and prerequisite warnings
- current repository state
- changed files
- command output
- failed check output
- first clear error
- validation results
- manual test observations
- current project context
- relevant briefing
- previous ticket outcome where dependencies or sequencing affect the current work
- known dependencies, prerequisites, assumptions, non-goals, and follow-up notes
- relevant ResolveOS role, context, skill, workflow, and governance files

Do not infer missing implementation evidence from memory.

# Workflow Principles

## Stop Before False Completion

Do not pretend the ticket is complete.

Do not claim work was completed, tested, deployed, committed, pushed, accepted, or source-ticket-updated unless there is direct evidence.

If the work is partial, blocked, failed, or not verified, say so directly.

## Current Ticket First

Current ticket first.

Review the current ticket, task, source item, or approved batch before considering future work.

Do not turn implementation review into future-ticket implementation.

Do not add unrelated scope while trying to resolve the failure.

## Evidence Over More Changes

When implementation starts failing or drifting, gather evidence before making more changes.

Inspect the current state, identify the first clear error where practical, and separate real failures from future-only features.

Do not keep making random changes after repeated failure.

## Real State Over Fake State

Empty state is better than fake state.

Do not use fake buttons, fake integrations, fake operational data, fake generated output, fake schema, fake success states, fake local fallback data, or pretend workflow behaviour to make implementation appear complete.

## Reviewability

Review output must make the state of work understandable.

It should state what happened, what was tried, what changed, what failed, what remains uncertain, and what highest-leverage unblocker or follow-up action is needed.

# Review Triggers

Start this workflow when any of the following happen:

- a required check fails and cannot be quickly resolved inside approved scope
- validation fails or cannot be performed
- manual testing is not possible
- acceptance criteria are unclear, missing, contradicted, or no longer satisfied
- implementation differs significantly from the original ticket plan
- scope starts expanding silently
- a future ticket is being implemented early
- a prerequisite is missing
- source context is missing or stale
- a dependency, schema, helper, migration, configuration, credential, or architecture gap appears
- repeated changes do not improve the failure
- the implementation path becomes unclear
- a security, paid API, deployment, or source-of-truth decision is needed
- documentation no longer matches implementation reality
- completion status cannot be stated honestly

# Stuck Loop Handling

If implementation enters a loop, repeated error, failed build cycle, dependency conflict, or unclear implementation path:

- stop after a reasonable number of attempts
- do not keep making random changes
- explain the issue in plain English
- explain what was tried
- explain the current state of the code or work
- explain what decision, help, source context, or prerequisite is needed
- mark the result as blocked or partially complete

Do not silently leave work in a failed state.

Do not pretend the ticket is complete.

When available evidence supports it, identify:

- exact command, page, route, action, or validation step involved
- first clear error
- related file or component
- whether the failure appears related to scoped work
- whether the failure appears unrelated or pre-existing
- highest-leverage unblocker or follow-up action

# Implementation Drift Handling

Implementation drift exists when implementation differs significantly from the original ticket plan.

Examples include:

- using a different library or framework approach than expected
- changing file structure substantially
- discovering the ticket depends on another piece of work
- implementing a smaller workaround instead of the intended solution
- splitting the ticket into partial implementation plus follow-up work
- removing or changing a visible feature to avoid fake functionality
- not being able to follow the acceptance criteria exactly

When drift occurs, report:

```text
Original plan:
- What the ticket appeared to ask for.

What actually happened:
- What was implemented instead.

Why it changed:
- The reason for the difference.

Impact:
- Whether this affects the acceptance criteria, future tickets, or user testing.

Follow-up needed:
- Any new ticket or decision required.
```

If the drift affects the acceptance criteria, do not mark the ticket complete unless the criteria are still satisfied.

If the drift changes product meaning, escalate to Product Manager.

If the drift changes requirement meaning, escalate to Business Analyst.

If the drift changes sequencing, architecture, dependency, build, or deployment risk, escalate to Technical Strategy Lead.

If the drift exposes strategy or roadmap risk, escalate to Strategic Product Director.

# Blocker Handling

If blocked:

- stop
- explain the blocker clearly
- explain why continuing would be unsafe or unsupported
- state what information, credential, config, source file, prerequisite, or admin decision is needed
- suggest the highest-leverage unblocker or follow-up action
- suggest whether a new prerequisite or follow-up ticket is needed

Do not silently work around blockers.

Do not work around security, architecture, source-of-truth, schema, dependency, configuration, paid API, or acceptance-criteria requirements just to continue.

Do not invent schema, fake functionality, fake data, fake integrations, fake generated output, or fake success states to make the ticket appear complete.

# Failed Validation Handling

If build, lint, test, runtime, deployment, manual validation, acceptance review, or QA validation fails:

- identify what failed
- identify the command, check, page, action, or criterion involved
- identify the first clear error when practical
- determine whether the failure is related to the scoped work
- fix related failures when practical and safe
- document unrelated or blocked failures clearly
- do not hide the failure
- do not claim completion while required validation fails

Manual testing must be possible for completed implementation work.

If manual testing is not possible, report the work as not verified, partial, or blocked unless admin explicitly accepts the limitation.

Project-specific command names, routes, deployment targets, and validation procedures belong in project context.

# Missing Context Handling

If required context is missing during implementation:

- stop or proceed only with an explicit limitation when safe
- name the missing context
- explain why it matters
- identify whether the missing context blocks implementation, validation, completion reporting, or source-of-truth confidence
- ask for the missing context or use an approved fallback
- state the limitation of any fallback

Do not guess missing acceptance criteria.

Do not infer missing project facts from memory.

Do not create implementation output that depends on missing files, source comments, tickets, credentials, configuration, schema, or decisions.

If the current source contradicts existing project context or ResolveOS governance, flag the contradiction instead of silently choosing the easier path.

# Role Responsibilities

Roles participate in this workflow without changing their authority.

Implementation Engineer:

- identifies implementation failure, drift, blockers, and validation state
- gathers evidence from current implementation and checks
- stops when repeated failure or unsafe assumptions appear
- reports complete, partial, blocked, failed, or not verified status only when evidence supports it

QA Tester:

- reviews validation evidence, acceptance criteria satisfaction, defect evidence, regression risk, and quality-gate status
- may identify or create defect tickets when evidence supports them
- does not approve product scope or own code execution

Technical Strategy Lead:

- reviews sequencing, dependency, architecture, implementation-governance, and delivery risk
- decides whether prerequisite work, ticket splitting, or implementation resequencing is needed
- stops further ticket progression when dependency, architecture, build, deployment, or source-of-truth risk makes continuation unsafe

Product Manager:

- reviews product scope, acceptance intent, product meaning, and product-side completion risk
- decides whether implementation drift still satisfies approved product objectives within low-risk clarification bounds

Business Analyst:

- reviews unclear requirements, business rules, assumptions, traceability, and acceptance criteria ambiguity
- helps prevent invented requirements or vague criteria from being treated as ready

Strategic Product Director:

- reviews strategy, roadmap, prioritisation, positioning, or whether something should exist when implementation exposes strategic drift

# Escalation Rules

Escalate to admin when:

- required source context is missing or contradictory
- continuing would require invented requirements, fake functionality, fake state, or unsupported assumptions
- repeated failures create a loop
- a failed check cannot be resolved safely
- completion status cannot be stated honestly
- manual approval is needed for git, deployment, paid API use, credentials, security, product scope, or source-of-truth changes

Escalate to Technical Strategy Lead when:

- dependencies are incomplete
- prerequisite tickets are needed
- build or deployment integrity breaks
- architecture direction changes
- implementation sequencing changes
- the current ticket cannot safely continue in the current order

Escalate to QA Tester when:

- validation ownership, defect verification, regression thinking, or quality-gate status is needed
- failed validation needs defect evidence or retest judgement

Escalate to Product Manager or Business Analyst when:

- product scope, acceptance intent, requirements, assumptions, traceability, or acceptance criteria are unclear or affected by implementation reality

Escalate to Strategic Product Director when:

- implementation exposes product strategy drift, roadmap coherence risk, positioning risk, or a question about whether the feature should exist

# Outputs

This workflow may produce:

- blocked status
- partially complete status
- failed status
- not verified status
- implementation drift report
- stuck-loop report
- failed-validation report
- blocker report
- missing-context report
- dependency or prerequisite report
- suggested follow-up ticket
- suggested documentation update
- escalation note
- admin-review question

Outputs should be plain, direct, practical, and traceable to available evidence.

# Anti-Patterns

Do not:

- keep making random changes after repeated failure
- silently leave work in a failed state
- silently work around blockers
- hide build, lint, test, deployment, runtime, manual validation, or acceptance failures
- claim completion when required checks or validation failed
- claim completion when acceptance criteria are missing, unclear, contradicted, or no longer satisfied
- pretend the ticket is complete
- invent schema, requirements, integrations, configuration, credentials, source context, validation evidence, or success states
- create fake functionality to pass review
- build future tickets early while resolving current-ticket failure
- add unrelated scope while debugging
- reclassify failed or partial work as complete because the report would be inconvenient
- bury blockers or uncertainty inside vague summaries
- make project-specific commands or paths global
- turn this workflow into a completion report template or debugging skill

# Examples

## Repeated Build Failure

```text
Trigger:
- The build fails repeatedly after scoped changes.

Handling:
- Stop after reasonable attempts.
- Identify the first clear error.
- State what was tried.
- State whether the failure appears related to scoped work.
- Mark the result blocked or partially complete.
- Suggest the highest-leverage unblocker or follow-up action.
```

## Drift From Scope

```text
Trigger:
- The implementation requires removing a visible feature to avoid fake functionality.

Handling:
- Report the original plan, what changed, why it changed, impact, and follow-up needed.
- Check whether acceptance criteria are still satisfied.
- Do not mark complete if the criteria are no longer satisfied.
```

## Missing Acceptance Criteria

```text
Trigger:
- Implementation reveals the source ticket has no testable acceptance criteria.

Handling:
- Stop before claiming completion.
- State that acceptance criteria are missing.
- Ask for criteria or escalate to Product Manager / Business Analyst.
- Do not guess the criteria.
```

## Dependency Blocker

```text
Trigger:
- Current implementation references schema, helper, migration, or configuration that does not exist.

Handling:
- Stop.
- Explain why continuing would require invented state or fake functionality.
- Suggest the prerequisite fix or ticket.
- Escalate sequencing to Technical Strategy Lead.
```

# Related Roles

- `02-roles/implementation-engineer.md`
- `02-roles/qa-tester.md`
- `02-roles/technical-strategy-lead.md`
- `02-roles/product-manager.md`
- `02-roles/business-analyst.md`
- `02-roles/strategic-product-director.md`

# Related Skills

- `03-skills/completion-reporting.md`
- `03-skills/acceptance-criteria.md`
- `03-skills/ticket-writing.md`

Future related skills may include:

- implementation review
- debugging support
- dependency management
- defect reporting
- smoke testing
- regression testing
- documentation update assessment
- risk assessment

# Related Workflows

- `05-workflows/ticket-to-implementation.md`

# Related Context

- `01-context/missing-context-behaviour.md`
- `01-context/project-loading-rules.md`
- `01-context/role-loading-rules.md`
- `01-context/context-loading-rules.md`

# Related Governance

- `00-system/ai-operating-principles.md`
- `06-governance/codex-working-rules.md`
- `06-governance/source-of-truth-rules.md`
- `06-governance/architecture-decisions.md`

# Deferred Items

Deferred because they belong in later files or require admin review:

- full completion report and blocker comment templates
- exact source-tracker comment format
- exact project-specific command lists, route names, paths, build tools, provider names, deployment targets, and environment variables
- standalone debugging-support skill
- standalone implementation-review skill
- standalone dependency-management skill
- standalone defect-reporting, smoke-testing, and regression-testing skills
- update-process governance and documentation timing labels
- global git, commit, push, and deploy procedure
- project-specific release/version handling

# Ambiguous Items For Admin Review

Admin review is needed for:

- whether this workflow should define a formal maximum number of failed attempts before stopping
- whether every project should provide a project-specific validation checklist consumed by this workflow
- whether source-tracker blocker comments should be mandatory when source-system access exists or left to project workflow
- whether documentation drift should block completion or only require a reported follow-up
- whether stuck-loop reports should become a reusable template

# What This Workflow Must Not Do

This workflow must not:

- create templates
- create skills
- create roles
- replace `05-workflows/ticket-to-implementation.md`
- replace `03-skills/completion-reporting.md`
- replace `01-context/missing-context-behaviour.md`
- own QA sign-off
- own product scope approval
- own architecture governance outside Technical Strategy Lead authority
- make project-specific commands global
- promote ResolvePM product doctrine into ResolveOS

---

# Source: 05-workflows/project-initiation.md

---
type: workflow
scope: global
owner: ResolveOS
version: 0.1
status: draft
source_project: ResolvePM
source_files:
  - migration/resolveos-architecture-review.md
  - migration/template-layer-review.md
  - migration/resolvepm-residual-audit.md
  - migration-review.md
related_roles:
  - 02-roles/product-manager.md
  - 02-roles/business-analyst.md
  - 02-roles/qa-tester.md
  - 02-roles/technical-strategy-lead.md
  - 02-roles/implementation-engineer.md
  - 02-roles/strategic-product-director.md
related_skills:
  - 03-skills/ticket-writing.md
  - 03-skills/acceptance-criteria.md
  - 03-skills/user-feedback-processing.md
  - 03-skills/completion-reporting.md
  - 03-skills/dependency-management.md
  - 03-skills/requirement-traceability.md
  - 03-skills/implementation-review.md
  - 03-skills/documentation-storage-architecture.md
related_templates:
  - 04-templates/briefing-template.md
  - 04-templates/chat-handoff-template.md
  - 04-templates/decision-log-template.md
  - 04-templates/role-prompt-template.md
  - 04-templates/ticket-context-template.md
related_context:
  - 01-context/running-context.md
  - 01-context/startup-context.md
  - 01-context/role-loading-rules.md
  - 01-context/project-loading-rules.md
  - 01-context/context-loading-rules.md
related_governance:
  - 06-governance/source-of-truth-rules.md
  - 06-governance/update-process.md
  - 06-governance/duplication-control.md
  - 06-governance/project-readiness.md
  - 06-governance/decision-maker-reporting.md
  - 06-governance/architecture-decisions.md
review_required: true
---

# Purpose

Define the canonical ResolveOS workflow for starting a new project, adopting an existing project, or continuing work on an existing project.

Project initiation is the governing ResolveOS workflow for new project initiation, existing project adoption, and existing project continuation.

`00-system/resolveos-entrypoint.md` is the canonical ResolveOS AI entrypoint.

Users should start from `README.md`. ResolveOS AI interactions should start from `00-system/resolveos-entrypoint.md`, which routes new project initiation, existing project adoption, and existing project continuation to this workflow when appropriate.

Project initiation determines the appropriate operating model, roles, chats, context, source-of-truth structure, setup requirements, known gaps, highest-leverage activity, and top recommended actions.

Project initiation should make ResolveOS value visible without exposing unnecessary internal framework complexity. It should show the project situation, what matters now, what is blocked, what team or specialist support is needed, and how to move forward.

Project initiation may be:

- new project initiation
- existing project adoption
- continue existing project

This workflow produces a Project Setup Report. It does not automatically create external systems, overwrite existing project state, create roles, create skills, create templates, create project files, or refactor existing repositories.

Source references:

- `01-context/project-loading-rules.md` > project repositories own project context
- `01-context/role-loading-rules.md` > role selection and role boundaries
- `01-context/running-context.md` > current-state and handoff discipline
- `06-governance/source-of-truth-rules.md` > ownership hierarchy
- `03-skills/documentation-storage-architecture.md` > storage architecture before writing to documentation and workspace tools
- `06-governance/update-process.md` > layer ownership and project artifact updates
- `06-governance/duplication-control.md` > avoid duplicate instruction stacks
- `migration/resolveos-architecture-review.md` > overall architecture and missing capabilities

# Trigger

Use this workflow when:

- a new project should start with ResolveOS support
- an existing project should adopt ResolveOS
- an existing project should continue under ResolveOS after a pause, handoff, chat change, stale context, or interrupted work
- a project needs an operating model before tickets, roles, or chats are created
- project source-of-truth systems are unclear
- project roles, chats, context files, or running context need initial assessment
- a project handoff needs structured setup before implementation starts
- multiple repositories, folders, trackers, databases, or implementations may exist and the canonical source must be identified
- tracker state, repository state, documentation, metadata, or implementation reality may disagree

Do not use this workflow to:

- implement project work
- rewrite an existing project
- create external systems automatically
- impose every ResolveOS role or chat on every project
- migrate project-specific doctrine into ResolveOS
- overwrite existing project state without explicit approval

# Inputs

For a new project, useful inputs include:

- project name
- project type
- objectives
- team structure
- preferred tooling
- constraints
- expected users, stakeholders, or review audiences
- expected delivery, research, validation, or operational cadence

For an existing project, useful inputs include:

- existing documentation
- existing tooling
- existing tickets
- existing team
- existing source-of-truth systems
- existing documentation and storage structure
- existing context files
- existing operating model
- existing roles, chats, prompts, workflows, templates, or handoff files
- current repository state where relevant
- current objective, active ticket, active batch, running context, or handoff state when continuing existing work
- current planning source, if one exists
- candidate canonical repository, implementation location, tracker, and documentation source
- known tracker, repository, documentation, metadata, database, or implementation inconsistencies
- known assumptions, validation evidence, confidence, or validation status where these affect readiness

If key inputs are missing, proceed with an explicit limitation only when the assessment can remain useful and read-only.

During setup, adoption, or continuation, ask or infer whether the user is working solo, with a team, with AI or automation support, or with a mix only when that changes the recommended team, handoff, or next action.

If unknown and not blocking, default to a light assumption:

```text
I will assume you are working solo for now unless you tell me otherwise.
```

# New Project Initiation

For a new project, identify what must be established before work begins.

Assess:

- project purpose and objectives
- project type and operating needs
- source systems needed
- project-owned context files needed
- initial running context
- recommended roles
- recommended chats
- recommended workflows and templates
- required tools and integrations
- recommended storage model for documentation, knowledge-base, workspace, repository, or project-management tools
- initial tickets, feedback capture, decision logs, or briefing needs
- constraints, risks, and gaps

Do not assume a new project needs every ResolveOS role, every chat, every workflow, every template, or every external tool.

# Existing Project Adoption

For an existing project, preserve current state first.

Assess:

- what already exists
- what source systems are authoritative
- what project context already governs work
- what roles or informal responsibilities already exist
- what chats, prompts, agents, or workflows are already in use
- what documentation is stale, missing, contradictory, or duplicated
- what ResolveOS can reference without replacing
- what should remain project-specific
- what requires admin approval before changing

Do not overwrite existing project structures.

Do not import project doctrine into ResolveOS.

Do not treat missing project documentation as permission to invent project facts.

# Continue Existing Project

For continuing an existing project, preserve current state before recommending action.

Use this mode when ResolveOS is already being applied to a project and the admin, agent, or chat needs to resume safely.

Assess:

- current objective
- highest-leverage activity
- top recommended actions
- current ticket, task, batch, or approved scope
- last completed item
- current running context or current-focus state
- active work, backlog, blockers, and risks
- latest handoff, completion report, blocker report, or decision log
- latest completion evidence
- latest decision evidence
- latest validation evidence
- source-system state
- repository state where relevant
- active role or role handoff
- active, pending, superseded, or rejected decisions
- open blockers, risks, dependencies, and decisions
- stale or missing context
- highest-leverage activity

When repository access exists, read the relevant project context and source-of-truth files before relying on chat memory.

Do not treat continuation as permission to overwrite existing operating structure.

Do not restart project initiation from scratch when current state can be loaded.

Do not continue implementation from memory when required current context, ticket scope, repository state, or validation evidence is missing.

# Discovery Questions

Ask only the questions needed for the project type and adoption state.

Core questions:

- Is this a new project, existing project adoption, or continue-existing-project situation?
- What is the project trying to achieve?
- What decisions, work, or outcomes does the project need to support?
- Who owns project decisions?
- What source systems already exist?
- What source systems are missing?
- Which source is canonical?
- What tools does the project already use?
- How are documentation and workspace tools structured today?
- What project constraints matter?
- What work is active now?
- What should not be changed?

New project questions:

- What should be true before the first ticket or delivery work starts?
- What initial project context should exist?
- What is the simplest useful operating model?
- Which roles are needed now, and which can wait?

Existing project questions:

- Which files, tickets, docs, chats, or systems are authoritative today?
- What is stale, duplicated, contradictory, or missing?
- Which existing processes should be preserved?
- What should ResolveOS reference rather than replace?
- Are there multiple repositories, folders, trackers, databases, or implementations that need reconciliation?
- Which repository, implementation location, tracker, and documentation source are authoritative?

Continue-existing-project questions:

- What was the last reliable current-state source?
- What is the current objective?
- What was the last completed item?
- What work is active now?
- What is next?
- What remains blocked, risky, unverified, or deferred?
- What is the latest completion evidence?
- What is the latest decision evidence?
- What assumptions remain unvalidated, partially validated, proven, or disproven?
- What role should continue the work?
- What context is stale or missing?
- What should not be repeated?

# Project Planning State

Project planning state answers:

- What are we trying to achieve?
- What are we doing now?
- What comes next?
- What is blocked?
- What risks matter?

Use these canonical planning concepts:

| Concept | Meaning |
| --- | --- |
| Objective | The current plain-English outcome the project is trying to achieve. |
| Highest-Leverage Activity | The single activity expected to create the greatest project progress, risk reduction, validation, learning, or delivery impact. |
| Top 3 Recommended Actions | The next three practical actions, prioritised by evidence and usefulness. |
| Active Work | Work currently approved, in progress, or being continued. |
| Backlog | Known future work that is not active now. |
| Blockers | Issues that prevent safe progress without more information, access, validation, prerequisite work, or a decision. |
| Risks | Uncertain conditions that may affect delivery, validation, cost, scope, architecture, quality, or source-of-truth integrity. |

Source-of-truth behaviour:

- If Jira, Notion, GitHub Issues, Azure DevOps, or another planning system is declared authoritative, use that system for planning state.
- If no planning system exists, support a lightweight project-owned planning model using the project's running context, current-focus file, plan, tracker, or equivalent source.
- Do not create a competing ResolveOS roadmap, backlog, or task-management system.
- Do not copy project-specific planning details into global ResolveOS files.
- When planning sources conflict, surface the conflict and the owner decision needed before recommending implementation.

The lightweight project-owned planning model should be enough to answer the four continuation questions above. It does not need to replicate external project-management tooling.

# Decision State

Use a lightweight decision lifecycle so project continuation can identify which decisions matter now.

Canonical decision states:

| State | Meaning |
| --- | --- |
| Proposed | A decision has been raised or recommended but is not yet accepted as governing work. |
| Active | The decision currently governs behaviour, scope, architecture, source ownership, validation, or project direction. |
| Superseded | The decision was previously active but has been replaced by a later decision. |
| Rejected | The decision was considered and explicitly not adopted. |

For ADRs that already use `Accepted`, treat `Accepted` as equivalent to `Active` unless a later ADR says otherwise.

Continuation should identify:

- active decisions that currently govern work
- proposed decisions that need review before safe progress
- superseded decisions that should not be followed as current guidance
- rejected decisions that should not be reintroduced without new evidence

Do not create extra decision bureaucracy. Use existing ADRs, project-owned decision records, source-system records, or the decision-log template where durable rationale needs to be preserved.

# Evidence And Validation State

Use lightweight validation concepts when readiness, continuation, product direction, commercial validation, or implementation validation depends on assumptions.

Core concepts:

| Concept | Meaning |
| --- | --- |
| Assumption | A claim, dependency, expected user behaviour, business rule, technical belief, or delivery condition that is not fully proven. |
| Evidence | A source-backed observation, test result, research finding, customer signal, repository state, completion report, validation report, or authoritative source-system record. |
| Confidence | The current strength of belief based on evidence: high, medium, low, or unknown. |
| Validation Status | The current validation state: proven, partially validated, unvalidated, or disproven. |

Validation statuses:

- Proven: strong evidence supports the claim for the current project context.
- Partially validated: some evidence supports the claim, but coverage, sample, environment, or scope is incomplete.
- Unvalidated: the claim is plausible but lacks reliable evidence.
- Disproven: evidence contradicts the claim or shows the expected result is false.

Use this model to improve readiness assessment and continuation. Do not turn ResolveOS into a research tracker. Project-specific research plans, analytics, test commands, customer records, and acceptance artifacts remain project-owned.

# Canonical Source Assessment

Determine the canonical project source before recommending implementation, validation, or cleanup work.

Explicitly identify:

- canonical repository
- canonical implementation location
- canonical tracker
- canonical documentation source
- canonical planning source
- canonical decision source
- canonical validation evidence source

Where multiple repositories, folders, databases, trackers, documents, or implementations exist, identify:

- which source appears authoritative
- which sources are stale, duplicate, incomplete, or contradictory
- which source requires admin or project-owner confirmation
- what inconsistencies affect the highest-leverage activity

Do not assume the nearest repository, loudest tracker, newest file, or most complete document is canonical.

Do not silently choose between conflicting sources when the choice affects project state, implementation, validation, or source-of-truth ownership.

# Readiness Assessment

Assess readiness independently.

Use `06-governance/project-readiness.md` for the detailed readiness rules.

Project initiation should report:

- Adoption Readiness
- Discovery Readiness
- Planning Readiness
- Implementation Readiness
- Validation Readiness

Being ready for one stage does not imply readiness for another.

For each readiness state, identify:

- ready / partially ready / blocked / unknown
- evidence
- blockers
- highest-leverage activity

Do not treat project adoption, planning, implementation, or validation readiness as interchangeable.

# Reconciliation Assessment

Check for inconsistencies between:

- tracker vs repository
- plan vs implementation
- metadata vs actual state
- repository vs external implementation
- documentation vs current source
- completion report vs repository reality
- decision record vs active project behaviour
- validation status vs available evidence

Surface differences explicitly.

Do not silently ignore mismatches between trackers, plans, reports, metadata, implementation status, and repository state.

If reconciliation affects source ownership, implementation safety, validation, or project direction, identify the decision owner or admin review needed.

# Continuation Evidence

Continuation requires evidence where possible.

Before implementation begins in continue-existing-project mode, identify:

- current objective
- highest-leverage activity
- top 3 recommended actions
- last completed work
- active work
- backlog, if relevant
- active blockers
- active risks
- latest completion evidence
- latest decision evidence
- latest validation evidence
- active, proposed, superseded, or rejected decisions
- latest running context

If evidence is missing, mark it as missing rather than relying on chat memory.

Do not continue implementation from an assumed state when required continuation evidence is unavailable.

# Operating Model Assessment

Recommend an operating model based on project needs.

Possible operating model elements:

- canonical source ownership
- project context ownership
- source-system ownership
- planning ownership
- decision ownership
- validation evidence ownership
- role usage
- chat/session structure
- ticket or task flow
- feedback flow
- decision logging
- running context or current focus
- readiness assessment
- reconciliation path
- completion and blocker reporting
- validation and review cadence
- update and duplication control

If a recommendation depends on project type, state the dependency.

If uncertain, recommend rather than assume.

# Role Assessment

Use `01-context/role-loading-rules.md` and the role files to recommend only the roles needed.

Use the user-facing label `Recommended Team`, not `AI Coverage`.

Recommended Team output should:

- show only roles or specialist support relevant to the current stage
- briefly explain why each visible role is needed
- say whether it is needed now or later
- explain how to action it
- say clearly when no additional specialist role is needed
- avoid giant all-role yes/no matrices in normal user output
- avoid asking the user to manage internal role files or workflows

Role recommendations are not the same as role loading. Recommend a visible team only when it helps the user understand next action, handoff, ownership, or specialist support.

Use clear user-facing labels when they communicate value better than internal role file names. Map them internally to existing ResolveOS roles, skills, or workflows:

| User-facing label | Internal ResolveOS source |
| --- | --- |
| Product Strategy Lead | Strategic Product Director role |
| Technical Strategy Lead | Technical Strategy Lead role |
| Implementation Engineer | Implementation Engineer role |
| QA / Validation Lead | QA Tester role |
| Business Analyst | Business Analyst role |
| Feedback Curator | User feedback processing skill and feedback-to-ticket workflow |

Do not create a new role when an exact internal role does not exist. Use the closest existing role, skill, or workflow only when its boundary fits, and make the mapping explicit when it matters.

Internal role selection guidance:

- Product Manager for product execution clarity, ticket readiness, scope, and feedback-to-work discipline.
- Business Analyst for requirements, assumptions, ambiguity, traceability, and business rules.
- QA Tester for validation, acceptance evidence, defects, and quality risk.
- Technical Strategy Lead for architecture, sequencing, dependency mapping, implementation governance, and prompt/context governance.
- Implementation Engineer for scoped implementation, debugging, checks, and completion reporting.
- Strategic Product Director for product direction, roadmap coherence, prioritisation, positioning, and whether something should exist.

Do not recommend every role by default.

Do not flatten specialist roles into generic project roles.

If a requested role does not exist, do not invent it. Recommend the closest existing role only when its boundary fits.

When a recommended role should act now, generate the specialist prompt or handoff immediately unless the user has asked not to. Use `04-templates/role-prompt-template.md` for role startup prompts and `04-templates/chat-handoff-template.md` for handoffs when session transfer is needed.

Recommended Team examples:

```text
Recommended Team for now:

- Product Strategy Lead - needed now because the value proposition and target user are still unclear.
  Next step: start a strategy chat using the prompt below.

No Implementation Engineer is needed yet because there is no approved implementation scope.
```

```text
No additional specialist role is needed right now. Continue in this chat with the current project setup.
```

# Chat Assessment

Recommend chats or sessions based on how the project should operate.

Possible chat/session types:

- project setup and governance chat
- strategy or direction chat
- product execution / ticket readiness chat
- requirements clarification chat
- technical planning / sequencing chat
- implementation chat
- QA / validation chat
- feedback triage chat
- handoff or review chat

Use role-specific chats only when they reduce confusion, preserve role boundaries, or make work easier to review.

Do not assume every project needs every chat.

Do not create overloaded multi-role chat stacks when a primary role plus supporting-role reference is enough.

When a chat becomes long, stale, interrupted, or needs migration, use `04-templates/chat-handoff-template.md`.

# Source Of Truth Assessment

Identify current and recommended source-of-truth systems.

Assess:

- product vision and strategy source
- roadmap source
- ticket/task source
- planning state source
- canonical repository
- canonical implementation location
- canonical tracker
- canonical documentation source
- project decisions source
- project architecture source
- domain terminology source
- feedback source
- validation and QA evidence source
- assumptions, confidence, and validation status source
- completion and blocker reporting source
- running context or current-focus source
- external tools and integrations
- documentation and storage architecture for source systems

If multiple candidates exist for any canonical source, record the inconsistency and the required confirmation.

Classify each source as:

- exists and is authoritative
- exists but stale
- exists but incomplete
- exists but contradictory
- missing
- not needed yet
- project-owned
- ResolveOS-owned

Project repositories own project-specific facts, decisions, commands, terminology, and context.

ResolveOS owns reusable operating behaviour.

For documentation and storage tools, also identify the existing hub, parent page, database, folder, repository path, ticket area, or document type that should receive routine project information. Do not recommend a new top-level page, file, folder, or database where an existing canonical structure should be used.

Recommended tool model:

- Notion: product context, strategy, decisions, risks, validation, feedback, and operating knowledge. Use hubs, child pages, and databases for repeatable records; avoid root-level clutter.
- Jira or Linear: execution tracking.
- GitHub: code, technical docs, implementation evidence, and repo-owned context.
- Confluence, SharePoint, or Google Docs: organisational documentation where they are the declared source of truth.

These are defaults. Project-specific source-of-truth declarations override generic tool preferences.

# Context Assessment

Identify what context should exist before work continues.

Recommended context may include:

- project overview or project context
- current focus or running context
- source-of-truth map
- role prompt references
- briefing for scattered or inaccessible context
- ticket context for active work
- decision logs for durable decisions
- chat handoff for session migration
- project-specific setup, commands, environment, or validation context

For new projects, recommend the smallest useful context set.

For existing projects, preserve and reference existing context before proposing new files.

Do not create context files as part of this workflow unless a separate approved task authorises file creation.

# Project Snapshot Guidance

Use a Project Snapshot when it adds orientation value.

A Project Snapshot is a compact user-facing view of the current project state.

Do not show a Project Snapshot on every message.

Project Snapshot must be shown when:

- a new conversation starts
- a stale conversation is resumed
- the user requests project status
- project readiness materially changes
- project objective materially changes
- project source-of-truth changes
- major risks or blockers materially change
- project adoption occurs
- project continuation requires reorientation

Project Snapshot should not be shown for:

- routine discussion
- tactical questions
- normal back-and-forth delivery conversations
- small clarification questions

Do not prepend a Project Snapshot to a full project initiation response.

Project initiation already performs project classification, readiness assessment, team assembly, context establishment, and recommendations. Adding a Project Snapshot before the full initiation output duplicates the same orientation and makes ResolveOS feel process-heavy.

A Project Snapshot should show:

```text
Project Detected:
- New Project / Existing Project / Continue Existing Project

Project Type:
- SaaS / Business Process / GitHub Project / Notion Project / Jira Project / Idea / Other

Current Readiness:
- Adoption / Discovery / Planning / Implementation / Validation

Current Objective:
- One plain-English sentence

Recommended Team:
- Recommended Team for now
- Only roles or specialist support that matter now.
- These may be real people, the user, specialist chats, AI assistants, AI agents, coding agents, engineers, consultants, or a mix.

Open Risks:
- Concise list

Open Decisions:
- Concise list, grouped as active or proposed when useful

Missing Information:
- Concise list

Highest-Leverage Activity:
- Single activity expected to create the greatest project progress, risk reduction, validation, learning, or delivery impact

Top 3 Recommended Actions:
- Prioritised, concrete, outcome-focused, practical, and time-bounded where possible
```

Keep the Project Snapshot user-facing and compact.

Use role names only as the visible recommended team. Do not require the user to choose roles, workflows, modes, or internal files.

If evidence is missing, show the missing information rather than delaying the whole response.

# Gap Analysis

Identify gaps without turning the workflow into implementation.

Gap categories:

- missing source system
- unclear canonical source
- unclear ownership
- tracker/repository mismatch
- plan/implementation mismatch
- metadata/actual-state mismatch
- repository/external-implementation mismatch
- missing readiness evidence
- missing continuation evidence
- missing project context
- stale context
- contradictory context
- missing role coverage
- over-broad or missing chat structure
- missing ticket/task flow
- missing feedback flow
- missing decision logging
- missing validation or QA evidence path
- missing update process
- duplicate or drifting guidance
- missing tools or integrations
- project-specific constraints not yet captured

For each gap, state:

- what is missing
- why it matters
- who should own it
- whether it blocks work
- the highest-leverage follow-up action

# Steps

## 1. Identify Project Mode

Classify the project as:

- new project initiation
- existing project adoption
- continue existing project
- unclear

If unclear, ask for the minimum clarification needed.

## 2. Orient The User When Orientation Adds Value

Use the Project Snapshot guidance when a snapshot trigger applies.

Do not automatically prepend a Project Snapshot to every first response or to a full Project Setup Report.

The user should not need to ask for project classification, readiness assessment, role selection, source-state assessment, risks, decisions, missing information, highest-leverage activity, or recommended actions when those items are needed for orientation.

## 3. Gather Project Inputs

Gather the smallest useful set of project inputs.

Use existing project files and source systems before asking the admin to restate context.

## 4. Identify Source Systems

List existing, missing, stale, contradictory, and not-yet-needed source systems.

Do not create or configure external tools automatically.

When recommending tools such as Notion, GitHub, Jira, Linear, SharePoint, Confluence, or Google Docs, also identify how they should be used well: source owner, parent structure, storage type, and whether routine records belong in existing pages, databases, tickets, comments, folders, or files.

## 5. Identify Canonical Sources

Identify the canonical repository, implementation location, tracker, and documentation source.

Where multiple candidates exist, report the inconsistency and the decision needed.

## 6. Assess Readiness

Assess adoption, discovery, planning, implementation, and validation readiness independently.

Do not allow one readiness state to imply another.

For each material readiness gap, state whether it blocks progress now, the smallest mitigation, and the next action. Do not dump a "not ready" finding on the user without a path forward.

## 7. Reconcile Source State

Compare tracker, repository, plan, metadata, external implementation, completion, and decision evidence where relevant.

Surface mismatches explicitly.

## 8. Assess Continuation Evidence

For continuing existing work, identify current objective, last completed work, active work, blockers, latest completion evidence, latest decision evidence, and latest running context.

If continuation evidence is missing, report the gap before implementation starts.

## 9. Assess Operating Model

Recommend the simplest useful operating model for the project.

Avoid heavy process where a smaller model is enough.

## 10. Assess Roles

Recommend the user-facing Recommended Team for now.

State why each role is needed.

State which roles are not needed yet when useful.

If no additional specialist role is needed, say so clearly.

If a role should act now, generate the prompt or handoff needed to action it.

## 11. Assess Chats

Recommend chat/session structure.

Keep chats role-aware and context-aware.

Avoid overloaded chats.

## 12. Assess Context

Recommend required project context, running context, briefings, ticket context, decision logs, and handoff needs.

For existing projects, identify what should be preserved.

## 13. Identify Gaps And Risks

List known gaps, blockers, risks, and uncertainty.

Do not hide missing source systems or stale context.

For each material gap or risk, include whether it blocks now, the smallest mitigation, who or what should handle it, and the next action.

## 14. Produce Project Setup Report

Produce a Project Setup Report using the output structure in this workflow.

Do not implement setup unless a separate approved task authorises implementation.

## 15. Recommend Highest-Leverage Activity And Top Actions

Recommend the single activity expected to create the greatest project progress, risk reduction, validation, learning, or delivery impact.

Also provide the Top 3 Recommended Actions when useful.

Each recommended action should be:

- concrete
- outcome-focused
- prioritised
- practical
- time-bounded where possible

The goal is maximum useful progress, not minimum effort.

Use Highest-Leverage Activity only when it is genuinely meaningful. It should be part of a practical plan forward, not a label applied to every response.

If the highest-leverage activity or a recommended action requires project-specific files, source systems, external tools, or integrations, state that it requires approval.

# Project Setup Report

The workflow output should include:

```text
Project:
- [Name]

Project mode:
- New project initiation / Existing project adoption / Continue existing project / Unclear

Project type:
- [Type, if known]

Project Snapshot:
- Project Detected:
- Project Type:
- Current Readiness:
- Current Objective:
- Recommended Team:
- Open Risks:
- Open Decisions:
- Missing Information:
- Highest-Leverage Activity:
- Top 3 Recommended Actions:

Objective:
- [Plain-English objective]

Recommended operating model:
-

Recommended Team for now:
-

Recommended chats:
-

Recommended context files:
-

Recommended source systems:
-

Canonical source assessment:
-

Readiness assessment:
- Adoption Readiness:
- Discovery Readiness:
- Planning Readiness:
- Implementation Readiness:
- Validation Readiness:

Reconciliation assessment:
-

Recommended integrations or tools:
-

Initial running context:
-

Continuation state:
-

Planning state:
- Objective:
- Highest-leverage activity:
- Top 3 recommended actions:
- Active work:
- Backlog:
- Blockers:
- Risks:

Continuation evidence:
- Current objective:
- Highest-leverage activity:
- Top 3 recommended actions:
- Last completed work:
- Active work:
- Backlog:
- Active blockers:
- Active risks:
- Latest completion evidence:
- Latest decision evidence:
- Latest validation evidence:
- Decisions by state:
  - Active:
  - Proposed:
  - Superseded:
  - Rejected:
- Assumptions and validation state:
- Latest running context:

Source-of-truth behaviour:
- Planning source:
- Decision source:
- Validation evidence source:
- Conflicts or missing sources:

Known gaps:
- [For each material gap: whether it blocks now, smallest mitigation, next action.]

Active risks:
- [For each material risk: whether it blocks now, smallest mitigation, next action.]

Blockers:
- [For each blocker: smallest unblocker, owner or role, next action.]

Project-specific items to preserve:
-

Items not recommended yet:
-

Next actions:
-

Specialist prompts or handoffs needed now:
-
```

# Running Context Establishment

Project initiation should establish the current-state layer.

For a ResolveOS-level project setup, use `01-context/running-context.md`.

For a project repository, recommend a project-owned current-focus or running-context file only when useful for that project's operating model.

Initial running context should capture:

- current phase
- current state
- objective
- highest-leverage activity
- top recommended actions
- active work
- backlog, if relevant
- open decisions
- active risks
- blockers
- assumptions and validation state where relevant
- current recommendations
- source-of-truth references
- what should not be repeated

For continue-existing-project mode, running context should also identify:

- last reliable current-state source
- what was just completed
- what is still active
- what comes next
- what remains blocked or unverified
- highest-leverage activity
- latest completion evidence
- latest decision evidence
- latest validation evidence
- active, proposed, superseded, and rejected decisions where relevant
- readiness state where relevant

Running context must remain current state only.

Do not turn running context into:

- chat history
- project history
- ticket history
- decision log
- changelog
- full project documentation

# Recommendations

Recommendations should be practical, minimal, and project-specific.

For each recommendation, state:

- what is recommended
- why it is recommended
- whether it is required now or can wait
- which role or source owner should review it
- what source evidence supports it

Do not recommend files, tools, roles, chats, or integrations without evidence.

# Outputs

This workflow may produce:

- Project Setup Report
- canonical source assessment
- readiness assessment
- reconciliation assessment
- continuation evidence summary
- recommended operating model
- recommended roles
- recommended chats
- recommended context files
- recommended source systems
- recommended tools or integrations
- known gaps
- blockers
- highest-leverage activity and top recommended actions
- admin-review questions

# Review Points

Admin review is required before:

- overwriting existing project state
- creating or changing external source systems
- creating project files
- adopting project-specific tooling
- promoting project-specific doctrine into ResolveOS
- changing role authority
- treating an existing project source as superseded

# Failure Modes

Failure modes include:

- assuming new project setup rules apply to an existing project
- overwriting existing state
- inventing missing project facts
- recommending every role or chat by default
- globalising project-specific doctrine
- creating external tools without approval
- treating missing source systems as if they exist
- treating tracker state as repository reality without checking
- treating planning readiness as implementation readiness
- treating implementation existence as validation readiness
- turning initiation into implementation
- restarting existing work from scratch when source-backed continuation context exists

# Anti-Patterns

Do not:

- overwrite existing project state without explicit approval
- automatically create external systems
- assume every project needs every role
- assume every project needs every chat
- create an alternative ResolveOS AI entrypoint
- create a duplicate project-initiation workflow
- treat readiness as a single state
- silently ignore tracker/repository, plan/implementation, metadata/state, or repository/external-implementation mismatches
- continue implementation without available continuation evidence
- use ResolvePM product doctrine as a global project-initiation model
- make project-specific commands, tools, ticket keys, provider names, deployment targets, or roadmap terms global
- invent project facts from memory
- flatten specialist roles into generic project roles
- create context files, tickets, templates, roles, skills, or workflows from this workflow
- turn the Project Setup Report into implementation approval

# Notes

Deferred because they belong elsewhere:

- project-specific setup files belong in project repositories
- external source-system creation belongs in approved project setup work
- detailed source-tracker handoff belongs in a future template, workflow, or project-owned process
- project-specific role prompt files belong in project repositories or generated prompts

Ambiguous items for admin review:

- whether every project should have a local project-initiation report
- whether every project should have a local running-context file or current-focus file
- whether project initiation should later have a companion template
- whether tool recommendations should be standardised by project type

# Related Roles

- `02-roles/product-manager.md`
- `02-roles/business-analyst.md`
- `02-roles/qa-tester.md`
- `02-roles/technical-strategy-lead.md`
- `02-roles/implementation-engineer.md`
- `02-roles/strategic-product-director.md`

# Related Skills

- `03-skills/ticket-writing.md`
- `03-skills/acceptance-criteria.md`
- `03-skills/user-feedback-processing.md`
- `03-skills/completion-reporting.md`
- `03-skills/dependency-management.md`
- `03-skills/requirement-traceability.md`
- `03-skills/implementation-review.md`

# Related Templates

- `04-templates/briefing-template.md`
- `04-templates/chat-handoff-template.md`
- `04-templates/decision-log-template.md`
- `04-templates/role-prompt-template.md`
- `04-templates/ticket-context-template.md`

# Related Context

- `01-context/running-context.md`
- `01-context/startup-context.md`
- `01-context/role-loading-rules.md`
- `01-context/project-loading-rules.md`
- `01-context/context-loading-rules.md`

# Related Governance

- `06-governance/source-of-truth-rules.md`
- `06-governance/update-process.md`
- `06-governance/duplication-control.md`
- `06-governance/project-readiness.md`
- `06-governance/decision-maker-reporting.md`
- `06-governance/architecture-decisions.md`

# What This Workflow Must Not Do

This workflow must not:

- create templates
- create skills
- create roles
- create external systems
- create project files without approval
- overwrite existing project state
- replace project-loading rules
- replace role-loading rules
- replace source-of-truth governance
- approve implementation work
- promote project-specific doctrine into ResolveOS

---

# Source: 05-workflows/ticket-to-implementation.md

---
type: workflow
scope: global
owner: ResolveOS
version: 0.1
status: draft
source_project: ResolvePM
source_files:
  - migration-review.md
  - migration/resolvepm-extraction-map.md
  - migration/resolvepm-extraction-audit.md
  - AGENTS.md.backup
  - docs/project-context/implementation-workflow.md
  - docs/ai-role-prompts/implementation-engineer-prompt.md
  - docs/ai-role-prompts/technical-strategy-lead-prompt.md
  - docs/codex-briefings/
related_roles:
  - 02-roles/product-manager.md
  - 02-roles/business-analyst.md
  - 02-roles/qa-tester.md
  - 02-roles/technical-strategy-lead.md
  - 02-roles/implementation-engineer.md
  - 02-roles/strategic-product-director.md
related_skills:
  - 03-skills/ticket-writing.md
  - 03-skills/acceptance-criteria.md
  - 03-skills/completion-reporting.md
related_context:
  - 01-context/context-loading-rules.md
  - 01-context/startup-context.md
  - 01-context/role-loading-rules.md
  - 01-context/project-loading-rules.md
  - 01-context/missing-context-behaviour.md
related_governance:
  - 00-system/ai-operating-principles.md
  - 06-governance/codex-working-rules.md
  - 06-governance/source-of-truth-rules.md
  - 06-governance/extraction-migration-guardrails.md
  - 06-governance/architecture-decisions.md
review_required: true
---

# Purpose

Define the canonical ResolveOS workflow for moving from an approved ticket, task, source item, or approved batch into implementation execution.

This workflow owns the sequence from approved scope to implementation execution. It is not a role, skill, template, backlog process, QA sign-off process, or implementation-review loop.

The workflow preserves ResolvePM's operational discipline: current ticket first, one ticket or approved batch at a time, small safe changes, review before implementation, no future-ticket implementation, no fake functionality, explicit blocker handling, validation evidence, documentation-drift awareness, and completion honesty.

# Trigger

Use this workflow when implementation has been approved for a specific ticket, task, source item, or batch.

Use it before:

- implementing a ticket
- starting a scoped code change
- continuing a ticket sequence
- acting from an approved epic briefing with child tickets available
- resolving an implementation blocker when the blocker resolution is approved scope
- producing a ticket implementation completion report

Do not use this workflow when the admin asks only for planning, audit, review, extraction, classification, strategy, ticket drafting, template creation, or role/skill design.

Do not start implementation from an epic alone when child implementation tickets are missing.

# Inputs

Use the smallest relevant context needed for the scoped implementation.

Required or useful inputs include:

- admin instruction
- active project repository
- approved ticket, task, source item, or approved batch
- ticket title, goal, scope, acceptance criteria, implementation notes, comments, and manual test steps
- current focus
- relevant briefing or epic context
- project context and project-specific verification commands
- relevant ResolveOS roles
- relevant ResolveOS skills
- existing codebase patterns and current repository state
- previous ticket outcome when working through a sequence
- known assumptions, dependencies, prerequisites, blockers, non-goals, and follow-up notes

If source-system access is unavailable, use approved briefing or pasted ticket context only when that fallback is explicitly available, and state the limitation.

# Workflow Principles

## Current Ticket First

Current ticket first.

Work only on the current ticket, task, source item, or approved batch.

Do not start future tickets unless explicitly asked.

Do not re-do the previous ticket. Use previous-ticket checks only to identify incomplete work, uncommitted changes, changed file structure, new assumptions, or prompt adjustments needed for the current ticket.

## One Ticket Or Approved Batch At A Time

Work one ticket, task, or approved batch at a time.

If useful extra work is noticed, do not implement it automatically. Report it as suggested follow-up work and explain why it should be separate.

## Small Safe Changes

Small safe tickets beat large rewrites.

Prefer:

- small changes
- clear scope
- reversible implementation
- explicit sequencing
- existing project patterns

Avoid:

- massive implementation tickets
- unclear scope
- speculative implementation
- unrelated refactors
- future-scope bundling

## Real State Over Fake State

Empty state is better than fake state.

Do not create fake buttons, fake integrations, fake operational data, fake AI outputs, fake dashboards, fake metrics, fake links, fake filters, fake success states, fake generated summaries, fake workflow behaviour, invented schema, or pretend features.

Every visible feature must either actually work, be clearly marked as not yet implemented, or not be shown.

## Evidence Before Completion

Do not claim implementation is complete unless the scoped work was completed and required checks, validation, or acceptance evidence support that status.

Do not pretend code was committed, pushed, deployed, tested, or source tickets updated unless that happened.

# Required Context

Before implementation begins, load or verify:

1. ResolveOS file, metadata, migration, source-of-truth, and Codex governance needed for the task.
2. ResolveOS context-loading, role-loading, project-loading, and missing-context rules.
3. The primary role for the work, normally Implementation Engineer.
4. Supporting role files only when the boundary materially affects the work.
5. Ticket-writing, acceptance-criteria, and completion-reporting skills when relevant.
6. Active project repository and project-owned context.
7. Current focus, briefing, ticket, comments, and accepted scope where relevant.
8. Current repository state and existing implementation patterns.
9. Project-specific checks or validation expectations, when available.

If required context is missing, stale, contradictory, or inaccessible, follow `01-context/missing-context-behaviour.md`.

Do not proceed from memory when required context files, ticket scope, acceptance criteria, source comments, project context, or repository state are needed for safe implementation.

# Role Responsibilities

Roles participate in this workflow. The workflow does not redefine their authority.

Product Manager:

- clarifies product scope, acceptance intent, and product-side blockers
- may make low-risk scope clarification decisions within approved objectives
- remains accountable for product scope alignment when implementation findings affect product outcome

Business Analyst:

- clarifies requirements, assumptions, business rules, traceability, and ambiguity
- helps keep requirements testable and aligned with tickets
- does not approve product scope or perform QA sign-off

QA Tester:

- verifies acceptance evidence, validation readiness, defects, regression risk, and quality-gate concerns
- may create defect tickets when evidence supports them
- does not approve product scope or own implementation execution

Technical Strategy Lead:

- owns technical sequencing, dependency mapping, architecture governance, delivery orchestration, and implementation-governance escalation
- may require prerequisite work before dependent implementation continues
- may create technical tickets without product approval authority

Implementation Engineer:

- executes scoped implementation work
- inspects existing code patterns
- makes small safe changes
- runs available checks
- reports blockers, implementation drift, validation evidence, and follow-up recommendations
- may propose tickets but should not independently create new work

Strategic Product Director:

- handles roadmap coherence, prioritisation, positioning, and whether something should exist
- should be escalated to when implementation reveals product strategy drift

# Steps

## 1. Confirm Scope

Confirm the current ticket, task, source item, or approved batch.

Identify:

- title or identifier, if one exists
- goal
- scope
- acceptance criteria
- implementation notes
- comments or blocker notes
- manual test steps
- non-goals
- dependencies and prerequisites

If acceptance criteria are missing, do not guess them.

## 2. Confirm Project And Source Of Truth

Confirm the active project repository and source-of-truth context for this implementation.

Use project-owned context for:

- product terms
- repository markers
- local commands
- routes
- schema names
- environment variables
- provider configuration
- deployment process
- ticket keys and source-system details

Do not make project-specific commands or terminology global ResolveOS rules.

## 3. Load Role And Project Context

Load the primary implementation role and only the supporting roles needed for the scope.

Avoid large multi-role prompt stacks.

Prefer persistent role, project, briefing, and ticket context over repeated long prompts.

## 4. Check Previous Work When Sequenced

When working through a ticket sequence, inspect the previous ticket outcome and current repository state where practical.

Use this only to identify:

- incomplete work
- uncommitted or unreviewed changes
- changed file structure
- new assumptions
- dependency risk
- prompt or context adjustments needed for the current ticket

If the previous ticket appears incomplete, blocked, inconsistent, or unsafe for the next ticket, stop and explain before coding.

## 5. Identify Dependencies And Blockers

Before editing, identify prerequisites, dependencies, blockers, missing schema, architecture gaps, source-of-truth conflicts, configuration gaps, security constraints, and paid API risks.

Do not retry a blocked dependent ticket until the prerequisite is complete enough for safe implementation.

If a required helper, schema field, configuration, credential, architecture decision, or source context is missing, treat it as a blocker rather than inventing around it.

## 6. Confirm Implementation Approach

Summarise the implementation approach in plain English when the workflow or task calls for it.

The approach should identify:

- what the ticket is trying to achieve
- why it matters, when useful for review
- the likely implementation path
- important assumptions
- important dependencies or blockers

Keep the plan short and tied to the actual repository structure.

## 7. Execute Scoped Implementation

Implement only the current approved scope.

Use existing project patterns before inventing new ones.

Keep changes as small as practical.

Avoid unrelated refactors, speculative architecture, hidden scope expansion, future-ticket implementation, and fake functionality.

If implementation reality shows the ticket cannot be completed safely as written, stop and use blocker handling instead of forcing completion.

## 8. Validate

Run the project-specific checks, tests, builds, linting, manual validation, or review steps that apply to the scoped change.

If a check fails:

- fix it if the failure is related to the scoped work and can be fixed safely
- if unrelated or blocked, document it clearly
- do not hide the failure

Do not claim completion if required build, lint, test, validation, or acceptance criteria fail.

## 9. Check Documentation Alignment

Check whether implementation revealed information that affects persistent context or future work.

Report suggested documentation updates when implementation changes or reveals:

- schema or data-model constraints
- setup or configuration requirements
- delivery sequencing
- implementation constraints
- architecture decisions
- blocker status
- future-ticket assumptions
- briefing or current-focus context

Do not create update-process governance inside this workflow.

## 10. Report Outcome

Use `03-skills/completion-reporting.md` to report the outcome as complete, partial, blocked, failed, or not verified.

Report follow-up work separately from completed scope.

# Blocker Handling

If blocked:

- stop
- explain the blocker clearly
- explain why continuing would be unsafe or unsupported
- state what information, credential, config, source file, prerequisite, or admin decision is needed
- suggest the highest-leverage unblocker or follow-up action
- suggest a prerequisite or follow-up ticket when needed

Do not silently work around blockers.

Do not work around security, architecture, source-of-truth, schema, dependency, configuration, paid API, or acceptance-criteria requirements just to continue.

Do not keep making random changes after repeated failure.

Do not silently leave work in a failed state.

# Dependency Handling

Dependencies must be explicit before implementation is treated as complete.

When a ticket depends on prerequisite work:

- confirm the prerequisite state where practical
- flag build, deployment, or runtime risk if dependent code references missing types, schema fields, helpers, migrations, configuration, or source context
- stop further implementation when branch, build, dependency, or source-of-truth state is unsafe
- escalate sequencing, architecture, or prerequisite-ticket decisions to Technical Strategy Lead

Project-specific git, branch, deploy, migration, and source-system requirements stay in project context.

# Validation

Validation should prove the current approved scope, not adjacent future work.

Validation may include:

- automated checks
- build or lint commands
- tests
- manual test steps
- acceptance criteria review
- defect reproduction or retest
- visual or workflow inspection
- source-of-truth verification

Project verification commands remain project-specific.

For manual validation, explain:

- what to run, open, click, type, inspect, or trigger
- what should happen
- what confirms success
- what was not verified

# Completion Reporting

Completion reporting must preserve implementation honesty.

A workflow completion report should identify:

- status
- ticket, task, source item, or approved batch
- what was achieved
- implementation path
- whether the implementation differed from the original plan
- files changed
- checks or validation run
- checks or validation not run
- manual test steps where useful
- expected result
- actual result or current state
- known issues
- blocker notes
- suggested follow-up tickets
- suggested documentation updates
- commit, deployment, or source-system update status if relevant

Do not claim commit, push, deployment, source-ticket update, or admin approval unless there is direct evidence.

# Outputs

This workflow may produce:

- scoped implementation
- implementation notes
- validation evidence
- blocker report
- dependency or prerequisite report
- implementation drift report
- completion report
- suggested follow-up ticket
- suggested documentation update
- admin-review question

Outputs should be direct, practical, traceable, and explicit about blockers, assumptions, uncertainty, and deferred work.

# Anti-Patterns

Do not:

- implement without an approved ticket, task, source item, or approved batch
- start implementation from an epic alone when child tickets are missing
- start future tickets unless explicitly asked
- add unrelated features
- silently expand scope
- perform broad rewrites unless required by the approved scope
- invent requirements or acceptance criteria
- invent schema fields, integrations, data, success states, or workflow behaviour
- create fake buttons, fake integrations, fake operational data, fake AI outputs, fake dashboards, fake metrics, fake links, fake filters, or fake success states
- hide blockers, dependency gaps, stale context, contradictory context, or failed checks
- silently work around security, architecture, source-of-truth, configuration, paid API, or prerequisite requirements
- keep making random changes after repeated failure
- claim completion without checks or evidence
- claim commit, push, deployment, source-system update, or ticket completion without direct evidence
- let documentation drift from implementation reality without flagging it

# Examples

## Ready Ticket

```text
Input:
- Approved ticket with goal, scope, acceptance criteria, implementation notes, and manual validation steps.

Handling:
- Load relevant role, project, briefing, and ticket context.
- Confirm dependencies and current repository state.
- Implement only the ticket scope.
- Validate with project-specific checks.
- Report completion, checks, known issues, follow-ups, and documentation update needs.
```

## Missing Acceptance Criteria

```text
Input:
- Ticket title and rough goal only.

Handling:
- Stop before implementation.
- Explain that acceptance criteria are missing.
- Ask for the criteria or produce only a clearly marked draft for review if the admin requests ticket refinement.
```

## Missing Prerequisite

```text
Input:
- Current ticket depends on helper, schema, configuration, or prior work that is not available.

Handling:
- Stop.
- Explain the prerequisite blocker.
- Explain why implementation would require fake state or unsupported assumptions.
- Suggest the smallest prerequisite fix or prerequisite ticket.
```

## Implementation Drift

```text
Input:
- Approved ticket expects one implementation path, but repository reality requires a different safe path.

Handling:
- Explain the original plan, what changed, why it changed, impact on acceptance criteria, and follow-up needed.
- Do not mark complete if acceptance criteria are no longer satisfied.
```

# Related Roles

- `02-roles/product-manager.md`
- `02-roles/business-analyst.md`
- `02-roles/qa-tester.md`
- `02-roles/technical-strategy-lead.md`
- `02-roles/implementation-engineer.md`
- `02-roles/strategic-product-director.md`

# Related Skills

- `03-skills/ticket-writing.md`
- `03-skills/acceptance-criteria.md`
- `03-skills/completion-reporting.md`

Future related skills may include:

- implementation review
- dependency management
- backlog refinement
- risk assessment
- debugging support
- defect reporting
- documentation update assessment
- AI workflow design

# Related Context

- `01-context/context-loading-rules.md`
- `01-context/startup-context.md`
- `01-context/role-loading-rules.md`
- `01-context/project-loading-rules.md`
- `01-context/missing-context-behaviour.md`

# Related Governance

- `00-system/ai-operating-principles.md`
- `06-governance/codex-working-rules.md`
- `06-governance/source-of-truth-rules.md`
- `06-governance/extraction-migration-guardrails.md`
- `06-governance/architecture-decisions.md`

# Deferred Items

Deferred because they belong in later files or require admin review:

- detailed implementation-review-loop behaviour for repeated failures, review cycles, stuck work, and post-implementation review
- full completion report, blocker comment, and per-ticket prompt templates
- project-specific ticket keys, CP sequences, release names, roadmap themes, routes, local paths, schema names, deployment URLs, provider names, environment variables, and verification commands
- exact git branch, commit, push, and deploy procedure beyond global honesty and project-owned command reporting
- documentation update timing labels and durable update governance
- dependency-management skill details beyond workflow-level dependency visibility
- backlog-refinement skill details for splitting large work before implementation
- AI workflow design details beyond cost-safe blocker and no-fake-output rules

# Ambiguous Items For Admin Review

Admin review is needed for:

- whether approved batch mode should be allowed beyond tightly scoped migration batches
- whether previous-ticket inspection is mandatory for every implementation or only sequenced ticket work
- whether branch and commit-order rules should become global governance, project context, or a future dependency-management skill
- whether this workflow applies to every ResolveOS-enabled implementation agent or only Codex-style implementation sessions
- whether approved briefing files should always be accepted as fallback scope when the source ticket system is unavailable

# What This Workflow Must Not Do

This workflow must not:

- redefine role authority
- create ticket templates
- create completion report templates
- create new skills
- create new roles
- approve product scope
- own QA sign-off
- own architecture decisions outside Technical Strategy Lead authority
- make project-specific commands global
- promote ResolvePM product doctrine into ResolveOS

---

# Source: 05-workflows/user-guide.md

---
type: workflow
scope: global
owner: ResolveOS
version: 0.1
status: draft
related_context:
  - 01-context/context-loading-rules.md
  - 01-context/project-loading-rules.md
  - 01-context/running-context.md
related_workflows:
  - 05-workflows/project-initiation.md
related_governance:
  - 06-governance/source-of-truth-rules.md
  - 06-governance/update-process.md
  - 06-governance/duplication-control.md
  - 06-governance/architecture-decisions.md
review_required: true
---

# Purpose

Provide the user-facing ResolveOS onboarding guide.

This guide explains how a user should start using ResolveOS without needing to understand roles, workflows, modes, architecture decisions, governance, repository structure, or implementation details.

ResolveOS should determine the right operating approach automatically from the user's project, available sources, and current goal.

ResolveOS should make project progress easier. When it identifies a role, risk, blocker, missing context item, readiness gap, or setup issue, it should also make clear whether it matters now and what practical step resolves it.

# Trigger

Use this guide when:

- a user is trying ResolveOS for the first time
- a tester receives a ChatGPT Project containing ResolveOS knowledge bundles
- a new project needs help getting started
- an existing project needs to adopt ResolveOS
- a partially complete project needs to continue without losing context
- a user is unsure what information to provide first

# Inputs

Users can start with any useful project material.

Useful inputs include:

- a rough idea
- a product or business goal
- a GitHub repository
- a Notion workspace or page
- a Jira project, board, or ticket
- existing documentation
- current tasks or priorities
- screenshots or notes
- an existing business process
- a partially complete project
- a description of what is confusing, blocked, or unfinished

The user does not need to prepare a perfect brief before starting.

If a project already uses Jira, Notion, GitHub Issues, Azure DevOps, or another planning source, ResolveOS should use that source. If no planning source exists, ResolveOS can work from a lightweight project-owned current-focus, running-context, plan, or equivalent note.

If a project already uses Notion, Confluence, SharePoint, Google Docs, GitHub, Jira, Linear, local folders, or another documentation or storage tool, ResolveOS should store information into the right existing structure where possible. It should avoid random top-level pages, documents, files, folders, or databases.

# Steps

## 1. Understand What ResolveOS Does

ResolveOS helps users turn ideas, existing projects, scattered notes, repositories, docs, tasks, and blockers into a clear project operating model.

It should help answer:

- what the project is trying to achieve
- what state the project is in
- what context is reliable
- what is missing
- what is blocked
- what risks matter now
- which team roles or specialist support are needed now
- what practical action should happen next
- whether the project is ready for planning, implementation, or validation
- what should be handed to an engineer, AI agent, specialist chat, consultant, or team member

ResolveOS should not only report project state. It should provide the practical path forward.

## 2. Get The Most Out Of ResolveOS

Users get the most value when they provide real project context.

Encourage users to:

- describe the goal or current problem in plain English
- say whether they are working solo, with a team, with AI or automation support, or with a mix
- provide source-of-truth links or pasted context where possible
- share current tasks, blockers, decisions, risks, feedback, validation notes, or handoffs
- ask for the project state, blocked items, Recommended Team, practical plan, readiness, or implementation handoff
- restart stale chats by asking for a Project Snapshot or continuation assessment
- ask ResolveOS to save, document, or preserve useful output without needing to design the storage structure first

If the user does not know the source of truth, ResolveOS should help identify it.

If the user does not know which role, workflow, or setup is needed, ResolveOS should infer the useful next step and ask only for the smallest missing input when needed.

When the user asks ResolveOS to save feedback, capture notes, put something in Notion, or create documentation from a conversation, ResolveOS should identify the information type, source owner, parent location, and storage type before writing. If the destination can be inferred safely, it should proceed with a labelled assumption and report where it stored the information and why.

## 3. Start With Plain English

The user should describe what they want ResolveOS to help with.

Examples:

```text
I have a SaaS startup idea for helping small agencies manage client approvals. Help me turn it into a workable project.
```

```text
Here is my GitHub repository. Help me understand what state the project is in and what to do next.
```

```text
I have a Notion workspace with product notes, user feedback, and roadmap ideas. Help me organise it into a project operating system.
```

```text
I have a Jira project that has become messy. Help me identify what is active, stale, blocked, or missing.
```

```text
This is an existing business process for onboarding clients. Help me document it, find gaps, and turn improvements into work.
```

```text
This project is partially complete. Help me figure out what was done, what is still active, and the safest next step.
```

## 4. Let ResolveOS Choose The Approach

Users do not need to choose internal operating details.

Users do NOT need to:

- choose roles
- choose workflows
- choose modes
- understand internal architecture
- understand ADRs
- understand governance
- understand repository structure
- know which ResolveOS file applies

ResolveOS should infer the right approach from the project situation.

It should decide whether the project needs:

- new project initiation
- existing project adoption
- continuation of existing work
- source-of-truth clarification
- requirements clarification
- planning
- implementation support
- validation support
- feedback processing
- blocker review

If ResolveOS cannot safely decide, it should ask a small number of plain-English questions.

## 5. Expect A Project Snapshot When It Helps

ResolveOS should show a compact Project Snapshot when orientation adds value.

The user should not need to ask for classification, readiness, team selection, risks, decisions, missing information, highest-leverage activity, or recommended actions when those items are needed to understand the project state.

A Project Snapshot is useful when:

- a new conversation starts
- a stale conversation is resumed
- the user asks for project status
- project readiness, objective, source of truth, risks, or blockers materially change
- ResolveOS is adopting an existing project
- continuation requires reorientation

ResolveOS should not show a Project Snapshot for routine discussion, tactical questions, normal delivery back-and-forth, or small clarification questions.

ResolveOS should not prepend a Project Snapshot to a full project initiation response because project initiation already includes classification, readiness, team, context, and recommendations.

When shown, the Project Snapshot should present:

```text
Project Detected:
- New Project / Existing Project / Continue Existing Project

Project Type:
- SaaS / Business Process / GitHub Project / Notion Project / Jira Project / Idea / Other

Current Readiness:
- Adoption / Discovery / Planning / Implementation / Validation

Current Objective:
- One plain-English sentence

Recommended Team:
- Recommended Team for now
- Only roles or specialist support that matter now.
- These may be real people, the user, specialist chats, AI assistants, AI agents, coding agents, engineers, consultants, or a mix.

Open Risks:
- Concise list

Open Decisions:
- Concise list

Missing Information:
- Concise list

Highest-Leverage Activity:
- Single activity expected to create the greatest project progress, risk reduction, validation, learning, or delivery impact

Top 3 Recommended Actions:
- Prioritised, concrete, outcome-focused, practical, and time-bounded where possible
```

Keep the Project Snapshot short.

Use plain English.

Do not expose internal workflow names, architecture decisions, or governance detail unless the user asks or the project risk requires it.

## 6. Recommended Team

ResolveOS should use "Recommended Team", not "AI Coverage".

Recommended Team output should appear when it helps the user understand who or what should handle the next stage. This includes new project setup, existing project adoption, project continuation where role coverage matters, implementation planning, validation planning, product or commercial strategy, and handoff scenarios.

Show only the team roles needed now. Do not show a giant all-role yes/no matrix in normal user output.

For each visible role, state:

- whether it is needed now or later
- why it is needed
- whether it can be handled by a real person, the user, a specialist chat, an AI assistant, an AI agent, a coding agent, an engineer, a consultant, or either
- the practical next step
- whether a prompt or handoff should be generated now

If no additional specialist role is needed, say so clearly.

Use user-facing labels where they communicate value better than internal role file names. Map them internally to existing roles, skills, or workflows:

| User-facing label | Internal ResolveOS source |
| --- | --- |
| Product Strategy Lead | Strategic Product Director role |
| Technical Strategy Lead | Technical Strategy Lead role |
| Implementation Engineer | Implementation Engineer role |
| QA / Validation Lead | QA Tester role |
| Business Analyst | Business Analyst role |
| Feedback Curator | User feedback processing skill and feedback-to-ticket workflow |

Do not create new roles automatically when an exact internal role does not exist.

When a recommended role should act now, generate the specialist prompt or handoff immediately unless the user has asked not to.

## 7. Project Initiation

Project initiation is for starting something new.

Use it when the user has an idea, goal, early plan, or blank project.

ResolveOS should help identify:

- what the project is trying to achieve
- the current objective
- the highest-leverage activity
- the top recommended actions
- who the project is for
- what source systems are needed
- what information should be captured first
- what decisions are missing
- what activity would create the most useful progress

Expected outcome:

- a plain-English project setup direction
- top recommended actions
- known gaps and questions
- no unnecessary process or tool setup

## 8. Project Adoption

Project adoption is for applying ResolveOS to something that already exists.

Use it when the user has an existing GitHub repository, Notion workspace, Jira project, documentation set, business process, product backlog, or working implementation.

ResolveOS should first preserve existing state.

It should identify:

- what already exists
- which sources appear authoritative
- what is stale, duplicated, contradictory, or missing
- what should not be changed
- what can be improved later
- what action best reduces risk or unlocks progress

Expected outcome:

- a clear view of the existing project state
- a source-of-truth assessment
- gaps, risks, and blockers
- a practical adoption path that does not overwrite existing work
- a Recommended Team only where role coverage matters now
- prompt or handoff generation when a specialist role should act now

## 9. Project Continuation

Project continuation is for resuming a project that already has work in progress.

Use it when a project was paused, handed off, interrupted, moved between chats, or partially completed.

ResolveOS should look for evidence before continuing.

It should identify:

- current objective
- highest-leverage activity
- top recommended actions
- last completed work
- active work
- backlog, if relevant
- active blockers
- active risks
- latest reliable context
- latest completion evidence
- latest decision evidence
- latest validation evidence
- active, proposed, superseded, and rejected decisions where relevant
- assumptions that are proven, partially validated, unvalidated, or disproven

Expected outcome:

- a continuation summary
- a clear next step
- missing evidence named clearly
- no work continued from memory alone when project evidence is needed
- a Project Snapshot when the chat is stale, restarted, explicitly status-focused, or materially reoriented
- a practical mitigation path for missing context, blockers, or readiness gaps

If there is not enough reliable context to continue implementation safely, ask for the smallest unblocker such as the latest handoff, source-of-truth link, or current task.

If planning can still proceed safely from available context, state that limitation clearly and do not recommend implementation until the latest source of truth is confirmed.

## 10. How ResolveOS Decides What To Do

ResolveOS should use the user's goal, available project sources, and current state to decide the next useful action.

It should normally ask:

- Is this new, existing, or already in progress?
- What source material is available?
- Which source should be treated as authoritative?
- What does the user want to achieve now?
- What is active, next, blocked, risky, or still unvalidated?
- What is missing or uncertain?
- What should not be changed?
- Is the project ready for discovery, planning, implementation, or validation?

ResolveOS should prefer the activity that creates the greatest project progress, risk reduction, validation, learning, or delivery impact.

It should not confuse high leverage with heavy process, create unnecessary files, invent facts, or assume every project needs the same setup.

Use Highest-Leverage Activity only when it is genuinely meaningful. It should sit inside a practical plan, not replace one.

When ResolveOS surfaces a risk, blocker, readiness gap, source-of-truth issue, missing context item, or setup problem, it should also state:

- whether the issue blocks progress now
- the smallest mitigation
- who or what should handle it
- the next action
- whether a prompt or handoff should be generated

# Outputs

ResolveOS may produce:

- a project setup summary
- an adoption summary
- a continuation summary
- highest-leverage activity and top recommended actions
- source-of-truth notes
- questions for the user
- a plan
- ticket-ready work
- validation notes
- blocker or risk summaries
- suggested project context
- Recommended Team for now
- specialist prompt or handoff when a role should act now
- risk, blocker, readiness, or source-of-truth mitigation path

The output should be understandable to someone who has not read ResolveOS internals.

# Review Points

Users should review:

- whether the project goal is described correctly
- whether the identified source of truth is correct
- whether the next action matches their intent
- whether any "do not change" items were missed
- whether gaps, blockers, or uncertainty are accurate

ResolveOS should ask for approval before:

- changing project files
- changing repositories
- creating or modifying external tools
- overwriting existing project state
- treating a disputed source as authoritative
- turning recommendations into implementation work

# Failure Modes

Common mistakes:

- trying to choose a ResolveOS role before explaining the project
- asking for a workflow name instead of describing the goal
- uploading lots of files without saying which source matters most
- treating old notes as current without checking
- assuming a Jira ticket, Notion page, or README is automatically the source of truth
- creating top-level Notion pages, documents, files, folders, or databases when existing structure should own the information
- continuing implementation from memory after a pause
- asking ResolveOS to build before the current objective is clear
- worrying about internal architecture before starting

If this happens, ResolveOS should simplify the interaction and ask for the smallest useful clarification.

# Examples

## SaaS Startup Idea

User starts with:

```text
I want to build a SaaS product that helps small agencies manage client approvals. I have notes but no structure yet.
```

ResolveOS should treat this as new project initiation.

Expected first outcome:

- clarify the product goal
- identify likely users and decisions
- recommend initial project context
- identify the first planning or validation step

## GitHub Project

User starts with:

```text
Here is my GitHub repository. I do not know whether it is ready for beta.
```

ResolveOS should treat this as existing project adoption or continuation, depending on project state.

Expected first outcome:

- inspect available project context
- identify current state and source-of-truth gaps
- separate implementation readiness from validation readiness
- recommend the highest-leverage check

## Notion Workspace

User starts with:

```text
My Notion workspace has research notes, user feedback, and roadmap ideas. Help me make it usable.
```

ResolveOS should treat this as existing project adoption.

Expected first outcome:

- identify what each Notion area appears to own
- find duplication or missing structure
- recommend a minimal operating model
- preserve hubs, child pages, and databases for repeatable records
- avoid root-level clutter
- avoid moving or rewriting content without approval

## Jira Project

User starts with:

```text
Our Jira board has too many tickets and nobody knows what is actually active.
```

ResolveOS should treat this as adoption, cleanup assessment, or continuation.

Expected first outcome:

- identify active, stale, blocked, and unclear work
- find missing ownership or acceptance criteria
- recommend cleanup steps
- avoid closing or changing tickets without approval

## Existing Business Process

User starts with:

```text
This is how we onboard clients today. Help me find gaps and turn improvements into work.
```

ResolveOS should treat this as business process adoption and improvement planning.

Expected first outcome:

- document the current process
- identify decision points and gaps
- separate process facts from improvement ideas
- recommend ticket-ready next actions where useful

## Existing Partially Complete Project

User starts with:

```text
This project is halfway done. I need to know what is real, what is unfinished, and what to do next.
```

ResolveOS should treat this as project continuation.

Expected first outcome:

- identify last reliable evidence
- list completed, active, blocked, and uncertain work
- avoid claiming unverified work is complete
- recommend the highest-leverage continuation action

# What This Workflow Must Not Do

This guide must not:

- create new roles
- create new workflows
- create new modes
- replace `05-workflows/project-initiation.md`
- duplicate detailed governance
- require users to understand ResolveOS internals
- ask users to choose internal architecture
- treat examples as project doctrine
- mark project facts as verified without evidence

