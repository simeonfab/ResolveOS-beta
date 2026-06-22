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
