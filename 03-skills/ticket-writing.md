---
type: skill
scope: global
owner: ResolveOS
version: 0.1
status: draft
source_project: ResolvePM
source_files:
  - migration/resolvepm-extraction-audit.md
  - migration/resolvepm-extraction-map.md
related_context:
  - 00-system/ai-operating-principles.md
  - 01-context/context-loading-rules.md
  - 01-context/startup-context.md
related_governance:
  - 06-governance/codex-working-rules.md
  - 06-governance/extraction-migration-guardrails.md
  - 06-governance/source-of-truth-rules.md
review_required: true
---

# Ticket Writing

## Purpose

Define the canonical ResolveOS skill for writing and refining implementation tickets.

This skill preserves reusable ticket-writing guidance extracted from ResolvePM. It is not generic Agile guidance. It exists to keep ticket work clear, scoped, sequenced, implementation-ready, testable, and honest about blockers, assumptions, non-goals, and production constraints.

Source references:

- Extraction map: `Global Ticket Writing Rules`
- Extraction map: `Proposed ResolveOS File Inventory`
- Audit: `Global Ticket Writing Rules`
- Audit: `Global Skill Candidates`

## When To Use

Use this skill when creating, reviewing, refining, splitting, or preparing tickets for implementation.

Use it for:

- implementation tickets
- prerequisite tickets
- follow-up tickets
- blocker resolution tickets
- ticket sequence planning
- ticket readiness review
- ticket prompts for implementation agents

Do not use this skill to create product roadmap direction, role behaviour, full completion report templates, or project-specific feature decisions unless those inputs already exist in the relevant project context.

Source references:

- Extraction map: `Global Ticket Writing Rules`
- Extraction map: `Global Context Loading Rules`
- ResolveOS: `06-governance/source-of-truth-rules.md`

## Inputs

Before writing or refining a ticket, gather the available source context:

- ticket key or source item identifier, when one exists
- title
- goal
- scope
- acceptance criteria
- implementation notes
- manual test steps
- relevant comments or blocker notes
- related briefing, epic, or current focus
- relevant project context
- known dependencies and prerequisites
- known non-goals
- current repository or implementation constraints, when implementation is near-term

If source-system access is unavailable, ask for the missing ticket description or relevant comments. Do not guess missing acceptance criteria.

Source references:

- Extraction table: `AGENTS.md.backup` read title, goal, scope, acceptance criteria, notes, comments, and manual test steps
- Extraction table: `AGENTS.md.backup` do not guess missing acceptance criteria
- Audit: `Global Ticket Writing Rules`

## Ticket Structure

Tickets should define:

- what is being achieved
- why it matters
- implementation scope
- assumptions
- dependencies
- sequencing notes
- non-goals where useful
- acceptance criteria
- implementation notes
- manual test steps
- documentation expectations, when relevant
- deployment or production considerations, when relevant

At minimum, a well-scoped implementation ticket should contain:

```text
Title:

Goal:

Background / Context:

Scope:

Out of Scope:

Assumptions:

Dependencies / Prerequisites:

Implementation Notes:

Acceptance Criteria:

Testing / Manual Test Steps:

Documentation Notes:

Deployment / Production Notes:
```

Use only the sections needed for the ticket. Do not over-format small tickets into heavy process documents.

Source references:

- Extraction table: `docs/project-context/implementation-workflow.md` tickets define outcome, value, scope, assumptions, dependencies, sequencing notes, non-goals
- Audit: `Global Ticket Writing Rules`
- Extraction map: `Global Ticket Writing Rules`

## Ticket Writing Process

### 1. Start From The Current Ticket Or Approved Scope

Ticket work must start from a ticket/source item or an explicitly approved scope.

Work one ticket at a time.

Do not start future tickets unless explicitly asked.

Do not start implementation from an epic alone if child implementation tickets are missing.

Source references:

- Extraction map: `Global Ticket Writing Rules`
- Extraction table: `AGENTS.md.backup` one ticket at a time
- Extraction table: `docs/codex-briefings/CP-7-knowledge-base.md` do not start implementation from epic alone

