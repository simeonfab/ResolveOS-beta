---
type: governance
scope: global
owner: ResolveOS
version: 0.1
status: draft
source_project: ResolvePM
source_files:
  - migration-review.md
  - migration/resolvepm-residual-audit.md
  - migration/resolvepm-extraction-map.md
  - migration/resolvepm-extraction-audit.md
  - AGENTS.md.backup
  - docs/project-context/implementation-workflow.md
  - docs/ai-roles/implementation-engineer.md
  - docs/ai-roles/technical-strategy-lead.md
  - docs/ai-core/operational-clarity-framework.md
related_roles:
  - 02-roles/product-manager.md
  - 02-roles/business-analyst.md
  - 02-roles/qa-tester.md
  - 02-roles/technical-strategy-lead.md
  - 02-roles/implementation-engineer.md
  - 02-roles/strategic-product-director.md
related_skills:
  - 03-skills/completion-reporting.md
  - 03-skills/ticket-writing.md
  - 03-skills/acceptance-criteria.md
  - 03-skills/user-feedback-processing.md
related_workflows:
  - 05-workflows/ticket-to-implementation.md
  - 05-workflows/implementation-review-loop.md
  - 05-workflows/feedback-to-ticket.md
related_governance:
  - 00-system/ai-operating-principles.md
  - 06-governance/codex-working-rules.md
  - 06-governance/source-of-truth-rules.md
  - 06-governance/architecture-decisions.md
review_required: true
---

# Purpose

Define the ResolveOS reporting philosophy that makes technical work understandable, reviewable, and challengeable by non-technical decision-makers.

ResolveOS reporting should support human review, validation, prioritisation, and decision-making. Technical detail should remain available, but it should not be the only reporting layer.

This file is governance. It is not a completion report template, blocker report template, ticket prompt template, skill, workflow, role, or executive-summary format.

Source references:

- `03-skills/completion-reporting.md` > completion reporting principles and outputs
- `05-workflows/ticket-to-implementation.md` > completion reporting
- `05-workflows/implementation-review-loop.md` > reviewability and drift handling
- `AGENTS.md.backup` > ticket startup, implementation drift, blocker, and completion response formats
- `migration/resolvepm-residual-audit.md` > residual template value and completion-report risk
- `migration-review.md` > migration strengths, duplication, and remaining candidates

# When To Use

Use this governance when reporting:

- completed work
- partial work
- failed work
- blocked work
- implementation drift
- validation or QA results
- risks and trade-offs
- recommendations
- follow-up work
- migration batches
- reviews
- decisions
- changes that need admin or stakeholder judgement

Use this when a report may be read by a product-minded, non-technical, or decision-making audience that needs to understand what happened and what to decide next.

# Reporting Principles

## Decision-Maker Context Where Appropriate

When reporting work, reviews, blockers, recommendations, implementations, risks, or changes, include decision-maker context where appropriate.

Explain:

- what problem is being solved
- what was actually done
- why it matters
- whether the outcome differs from the original intent
- what the decision-maker should consider next

Source references:

- ADR-036 in `06-governance/architecture-decisions.md`
- `AGENTS.md.backup` > `What I think we are achieving`, `What was achieved`, `Why it matters`, `Did this differ from the original plan?`

## Truth Before Framing

Decision-maker reporting must not soften or hide reality.

Do not claim work was done unless it was actually done.

Do not imply validation, testing, deployment, commit, source-ticket update, storage, approval, or completion happened unless there is direct evidence.

Source references:

- `00-system/ai-operating-principles.md` > truthfulness and implementation honesty
- `03-skills/completion-reporting.md` > truthfulness before fluency
- `06-governance/codex-working-rules.md` > do not invent implementation claims

## Plain English Before Dense Technical Detail

Start with the decision-maker layer when the output is meant for review.

Use plain English to explain the intent, outcome, impact, risk, uncertainty, and next step.

Technical details should remain available after the decision-maker layer or alongside it when they are needed to verify the claim.

Source references:

- `00-system/ai-operating-principles.md` > plain-English communication
- `AGENTS.md.backup` > explain the outcome in plain English
- `02-roles/implementation-engineer.md` > simple enough for a non-expert product-minded admin to follow

## Reviewable And Challengeable

Reports should make the work reviewable.

A reviewer should be able to challenge:

- whether the work matched the original intent
- whether the acceptance criteria are still satisfied
- whether the reported validation proves enough
- whether blockers or risks remain
- whether follow-up work is separate from completed scope
- whether technical decisions changed product, requirement, delivery, or validation meaning

Source references:

- `03-skills/completion-reporting.md` > preserve reviewability
- `05-workflows/implementation-review-loop.md` > reviewability
- `migration-review.md` > traceability and completion honesty duplication

## Both Layers Matter

Do not reduce reporting to purely technical output.

Do not reduce reporting to an executive summary that hides technical evidence.

Keep both layers:

