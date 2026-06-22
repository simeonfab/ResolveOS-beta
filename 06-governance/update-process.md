---
type: governance
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
  - migration/resolvepm-extraction-map.md
  - migration/resolvepm-extraction-audit.md
  - AGENTS.md.backup
  - docs/project-context/implementation-workflow.md
  - docs/ai-roles/technical-strategy-lead.md
  - docs/ai-roles/implementation-engineer.md
related_context:
  - 01-context/running-context.md
  - 01-context/context-loading-rules.md
  - 01-context/startup-context.md
  - 01-context/role-loading-rules.md
  - 01-context/project-loading-rules.md
related_governance:
  - 06-governance/source-of-truth-rules.md
  - 06-governance/decision-maker-reporting.md
  - 06-governance/architecture-decisions.md
review_required: true
---

# Purpose

Define how ResolveOS artifacts are maintained, updated, reviewed, and kept aligned over time.

This governance preserves the update discipline extracted from ResolvePM: do not let important context drift, update the correct file, explain why the update is needed, keep ownership explicit, and avoid spreading duplicate behaviour across layers.

ResolveOS uses a defined update process to maintain architectural integrity.

This file is governance. It is not a template, skill, workflow, role, context file, ADR, or project-specific update checklist.

Source references:

- `migration/resolveos-architecture-review.md` > `Recommended Next Batch`
- `migration/resolveos-architecture-review.md` > `Architectural Weaknesses`
- `06-governance/source-of-truth-rules.md` > `Core Principle`
- `01-context/running-context.md` > `Usage Guidance`
- `docs/project-context/implementation-workflow.md` > documentation update check
- `docs/ai-roles/technical-strategy-lead.md` > documentation update timing labels
- `docs/ai-roles/implementation-engineer.md` > persistent context update flagging
- `AGENTS.md.backup` > `Update documentation`

# Update Principles

## Update The Source Of Ownership

Updates should occur at the source of ownership rather than through duplication.

Every important rule should have one canonical home. Copies, summaries, references, and derived versions may exist, but ownership must remain explicit.

If the needed change affects global behaviour, update the owning ResolveOS layer.

If the needed change affects project facts, project decisions, tickets, roadmap, commands, terminology, or implementation constraints, update the project-owned artifact.

## Apply Changes To The Correct Layer

Changes should be applied to the correct layer.

Running context, ADRs, governance, roles, skills, workflows, templates, and project-specific artifacts each have distinct update responsibilities.

Do not move behaviour between layers just because the nearby file is convenient.

## Preserve Architectural Boundaries

Updates must preserve the current ResolveOS architecture:

- roles own responsibilities and authority
- skills own reusable task methods
- workflows own process sequence
- templates own communication structure
- context files own loading, precedence, current-state, and missing-context handling
- governance owns system rules
- ADRs own durable architecture decisions
- project repositories own project-specific facts and doctrine

## Do Not Let Important Context Drift

When planning, ticketing, roadmap, architecture, implementation, review, migration, or governance work reveals persistent context that has changed, flag the update need.

If an update is needed, explicitly identify:

- which file or source should be updated
- why it should be updated
- whether the update is immediate, next task, when convenient, or optional
- who owns the update

Use concrete timing labels. Do not describe urgency only as vague levels like low, medium, or high.

## Preserve Reviewability

Updates should be reviewable.

Prefer small, focused changes. Do not create broad rewrites or mixed-purpose updates unless the batch explicitly approves them.

When update impact is uncertain, report the uncertainty rather than changing multiple layers defensively.

# Layer Ownership

| Layer | Owns | Must Not Own |
| --- | --- | --- |
| `00-system/` | file standards, metadata standards, operating principles, migration strategy | project doctrine, role behaviour, workflow sequence |
| `01-context/` | loading order, startup assumptions, running state, missing context, role/project loading | role responsibility, skill method, project facts |
| `02-roles/` | reusable role purpose, responsibilities, authority, escalation, anti-patterns | skill procedures, workflow sequence, templates, project doctrine |
| `03-skills/` | reusable task methods | role authority, workflow sequence, report templates, project commands |
| `04-templates/` | communication and prompt structures | behaviour definitions, approval authority, workflow sequence |
| `05-workflows/` | multi-step process sequence | role authority, skill method detail, project-specific commands |
| `06-governance/` | system rules, source ownership, update rules, decision reporting, architecture decisions | project facts, ticket status, implementation reports |
| project repositories | product vision, roadmap, active tickets, project decisions, commands, architecture, local constraints | global ResolveOS behaviour unless reviewed and promoted |

# When To Update Running Context

Update running context when current working state materially changes.

Use running context for:

- current phase
- current state
- recently completed work
- active work
- open decisions
- active risks
- current recommendations
- do-not-repeat lessons
- source-of-truth references for current work

Running context is current-state context only.

Do not use running context for:

- historical changelogs
- durable architecture decisions
- detailed migration history
- project-specific current focus
- source-system status
- implementation reports

Replace stale current-state items instead of appending a long history.

# When To Update ADRs

Update ADRs when a durable architecture decision affects:

- reusable ResolveOS behaviour
- migration boundaries
- source ownership
- role/skill/workflow/template separation
- context-loading architecture
- governance architecture
- future file creation
- global/project ownership rules

ADRs preserve decisions, rationale, impact, and source references.

Do not use ADRs for:

- temporary current state
- routine implementation status
- ticket history
- changelogs
- project-specific decisions unless they affect ResolveOS globally

If a decision is durable but not architecture-level, use a decision log or project-owned decision record instead.

