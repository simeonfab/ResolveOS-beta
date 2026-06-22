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
