---
type: template
scope: global
owner: ResolveOS
version: 0.1
status: draft
source_project: ResolvePM
source_files:
  - migration/resolvepm-residual-audit.md
  - migration-review.md
  - migration/resolvepm-extraction-map.md
  - migration/resolvepm-extraction-audit.md
  - AGENTS.md.backup
  - DEBUGGING.md
related_roles:
  - 02-roles/product-manager.md
  - 02-roles/business-analyst.md
  - 02-roles/qa-tester.md
  - 02-roles/technical-strategy-lead.md
  - 02-roles/implementation-engineer.md
  - 02-roles/strategic-product-director.md
related_skills:
  - 03-skills/completion-reporting.md
related_workflows:
  - 05-workflows/ticket-to-implementation.md
  - 05-workflows/implementation-review-loop.md
related_governance:
  - 06-governance/decision-maker-reporting.md
  - 06-governance/architecture-decisions.md
  - 06-governance/source-of-truth-rules.md
review_required: true
---

# Purpose

Provide the canonical ResolveOS completion report template for completed, partial, blocked, failed, deferred, or not-verified work.

This template implements existing completion-reporting, decision-maker-reporting, ticket-to-implementation, and implementation-review behaviour. It is a communication structure, not a behavioural definition.

Use this template to make completion reports readable for non-technical review and specific enough for technical validation.

Source references:

- `06-governance/decision-maker-reporting.md` > `Required Reporting Layers`
- `03-skills/completion-reporting.md` > `Outputs`
- `05-workflows/ticket-to-implementation.md` > `Completion Reporting`
- `05-workflows/implementation-review-loop.md` > `Outputs`
- `AGENTS.md.backup` > required completion format
- `migration/resolvepm-residual-audit.md` > `completion-report-template.md`

# Template

Use the sections below as the completion report structure.

Keep the report as short as the work allows, but do not remove sections that are needed to answer:

- Did the AI understand the objective?
- Did it solve the correct problem?
- Did it stay within scope?
- What changed?
- How was it validated?
- What risks remain?
- What should happen next?

# Ticket

```text
Ticket, task, source item, approved batch, or scope:
- [Identifier and title]

Status:
- Complete / Partially complete / Blocked / Failed / Not verified / Deferred
```

# What I Think We Are Achieving

```text
[Plain-English statement of the objective, problem being solved, intended outcome, and scope.]

Assumptions:
-

Non-goals or out-of-scope items:
-
```

# What Was Achieved

```text
[Plain-English summary of what was actually completed, found, changed, reviewed, or produced.]
```

# Why It Matters

```text
[Short explanation of the business, product, operational, review, delivery, or validation impact.]
```

# Did This Differ From The Original Plan?

```text
No / Yes / Not applicable

If yes:
- Original plan:
- What changed:
- Why it changed:
- Impact:
- Follow-up needed:
```

# Implementation Summary

```text
Implementation path:
- [Brief explanation of the actual steps taken.]

Technical impact:
- [Technical change, dependency, architecture, integration, data, configuration, or documentation impact.]

Business or product impact:
- [User-facing, stakeholder, workflow, requirement, prioritisation, or acceptance impact.]
```

# Files Created

```text
-
```

# Files Updated

```text
-
```

# Validation Performed

```text
Checks, tests, review steps, or validation performed:
-

Result:
- Passed / Failed / Partial / Not run / Not applicable

What this proves:
-

Validation not performed:
-

Why not performed:
-

Residual validation risk:
-
```

# Scope Completed

```text
-
```

# Scope Deferred

```text
-

Reason deferred:
-
```

# Known Issues

```text
-
```

# Risks

```text
-
```

# Blockers

```text
Current blocker:
- [Specific missing context, failed check, credential, configuration, prerequisite, source file, admin decision, or architecture issue.]

Why continuing would be unsafe or unsupported:
-

Needed input, config, source, credential, prerequisite, or decision:
-

Highest-leverage unblocker or follow-up action:
-
```

# Suggested Follow-Up Work

```text
Suggested follow-up tickets or tasks:
-

Why separate:
-

Required or optional:
-
```

# Next Recommended Ticket

```text
-
```

# Verification Status

```text
Verification status:
- Verified / Partially verified / Not verified / Blocked / Failed / Requires admin review

Evidence:
-

Limitations:
-
```