### 2. Confirm Understanding Before Writing Or Implementing

Before implementation, the ticket should make clear:

- what the ticket is trying to achieve
- why it matters
- how it fits into the larger project or workflow
- what assumptions are being made
- what dependencies or blockers exist

Ticket prompts and implementation handoffs should summarise this in plain English.

Source references:

- Extraction table: `AGENTS.md.backup` summarise task understanding before implementation
- Extraction map: `Global Communication Rules`
- Audit: `Global User Working Preferences`

### 3. Keep Scope Small, Safe, And Reversible

Prefer:

- small tickets
- clear scope
- reversible changes
- explicit sequencing

Avoid:

- massive implementation tickets
- unclear scope
- speculative implementation
- future scope bundling

If useful extra work is identified, do not add it silently to the current ticket. Add it as suggested follow-up work and explain why it should be separate.

Source references:

- Extraction table: `docs/project-context/implementation-workflow.md` small safe tickets
- Extraction table: `AGENTS.md.backup` useful extra work goes to suggested follow-up tickets
- Extraction map: `Global Working Preferences`

### 4. Define Sequencing And Dependencies

Tickets should identify prerequisites clearly.

If implementation reveals missing schema, architecture gaps, prerequisite work, or unsafe assumptions, suggest follow-up or prerequisite tickets.

If prerequisite work is missing, stop and identify the prerequisite before writing around it.

Do not retry a blocked dependent ticket until the prerequisite is complete.

Source references:

- Extraction table: `docs/project-context/implementation-workflow.md` sequencing matters
- Extraction table: `docs/codex-briefings/CP-5-roadmap.md` do not retry blocked dependent ticket until prerequisite is complete
- Audit: `Global Ticket Writing Rules`

### 5. Keep Prompts Short When Persistent Context Exists

Per-ticket prompts should stay short by default when the ticket and project context already exist.

Do not repeat full persistent context in every ticket prompt. Reference the relevant role, project context, briefing, and ticket instead.

Ask for a longer prompt only when:

- important scope is missing
- comments reveal a blocker that needs clarification
- the ticket contradicts the current repo state
- the ticket is unusually risky
- the admin is asking for work outside the ticket

Source references:

- Extraction table: `AGENTS.md.backup` keep per-ticket prompts short
- Extraction map: `Global Context Loading Rules`
- Audit: `Context Loading Rules Found`

## Acceptance Criteria Guidance

Acceptance criteria should describe observable completion conditions.

Use clear Given / When / Then wording where it improves precision:

```text
Given [starting condition],
When [user or system action happens],
Then [observable result is true].
```

Acceptance criteria should cover:

- expected user-visible behaviour
- important data persistence or state changes
- empty states where relevant
- error states where relevant
- permission, security, or configuration constraints where relevant
- build, test, or deployment gates where relevant

Do not guess missing acceptance criteria. If acceptance criteria are missing or contradicted by implementation reality, flag the gap for admin review or write a draft clearly marked for review.

If implementation drift affects acceptance criteria, the ticket should not be marked complete unless the criteria are still satisfied.

Source references:

- Extraction table: `AGENTS.md.backup` do not guess missing acceptance criteria
- Extraction table: `AGENTS.md.backup` if drift affects acceptance criteria, do not mark complete unless criteria are still satisfied
- Extraction map: `Global Ticket Writing Rules`
- Audit: `Global Ticket Writing Rules`

## Testing Guidance

Every implementation ticket should include test or validation expectations.

Manual test steps should be simple enough for a non-technical admin to follow and should include:

- what to run
- what page or surface to open, if applicable
- what to click, type, inspect, or trigger
- what the admin should see
- what confirms success

Automated or command checks should be listed when relevant, but check names must remain project-overridable.

If a command or test is required for completion, the ticket should say so. If a check is unavailable, out of scope, or blocked, the ticket should make that clear.

