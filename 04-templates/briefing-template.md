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
related_templates:
  - 04-templates/ticket-context-template.md
  - 04-templates/blocker-report-template.md
  - 04-templates/completion-report-template.md
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

Provide the canonical ResolveOS briefing template.

A briefing captures reviewed context for a role, task, ticket, project, decision, or implementation session when direct source-system context may be incomplete, scattered, inaccessible, or in need of consolidation.

This template supports context loading, ticket context, role loading, project loading, implementation planning, review, and decision-making. It is a briefing structure, not a source-of-truth replacement, workflow, skill, role, ticket template, or approval record.

Source references:

- `04-templates/ticket-context-template.md` > source, scope, missing context, validation, next action
- `01-context/role-loading-rules.md` > role, project, briefing, and ticket context
- `01-context/project-loading-rules.md` > project context and traceability
- `01-context/missing-context-behaviour.md` > approved briefing fallback and limitations
- `05-workflows/ticket-to-implementation.md` > approved briefing when source-system access is unavailable
- `05-workflows/implementation-review-loop.md` > missing context and evidence handling
- `06-governance/decision-maker-reporting.md` > decision-maker context
- `AGENTS.md.backup` > short task understanding and persistent context discipline
- `docs/project-context/implementation-workflow.md` > briefing files
- `docs/codex-briefings/` > repeated briefing structures
- `migration/resolvepm-residual-audit.md` > `briefing-template.md`

# Template

Use the sections below as the briefing structure.

The briefing should let a reviewer quickly answer:

- What context is being consolidated?
- Which sources informed it?
- What are we trying to achieve?
- Why does it matter?
- What is approved?
- What is excluded?
- Which decisions, constraints, dependencies, risks, assumptions, and missing context matter?
- Which roles, skills, validation, review, or next action should be loaded?

# Briefing Title

```text
[Short title for the role, task, ticket, project, decision, implementation session, or context area.]
```

# Purpose

```text
[Why this briefing exists and what work or decision it supports.]
```

# Source Context

```text
Canonical source system or source files:
-

Source status:
- Current / Draft / Reviewed / Incomplete / Inaccessible / Stale / Contradictory / Unknown

Source facts:
-

Interpretation or synthesis:
-

Source limitations:
-
```

# What We Are Trying To Achieve

```text
[Plain-English statement of the intended objective or outcome.]
```

# Why It Matters

```text
[Short explanation of the product, operational, delivery, review, decision, technical, or admin value.]
```

# Background

```text
Relevant background:
-

Prior context, ticket sequence, decision, review, or project state:
-
```

# Approved Scope

```text
In scope:
-

Approved use of this briefing:
-
```

# Out Of Scope

```text
Not included:
-

Future work, adjacent work, or tempting extras that must not be started from this briefing:
-
```

# Key Decisions

```text
Known decisions:
-

Decision owner or source:
-

Decision status:
- Approved / Draft / Needs review / Superseded / Unknown
```

# Constraints

```text
Product, business, technical, security, cost, configuration, source-of-truth, role-boundary, or workflow constraints:
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

# Risks

```text
Risks:
-

Risk impact:
-
```

# Assumptions

```text
Known assumptions:
-

Assumptions requiring review:
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

Limitation of fallback:
-
```

# Relevant Roles

```text
Primary role:
- [Role]

Supporting roles:
-

Role-loading notes:
-
```

# Relevant Skills

```text
Relevant skills:
-

Skill-loading notes:
-
```

# Validation / Review Expectations

```text
Review needed:
-

Validation expected:
-

What confirms this briefing is usable:
-
```

# Highest-Leverage Activity

```text
Highest-leverage activity:
-

Owner:
- Admin / Product Manager / Business Analyst / QA Tester / Technical Strategy Lead / Implementation Engineer / Strategic Product Director / Project owner / Unknown

Top 3 recommended actions:
- [prioritised, concrete, outcome-focused, practical, time-bounded where possible]
- [prioritised, concrete, outcome-focused, practical, time-bounded where possible]
- [prioritised, concrete, outcome-focused, practical, time-bounded where possible]
```

# Notes

```text
-
```

# Usage Guidance

Use this template when context needs to be consolidated before a role, task, ticket, project, decision, implementation, review, or migration session.

This template inherits behaviour from:

- `01-context/context-loading-rules.md`
- `01-context/role-loading-rules.md`
- `01-context/project-loading-rules.md`
- `01-context/missing-context-behaviour.md`
- `05-workflows/ticket-to-implementation.md`
- `05-workflows/implementation-review-loop.md`
- `06-governance/decision-maker-reporting.md`

Briefings may support ticket context, role loading, project loading, implementation planning, or decision-making when source context is scattered, inaccessible, or needs consolidation.

Briefings do not replace canonical source systems unless explicitly approved as fallback context.

When a briefing is used as fallback context, state:

- what source context is unavailable
- why the briefing is allowed as fallback
- what limitation remains
- what source update, admin review, or verification is still needed

Keep source facts separate from interpretation, assumptions, and recommendations.

If this briefing reveals a blocker, use `04-templates/blocker-report-template.md`.

If this briefing is used to populate ticket context, use `04-templates/ticket-context-template.md`.

# Example

```text
Briefing Title