- decision-maker context for understanding and judgement
- technical evidence for verification and auditability

# Decision-Maker Context

Decision-maker context explains why the technical work matters to the human reviewing it.

It should answer the practical review questions:

- What were we trying to achieve?
- What actually happened?
- Why does this matter?
- Did reality differ from the plan?
- What is still uncertain, risky, blocked, partial, or deferred?
- What decision or next action is needed?

Use decision-maker context when technical facts alone would leave the admin or stakeholder unable to judge whether the work is acceptable, risky, incomplete, strategically relevant, or ready for follow-up.

# Required Reporting Layers

Use only the layers that fit the report, but do not omit an important layer just because it is not technical.

## 1. Intent Layer

Explain the original intent, goal, ticket, task, review question, or problem being solved.

Preserved source concepts:

- `What I think we are achieving`
- ticket, task, or scope
- goal
- why it matters
- assumptions

## 2. Outcome Layer

Explain what was actually done or found.

Preserved source concepts:

- `What was achieved`
- implementation path
- validation result
- review result
- current status

## 3. Difference Layer

Explain whether the result differs from the original plan, ticket, acceptance criteria, or expected path.

Preserved source concepts:

- `Did this differ from the original plan?`
- original plan
- what actually happened
- why it changed
- impact
- follow-up needed

## 4. Risk And Uncertainty Layer

Explain known issues, blockers, failed checks, missing context, assumptions, uncertainty, and residual risk.

Preserved source concepts:

- known issues
- blockers
- checks not run
- not verified
- partial or blocked status
- first clear failure where available

## 5. Recommendation Layer

Explain what should happen next.

Preserved source concepts:

- suggested follow-up tickets
- suggested documentation updates
- next recommended ticket
- highest-leverage follow-up action
- admin-review question

## 6. Evidence Layer

Provide enough technical detail to support review.

Evidence may include files changed, commands run, checks not run, validation performed, exact blocker, changed source context, defect evidence, or source references.

Technical evidence should support the decision-maker layer. It should not replace it.

# Technical Versus Business Reporting

Technical reporting answers:

- what files changed
- what commands ran
- what checks passed or failed
- what implementation path was used
- what error appeared
- what dependency or schema issue exists

Decision-maker reporting answers:

- what problem this relates to
- why the change matters
- whether the result satisfies the intent
- what trade-off or risk exists
- what still needs decision, review, or follow-up

Both are needed for serious work.

If the output contains only commands, file names, stack traces, or implementation facts, it may be technically detailed but not decision-maker reviewable.

If the output contains only business summary with no evidence, it may be readable but not auditable.

# Explaining Intent

Explain intent before reporting details when the reader needs context.

Good intent reporting identifies:

- the task, ticket, source item, batch, or review question
- what the work was trying to achieve
- why the work mattered
- relevant scope or non-goals
- important assumptions

Do not invent intent. If the intent was unclear, say so and identify the missing context.

# Explaining Outcomes

Explain outcomes as actual state, not aspiration.

Outcome reporting should distinguish:

- completed work
- partial work
- failed work
- blocked work
- not verified work
- deferred work
- recommendations that were not implemented

Do not use polished wording to make partial, blocked, failed, or unverified work sound complete.

# Explaining Impact

Explain impact when it affects review, acceptance, prioritisation, stakeholder meaning, product scope, delivery sequencing, validation, or future work.

Impact may include:

- user-facing impact
- product-scope impact
- requirement or acceptance impact
- validation impact
- delivery or sequencing impact
- architecture or dependency impact
- documentation impact
- cost, security, deployment, or operational risk

Do not exaggerate impact. If impact is unknown, say it is unknown and explain what would be needed to know.

# Explaining Deviations

When work differs from the original plan, explain the drift.

Use the preserved ResolvePM concepts:

- original plan
- what actually happened
- why it changed
- impact
- follow-up needed

If the drift affects acceptance criteria, do not mark the work complete unless the criteria are still satisfied.

If the drift changes product meaning, requirement meaning, sequencing, architecture, validation, or strategy, escalate to the accountable role.

Source references:

- `AGENTS.md.backup` > implementation drift format
- `05-workflows/implementation-review-loop.md` > implementation drift handling
- `02-roles/implementation-engineer.md` > implementation drift reporting

# Explaining Risk And Uncertainty

Risk and uncertainty must be visible.

Explain:

- what is known
- what is missing
- what is inferred
- what is not verified
- what is blocked
- what could fail later
- what decision or context would reduce the uncertainty

Do not hide uncertainty behind confidence.

Do not bury blockers, failed checks, missing context, known issues, or risk inside vague summaries.

Source references:

- `00-system/ai-operating-principles.md` > explicit uncertainty
- `01-context/missing-context-behaviour.md` > explicit uncertainty and blocker handling
- `05-workflows/implementation-review-loop.md` > failed validation and missing context handling

# Explaining Recommendations

Recommendations should be separate from completed work.