Source references:

- Extraction table: `AGENTS.md.backup` manual testing format
- Extraction table: `AGENTS.md.backup` run appropriate checks after implementation
- Extraction map: `Global Ticket Writing Rules`
- ResolveOS: `06-governance/codex-working-rules.md`

## Documentation Guidance

Tickets should include documentation expectations when implementation may affect persistent project context, future tickets, setup, deployment, security posture, or user-facing instructions.

Do not let documentation drift from reality.

Documentation notes should identify:

- which document or context file may need updating
- why it may need updating
- whether the update is required for this ticket or can be follow-up work
- the specific wording or summary to add, when useful

Do not create heavy documentation requirements for small tickets unless the change affects future work, setup, production behaviour, or admin understanding.

Source references:

- Extraction table: `AGENTS.md.backup` do not let documentation drift from reality
- Audit: `Global User Working Preferences`
- Extraction map: `Duplicate Content Consolidation Plan`

## Production Considerations

Ticket-writing should identify production or deployment considerations when relevant.

Include production notes for:

- environment configuration
- paid AI/API usage
- security or privacy constraints
- data migrations
- deployment ordering
- prerequisite commits or pushes
- disabled states when configuration is missing
- real data versus mock/demo data

Do not ask implementers to fake paid API responses, fake integrations, fake data, or fake success states to satisfy a ticket.

For AI/API-backed work, tickets should preserve cost-safe behaviour:

- require explicit configuration before paid calls are enabled
- make paid calls user-triggered by default
- avoid automatic retry or regeneration loops
- provide honest disabled/error states when configuration is missing
- do not fake paid API responses as real output

Source references:

- Extraction table: `docs/ai-roles/implementation-engineer.md` cost-safe external API rules
- Extraction table: `docs/codex-briefings/CP-8-ai-updates.md` cost-safe AI workflow design
- Extraction map: `Global Working Preferences`
- ResolveOS: `00-system/ai-operating-principles.md`

## Blocker Handling

If a ticket is blocked:

- stop
- explain the blocker clearly
- explain why continuing would be unsafe or unsupported
- identify the smallest prerequisite fix
- suggest a new prerequisite ticket if needed

Do not silently work around blockers.

Do not invent schema, fake functionality, fake data, fake integrations, or fake success states to make a ticket appear complete.

If the ticket cannot be completed as written, the ticket should be updated or followed by a prerequisite/follow-up ticket rather than forcing implementation through unsafe assumptions.

Source references:

- Extraction table: `AGENTS.md.backup` blocker handling
- Extraction table: `docs/project-context/implementation-workflow.md` blocker behaviour
- Audit: `Risks / Things Not To Lose`
- ResolveOS: `00-system/ai-operating-principles.md`

## Outputs

This skill should produce tickets or ticket review notes that include:

- clear title
- goal
- background or context
- scoped implementation work
- explicit non-goals
- assumptions
- dependencies and prerequisites
- acceptance criteria
- testing expectations
- documentation expectations, when relevant
- production or deployment notes, when relevant
- blocker notes, when relevant
- suggested follow-up tickets, when useful

Outputs should be practical, implementation-ready, and reviewable.

Source references:

- Extraction map: `Global Ticket Writing Rules`
- Audit: `Global Skill Candidates`

## Anti-Patterns

Do not:

- write tickets from unsupported assumptions
- guess missing acceptance criteria
- hide dependencies
- hide blockers
- bundle unrelated future scope into the current ticket
- start implementation from an epic alone when child tickets are missing
- create massive implementation tickets when smaller safe tickets are possible
- write vague tickets that do not say what is being achieved or why it matters
- rely on fake functionality, fake data, fake integrations, or fake success states
- over-plan distant roadmap work too early
- replace specific admin ticket-writing rules with generic Agile wording
- create project-specific product doctrine in global ResolveOS tickets

Source references:

