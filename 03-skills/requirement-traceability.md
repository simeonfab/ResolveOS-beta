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
