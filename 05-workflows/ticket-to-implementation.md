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