# When To Update Governance

Update governance when the change defines or changes a system rule.

Governance should own:

- source-of-truth rules
- update process
- duplication control
- Codex execution constraints
- decision-maker reporting
- extraction and migration guardrails
- architecture decisions
- review and enforcement rules

Governance should not absorb role behaviour, skill methods, workflow steps, or template structure.

If governance reveals missing role, skill, workflow, or template behaviour, defer that behaviour to the correct layer.

# When To Update Roles

Update role files when reusable role behaviour changes.

Role updates may be needed when:

- responsibilities change
- decision authority changes
- escalation boundaries change
- role anti-patterns change
- source evidence clarifies role behaviour
- a role boundary conflict needs preservation

Do not update a role file to add a full skill method, workflow sequence, template structure, project-specific doctrine, project commands, or ticket status.

Specialist roles must not be flattened during updates.

# When To Update Skills

Update skill files when a reusable task method changes.

Skill updates may be needed when:

- the process for a task changes
- inputs or outputs change
- anti-patterns for the method change
- examples need to preserve clearer source guidance
- repeated method guidance needs a canonical home

Do not update skills to grant role authority, define workflow sequence, create templates, or store project-specific commands.

# When To Update Workflows

Update workflows when a multi-step operating process changes.

Workflow updates may be needed when:

- trigger conditions change
- required inputs change
- process steps change
- handoff points change
- review points change
- failure modes change

Do not update workflows to redefine role authority, skill methods, template structures, or project-owned commands.

Project-specific workflows remain project-owned unless reviewed and promoted as reusable ResolveOS workflows.

# When To Update Templates

Update templates when a reusable communication, prompt, briefing, report, or log structure changes.

Template updates may be needed when:

- a report needs a new review surface
- a prompt needs a new reference field
- a handoff needs a clearer structure
- decision-maker reviewability requires a missing section
- source traceability needs to be made visible

Templates implement behaviour. They do not define it.

If a template reveals missing behaviour, update or create the correct role, skill, workflow, context, or governance file in a separate approved batch.

# When To Update Project Artifacts

Update project artifacts when the change is project-specific.

Project repositories own:

- product vision
- product strategy
- roadmap
- project decisions
- active tickets
- current focus
- project architecture decisions
- source-system status
- domain terminology
- project-specific workflows
- project-specific commands
- environment configuration
- provider configuration
- deployment targets
- release notes and changelogs

Do not migrate project-specific facts into ResolveOS just because a project file needs an update.

When project context changes, update the project-owned source rather than creating a ResolveOS global rule.

# Change Propagation Rules

When a change affects multiple files:

1. Identify the canonical source of ownership.
2. Update the canonical source first.
3. Identify derived references, examples, templates, prompts, or project consumers that may need alignment.
4. Update derived files only when the batch scope allows it.
5. If alignment is needed but out of scope, report it as deferred work.
6. Do not silently make broad updates across layers.

When a rule appears in multiple files:

- preserve the strongest wording in the canonical source
- keep necessary local reminders only where they protect reviewability or safety
- replace unnecessary duplication with references when a cleanup batch approves it
- do not remove wording-sensitive rules until duplication-control governance exists and the cleanup is reviewed

When source material conflicts:

- apply the migration priority for the current batch
- prefer existing ResolveOS governance and context over older source material
- flag contradictions rather than silently choosing the easier source
- defer uncertain ownership for admin review

# Review Expectations

Review is required before:

- changing global standards
- changing source-of-truth rules
- changing context-loading behaviour
- changing role authority or role boundaries
- changing skill method semantics
- changing workflow sequence
- changing template ownership boundaries
- changing ADR decisions
- promoting project-specific doctrine into ResolveOS
- removing duplicated high-value rules
- refactoring project repositories to depend on ResolveOS

Completion reports for update work should identify:

- files created or updated
- source sections used
- ownership decisions made
- deferred update needs
- ambiguity requiring admin review
- contradictions found
- validation performed or not performed

# Anti-Patterns

Do not:

- update the nearest file instead of the owning file
- duplicate behaviour instead of updating the source of ownership
- move role behaviour into templates
- move skill methods into governance
- move workflow sequence into roles
- move project doctrine into ResolveOS
- use running context as a changelog
- use ADRs for routine implementation status
- use templates to create approval authority
- silently update multiple layers without review
- remove repeated high-value rules before duplication-control governance exists
- let documentation drift from reality
- infer project-specific updates from memory
- treat migration reports as current state
- refactor ResolvePM before ResolveOS ownership and cleanup rules are reviewed

# Notes

This file intentionally defines update ownership and propagation only.

Deferred because they belong elsewhere:

- detailed duplication cleanup rules belong in future `06-governance/duplication-control.md`
- dependency progression belongs in a future dependency-management skill or governance decision
- source-tracker posting rules belong in a future source-tracker handoff template, workflow, or project-owned process
- project-specific update locations belong in project repositories
- exact release-note or changelog formats remain project-specific until proven reusable

Admin review is needed for:

- whether every project should define a standard local update-process override
- whether running context should be added to global startup loading rules in a dedicated context batch
- whether update timing labels should be exactly `Immediate`, `Next Task`, `When Convenient`, and `Optional`
- whether historical Codex prompt artifacts should remain under `05-workflows/` or move to a migration/prompt location later

What this governance must not do:

- create templates
- create skills
- create workflows
- create roles
- replace source-of-truth rules
- replace architecture decisions
- replace running context
- define project-specific update procedures
- promote ResolvePM project doctrine into ResolveOS
