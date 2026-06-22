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