When recommending next steps, explain:

- what is recommended
- why it is separate from completed scope
- whether it is required, optional, blocked, or deferred
- what role or decision-maker should review it
- what source evidence supports it

Do not imply recommended follow-up work was implemented.

Do not convert recommendations into current scope without admin approval or an established workflow.

Source references:

- `03-skills/completion-reporting.md` > reporting follow-up work
- `05-workflows/feedback-to-ticket.md` > review outcomes and scope control
- `06-governance/codex-working-rules.md` > work one ticket or batch at a time

# Anti-Patterns

Do not:

- report only technical details when a decision-maker needs context
- provide an executive-style summary that hides evidence, blockers, failed checks, or uncertainty
- claim success when status is unknown
- bury known issues in vague language
- present partial, blocked, failed, or unverified work as complete
- omit why the work matters when impact is needed for review
- omit whether the outcome differed from the original intent when drift occurred
- omit next-step guidance when a decision, blocker, risk, or follow-up remains
- mix recommendations into completed work
- make follow-up work look implemented
- turn this governance into a completion report template
- create role, skill, workflow, or template behaviour inside this governance file

# Examples

Decision-maker layer with technical evidence:

```text
Intent:
The work was meant to make the current ticket ready for implementation.

Outcome:
The scope is clearer, but acceptance criteria are still missing.

Why it matters:
Implementation would require guessing what success looks like.

Decision needed:
Admin should confirm the missing acceptance criteria before implementation starts.

Evidence:
The loaded ticket context includes goal and scope, but no acceptance criteria section.
```

Blocked reporting:

```text
Problem:
The requested implementation depends on source context that is not available.

Current state:
No safe implementation change was made.

Risk:
Continuing would require invented requirements or fake completion.

Next step:
Provide the missing source item or approve a clearly limited draft.
```

Drift reporting:

```text
Original intent:
The ticket expected one implementation path.

What changed:
Repository reality required a smaller safe path.

Impact:
Acceptance criteria still need review before completion can be claimed.

Follow-up:
Create or review a follow-up ticket if the original path remains required.
```

These are examples of reporting philosophy. They are not canonical templates.

# Related Roles

- `02-roles/product-manager.md`
- `02-roles/business-analyst.md`
- `02-roles/qa-tester.md`
- `02-roles/technical-strategy-lead.md`
- `02-roles/implementation-engineer.md`
- `02-roles/strategic-product-director.md`

# Related Skills

- `03-skills/completion-reporting.md`
- `03-skills/ticket-writing.md`
- `03-skills/acceptance-criteria.md`
- `03-skills/user-feedback-processing.md`

Future related skills may include:

- implementation review
- risk assessment
- decision-log writing
- debugging support

# Related Workflows

- `05-workflows/ticket-to-implementation.md`
- `05-workflows/implementation-review-loop.md`
- `05-workflows/feedback-to-ticket.md`

# Related Governance

- `00-system/ai-operating-principles.md`
- `01-context/missing-context-behaviour.md`
- `06-governance/codex-working-rules.md`
- `06-governance/source-of-truth-rules.md`
- `06-governance/architecture-decisions.md`

# Deferred Items

Deferred because they belong in future templates, roles, skills, or workflows:

- exact completion report template
- exact blocker report template
- exact ticket-context prompt template
- exact source-tracker comment format
- role-specific reporting obligations beyond references to existing roles
- implementation-review skill details beyond governance principles
- risk-assessment skill details
- decision-log-writing skill details
- project-specific report formats, source-system fields, commands, ticket keys, routes, or deployment details

# Candidate Files Requiring Future ADR-036 Alignment

Future work should review these files for ADR-036 alignment when they are created or updated:

- `04-templates/completion-report-template.md`
- `04-templates/blocker-report-template.md`
- `04-templates/ticket-context-template.md`
- `04-templates/briefing-template.md`
- `04-templates/decision-log-template.md`
- `03-skills/implementation-review.md`
- `03-skills/risk-assessment.md`
- `03-skills/debugging-support.md`
- `03-skills/decision-log-writing.md`
- `06-governance/update-process.md`
- `06-governance/duplication-control.md`

# Ambiguous Items For Admin Review

Admin review is needed for:

- Whether all future templates must include a decision-maker context layer by default or only when the task is review-facing.
- Whether completion reports should always include `why it matters` or only when useful for decision-making.
- Whether decision-maker reporting should become part of `completion-reporting.md` later, or remain governance inherited by templates and workflows.
- Whether stakeholder-facing reporting needs stricter language than admin-facing reporting.
- Whether ADR-035 should be reserved, restored, or left absent.

# What This Governance Must Not Do

This governance must not:

- create templates
- create skills
- create workflows
- create roles
- replace `03-skills/completion-reporting.md`
- replace `05-workflows/implementation-review-loop.md`
- define project-specific report formats
- make technical detail optional where verification requires it
- weaken implementation honesty or explicit uncertainty