- Extraction map: `Assistant Anti-Patterns`
- Extraction map: `Global Ticket Writing Rules`
- Audit: `Global Assistant Anti-Patterns / Prohibited Behaviours`
- ResolveOS: `06-governance/extraction-migration-guardrails.md`

## Examples

### Example Ticket Skeleton

```text
Title:
[Short implementation outcome]

Goal:
[What this ticket achieves]

Background / Context:
[Why this is needed and what source context informs it]

Scope:
- [Specific implementation item]
- [Specific implementation item]

Out of Scope:
- [Explicit non-goal]
- [Future work not included]

Assumptions:
- [Assumption, or None]

Dependencies / Prerequisites:
- [Required prior work, schema, config, source, or decision]

Implementation Notes:
- [Relevant implementation guidance]
- [Existing pattern or helper to use, if known]

Acceptance Criteria:
- Given [starting condition], when [action], then [observable result].
- Given [error or empty condition], when [action], then [honest state is shown].

Testing / Manual Test Steps:
1. [What to run/open/do]
   Why: [What this proves]
2. [What to inspect]
   Why: [What this proves]

Documentation Notes:
- [File/context to update, or Not needed]

Deployment / Production Notes:
- [Config, migration, rollout, or disabled-state notes, or Not needed]
```

### Example Blocked Ticket Note

```text
Status:
Blocked

Current blocker:
[Specific missing prerequisite, context, credential, schema, decision, or implementation dependency]

Why continuing is unsafe:
[Why implementation would require guessing, fake functionality, or unsupported assumptions]

Highest-leverage unblocker or follow-up action:
[Prerequisite fix or admin decision needed]

Suggested prerequisite ticket:
[Ticket title or None]
```

Source references:

- Extraction table: `AGENTS.md.backup` ticket startup and blocker formats
- Extraction table: `docs/project-context/implementation-workflow.md` ticket and blocker rules

## Related Context

- `00-system/ai-operating-principles.md`
- `01-context/context-loading-rules.md`
- `01-context/startup-context.md`

## Related Governance

- `06-governance/codex-working-rules.md`
- `06-governance/extraction-migration-guardrails.md`
- `06-governance/source-of-truth-rules.md`

## Source Merge Notes

Multiple source variants were consolidated:

- The ticket structure rule uses the strongest general wording from `docs/project-context/implementation-workflow.md`, expanded with specific fields preserved from `AGENTS.md.backup` and the extraction map.
- One-ticket-at-a-time guidance uses repeated wording from `AGENTS.md.backup`, `implementation-workflow.md`, role prompts, and epic briefings.
- Blocker handling preserves the stronger stop-and-explain wording from `AGENTS.md.backup` and `implementation-workflow.md`.
- Testing guidance preserves `AGENTS.md.backup` manual testing details while keeping project-specific command names project-overridable.
- Production considerations preserve reusable cost-safe and real-state rules without copying ResolvePM-specific Supabase, Vercel, CP ticket, or roadmap details.

## Deferred Items

Deferred because they are out of scope for Batch 2A or require admin review:

- a standalone `acceptance-criteria.md` skill
- a standalone completion-reporting skill or template
- role-specific implementation behaviour
- ResolvePM CP ticket sequences
- ResolvePM product roadmap, product vision, or product terminology
- project-specific deployment commands, Supabase details, and Vercel details
- richer feedback-processing taxonomy
- exact completion report format from `AGENTS.md.backup`

## Ambiguous Items For Admin Review

- Whether completion reporting should become its own skill or template in a later batch.
- Whether Given / When / Then should be mandatory or only recommended when it improves precision.
- Whether check commands should be globally standardised or remain entirely project-overridable.
- Whether dependency commit-order rules belong in ticket writing, Codex governance, or a future implementation workflow.

## What This Skill Must Not Do

This skill must not:

- create or modify tickets automatically without admin instruction
- define role responsibilities
- define full acceptance-criteria or completion-reporting skills
- replace project-specific source-of-truth files
- promote ResolvePM product doctrine into global ResolveOS guidance
- invent ticket rules not supported by the extraction map or audit