Current implementation session briefing

Purpose

Capture reviewed context for an implementation session where the source ticket exists but comments and dependencies are scattered across project files.

Source Context

Canonical source system or source files:
- Source ticket
- Current focus
- Project context

Source status:
- Reviewed

Source facts:
- The source ticket defines the current objective.
- A project context file identifies a prerequisite.

Interpretation or synthesis:
- The current ticket can proceed only after the prerequisite state is confirmed.

Source limitations:
- Source-system comments may not be fully loaded.

What We Are Trying To Achieve

Make the implementation context clear enough to start safely or report a blocker.

Why It Matters

The implementer needs enough context to avoid guessing, hidden scope expansion, and false completion.

Background

Relevant background:
- The work belongs to an approved ticket sequence.

Prior context, ticket sequence, decision, review, or project state:
- Previous-ticket state may affect whether the current ticket can start.

Approved Scope

In scope:
- Load current ticket context.
- Confirm prerequisite state.
- Identify blockers before implementation.

Approved use of this briefing:
- Context loading and implementation planning.

Out Of Scope

Not included:
- Future ticket implementation.
- Project roadmap changes.

Future work, adjacent work, or tempting extras that must not be started from this briefing:
- Adjacent refactors.

Key Decisions

Known decisions:
- Current ticket first.

Decision owner or source:
- ResolveOS workflow and project source context.

Decision status:
- Approved

Constraints

Product, business, technical, security, cost, configuration, source-of-truth, role-boundary, or workflow constraints:
- Do not start future tickets unless explicitly asked.

Dependencies

Prerequisites:
- Previous-ticket outcome should be checked.

Related dependency state:
- Unknown

Risks

Risks:
- Starting without dependency confirmation may create false completion risk.

Risk impact:
- Implementation may need to stop and report a blocker.

Assumptions

Known assumptions:
- The source ticket remains the primary scope source.

Assumptions requiring review:
- Whether the previous ticket is complete enough.

Missing Context

Missing, stale, contradictory, inaccessible, ambiguous, or unsupported context:
- Previous-ticket outcome.

Why it matters:
- It may affect implementation safety.

Approved fallback, if any:
- Use available briefing only for planning, not for claiming source-system status.

Limitation of fallback:
- Source-system status cannot be reported as updated unless actually updated.

Relevant Roles

Primary role:
- Implementation Engineer

Supporting roles:
- Technical Strategy Lead, if dependency sequencing is blocked.

Relevant Skills

Relevant skills:
- ticket-writing
- acceptance-criteria
- completion-reporting

Validation / Review Expectations

Review needed:
- Confirm the briefing accurately reflects source context.

Validation expected:
- Confirm prerequisite state before implementation.

What confirms this briefing is usable:
- The current ticket, scope, dependency, and next action are clear.

Highest-Leverage Activity

Highest-leverage activity:
- Check previous-ticket outcome and then populate ticket context.

Owner:
- Implementation Engineer

Top 3 recommended actions:
- Confirm previous-ticket outcome.
- Populate ticket context from source evidence.
- Identify any blocker or missing prerequisite before implementation starts.

Notes

- This briefing is not implementation approval by itself.
```

# Anti-Patterns

Do not:

- invent missing facts
- blur source facts, assumptions, interpretations, and recommendations
- treat a briefing as canonical source-system truth unless explicitly approved as fallback context
- use a briefing to start implementation when child ticket scope or approved scope is missing
- hide missing, stale, contradictory, inaccessible, ambiguous, or unsupported context
- omit source limitations
- silently expand scope
- use project-specific ticket keys, routes, product doctrine, local commands, provider names, deployment targets, or roadmap details as global ResolveOS content
- turn this template into a role, skill, workflow, governance file, ticket template, or source-of-truth replacement

# Related Templates

- `04-templates/ticket-context-template.md`
- `04-templates/blocker-report-template.md`
- `04-templates/completion-report-template.md`

# Related Context

- `01-context/context-loading-rules.md`
- `01-context/startup-context.md`
- `01-context/role-loading-rules.md`
- `01-context/missing-context-behaviour.md`
- `01-context/project-loading-rules.md`

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
- decision log template
- source-tracker comment template
- epic completion summary template
- phase-readiness review template
- dependency-management skill
- requirement-traceability skill
- backlog-refinement skill
- documentation update assessment skill or governance
- project-specific briefing fields, ticket keys, local commands, routes, deployment targets, provider names, environment variables, roadmap themes, and product terminology

# Ambiguous Items For Admin Review

Admin review is needed for:

- whether briefings require explicit admin approval before they can be used as fallback context
- whether every briefing must separate `Source facts` from `Interpretation or synthesis`
- whether epic briefings should use this general briefing template or a future epic-specific template
- whether briefings should include a formal freshness or last-reviewed field
- whether role-loading notes should remain inside this template or be handled only by `01-context/role-loading-rules.md`

# What This Template Must Not Do

This template must not:

- replace canonical source systems
- replace `01-context/missing-context-behaviour.md`
- replace `01-context/role-loading-rules.md`
- replace `01-context/project-loading-rules.md`
- replace `04-templates/ticket-context-template.md`
- approve implementation scope
- define role authority
- define workflow sequence
- create project-specific doctrine in ResolveOS
