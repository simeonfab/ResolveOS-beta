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
  - docs/project-context/implementation-workflow.md
  - docs/codex-briefings/
related_context:
  - 01-context/context-loading-rules.md
  - 01-context/startup-context.md
  - 01-context/role-loading-rules.md
  - 01-context/missing-context-behaviour.md
  - 01-context/project-loading-rules.md
related_skills:
  - 03-skills/ticket-writing.md
  - 03-skills/acceptance-criteria.md
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

Provide the canonical ResolveOS ticket-context template.

Use this template to capture enough ticket, task, source-item, or approved-batch context before work begins.

This template supports role loading, project loading, implementation planning, acceptance criteria review, blocker detection, validation planning, and completion reporting. It is a context structure, not a ticket-writing skill, acceptance-criteria skill, implementation workflow, role definition, or approval record.

Source references:

- `03-skills/ticket-writing.md` > `Inputs`
- `03-skills/ticket-writing.md` > `Ticket Structure`
- `03-skills/acceptance-criteria.md` > `Inputs`
- `05-workflows/ticket-to-implementation.md` > `Inputs`
- `05-workflows/ticket-to-implementation.md` > `Confirm Scope`
- `01-context/role-loading-rules.md` > current ticket and role-loading context
- `01-context/missing-context-behaviour.md` > missing acceptance criteria and missing context
- `06-governance/decision-maker-reporting.md` > decision-maker context
- `AGENTS.md.backup` > per-ticket startup prompt
- `migration/resolvepm-residual-audit.md` > `ticket-context-template.md`

# Template

Use the sections below as the ticket-context structure.

The template should let a reviewer quickly answer:

- What is this work trying to achieve?
- Why does it matter?
- What is approved?
- What is excluded?
- What acceptance criteria must be satisfied?
- What dependencies or blockers exist?
- How will success be validated?
- What should not be started yet?

# Ticket

```text
Ticket, task, source item, approved batch, or scope:
- [Identifier]

Source system or source file:
- [Jira, GitHub issue, project document, briefing, admin instruction, or other source]

Source status:
- Draft / Approved / In review / Blocked / In progress / Complete / Unknown
```

# Title

```text
[Short title that describes the intended outcome.]
```

# What We Are Trying To Achieve

```text
[Plain-English statement of what the work is trying to achieve.]
```

# Why It Matters

```text
[Short explanation of the product, business, operational, delivery, review, or technical value.]
```

# Background

```text
Relevant context:
-

Source notes or comments:
-

Previous-ticket or briefing context, if relevant:
-
```

# Approved Scope

```text
In scope:
-

Approved implementation, review, planning, migration, or analysis work:
-
```

# Out Of Scope

```text
Not included:
-

Future tickets, adjacent work, or tempting extras that must not be started yet:
-
```

# Acceptance Criteria

```text
Acceptance criteria:
-

Acceptance criteria source:
- Ticket / Source item / Briefing / Admin instruction / Draft for review / Missing

If acceptance criteria are missing or incomplete:
- [Name the gap. Do not guess missing acceptance criteria.]
```

# Constraints

```text
Technical constraints:
-

Product, business, security, cost, configuration, source-of-truth, or role-boundary constraints:
-
```

# Dependencies

```text
Prerequisites:
-

Related dependency state:
- Complete / Incomplete / Unknown / Blocked / Not applicable

Dependency notes:
-
```

# Assumptions

```text
Known assumptions:
-

Assumptions requiring review:
-
```

# Risks

```text
Implementation, validation, delivery, security, cost, dependency, source-of-truth, or scope risks:
-
```

# Missing Context

```text
Missing, stale, contradictory, inaccessible, ambiguous, or unsupported context:
-

Why it matters:
-

Approved fallback, if any:
-
```

# Validation Expectations

```text
Validation or review expected:
-

Manual test expectations:
-

Project-specific checks or commands, if provided by project context:
-

What confirms success:
-
```

# Documentation Expectations

```text
Documentation or persistent context likely affected:
-

Documentation update required in this scope?
- Yes / No / Unknown / Follow-up

Notes:
-
```

# Related Tickets

```text
Previous ticket, if sequencing matters:
-

Follow-up, prerequisite, dependency, blocker, or related tickets:
-
```

# Current Status

```text
Status:
- Ready for implementation / Ready for review / Needs clarification / Blocked / Partially ready / Draft only / Unknown

Reason:
-
```

# Highest-Leverage Activity

```text
Highest-leverage activity:
-

Owner:
- Admin / Product Manager / Business Analyst / QA Tester / Technical Strategy Lead / Implementation Engineer / Strategic Product Director / Project owner / Unknown

Top 3 recommended actions:
-
-
-
```

# Notes

```text
-
```

# Usage Guidance

Use this template before work begins when a ticket, task, source item, approved batch, or briefing needs to be loaded into a ResolveOS-enabled session.

This template inherits behaviour from:

- `03-skills/ticket-writing.md`
- `03-skills/acceptance-criteria.md`
- `05-workflows/ticket-to-implementation.md`
- `05-workflows/implementation-review-loop.md`
- `01-context/role-loading-rules.md`
- `01-context/missing-context-behaviour.md`
- `01-context/project-loading-rules.md`
- `06-governance/decision-maker-reporting.md`

Do not use this template to approve work, write new ticket rules, define acceptance criteria behaviour, redefine implementation workflow sequence, or override project source-of-truth rules.

If acceptance criteria are missing, mark them as missing. Do not guess them.