# Notes

```text
-
```

# Usage Guidance

Use this template after implementation, migration, review, debugging, validation, failed work, blocked work, or deferred work when a structured completion report is needed.

This template inherits behaviour from:

- `03-skills/completion-reporting.md`
- `06-governance/decision-maker-reporting.md`
- `05-workflows/ticket-to-implementation.md`
- `05-workflows/implementation-review-loop.md`

Do not use this template to redefine completion honesty, validation rules, role authority, workflow sequence, source-of-truth precedence, or project-specific verification commands.

For checks or commands that were run, report the method and result. For checks or commands not run, say they were not run, explain why, and state the residual risk.

Follow-up work must remain separate from completed scope unless the admin explicitly approves expanding the current scope.

# Example

```text
Ticket

Ticket, task, source item, approved batch, or scope:
- Batch 4C.2.1B - Completion Report Template

Status:
- Complete for the requested scope

What I Think We Are Achieving

Create a reusable completion report template that preserves ResolvePM's rich reporting structure while relying on existing ResolveOS behaviour files for rules.

What Was Achieved

Created the completion report template and added the related architecture decision.

Why It Matters

The admin and reviewers can understand intent, outcome, validation, risk, and next steps without losing technical evidence.

Did This Differ From The Original Plan?

No.

Implementation Summary

Implementation path:
- Extracted the structure from existing reporting governance, completion reporting skill, workflows, and ResolvePM source material.

Files Created

- 04-templates/completion-report-template.md

Files Updated

- 06-governance/architecture-decisions.md

Validation Performed

Checks, tests, review steps, or validation performed:
- Reviewed the created template and ADR update.

Result:
- Passed

Validation not performed:
- No project test suite was run because this is a markdown governance/template change.

Scope Completed

- Completion report template created.
- ADR added.

Scope Deferred

- Blocker report template.
- Ticket context template.

Known Issues

- None identified.

Risks

- Admin may decide a shorter default report is needed later.

Blockers

- None.

Suggested Follow-Up Work

- Create blocker report template in a later approved batch.

Next Recommended Ticket

- Create the next approved template or governance file from the migration plan.

Verification Status

Verification status:
- Requires admin review

Evidence:
- Template and ADR are present in the repository.

Notes

- This template implements existing behaviour; it does not redefine it.
```

# Anti-Patterns

Do not:

- claim work was done unless it was actually done
- claim checks, tests, deployment, commits, pushes, source-ticket updates, or admin approval happened without direct evidence
- bury failed validation, blockers, known issues, risk, deferred scope, or uncertainty
- report follow-up work as completed scope
- remove the decision-maker context when it is needed for review
- replace technical evidence with a polished business summary
- replace business impact with only file names and command output
- make project-specific commands, ticket keys, routes, tools, or deployment processes global
- turn this template into a role, skill, workflow, or governance file

# Related Skills

- `03-skills/completion-reporting.md`

# Related Workflows

- `05-workflows/ticket-to-implementation.md`
- `05-workflows/implementation-review-loop.md`

# Related Governance

- `06-governance/decision-maker-reporting.md`
- `06-governance/architecture-decisions.md`
- `06-governance/source-of-truth-rules.md`

# Deferred Items

Deferred because they belong in future templates, skills, workflows, or project context:

- blocker report template
- ticket context prompt template
- briefing template
- decision log template
- exact source-tracker comment format
- implementation-review skill
- debugging-support skill
- project-specific command lists, local routes, ticket keys, deployment targets, provider names, and environment variables

# Ambiguous Items For Admin Review

Admin review is needed for:

- whether every completion report must include every section, or whether some sections may be marked `Not applicable`
- whether `Next Recommended Ticket` should always be present or only when sequencing exists
- whether file removals should become a dedicated first-class section or be reported in `Implementation Summary` and `Notes`
- whether manual git commands should be part of a future Codex-specific template rather than this global completion report template

# What This Template Must Not Do

This template must not:

- define completion-reporting behaviour
- redefine role responsibilities
- redefine workflow sequence
- replace validation or source-of-truth governance
- promote ResolvePM product doctrine into ResolveOS
- imply that project-specific verification commands are global ResolveOS requirements
