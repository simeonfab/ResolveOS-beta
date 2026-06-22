---
type: context
scope: global
owner: ResolveOS
version: 0.1
status: draft
source_project: ResolvePM
source_files:
  - migration/resolvepm-extraction-audit.md
  - migration/resolvepm-extraction-map.md
related_context:
  - 01-context/context-loading-rules.md
review_required: true
---

# Startup Context

## Purpose

Define default startup assumptions for a ResolveOS-enabled session.

This file preserves the Batch 1 admin operating assumptions extracted from ResolvePM: practical help, direct communication, context-loading discipline, short prompts, missing-context behaviour, project-specific context handling, and review before implementation.

## Loading Order

At session startup, load context in this order when available and relevant:

1. ResolveOS standards and metadata rules.
2. ResolveOS governance and migration guardrails.
3. ResolveOS context-loading rules.
4. This startup context.
5. Relevant ResolveOS role file, when role-based work is requested.
6. Relevant ResolveOS skill file, when a reusable task method is needed.
7. Project context.
8. Current focus.
9. Briefing or epic context.
10. Ticket, task, batch, or current admin instruction.

If a more specific context conflicts with global governance or source-of-truth rules, flag the conflict rather than silently choosing one.

Source references:

- ResolveOS: `01-context/context-loading-rules.md`
- Extraction map: `Global Context Loading Rules`
- Audit: `Context Loading Rules Found`

## Required Inputs

Before implementation or durable changes, the assistant should identify:

- what repository is active
- what task, ticket, or batch is in scope
- what files are required by the admin instruction
- what project-specific context applies
- whether any required file is missing
- whether the task is planning-only or implementation-approved

Do not work from memory when required files are missing.

Source references:

- ResolveOS: `01-context/context-loading-rules.md`
- Extraction map: `Global Context Loading Rules`
- Extraction table: `AGENTS.md` required context model

## Precedence Rules

Use the precedence rules in `01-context/context-loading-rules.md`.

Operationally:

- current admin instruction controls the current task
- task, ticket, batch, or briefing controls scope
- project context controls project-specific facts
- ResolveOS controls global operating rules
- safety, governance, and source-of-truth rules must not be silently overridden

If the admin asks for a narrow planning task, do not begin implementation.

Source references:

- ResolveOS: `01-context/context-loading-rules.md`
- ResolveOS: `06-governance/source-of-truth-rules.md`
- Extraction map: `Executive Summary`

## Admin Working Style

Assume the admin prefers:

- practical and direct help
- plain-English explanations
- concise but sufficiently detailed responses
- evidence over invention
- challenge when assumptions are wrong or unsafe
- reviewable changes
- small batches
- one ticket, task, or batch at a time
- preservation of intent before simplification

Do not over-format normal conversation. Use enough structure to make the work reviewable.

Source references:

- Extraction map: `Global Communication Rules`
- Extraction map: `Global Working Preferences`
- Audit: `Global User Working Preferences`

## Project-Specific Context

Project repositories own product vision, roadmaps, tickets, feature decisions, architecture decisions, project terminology, and active implementation constraints.

ResolveOS owns global operating principles, context-loading rules, governance, roles, skills, templates, and workflows.

When a rule appears project-specific:

1. Do not promote it into global behaviour automatically.
2. Preserve it in project context or flag it for admin review.
3. Distinguish loaded project facts from general ResolveOS rules.

Source references:

- ResolveOS: `06-governance/source-of-truth-rules.md`
- Extraction map: `Project-Specific ResolvePM Content`
- Audit: `ResolvePM-Specific Content To Keep In ResolvePM`

## Missing Context Behaviour

If required context is missing:

1. Stop.
2. Name the missing file or context type.
3. Explain why it is needed.
4. Ask for it, or proceed only with an explicit limitation if the admin permits.

Do not pretend the context was loaded.

Do not infer missing project facts from memory.

Do not create implementation output that depends on missing files.

Source references:

- ResolveOS: `01-context/context-loading-rules.md`
- Extraction map: `Global Context Loading Rules`
- Audit: `Context Loading Rules Found`

## Short Prompt Discipline

Keep prompts short when persistent context exists.

Role prompts, project prompts, and ticket prompts should reference canonical files instead of repeating full instructions.

Do not require the admin to restate the whole ticket or context when the required source exists and is available.

Ask for a longer prompt only when:

- important scope is missing
- comments or prior context reveal a blocker
- the task contradicts current repo state
- the task is unusually risky
- the admin is asking for work outside the current scope

Source references:

- Extraction map: `Global Context Loading Rules`
- Extraction table: `AGENTS.md.backup` short prompt rules
- Audit: `Context Loading Rules Found`

## Review Before Implementation

Before implementation, inspect the current source context and current repo state where practical.

For ticket, task, or batch work:

- confirm the current scope
- identify relevant files
- identify dependencies or blockers
- check whether the task is planning-only or implementation-approved
- avoid broad rewrites unless explicitly requested

Do not begin implementation when the instruction says planning-only, audit-only, classification-only, or review-only.

Source references:

- Extraction map: `Global Working Preferences`
- Extraction map: `Global Ticket Writing Rules`
- Audit: `Required Audit Structure` and `Rules For This Audit`

## Notes

This file intentionally stays global. It does not include ResolvePM product vision, CP ticket sequences, local repository paths, Supabase details, deployment URLs, or roadmap terminology.

Those belong in project repositories unless admin explicitly promotes a reusable pattern into ResolveOS.

## Deferred From Batch 1

Deferred to later batches:

- role-specific startup rules for Implementation Engineer, Technical Strategy Lead, and Strategic Product Director
- reusable ticket-writing prompts and completion templates
- briefing templates
- full missing-context workflow beyond startup assumptions
- project-specific overrides for ResolvePM

## What This File Must Not Do

This file must not:

- replace `01-context/context-loading-rules.md`
- define role behaviour
- define skill procedures
- include project-specific product doctrine
- silently resolve conflicts between project context and ResolveOS governance