If the work is based on an approved fallback such as a briefing, state the fallback and its limitation.

If context reveals a blocker, use `04-templates/blocker-report-template.md` for the blocker report.

If work completes, use `04-templates/completion-report-template.md` for the completion report.

# Example

```text
Ticket

Ticket, task, source item, approved batch, or scope:
- CP-XX

Source system or source file:
- Source ticket

Source status:
- Approved

Title

Prepare the implementation-ready context for the current ticket.

What We Are Trying To Achieve

Make the current ticket clear enough that an implementation role can work from approved scope without guessing.

Why It Matters

The work needs enough intent, scope, acceptance, dependency, and validation context to avoid hidden scope expansion and false completion.

Background

Relevant context:
- The ticket is part of an approved sequence.

Source notes or comments:
- Comments mention a dependency that should be checked before implementation.

Approved Scope

In scope:
- Capture the current ticket context.
- Identify acceptance criteria, dependencies, and validation expectations.

Out Of Scope

Not included:
- Future ticket implementation.
- Adjacent refactors.

Acceptance Criteria

Acceptance criteria:
- Given the ticket context is loaded, when implementation planning starts, then the implementer can identify objective, scope, exclusions, dependencies, and validation expectations.

Acceptance criteria source:
- Ticket

Constraints

Technical constraints:
- Use existing project patterns.

Product, business, security, cost, configuration, source-of-truth, or role-boundary constraints:
- Do not expand current scope without admin approval.

Dependencies

Prerequisites:
- Previous ticket outcome should be checked because sequencing matters.

Related dependency state:
- Unknown

Assumptions

Known assumptions:
- The source ticket is the current source of detailed scope.

Risks

Implementation, validation, delivery, security, cost, dependency, source-of-truth, or scope risks:
- Missing dependency state may block implementation.

Missing Context

Missing, stale, contradictory, inaccessible, ambiguous, or unsupported context:
- Previous-ticket outcome is not yet checked.

Why it matters:
- It may affect whether the current ticket can start safely.

Validation Expectations

Validation or review expected:
- Confirm acceptance criteria are present and testable.

Manual test expectations:
- Not applicable at context-loading stage.

What confirms success:
- Context is ready or blocker is reported clearly.

Documentation Expectations

Documentation or persistent context likely affected:
- Unknown.

Documentation update required in this scope?
- Unknown

Related Tickets

Previous ticket, if sequencing matters:
- Previous sequence item.

Follow-up, prerequisite, dependency, blocker, or related tickets:
- To be identified if dependency is incomplete.

Current Status

Status:
- Needs clarification

Reason:
- Previous-ticket state needs checking before implementation starts.

Highest-Leverage Activity

Highest-leverage activity:
- Check the previous ticket outcome and current repository state before implementation.

Owner:
- Implementation Engineer

Top 3 recommended actions:
- Confirm previous-ticket outcome.
- Check current repository state.
- Identify any blocker or missing prerequisite before implementation starts.

Notes

- This context does not authorise future-ticket implementation.
```

# Anti-Patterns

Do not:

- use this template to start future tickets unless explicitly asked
- treat an epic or briefing as implementation approval when child implementation scope is missing
- silently expand scope
- hide out-of-scope items
- guess missing acceptance criteria
- invent requirements, dependencies, validation expectations, source facts, or project context
- treat ticket creation or context capture as approval authority
- omit dependencies or blockers because they are inconvenient
- make project-specific ticket keys, commands, routes, deployment targets, provider names, or product doctrine global
- turn this template into a role, skill, workflow, or governance file

# Related Context

- `01-context/context-loading-rules.md`
- `01-context/startup-context.md`
- `01-context/role-loading-rules.md`
- `01-context/missing-context-behaviour.md`
- `01-context/project-loading-rules.md`

# Related Skills

- `03-skills/ticket-writing.md`
- `03-skills/acceptance-criteria.md`
- `03-skills/completion-reporting.md`

# Related Workflows

- `05-workflows/ticket-to-implementation.md`
- `05-workflows/implementation-review-loop.md`

# Related Governance

- `06-governance/decision-maker-reporting.md`
- `06-governance/architecture-decisions.md`
- `06-governance/source-of-truth-rules.md`

# Deferred Items

Deferred because they belong in future templates, skills, workflows, governance, or project context:

- role prompt template
- briefing template
- source-tracker comment template
- decision log template
- dependency-management skill
- requirement-traceability skill
- backlog-refinement skill
- documentation update assessment skill or governance
- project-specific ticket fields, local commands, routes, deployment targets, provider names, environment variables, ticket keys, and product terminology

# Ambiguous Items For Admin Review

Admin review is needed for:

- whether `Ticket` and `Title` should be separate sections or combined in future revisions
- whether every ticket context must include `Why It Matters`, or whether small technical tasks may mark it `Not applicable`
- whether approved briefing files can always populate this template when source-system access is unavailable
- whether related tickets should distinguish previous, prerequisite, follow-up, duplicate, and blocked-by relationships in a richer schema
- whether ticket context should include a dedicated role-loading section or rely on `01-context/role-loading-rules.md`

# What This Template Must Not Do

This template must not:

- replace `03-skills/ticket-writing.md`
- replace `03-skills/acceptance-criteria.md`
- replace `05-workflows/ticket-to-implementation.md`
- replace `01-context/role-loading-rules.md`
- approve implementation scope
- define role authority
- define workflow sequence
- create or modify tickets automatically
- promote ResolvePM project doctrine into ResolveOS
